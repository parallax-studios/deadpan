# DEADPAN — Technical Architecture Document

**Project**: DEADPAN — Stand-up Comedy Empire Simulation
**Architect**: BYTE
**Status**: Production Architecture — Ready for Prototype Build
**Target Platform**: PC (Steam Primary), Nintendo Switch (Secondary), Mobile (Stretch)
**Estimated Development Time**: 18-24 months to 1.0 release

---

## 1. Executive Summary

DEADPAN is a comedy empire simulation with two core technical challenges: (1) a deep, combinatorial joke construction system that must feel like creative writing, not data entry, and (2) a reactive audience AI that must feel predictable enough to learn from but dynamic enough to never feel solved.

Ship it in layers. Prototype the 30-second loop first. If the Bit Builder + Crowd Engine + Laugh Graph feels good in isolation, the game works. Everything else — career progression, scene AI, economy — is scaffolding around that core.

The architecture is designed for rapid iteration. Component-based systems throughout. Clear data/logic separation. Aggressive use of scriptable data for tuning. The Crowd Engine needs 50+ hours of balancing. We're not guessing our way there — we're building observability and tuning tools from day one.

**Key Technical Risks**:
- Bit Builder UI feels like a spreadsheet instead of a creative tool (risk level: HIGH)
- Crowd Engine reactions feel random instead of legible (risk level: VERY HIGH)
- Late-game content generation can't keep pace with player consumption (risk level: MEDIUM)
- Performance at scale: simulating 2000+ audience members in real-time (risk level: MEDIUM)

**Core Technical Bet**: The Crowd Engine is a deterministic simulation, not an ML model. We're not using LLMs to generate jokes or predict reactions. This is a rules-based system with legible outputs. The player must understand WHY a joke bombed. Black-box AI kills the loop.

---

## 2. Engine and Framework Selection

### Recommendation: Unity (C#)

**Rationale**:

1. **UI Complexity**: The Bit Builder, Laugh Graph, and career management screens are UI-heavy. Unity's UI Toolkit (or legacy Canvas system) handles this better than any 2D-specific engine. We're building a game that lives in menus and data visualization as much as it lives on stage.

2. **Cross-Platform**: PC, Switch, and Mobile from one codebase. Unity's input system abstraction handles mouse, controller, and touch with minimal branching. The Switch port isn't an afterthought — it's a design constraint.

3. **Asset Pipeline**: The game is 60% data (component cards, audience archetypes, venue definitions, AI comedian profiles). Unity's ScriptableObject system is purpose-built for this. Designers can create and balance content without touching code.

4. **Team Access**: Unity has the broadest hiring pool. If we need to scale the team mid-development, C# + Unity developers are everywhere. Godot would be leaner but the talent pool is 1/10th the size.

5. **Performance**: This isn't a physics-heavy game. The Crowd Engine is the only computationally expensive system, and it's easily optimized (burst compiled jobs for reaction calculations). Unity handles our perf requirements with room to spare.

**What We're NOT Using**:

- **Unreal Engine**: Overkill. We don't need physically-based rendering or nanite. The visual style is warm, stylized, and 2D-focused. Unreal's strengths don't map to our needs. Also, Blueprint is a nightmare for data-driven systems.
- **Godot**: Strong candidate, but the Switch export is still immature (as of 2025). The mobile export is better than Unity's, but we can't risk the Switch port on a less proven path.
- **Custom Engine**: Absolute non-starter. We learned this lesson. The game never ships.

### Core Libraries and Middleware

| System | Library | Rationale |
|--------|---------|-----------|
| **UI Framework** | Unity UI Toolkit | Modern, performant, supports runtime + editor tools. The Laugh Graph needs SVG-like vector rendering. UI Toolkit's vector API is purpose-built for this. |
| **Data Serialization** | Unity ScriptableObjects + JSON.NET | ScriptableObjects for design-time data (component cards, venues, archetypes). JSON for save files and runtime-generated content (player jokes, AI comedian states). |
| **State Management** | Custom FSM (Finite State Machine) | Career progression, performance flow, UI navigation. Simple enough to hand-roll. State pattern with ScriptableObject-based state definitions. |
| **Audio** | FMOD or Wwise | Procedural crowd audio is 50% of the game feel. Canned laughter loops will kill immersion. We need layered audio with per-cluster control. FMOD's parameter-based mixing is the right tool. If budget is tight, Unity's AudioMixer with heavy scripting can work, but it's a worse dev experience. |
| **Analytics** | Unity Analytics + Custom Event Pipeline | Track Bit Builder usage patterns, Laugh Graph interpretation, setlist construction decisions. We need telemetry to balance the Crowd Engine. Ship a custom event recorder that dumps JSON logs locally during playtesting. |
| **Localization** | Unity Localization Package | Text-heavy game. Component cards have 300+ unique text strings. The Localization package handles this cleanly. Start with English-only, but architect for localization from day one. Joke components are culturally specific — localization isn't just translation, it's cultural adaptation. That's a post-1.0 problem, but the tech needs to support it. |

---

## 3. Core Systems Architecture

### 3.1 Component Diagram

```
┌─────────────────────────────────────────────────────────────────┐
│                        GAME MANAGER (Singleton)                  │
│  - Session state (current tier, week, city)                     │
│  - Save/Load orchestration                                      │
│  - Scene transitions                                            │
└────────────┬────────────────────────────────────────────────────┘
             │
   ┌─────────┴─────────┬──────────────┬──────────────┬────────────┐
   │                   │              │              │            │
┌──▼────────┐  ┌───────▼──────┐  ┌───▼───────┐  ┌──▼──────┐  ┌──▼─────────┐
│ BIT       │  │  CROWD       │  │  LAUGH    │  │ VOICE   │  │  CAREER    │
│ BUILDER   │  │  ENGINE      │  │  GRAPH    │  │ IDENTITY│  │  MANAGER   │
│ SYSTEM    │  │  SYSTEM      │  │  SYSTEM   │  │ SYSTEM  │  │  SYSTEM    │
└───┬───────┘  └───┬──────────┘  └───┬───────┘  └──┬──────┘  └──┬─────────┘
    │              │                  │              │            │
    │   Joke       │  Reaction        │  Graph       │  Voice     │  Career
    │   Data       │  Data            │  Data        │  Shift     │  Events
    │              │                  │              │            │
┌───▼──────────────▼──────────────────▼──────────────▼────────────▼─────────┐
│                         DATA LAYER (ScriptableObjects)                     │
│  - Component Cards Library                                                │
│  - Audience Archetype Definitions                                         │
│  - Venue Configurations                                                   │
│  - AI Comedian Profiles                                                   │
│  - Career Tier Definitions                                                │
└────────────────────────────────────────┬───────────────────────────────────┘
                                         │
                      ┌──────────────────┴──────────────────┐
                      │                                     │
                 ┌────▼──────┐                     ┌────────▼────────┐
                 │  SAVE     │                     │  THE SCENE      │
                 │  SYSTEM   │                     │  (AI Comedians) │
                 └───────────┘                     └─────────────────┘
```

### 3.2 Data Flow: Performance Loop

```
1. SETLIST CONSTRUCTION
   Player -> BitBuilderUI -> JokeData[] -> SetlistData

2. VENUE SELECTION
   Player -> VenueSelectionUI -> VenueConfig -> CrowdEngine.Initialize()

3. PERFORMANCE START
   GameManager -> PerformanceController.StartSet(SetlistData, VenueConfig)
   PerformanceController -> CrowdEngine.GenerateCrowd(VenueConfig)

4. PER-JOKE EXECUTION (loop)
   PerformanceController.PresentJoke(JokeData)
   -> CrowdEngine.EvaluateJoke(JokeData)
      -> For each AudienceCluster:
           CalculateReaction(JokeData, ArchetypePreferences)
           -> ReactionData
   -> LaughGraph.RecordReaction(ReactionData)
   -> Audio.PlayCrowdReaction(ReactionData)
   -> UI.UpdateLaughMeter(ReactionData)

   [Optional: Pivot Point]
   IF PlayerInputDetected() AND PivotPointsRemaining > 0:
      Player -> PivotUI.SelectAlternateJoke()
      -> Replace current joke in sequence

5. SET COMPLETION
   PerformanceController.EndSet()
   -> LaughGraph.GenerateReport(allReactionData)
   -> VoiceIdentity.UpdateFromSet(SetlistData, ReactionData)
   -> CareerManager.AwardREP(CalculateREPEarned())
   -> CareerManager.AwardCASH(CalculateCASHEarned())
   -> SceneManager.UpdateRivals(performanceOutcome)

6. POST-SET ANALYSIS
   Player -> LaughGraphUI.ExploreReport()
   Player -> BitBuilderUI.IterateJokes(insightsFromReport)
```

---

## 4. Key Gameplay Systems — Technical Design

### 4.1 Bit Builder System

**Architecture**: Model-View-Controller pattern with reactive UI.

**Data Model**:

```csharp
[CreateAssetMenu(fileName = "ComponentCard", menuName = "DEADPAN/Component Card")]
public class ComponentCard : ScriptableObject
{
    public ComponentType Type; // Premise, Setup, Misdirection, Punchline, Tag
    public string DisplayText;
    public string[] ThematicTags; // e.g., ["family", "technology", "absurd"]

    // Humor Axes (0-10)
    public float Cleverness;
    public float Relatability;
    public float Edge;
    public float Absurdity;
    public float Physicality;

    public int WordCount; // For timing calculations
    public bool IsUnlocked; // Player progression flag
}

public class JokeData
{
    public ComponentCard Premise;
    public ComponentCard Setup;
    public ComponentCard Misdirection;
    public ComponentCard Punchline;
    public ComponentCard Tag; // Nullable
    public JokeData CallbackTarget; // Nullable, references another JokeData

    // Cached calculated values
    public HumorProfile Profile; // Calculated from components
    public float QualityScore; // 0-100
}

public struct HumorProfile
{
    public float Cleverness;
    public float Relatability;
    public float Edge;
    public float Absurdity;
    public float Physicality;
}
```

**Quality Calculation** (runs on JokeData creation/modification):

```csharp
public class JokeQualityCalculator
{
    public static float Calculate(JokeData joke)
    {
        float coherence = CalculateCoherence(joke);      // 0-30
        float surprise = CalculateSurprise(joke);        // 0-30
        float timing = CalculateTiming(joke);            // 0-20
        float tagBonus = CalculateTagBonus(joke);        // 0-10 or -5
        float baseQuality = coherence + surprise + timing + tagBonus;

        float callbackMultiplier = CalculateCallbackMultiplier(joke); // 1.0-1.5

        return Mathf.Clamp(baseQuality * callbackMultiplier, 0f, 100f);
    }

    private static float CalculateCoherence(JokeData joke)
    {
        // Tag overlap between components
        var allTags = new HashSet<string>();
        var sharedTags = new HashSet<string>(joke.Premise.ThematicTags);

        allTags.UnionWith(joke.Premise.ThematicTags);
        allTags.UnionWith(joke.Setup.ThematicTags);
        sharedTags.IntersectWith(joke.Setup.ThematicTags);

        float baseCoherence = 20f * ((float)sharedTags.Count / (float)allTags.Count);

        // Bonus: Misdirection and Punchline share Premise domain
        if (HasSharedDomain(joke.Premise, joke.Misdirection, joke.Punchline))
            baseCoherence += 10f;

        return Mathf.Clamp(baseCoherence, 0f, 30f);
    }

    private static float CalculateSurprise(JokeData joke)
    {
        // Euclidean distance between Misdirection and Punchline profiles
        var misdirProfile = GetHumorProfile(joke.Misdirection);
        var punchProfile = GetHumorProfile(joke.Punchline);

        float distance = Vector5.Distance(misdirProfile, punchProfile);
        float maxDistance = Mathf.Sqrt(5 * 100); // Max distance in 5D space with 0-10 range

        return 30f * (distance / maxDistance);
    }

    private static float CalculateTiming(JokeData joke)
    {
        int setupWords = joke.Setup.WordCount + joke.Misdirection.WordCount;
        int punchlineWords = joke.Punchline.WordCount;

        float ratio = (float)setupWords / (float)punchlineWords;

        // Ideal ratio: 1.5x to 2.5x
        float timingScore = 0f;
        if (ratio >= 1.5f && ratio <= 2.5f)
            timingScore = 20f;
        else if (ratio >= 1.0f && ratio <= 3.0f)
            timingScore = 10f;
        else
            timingScore = 5f;

        // Rule of threes bonus (check thematic tags for pattern)
        if (HasRuleOfThreesPattern(joke))
            timingScore += 10f;

        return Mathf.Min(timingScore, 20f);
    }
}
```

**UI Implementation**: Drag-and-drop card interface. Unity UI Toolkit with custom drag handlers.

**Performance Target**: Joke quality recalculation must be < 1ms. This runs on every card drag. Optimization: cache HumorProfile calculations on ComponentCards, only recalculate JokeData fields on modification.

**Content Pipeline**: Component cards are ScriptableObjects created via Unity editor tools. Build a custom editor window for batch card creation. Export/import from CSV for easier content iteration (designers work in spreadsheets, import to Unity).

---

### 4.2 Crowd Engine System

**Architecture**: ECS-inspired audience simulation. Each audience cluster is a lightweight data struct. Reactions are calculated in parallel via Unity Jobs system.

**Data Model**:

```csharp
[CreateAssetMenu(fileName = "AudienceArchetype", menuName = "DEADPAN/Audience Archetype")]
public class AudienceArchetype : ScriptableObject
{
    public string ArchetypeName;
    public HumorProfile Preferences; // What they like
    public float Patience;          // 0-10, how long they'll tolerate bad material
    public float Volatility;        // 0-10, likelihood of heckling/walking out
    public float ViralPotential;    // 0-10, likelihood of recording/sharing
}

public struct AudienceCluster
{
    public int ClusterID;
    public AudienceArchetype Archetype;
    public int Size; // 2-6 people
    public Vector2 SpatialPosition; // For bleed calculations
    public float CurrentEngagement; // 0-1, tracks accumulated reaction
    public float CurrentFatigue; // Starts at 1.0, decreases per joke
}

[CreateAssetMenu(fileName = "VenueConfig", menuName = "DEADPAN/Venue")]
public class VenueConfig : ScriptableObject
{
    public string VenueName;
    public int CareerTier;
    public int MinAudience;
    public int MaxAudience;
    public ArchetypeDistribution[] ArchetypeWeights;
}

[System.Serializable]
public struct ArchetypeDistribution
{
    public AudienceArchetype Archetype;
    public float Probability; // 0-1
}
```

**Crowd Generation** (runs at performance start):

```csharp
public class CrowdEngine : MonoBehaviour
{
    private List<AudienceCluster> activeCrowd;
    private float currentMomentum = 1.0f;

    public void GenerateCrowd(VenueConfig venue)
    {
        activeCrowd = new List<AudienceCluster>();
        int totalAudience = Random.Range(venue.MinAudience, venue.MaxAudience);

        // Sample from archetype distribution
        while (totalAudience > 0)
        {
            var archetype = SampleArchetype(venue.ArchetypeWeights);
            int clusterSize = Random.Range(2, 7);
            clusterSize = Mathf.Min(clusterSize, totalAudience);

            activeCrowd.Add(new AudienceCluster
            {
                ClusterID = activeCrowd.Count,
                Archetype = archetype,
                Size = clusterSize,
                SpatialPosition = GenerateRandomPosition(),
                CurrentEngagement = 0.5f,
                CurrentFatigue = 1.0f
            });

            totalAudience -= clusterSize;
        }
    }

    public ReactionData EvaluateJoke(JokeData joke)
    {
        // Parallel reaction calculation
        var reactionJob = new ReactionCalculationJob
        {
            JokeProfile = joke.Profile,
            JokeQuality = joke.QualityScore,
            Momentum = currentMomentum,
            Clusters = new NativeArray<AudienceCluster>(activeCrowd.ToArray(), Allocator.TempJob),
            ReactionScores = new NativeArray<float>(activeCrowd.Count, Allocator.TempJob)
        };

        var handle = reactionJob.Schedule(activeCrowd.Count, 64);
        handle.Complete();

        // Process results
        var reactionData = new ReactionData
        {
            PerClusterReactions = new float[activeCrowd.Count],
            AggregateScore = 0f
        };

        for (int i = 0; i < activeCrowd.Count; i++)
        {
            float score = reactionJob.ReactionScores[i];
            reactionData.PerClusterReactions[i] = score;
            reactionData.AggregateScore += score * activeCrowd[i].Size;

            // Update cluster state
            var cluster = activeCrowd[i];
            cluster.CurrentEngagement = Mathf.Lerp(cluster.CurrentEngagement, score, 0.3f);
            cluster.CurrentFatigue -= 0.02f; // Per-joke fatigue
            activeCrowd[i] = cluster;
        }

        reactionData.AggregateScore /= activeCrowd.Sum(c => c.Size);

        // Update momentum
        UpdateMomentum(reactionData.AggregateScore);

        // Spatial bleed (optional, can be disabled for perf)
        ApplySpatialBleed();

        // Heckler check
        CheckForHecklers(reactionData);

        reactionJob.Clusters.Dispose();
        reactionJob.ReactionScores.Dispose();

        return reactionData;
    }
}

[BurstCompile]
public struct ReactionCalculationJob : IJobParallelFor
{
    [ReadOnly] public HumorProfile JokeProfile;
    [ReadOnly] public float JokeQuality;
    [ReadOnly] public float Momentum;
    [ReadOnly] public NativeArray<AudienceCluster> Clusters;

    public NativeArray<float> ReactionScores;

    public void Execute(int index)
    {
        var cluster = Clusters[index];
        var prefs = cluster.Archetype.Preferences;

        // Dot product of joke profile and archetype preferences
        float alignment = DotProduct(JokeProfile, prefs) / 50f; // Normalized to 0-1

        // Apply quality modifier
        float qualityMod = JokeQuality / 100f;

        // Apply momentum
        float momentumMod = Momentum;

        // Apply fatigue
        float fatigueMod = cluster.CurrentFatigue;

        float reactionScore = alignment * qualityMod * momentumMod * fatigueMod;

        ReactionScores[index] = Mathf.Clamp(reactionScore, 0f, 1f);
    }

    private float DotProduct(HumorProfile a, HumorProfile b)
    {
        return a.Cleverness * b.Cleverness +
               a.Relatability * b.Relatability +
               a.Edge * b.Edge +
               a.Absurdity * b.Absurdity +
               a.Physicality * b.Physicality;
    }
}
```

**Performance Budget**:
- Crowd generation: < 10ms for 2000-person audience (typical max is ~500 clusters)
- Per-joke evaluation: < 5ms for 500 clusters (burst-compiled job parallelism)
- Target: 60 FPS maintained during performance sequences

**Tuning Strategy**: All formulas have exposed float multipliers in a `CrowdBalanceConfig` ScriptableObject. No magic numbers in code. Designers can tweak reaction sensitivity, momentum decay, fatigue rate without programmer intervention.

---

### 4.3 Laugh Graph System

**Architecture**: Data visualization layer. Reads ReactionData history, generates UI graphs.

**Implementation**: Unity UI Toolkit vector graphics API for the waveform. SVG-like path rendering.

**Data Structure**:

```csharp
public class LaughGraphData
{
    public List<JokePerformanceRecord> Records;

    public struct JokePerformanceRecord
    {
        public JokeData Joke;
        public ReactionData Reaction;
        public float Timestamp; // Seconds into the set
        public Dictionary<AudienceArchetype, float> PerArchetypeReactions;
    }
}

public class LaughGraphUI : MonoBehaviour
{
    public void RenderWaveform(LaughGraphData data)
    {
        // Generate path from reaction scores
        var path = new UIPath();
        for (int i = 0; i < data.Records.Count; i++)
        {
            float x = (float)i / data.Records.Count;
            float y = data.Records[i].Reaction.AggregateScore;

            if (i == 0)
                path.MoveTo(new Vector2(x, y));
            else
                path.LineTo(new Vector2(x, y));
        }

        waveformElement.vectorImage = path.ToVectorImage();

        // Color based on momentum (blue = cold, gold = hot)
        float avgMomentum = CalculateAverageMomentum(data);
        waveformElement.tintColor = Color.Lerp(coldColor, hotColor, avgMomentum);
    }
}
```

**Post-Set Analysis Views**:
1. Overview: Full waveform with joke labels (hover for details)
2. Per-Segment: Stacked area chart showing reactions by archetype
3. Pivot Analysis: Comparison overlay (what-if scenario)
4. Setlist Flow: Energy arc with momentum visualization
5. Comparison: Multi-set overlay

Each view is a prefab with its own data renderer. Tab-based navigation.

**Performance**: Graph rendering is one-time at set end. No real-time constraints. Target < 100ms to render full analysis suite.

---

### 4.4 Voice Identity System

**Architecture**: Accumulator-based stat tracking. Every performed joke shifts the player's voice.

**Data Model**:

```csharp
public class VoiceIdentity
{
    // Five spectra, -10 to +10
    public float ObservationalAbsurdism; // -10 = Observational, +10 = Absurdist
    public float CleanDark;              // -10 = Clean, +10 = Dark
    public float PoliticalPersonal;      // -10 = Political, +10 = Personal
    public float CerebralPhysical;       // -10 = Cerebral, +10 = Physical
    public float WarmConfrontational;    // -10 = Warm, +10 = Confrontational

    public float Authenticity; // 0-100

    private Queue<JokeData> recentPerformances; // Last 20 performances
}

public class VoiceIdentitySystem : MonoBehaviour
{
    public void UpdateFromJoke(JokeData joke, int audienceSize, float reactionScore)
    {
        float audienceMod = Mathf.Clamp(audienceSize / 200f, 0.5f, 3.0f);
        float reactionMod = Mathf.Lerp(0.5f, 2.0f, reactionScore);

        // Map joke's humor profile to voice spectra
        float absurdismShift = (joke.Profile.Absurdity - 5f) * 0.01f * audienceMod * reactionMod;
        playerVoice.ObservationalAbsurdism += absurdismShift;

        // (Repeat for other axes...)

        // Clamp to -10/+10 range
        playerVoice.ObservationalAbsurdism = Mathf.Clamp(playerVoice.ObservationalAbsurdism, -10f, 10f);

        // Update authenticity
        UpdateAuthenticity(joke);
    }

    private void UpdateAuthenticity(JokeData joke)
    {
        // Check alignment with current voice
        float deviation = CalculateVoiceDeviation(joke, playerVoice);

        if (deviation < 2f) // Close alignment
            playerVoice.Authenticity = Mathf.Min(playerVoice.Authenticity + 1f, 100f);
        else if (deviation > 4f) // Significant deviation
            playerVoice.Authenticity = Mathf.Max(playerVoice.Authenticity - 3f, 0f);
    }
}
```

**Career Gating**: CareerManager queries VoiceIdentity before unlocking opportunities.

```csharp
public bool CanUnlockOpportunity(CareerOpportunity opportunity)
{
    if (opportunity.RequiresAuthenticityMin > playerVoice.Authenticity)
        return false;

    foreach (var req in opportunity.VoiceRequirements)
    {
        if (!VoiceMeetsRequirement(req))
            return false;
    }

    return true;
}
```

---

### 4.5 AI Comedian System (The Scene)

**Architecture**: State-machine-based AI with personality-driven behavior trees.

**Data Model**:

```csharp
[CreateAssetMenu(fileName = "AIComedian", menuName = "DEADPAN/AI Comedian")]
public class AIComedianProfile : ScriptableObject
{
    public string Name;
    public VoiceIdentity Voice;
    public float SkillLevel; // 1-100
    public int CareerTier;
    public AIPersonality Personality; // Generous, Neutral, Cutthroat
    public AIAmbition Ambition; // Low, Medium, High
    public AICareerArc Arc; // Steady Climber, Flash in the Pan, etc.
}

public class AIComedian
{
    public AIComedianProfile Profile;
    public float RelationshipWithPlayer; // -100 to +100
    public List<JokeData> MaterialLibrary;
    public CareerState CurrentState;
}

public class SceneManager : MonoBehaviour
{
    private List<AIComedian> activeComics;

    public void SimulateWeek()
    {
        foreach (var comic in activeComics)
        {
            // AI writes new material
            if (Random.value < 0.3f)
                comic.MaterialLibrary.Add(GenerateAIMaterial(comic));

            // AI books gigs and performs
            var gig = BookGigForAI(comic);
            if (gig != null)
                SimulateAIPerformance(comic, gig);

            // AI career progression
            UpdateAICareer(comic);

            // Check for scene events
            CheckSceneEvents(comic);
        }

        // Check for material overlap with player
        DetectMaterialTheft();
    }

    private void DetectMaterialTheft()
    {
        foreach (var comic in activeComics)
        {
            foreach (var aiJoke in comic.MaterialLibrary)
            {
                foreach (var playerJoke in playerMaterialLibrary)
                {
                    float similarity = CalculateJokeSimilarity(aiJoke, playerJoke);
                    if (similarity < 1.5f) // Close similarity
                    {
                        ResolveOverlap(aiJoke, playerJoke, comic);
                    }
                }
            }
        }
    }
}
```

**AI Material Generation**: AI comedians generate jokes using the same JokeQualityCalculator as the player, but with skill-based randomness. A high-skill AI produces higher-quality combinations. A low-skill AI produces lower-quality jokes.

```csharp
private JokeData GenerateAIMaterial(AIComedian comic)
{
    // Select components weighted by AI's voice preferences
    var premise = SelectComponentWeighted(ComponentType.Premise, comic.Profile.Voice);
    var setup = SelectComponentWeighted(ComponentType.Setup, comic.Profile.Voice);
    var misdirection = SelectComponentWeighted(ComponentType.Misdirection, comic.Profile.Voice);
    var punchline = SelectComponentWeighted(ComponentType.Punchline, comic.Profile.Voice);

    var joke = new JokeData
    {
        Premise = premise,
        Setup = setup,
        Misdirection = misdirection,
        Punchline = punchline
    };

    // Quality variance based on skill
    joke.QualityScore = JokeQualityCalculator.Calculate(joke);
    joke.QualityScore *= Mathf.Lerp(0.4f, 1.2f, comic.Profile.SkillLevel / 100f);

    return joke;
}
```

**Performance Budget**: Scene simulation runs during the player's "week advance" action. Target < 200ms for 15 AI comedians.

---

## 5. Save System Design

**Architecture**: JSON-based serialization with versioning support.

**What Gets Saved**:
- Player material library (all JokeData instances)
- Player voice identity (current state + history)
- Career progression (tier, REP, cash, unlocked venues, agent relationship)
- AI comedian states (current tier, relationship, material library sample)
- Scene state (active events, upcoming gigs, cultural moments)
- Game week counter

**Save File Structure**:

```json
{
  "version": "1.0.0",
  "saveDate": "2026-02-07T14:30:00Z",
  "playerData": {
    "careerTier": 3,
    "rep": 1250,
    "cash": 8500,
    "voiceIdentity": { /* ... */ },
    "materialLibrary": [ /* JokeData[] */ ]
  },
  "sceneData": {
    "aiComedians": [ /* AIComedianState[] */ ],
    "activeEvents": [ /* SceneEvent[] */ ]
  },
  "gameState": {
    "currentWeek": 52,
    "currentCity": "New York"
  }
}
```

**Implementation**:

```csharp
public class SaveSystem
{
    private static string SavePath =>
        Path.Combine(Application.persistentDataPath, "saves");

    public static void SaveGame(int slotIndex)
    {
        var saveData = new SaveData
        {
            Version = Application.version,
            SaveDate = System.DateTime.UtcNow,
            PlayerData = GameManager.Instance.Player.Serialize(),
            SceneData = SceneManager.Instance.Serialize(),
            GameState = GameManager.Instance.SerializeState()
        };

        string json = JsonUtility.ToJson(saveData, true);
        string filePath = Path.Combine(SavePath, $"save_{slotIndex}.json");
        File.WriteAllText(filePath, json);
    }

    public static SaveData LoadGame(int slotIndex)
    {
        string filePath = Path.Combine(SavePath, $"save_{slotIndex}.json");
        if (!File.Exists(filePath))
            return null;

        string json = File.ReadAllText(filePath);
        var saveData = JsonUtility.FromJson<SaveData>(json);

        // Version migration logic here if needed
        if (saveData.Version != Application.version)
            saveData = MigrateSaveData(saveData);

        return saveData;
    }
}
```

**Auto-Save**: Trigger on week advance, tier unlock, and performance completion. Keep last 3 auto-saves as rollback safety.

**Cloud Save** (Steam): Use Steamworks.NET wrapper. Upload save JSON to Steam Cloud on game exit.

---

## 6. Performance Budget and Optimization Strategy

### 6.1 Target Framerate

- **PC**: 60 FPS locked, with 120 FPS support for high-refresh monitors
- **Switch**: 30 FPS minimum, 60 FPS target (UI-heavy scenes can run at 60)
- **Mobile**: 60 FPS on high-end devices (iPhone 13+), 30 FPS minimum on mid-tier

### 6.2 Performance Bottlenecks

| System | Expected Cost | Optimization Strategy |
|--------|---------------|----------------------|
| **Crowd Engine** | 2-5ms per joke evaluation | Burst-compiled jobs. Parallel processing. Reduce cluster count at higher audience sizes (100+ people = ~50 clusters max, not 1:1 simulation). |
| **UI Rendering** | 1-3ms | UI Toolkit is GPU-accelerated. Minimize overdraw. Cache vector paths. Disable offscreen UI elements. |
| **Audio Mixing** | 1-2ms | FMOD handles mixing on separate thread. Use parameter blending instead of per-cluster audio sources. Max 8-12 simultaneous crowd audio layers. |
| **Scene Simulation** | < 200ms per week | Run on background thread. Player doesn't wait for AI simulation in real-time. |
| **Save/Load** | < 500ms | Save files are < 1MB. JSON serialization is fast. Load on separate thread with loading screen. |

### 6.3 Memory Budget

- **PC**: Target 2GB max RAM usage
- **Switch**: Target 1GB max RAM usage (Switch has 4GB, but OS reserves ~1GB)
- **Mobile**: Target 512MB max RAM usage

**Content Streaming**: Component card library is loaded in chunks. Only load unlocked cards into memory. Late-game players have 200+ cards unlocked, but only ~50 are actively used per session. Implement LRU cache for card data.

### 6.4 Profiling Strategy

Ship with built-in profiler overlay (debug builds only). Track:
- Frame time breakdown (update, render, jobs)
- Crowd Engine evaluation time per joke
- UI render time per frame
- Memory allocations per frame (zero-alloc target in hot path)

Use Unity Profiler during development. Export profiler data to JSON for analysis. Build automated perf tests: "simulate 100-joke set with 500-person audience, must average < 16ms per frame."

---

## 7. Platform Considerations

### 7.1 PC (Steam)

**Input**: Mouse + keyboard primary. Controller support secondary (full UI navigation with gamepad).

**Resolution**: Support 1920x1080 minimum, 4K maximum. UI scales with resolution (UI Toolkit handles this natively).

**Steam Integration**:
- Steamworks.NET for achievements, cloud saves, leaderboards (optional: "Best Set at [Venue]" leaderboards)
- Steam Input API for controller rebinding
- Workshop support (stretch goal: user-generated component cards)

**Early Access Strategy**: Ship with Tier 1-4 content complete, Tier 5-6 in development. Community feedback drives Crowd Engine balancing. 6-month Early Access window.

### 7.2 Nintendo Switch

**Input**: Joy-Con and Pro Controller. No touch support (docked mode primary).

**Performance**: Target 30 FPS minimum. Reduce crowd cluster count on Switch (max 250 clusters vs. 500 on PC). Lower-resolution UI assets.

**Certification Considerations**: Nintendo requires no crashes, stable framerate, and proper sleep/resume handling. Allocate 2-3 months for certification after PC version is stable.

**Port Strategy**: Unity's Switch export is mature. Main work is input remapping and performance tuning. Budget 4-6 weeks for Switch-specific work post-PC launch.

### 7.3 Mobile (iOS/Android) — Stretch Goal

**Input**: Touch-first. Redesign Bit Builder UI for touch (larger drag targets, swipe gestures).

**Performance**: Reduce crowd simulation complexity. Max 100 clusters. Lower audio quality.

**Monetization** (if mobile): Premium upfront ($9.99). No F2P/IAP. The design doesn't support microtransactions without gutting the progression.

**Port Effort**: 8-12 weeks for UI redesign + performance optimization. Not a launch platform. Post-1.0 consideration only.

---

## 8. Build Pipeline and Tools

### 8.1 Build Automation

**CI/CD**: GitHub Actions for automated builds.

Pipeline:
1. Commit to `main` branch
2. GitHub Actions trigger
3. Run unit tests (JokeQualityCalculator tests, reaction calculation tests)
4. Build Windows, Mac, Linux (Steam SDK included)
5. Upload to Steam (internal beta branch)
6. Notify team on Discord

**Build Targets**:
- **Development**: Daily automated builds. Full debug symbols, profiler enabled.
- **Playtest**: Weekly builds. Debug disabled, profiler enabled, analytics enabled.
- **Release Candidate**: Manual trigger. Full optimizations, no debug code.

### 8.2 Content Tools

**Component Card Editor**: Custom Unity editor window.

Features:
- Batch create cards from CSV import
- Preview joke assembly with drag-drop test
- Humor profile radar chart visualization
- Thematic tag autocomplete
- Quality score preview

**Crowd Balance Tool**: Runtime debug window (development builds only).

Features:
- Live editing of CrowdBalanceConfig values
- Real-time reaction recalculation
- Export tuning values to JSON
- A/B testing mode (run same joke through two different balance configs, compare results)

**Analytics Dashboard**: Web-based dashboard (internal tool, not shipped with game).

Reads analytics JSON logs from playtest builds. Visualizes:
- Most-used component cards
- Average joke quality by tier
- Crowd reaction distributions by venue
- Laugh Graph patterns (which joke positions have highest variance?)

Built with: Python (Flask) + JavaScript (Chart.js). Hosted on internal server.

### 8.3 Version Control

**Repo Structure**:
```
/DEADPAN
  /Assets
    /Scripts       (C# code)
    /Data          (ScriptableObjects)
    /UI            (UI Toolkit assets)
    /Audio         (FMOD project)
    /Art           (Sprites, textures)
  /Docs
    /Design        (GDD, tech docs)
    /Art           (Concept art, style guide)
  /Tools           (Python scripts for content pipeline)
```

**Git LFS**: Use LFS for audio files, textures, and FMOD banks. Keep repo size under 5GB.

**Branching Strategy**:
- `main`: Always stable. Release candidates only.
- `develop`: Active development. Daily commits.
- Feature branches: `feature/callback-system`, `feature/heckler-duels`, etc.

**Code Review**: All merges to `develop` require one approval. Core systems (Bit Builder, Crowd Engine) require two approvals.

---

## 9. Technical Risk Assessment

### Risk 1: Bit Builder Feels Like a Spreadsheet (Severity: HIGH)

**Mitigation**:
- Thematic tags and human-readable text on every component
- UI emphasizes text over stats (stats are secondary info, shown on hover)
- Component card art (small icons representing joke themes)
- Playtest with non-gamers (Steam friends/family beta)

**Fallback**: If quality score calculation feels too opaque, add a "Why this score?" breakdown UI that explains Coherence/Surprise/Timing contributions in plain English.

**Timeline Impact**: If this risk manifests in playtest, budget 4 weeks for UI redesign.

### Risk 2: Crowd Engine Feels Random (Severity: VERY HIGH)

**Mitigation**:
- Laugh Graph per-segment breakdown must be crystal clear
- Pre-show crowd composition display with archetype preference tooltips
- Post-set "What went wrong?" analysis with explicit suggestions ("College Students prefer higher Edge — try reworking Joke 3")
- Telemetry to detect patterns in player confusion (if players replay the same joke at the same venue, the system is failing)

**Fallback**: Add a "Prediction Mode" to the Bit Builder — select a joke, select a venue, get a predicted reaction score range before performing. This adds a layer of agency/control.

**Timeline Impact**: This is the core loop. If it's not working by Month 6 of development, we're in trouble. Allocate 50% of prototype phase to tuning this.

### Risk 3: Late-Game Content Starvation (Severity: MEDIUM)

**Problem**: Players at Tier 5-6 consume component cards faster than we can create them. The Bit Builder feels stale.

**Mitigation**:
- Target 500+ component cards at launch (300 announced in GDD is minimum, not target)
- Cultural Moments generate new Premise cards dynamically (system-generated, not hand-authored)
- Callback system creates combinatorial depth without new content (100 jokes = 4950 possible callback pairs)
- Stretch goal: Procedural component variation (take existing card, modify one axis by +/-2, generate "variant" card with slightly different flavor text)

**Fallback**: Post-launch content DLCs. "Brooklyn Pack" with 50 new cards themed around NYC comedy scene. "Dark Material Pack" with high-Edge content. Each DLC is 1-2 weeks of writing work.

**Timeline Impact**: Not a launch blocker. Monitor via telemetry post-EA launch.

### Risk 4: Performance at Scale (Severity: MEDIUM)

**Problem**: 2000-person audience simulation tanks framerate.

**Mitigation**:
- Cluster-based simulation (max 500 clusters, not 1:1 people)
- Burst-compiled jobs for parallelism
- LOD system for crowd rendering (distant clusters are simplified meshes)
- Audio is parameter-based, not per-cluster sources

**Fallback**: Dynamic quality scaling. On lower-end PCs, reduce max cluster count to 250. On Switch, reduce to 150. The gameplay doesn't change — the player never knows the exact audience size, only the venue's approximate capacity.

**Timeline Impact**: Addressable in optimization phase (Months 15-18). Not a prototype concern.

### Risk 5: Switch Certification Failure (Severity: LOW)

**Problem**: Nintendo certification rejects the build for stability/performance issues.

**Mitigation**:
- Stability pass before submission (2-week soak test on dev kits)
- Performance profiling on real hardware (not just Unity Editor on PC)
- Proper sleep/resume handling (Unity handles this mostly automatically, but test extensively)

**Fallback**: Delay Switch launch by 2-3 months if certification fails. PC launch is unaffected.

**Timeline Impact**: Certification is Month 22-24. If it fails, Switch slips to Month 25-27. Not a critical path blocker.

---

## 10. Development Milestones (Technical Perspective)

### Milestone 1: Vertical Slice Prototype (Months 1-3)

**Goal**: Prove the 30-second loop works.

**Deliverables**:
- Bit Builder with 20 component cards (4 per type)
- Crowd Engine with 3 audience archetypes
- Single venue (dive bar open mic, 20-person audience)
- Laugh Graph basic visualization
- One performance loop: build joke, perform, see results

**Success Criteria**: External playtest (10 people) — 8/10 say "I understand why the joke succeeded/failed."

**Tech Risks to Validate**: Bit Builder UI feel, Crowd Engine legibility.

### Milestone 2: Core Systems Complete (Months 4-6)

**Goal**: All five core systems functional.

**Deliverables**:
- Bit Builder with 80 component cards
- Crowd Engine with 9 archetypes, 5 venue types
- Laugh Graph with all 5 analysis views
- Voice Identity tracking (visible UI)
- Career progression Tier 0-2
- Save/Load system

**Success Criteria**: Internal team can play a 2-hour session from Tier 0 to Tier 2 without game-breaking bugs.

**Tech Risks to Validate**: Voice Identity feels meaningful, save system handles edge cases.

### Milestone 3: Mid-Game Content (Months 7-10)

**Goal**: Tier 3-4 content, economy systems, The Scene.

**Deliverables**:
- Career progression Tier 3-4
- AI comedian system (15 active comics)
- Rival/collaborator interactions
- Economy systems (agent, merch, cash flow)
- 200 component cards total
- Setlist construction with callbacks

**Success Criteria**: Playtest (20 people, 8-hour session target) — "The mid-game grind feels engaging, not repetitive."

**Tech Risks to Validate**: AI comedian simulation performance, scene events feel dynamic.

### Milestone 4: Late-Game and Polish (Months 11-14)

**Goal**: Tier 5-6, The Special, audio/visual polish.

**Deliverables**:
- Career progression Tier 5-6
- Special taping sequence (60-minute set)
- FMOD procedural crowd audio
- UI polish (animations, juice, screen transitions)
- 300+ component cards
- Cultural Moment system

**Success Criteria**: Full playthrough (Tier 0 to Special) feels like a complete arc.

**Tech Risks to Validate**: Special sequence is climactic, audio adds 50% to game feel.

### Milestone 5: Early Access Launch (Month 15)

**Goal**: Ship to Steam Early Access.

**Deliverables**:
- Tier 1-4 fully polished
- Tier 5-6 feature-complete but content-light
- Steam integration (achievements, cloud saves)
- Telemetry and analytics pipeline
- Community feedback channels (Discord, Steam forums)

**Success Criteria**: 500 wishlists before launch, 70%+ positive reviews in first month.

**Post-Launch Focus**: Crowd Engine balancing based on player data.

### Milestone 6: 1.0 Release (Months 16-18)

**Goal**: Full content, final balance, launch marketing push.

**Deliverables**:
- Tier 5-6 content complete
- 400+ component cards
- Final Crowd Engine balance pass
- Performance optimization (hit framerate targets on min-spec PC)
- Launch trailer and press kit

**Success Criteria**: 80%+ positive reviews on Steam, 10K units sold in first month.

### Milestone 7: Switch Port (Months 19-24)

**Goal**: Launch on Nintendo Switch.

**Deliverables**:
- Switch-optimized build (30 FPS stable)
- Controller-native UI
- Nintendo certification
- eShop listing and launch trailer

**Success Criteria**: Certification pass on first submission, 5K units sold in first month.

---

## 11. Team Structure and Skill Requirements

### Core Team (Months 1-15)

| Role | Count | Key Responsibilities |
|------|-------|---------------------|
| **Lead Programmer** | 1 | Architecture, core systems, optimization |
| **Gameplay Programmer** | 1 | Bit Builder, Crowd Engine, career systems |
| **UI Programmer** | 1 | UI Toolkit implementation, Laugh Graph |
| **Game Designer** | 1 | System design, balance tuning, playtesting |
| **Content Designer** | 1 | Component card writing, venue design |
| **Technical Artist** | 1 | UI art, shaders, VFX |
| **2D Artist** | 1 | Character portraits, venue backgrounds |
| **Audio Designer** | 1 | FMOD implementation, crowd audio design |

**Total**: 8 people.

### Expanded Team (Months 15-24, post-EA launch)

Add:
- QA Tester (1)
- Community Manager (1, part-time)
- Additional Content Designer (1, for late-game content)

**Total**: 11 people.

### Outsourcing Opportunities

- **Music Composition**: Main menu theme, performance music stings. 2-3 tracks. Budget: $3K-5K.
- **Localization**: Post-1.0. French, German, Spanish. Budget: $20K-30K (text-heavy game).
- **Marketing Assets**: Key art, trailer editing. Budget: $10K-15K.

---

## 12. Technology Stack Summary

| Layer | Technology | Rationale |
|-------|------------|-----------|
| **Engine** | Unity 2023 LTS | Cross-platform, UI-heavy, large talent pool |
| **Language** | C# | Unity's native language, strong typing, good tooling |
| **UI Framework** | Unity UI Toolkit | Modern, performant, vector graphics support |
| **Audio** | FMOD Studio | Procedural crowd audio, parameter-based mixing |
| **Build Automation** | GitHub Actions | Free for public repos, integrates with Steam |
| **Version Control** | Git + GitHub | Industry standard |
| **Analytics** | Unity Analytics + Custom JSON logs | Telemetry for balancing |
| **Platform SDK** | Steamworks.NET | Steam integration |
| **Serialization** | JSON.NET | Human-readable save files, version migration support |
| **Performance** | Unity Jobs System + Burst Compiler | Parallel crowd simulation |

---

## 13. Post-Launch Roadmap (Technical)

### Month 18-24: Quality of Life Updates

- **Setlist Templates**: Save and reuse setlists
- **Material Filtering**: Advanced search/filter in Bit Builder
- **Accessibility**: Colorblind mode, text-to-speech for component cards
- **Mod Support** (PC only): Expose component card JSON for community creation

### Month 24-36: Expansion Content (If Successful)

- **New Cities**: Expand beyond initial 4 cities. Each city has unique venue types and audience archetypes. (Example: Austin has "Podcast Studio" venue with 90% Podcast Listener archetype.)
- **Heckler Duels**: Full implementation of real-time heckler response mini-game.
- **Writers' Room Mode**: Separate game mode for TV writing career path.
- **Legacy Mode**: Start new comedian in world shaped by previous playthrough.

### Long-Term Vision (If Wildly Successful)

- **Multiplayer Comedy Battles**: Async competition. Build a set, upload to server, other players' Crowd Engines rate it. Leaderboards.
- **Touring DLC**: Full touring management sim (bus routes, venue booking, crew management).
- **Documentary Mode**: After completing The Special, unlock a "making of" mode that shows your career stats, graph of Voice Identity over time, Laugh Graphs from every major set. A narrative reflection on the journey.

---

## 14. Final Notes from BYTE

This architecture is designed to ship. It's not elegant — it's pragmatic. The Crowd Engine is a deterministic rules system because that's what the loop demands. We're not using ML because we can't debug it and the player can't learn from it.

The component-based design (ScriptableObjects everywhere) means designers can work in parallel with programmers. The Bit Builder, Crowd Engine, and Laugh Graph are modular — we can tune them independently without cascading changes.

The biggest risk is the Crowd Engine feeling opaque. We mitigate this with aggressive feedback: Laugh Graph breakdowns, pre-show crowd previews, post-set analysis. If the player can't diagnose why they failed, the loop is dead. We're building a diagnostics-first system.

The save system is JSON because we need human-readable data for debugging. We'll get bug reports that say "my game is broken" and we'll need to inspect their save file. Binary saves are faster, but JSON is debuggable. Pick your battles.

The performance budget is achievable. We're not rendering 2000 people — we're simulating 500 clusters and rendering abstract crowd meshes. The Crowd Engine jobs are embarrassingly parallel. Burst compilation gives us 10x perf over naive C#. We hit 60 FPS or we cut cluster count. No heroics required.

The Early Access strategy is critical. We're shipping Tier 1-4 and using community feedback to balance the Crowd Engine. The first 1000 players are our QA team. We watch their Laugh Graph data, identify patterns ("everyone bombs at college shows with high-Edge material"), and tune the archetypes. This game is too complex to balance in a vacuum.

Ship the vertical slice in 3 months. If the loop doesn't feel good at month 3, the game doesn't work. Everything else is risk mitigation.

Profile before you optimize. Never guess where the bottleneck is.

Does it compile? Does it run? Ship it. Then make it right. Then make it fast.

---

**Document Version**: 1.0
**Last Updated**: 2026-02-07
**Next Review**: Post-Vertical Slice Playtest (Month 3)

END DOCUMENT
