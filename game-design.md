# DEADPAN -- Game Design Document

**Stand-up comedy empire simulation**
**Designer**: REED
**Status**: Full GDD -- ready for prototype scoping

---

## 1. Player Fantasy Statement

**"I am a stand-up comedian clawing my way from open mics to an HBO special, and every joke I tell is a machine I built with my own hands."**

The player wants to feel like a craftsperson AND a performer. The Bit Builder gives them the craftsperson fantasy -- the satisfaction of assembling components into something that works, the diagnostic clarity of understanding WHY it worked. The Crowd Engine gives them the performer fantasy -- the terror of a silent room, the electricity of a room that turns. The career arc gives them the empire fantasy -- watching doors open because you earned it, choosing which doors to walk through.

What's the loop? The loop is: build a joke, test it on a crowd, read the results, iterate. That's the 30-second heartbeat. Everything else -- career, economy, scene, voice -- exists to give that heartbeat stakes.

---

## 2. Core Loop

### 30-Second Loop: The Joke Workshop

Write/modify a joke using the Bit Builder. Drag component cards. See the Humor Profile shift in real time. Slot it into a setlist. This is the atomic creative act.

### 5-Minute Loop: The Set

Arrange setlist. Choose venue. Perform. Read crowd reactions via Laugh Graph. Use Pivot Points mid-set. Post-set: review per-joke breakdown, collect REP and cash, identify which bits to rework.

### Meta Loop: The Career Week (30-60 min session)

Book gigs. Write new material. Workshop bits at low-stakes venues. Perform at high-stakes gigs. Manage relationships with bookers, agents, and rivals. Spend REP to unlock new tiers. Shift or solidify your Voice Identity. Chase the next milestone.

### Core Loop Diagram

```
                    +------------------+
                    |   BIT BUILDER    |
                    | (Craft the Joke) |
                    +--------+---------+
                             |
                     Joke with Humor Profile
                             |
                             v
                    +------------------+
                    |  SETLIST BUILDER |
                    | (Arrange the Set)|
                    +--------+---------+
                             |
                     Ordered set + venue context
                             |
                             v
                    +------------------+
                    |   THE STAGE      |
                    | (Perform the Set)|<-------- Pivot Points
                    +--------+---------+         (mid-set swaps)
                             |
                     Real-time crowd reactions
                             |
                             v
                    +------------------+
                    |   LAUGH GRAPH    |
                    | (Read Results)   |
                    +--------+---------+
                             |
              +--------------+--------------+
              |              |              |
              v              v              v
        +----------+  +-----------+  +------------+
        |   REP    |  |   CASH    |  | DIAGNOSTIC |
        | (Career  |  | (Economy) |  | (What to   |
        |  unlock) |  |           |  |  rework)   |
        +----+-----+  +-----+-----+  +-----+------+
              |              |              |
              v              v              v
        +-----------+  +-----------+  +-----------+
        |  CAREER   |  |  ECONOMY  |  |    BIT    |
        |PROGRESSION|  |  CHOICES  |  |  BUILDER  |
        |(new venues|  |(agent,    |  | (iterate) |
        | new stakes)|  |merch,etc)|  |           |
        +-----------+  +-----------+  +-----+-----+
              |                              |
              +------------>-<---------------+
                         |
                   VOICE IDENTITY
                  (who are you becoming?)
                         |
                    THE SCENE
               (rivals, collaborators,
                industry dynamics)
```

How does this feel at hour 20? At hour 20, the player is deep in the 5-minute loop -- they have enough component cards that setlist construction is a real decision space, they've developed enough Voice Identity that career gating matters, and they have rivals they care about. The 30-second loop is still crisp because new component cards keep the Bit Builder fresh. The meta loop has enough branching (agent offers, venue unlocks, scene events) that each session has a unique texture.

---

## 3. Core Mechanics

### 3.1 The Bit Builder (Joke Construction System)

**Player verb**: Drag, snap, combine, iterate.

**Component Types (6)**:

| Component | Role | Required? | Cards at Launch |
|-----------|------|-----------|-----------------|
| **Premise** | The observation or idea. "What's the deal with..." The seed. | Yes | 80 |
| **Setup** | The framing that establishes context and audience expectations. | Yes | 60 |
| **Misdirection** | Where the audience THINKS you're going. The fake destination. | Yes | 50 |
| **Punchline** | The actual destination. The turn. The laugh trigger. | Yes | 70 |
| **Tag** | An extra punchline that rides the wave of the first laugh. Optional but powerful. | No | 40 |
| **Callback** | A reference to material performed earlier in the set. Requires a valid target joke. | No | N/A (generated from existing jokes) |

Total unique component cards at launch: approximately 300. Combinatorial space: conservative estimate of 50,000+ viable joke configurations before Tags and Callbacks.

**The Five Humor Axes**:

Every component card has stats from 0-10 on each axis. The joke's final Humor Profile is the weighted average of all its components, with the Punchline weighted at 2x (it dominates the joke's identity).

| Axis | Low End | High End | Example Low | Example High |
|------|---------|----------|-------------|--------------|
| **Cleverness** | Simple/direct | Layered/intellectual | "I'm so broke..." | "Schrodinger's bank account..." |
| **Relatability** | Niche/specific | Universal/shared | "As a left-handed cellist..." | "You ever stand in front of the fridge..." |
| **Edge** | Safe/clean | Dark/provocative | "My dog is silly" | "My therapist fired me" |
| **Absurdity** | Grounded/realistic | Surreal/bizarre | "Traffic was bad today" | "Traffic was sentient today" |
| **Physicality** | Cerebral/verbal | Physical/performative | Pure wordplay | Full-body impression |

**Humor Profile Calculation**:

```
For each axis A:
  JokeScore[A] = (Premise[A] + Setup[A] + Misdirection[A] + (Punchline[A] * 2) + Tag[A]) / (NumComponents + 1)
```

If no Tag is attached, its contribution is zero and the divisor adjusts accordingly.

**Joke Quality Score**: Beyond the Humor Profile, each joke has a Quality score (0-100) determined by:

- **Coherence** (0-30): How well do the components fit together thematically? Premise and Setup should share at least one thematic tag (e.g., "family," "technology," "food"). Mismatched themes reduce Coherence. Formula: `base_coherence = 20 * (shared_tags / total_tags)`. Bonus +10 if Misdirection and Punchline share the same Premise domain but diverge on approach.
- **Surprise** (0-30): The delta between the Misdirection's implied direction and the Punchline's actual direction. Measured as the Euclidean distance between the Misdirection's Humor Profile and the Punchline's Humor Profile across all five axes, normalized to 0-30. Higher distance = more surprise. `surprise = 30 * (euclidean_dist(Misdirection, Punchline) / max_possible_dist)`.
- **Timing** (0-20): Component word count. Each component has a Word Count stat. Setup + Misdirection should be 1.5x-2.5x the length of the Punchline. Outside that ratio, Timing drops. The "rule of threes" bonus: if the Setup establishes a pattern of three items with the Punchline breaking the pattern on the third, +10 Timing.
- **Tag Bonus** (0-10): A well-matched Tag (shares thematic tags with Punchline, has higher Edge or Absurdity than the Punchline) adds up to 10 points. A mismatched Tag subtracts up to 5.
- **Callback Multiplier** (1.0x-1.5x): Callbacks multiply the joke's Quality by 1.0x (poor connection to source joke) to 1.5x (strong thematic resonance AND high Surprise relative to the original). Callbacks that reference a joke the audience already laughed at during THIS set get an additional +0.1x multiplier.

**Depth**: A beginner grabs random cards and gets Quality scores of 15-30. They learn that matching themes raises Coherence. They learn that contrasting Misdirection and Punchline raises Surprise. They learn that tight Punchlines land harder. An expert reads a venue's crowd composition, identifies the dominant audience archetype preferences, then reverse-engineers jokes that hit those preferences while maintaining their Voice Identity. They build setlists with deliberate Callback chains -- Joke 3 references Joke 1, Joke 7 references both, and the Closer calls back to all three for a cascading multiplier. The ceiling is very high.

**Feedback**: The Bit Builder shows a real-time Quality estimate as you assemble. Color-coded: red (0-25), orange (26-50), yellow (51-70), green (71-85), gold (86-100). The Humor Profile radar chart updates live. When you snap a Punchline onto a Setup+Misdirection and the Surprise score jumps, there's a satisfying visual pop and audio cue -- the game rewards you for finding a good combination before you ever step on stage.

**Component Card Acquisition**: Cards are earned through:
- **Life Events** (random events in the career sim): 40% of new cards
- **Cultural Moments** (trending topics in the game world): 20% of new cards
- **Workshops** (spending time with other comedians): 20% of new cards
- **Observation Mode** (a passive activity you can schedule during the week): 15% of new cards
- **Theft** (stealing another comic's bit -- high risk, high reward, reputation consequences): 5% of new cards

Pacing target: 3-5 new component cards per in-game week during early career, tapering to 1-3 per week in late career as the player's existing library becomes the primary resource.

---

### 3.2 The Crowd Engine (Audience AI)

**Player verb**: Read, adapt, survive.

The audience is not a number. The audience is a room full of people with preferences, patience, and the power to make or break you.

**Audience Archetypes (9)**:

| Archetype | Cleverness Pref | Relatability Pref | Edge Pref | Absurdity Pref | Physicality Pref | Patience | Volatility | Viral Potential |
|-----------|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Comedy Nerds** | 9 | 4 | 6 | 8 | 3 | High (8) | Low (2) | Medium (5) |
| **Date Night Couples** | 4 | 9 | 3 | 5 | 6 | Medium (5) | Medium (4) | Low (2) |
| **Bachelor/ette Parties** | 2 | 6 | 7 | 7 | 9 | Low (3) | High (8) | High (8) |
| **College Students** | 5 | 7 | 8 | 7 | 6 | Low (4) | High (7) | High (9) |
| **Industry Scouts** | 8 | 5 | 5 | 6 | 4 | High (9) | Low (1) | Medium (6) |
| **Drunk Hecklers** | 1 | 3 | 5 | 4 | 8 | Very Low (1) | Very High (10) | High (7) |
| **Fellow Comedians** | 8 | 5 | 7 | 7 | 5 | High (7) | Low (3) | Medium (5) |
| **Podcast Listeners** | 7 | 8 | 6 | 5 | 3 | Medium (6) | Low (3) | Very High (10) |
| **Tourists/Casuals** | 3 | 8 | 2 | 6 | 7 | Medium (5) | Medium (5) | Low (3) |

**Crowd Composition**: Each venue defines a probability distribution of archetypes. The actual crowd for any given show is sampled from this distribution, introducing variance. You know the venue's typical composition (shown before booking), but the specific crowd on any given night varies by +/- 15%.

**Reaction Model**: Each audience cluster (grouped by table, 2-6 people per cluster) reacts to each joke independently. The reaction formula:

```
ReactionScore = DotProduct(JokeHumorProfile, ArchetypePreferences) / 50
              * JokeQuality / 100
              * MomentumModifier
              * FatigueModifier
```

- **DotProduct**: Normalized 0-1 alignment between what the joke IS and what the archetype LIKES.
- **JokeQuality**: The 0-100 score from the Bit Builder. Even a perfectly targeted joke falls flat if it's poorly constructed.
- **MomentumModifier**: Ranges from 0.7 (cold room, no laughs in the last two jokes) to 1.5 (hot room, three consecutive strong reactions). Momentum builds and decays. A single bomb joke reduces Momentum by 0.15. A strong laugh increases it by 0.1. This creates the "rolling" phenomenon -- once a room is hot, even medium jokes land. But once it cools, you need a big hit to recover.
- **FatigueModifier**: Starts at 1.0 and decreases by 0.02 per joke in the set. By joke 12, it's at 0.78. Longer sets are harder. Tags partially reset Fatigue for a cluster (successful Tags give a +0.05 Fatigue recovery to that cluster). This forces set length discipline.

**Reaction Outputs**: Each cluster's ReactionScore maps to a behavior:

| Score Range | Behavior | Visual/Audio |
|---|---|---|
| 0.0-0.15 | **Silence** | Nothing. Worst sound in comedy. |
| 0.16-0.30 | **Polite smile** | Slight head movement, no audio |
| 0.31-0.50 | **Chuckle** | Brief laugh audio, small Laugh Graph blip |
| 0.51-0.70 | **Solid laugh** | Clear laughter, medium Laugh Graph wave |
| 0.71-0.85 | **Big laugh** | Full laughter, table engagement, tall wave |
| 0.86-0.95 | **Eruption** | Sustained laughter, clapping, people leaning on each other, major spike |
| 0.96-1.0 | **Standing ovation moment** | Rare. The room breaks. People are crying. Phones come out. |

**Bleed Mechanic**: Crowd clusters influence adjacent clusters. A laughing table makes nearby tables 10% more likely to laugh (social proof). A walking-out table makes nearby tables 5% more likely to disengage. A heckler activates with probability `Volatility * (1 - current_ReactionScore)` -- bored, volatile audience members are heckle risks.

**Heckler System**: When a heckler activates, the player has three options:
1. **Ignore** -- Lose 0.1 Momentum, heckler has a 40% chance of escalating.
2. **Acknowledge** -- Spend a Pivot Point to deliver a pre-selected comeback. If the comeback's Quality is > 50, gain 0.15 Momentum (crowd respects the handle). If < 50, lose 0.2 Momentum.
3. **Engage** (stretch goal: Heckler Duel mini-game) -- High risk, high reward real-time response.

---

### 3.3 The Laugh Graph (Performance Feedback System)

**Player verb**: Analyze, diagnose, learn.

The Laugh Graph is displayed during AND after every set.

**During the set**: A real-time waveform at the bottom of the screen. The X-axis is time (joke by joke). The Y-axis is aggregate audience engagement. The waveform pulses with each reaction. The player sees peaks (laughs), valleys (silence), and can feel the momentum building or dying. Color shifts from blue (cold) to gold (hot) based on Momentum.

**After the set**: The full diagnostic view. This is where mastery happens.

Post-set Laugh Graph tabs:
1. **Overview**: The full waveform with joke labels. Hovering over a peak shows which joke, which components, and the Quality/Surprise/Timing breakdown.
2. **Per-Segment**: Breaks the audience into archetype clusters. Shows which segments laughed at which jokes. The player might discover that Comedy Nerds loved Joke 4 but Date Night Couples checked out. This informs future setlist construction for similar venues.
3. **Pivot Analysis**: If the player used Pivot Points, shows the counterfactual -- what the swapped-out joke's predicted performance would have been vs. what the swapped-in joke actually did.
4. **Setlist Flow**: Visualizes energy arc. Shows where momentum built, where it broke, where callbacks connected. Highlights the "kill chain" -- sequences of three or more jokes that each increased momentum.
5. **Comparison**: Layover the current set's graph against the previous performance of the same setlist at a different venue. Reveals how audience composition changes performance.

**Design intent**: The Laugh Graph is the bridge between "I don't know why that bombed" and "I know exactly why that bombed, and I know how to fix it." Without it, the Bit Builder is a guessing game. With it, the Bit Builder becomes a precision tool. This is where the depth lives.

---

### 3.4 Voice Identity System

**Player verb**: Commit, drift, discover.

Five spectra, each ranging from -10 to +10:

| Spectrum | -10 | +10 |
|----------|-----|-----|
| **Observation/Absurdism** | Pure observational (Seinfeld) | Pure absurdist (Mitch Hedberg) |
| **Clean/Dark** | Family-friendly (Jim Gaffigan) | Pitch-black (Anthony Jeselnik) |
| **Political/Personal** | All political (Hasan Minhaj) | All personal (Mike Birbiglia) |
| **Cerebral/Physical** | All wordplay (Steven Wright) | All physical (Kevin Hart) |
| **Warm/Confrontational** | Audience is your friend (John Mulaney) | Audience is your target (Bill Burr) |

**Tracking**: Every joke performed shifts the player's Voice Identity. A joke with Absurdity 8 and Cleverness 3 nudges the Observation/Absurdism spectrum toward Absurdism. The shift magnitude is proportional to the joke's Quality and the audience's reaction -- a joke that kills in front of 500 people shifts your Voice more than one that gets polite chuckles from 12.

**Voice Shift Formula**:
```
shift_per_axis = (joke_axis_score - 5) * 0.01 * audience_size_modifier * reaction_modifier
```
Where `audience_size_modifier` ranges from 0.5 (open mic, 10 people) to 3.0 (theater, 2000+ people), and `reaction_modifier` ranges from 0.5 (bombed) to 2.0 (eruption).

**Authenticity Score**: Ranges from 0-100. Starts at 50. Increases by 1 per set where the performed material's Humor Profile aligns with the player's current Voice Identity (within 2 points on each axis). Decreases by 2-5 per set where material deviates sharply from Voice Identity (more than 4 points on any axis).

Authenticity affects:
- **Fan loyalty**: High Authenticity (70+) means fans stick around through bad sets. Low Authenticity (below 30) means fans churn 3x faster.
- **Career gating**: Certain career milestones require minimum Authenticity. An HBO special requires 65+. A cult following podcast requires 75+.
- **REP multiplier**: Authenticity above 60 multiplies REP earnings by `1 + (Authenticity - 60) * 0.01`. At 100 Authenticity, REP earnings are 1.4x. Below 40, REP earnings are penalized by `1 - (40 - Authenticity) * 0.015`. At 0 Authenticity, REP earnings are 0.4x.

**Career Path Gating** (examples):
- Sitcom deal: requires Warm > +5, Clean > +3, Relatability average > 6 across material
- Late-night writing job: requires Cleverness average > 7, Cerebral > +4
- Cult podcast empire: requires Authenticity > 75, any strong Voice commitment (at least 3 axes beyond +/-7)
- Netflix hour special: requires minimum 60 Authenticity, minimum Tier 4 career, 20+ unique jokes with Quality > 70
- Theater touring: requires any Voice configuration, but minimum 500 dedicated fans and Authenticity > 55

**Strategic tension**: The highest-paying career paths (sitcom, Netflix) reward specific Voice configurations. The most artistically satisfying paths (cult following, respected-by-peers) reward extreme commitment to ANY voice. The player must choose: optimize for the market, or optimize for authenticity? The game does not judge either choice -- but it makes both choices feel meaningfully different.

---

### 3.5 The Scene (Rival and Collaborator AI)

**Player verb**: Navigate, ally, compete.

15 AI comedians populate the scene at game start, with 2-3 new ones emerging per in-game year and 1-2 retiring or flaming out.

**AI Comedian Properties**:
- **Voice Identity**: Same five spectra as the player, fixed at generation with minor drift over time.
- **Skill Level**: 1-100, increases over time (faster for some, plateaus for others). Determines the average Quality of their jokes.
- **Career Tier**: Same tier system as the player. They progress independently.
- **Ambition**: Low/Medium/High. Determines how aggressively they pursue opportunities.
- **Personality**: Generous/Neutral/Cutthroat. Determines behavior in interactions.
- **Relationship with Player**: -100 (bitter rival) to +100 (ride-or-die collaborator). Starts at 0. Modified by player actions.

**Interactions**:
- **Gig Competition**: When you and an AI comic both want the same gig slot, the booker picks based on: REP (40%), relationship with booker (30%), Voice fit for the venue (30%). If you lose a slot to a rival, it stings. If you bump a friend, relationship drops.
- **Material Overlap**: If your joke has a Humor Profile within 1.5 Euclidean distance of an AI comic's existing bit, and they performed it at a bigger venue first, your joke gets a "Derivative" tag. Quality penalty of -15. The audience has heard something like this. You either rework it or eat the penalty. If YOU performed first and the AI steals it: your version keeps priority, their relationship drops by 20, and the scene gossips (other AI comics' relationship with the thief drops by 5).
- **Collaboration**: Comics with relationship > 50 can be invited to collaborate. Options include co-writing sessions (both players gain 2-3 component cards with shared thematic tags), podcast guesting (REP boost for both), and tour support (they open for you or vice versa, shared audience bleed of 10-15%).
- **Rivalry**: Comics with relationship < -30 become active rivals. They target your gig slots, their fans trash you on social media (slight REP drain), and beating them at the same venue gives a 1.5x REP bonus ("the crowd loves a rivalry").
- **Scene Events**: Periodic events create drama -- a comic gets cancelled, a comic gets a surprise Netflix deal, a club closes, a new club opens, a comedy festival invites applications. These are decision points: do you support the cancelled comic (relationship boost with them, potential REP risk) or distance yourself (safe but cold)?

**AI Career Arcs**: Each AI comic has a narrative arc sampled from templates: Steady Climber, Flash in the Pan, Late Bloomer, Burnout and Comeback, The Sellout, The Purist. These arcs determine their trajectory and create story beats that the player encounters naturally. You watch a fellow open-mic-er become a headliner. You watch a headliner flame out. The scene feels alive because it is -- these aren't static NPCs, they're parallel careers.

---

### 3.6 Career Progression Tiers

**Player verb**: Climb, choose, sacrifice.

| Tier | Name | Venues | Audience Size | REP to Unlock | What Changes |
|------|------|--------|:---:|:---:|---|
| 0 | **The Bomb** | Your apartment (writing only) | 0 | Start here | Tutorial. Bit Builder introduction. No performing yet. |
| 1 | **Open Mic** | Dive bars, coffee shops, laundromats | 8-25 | 0 (after tutorial) | First performances. Crowds are 50%+ fellow comics. Low stakes, low pay. Learning the Laugh Graph. |
| 2 | **Barker/Regular** | Comedy club guest spots, bar shows | 30-80 | 100 REP | Real audiences. Hecklers appear. First agent contact. Setlists expand to 8 jokes. Rival system activates. |
| 3 | **Featuring Act** | Comedy club feature spots, college shows, corporate gigs | 60-200 | 500 REP | Opening for headliners. Crowd Engine adds Industry Scouts. Voice Identity system fully active. Agent negotiations begin. Setlists expand to 12 jokes. |
| 4 | **Headliner** | Comedy club headlining, small theaters, festival slots | 150-800 | 2,000 REP | You're the name on the marquee. Merch unlocks. Podcast option unlocks. Touring becomes available. Setlists expand to 15+ jokes. |
| 5 | **Draw** | Theaters, large festivals, late-night TV appearances | 500-3,000 | 8,000 REP | TV appearances. Special taping becomes available. National touring. Fan demographics become granular. The "stay authentic or go broad" decision reaches maximum pressure. |
| 6 | **Empire** | Arenas, HBO/Netflix specials, development deals | 2,000-15,000+ | 25,000 REP | Endgame. Multiple revenue streams. Legacy decisions. The question becomes: what kind of comic do you want to be remembered as? |

**Pacing**: Tier 0 lasts approximately 15-20 minutes (tutorial). Tier 1 lasts 1-2 hours. Tier 2 lasts 2-4 hours. Tier 3 lasts 3-5 hours. Tier 4 lasts 4-6 hours. Tier 5 lasts 4-8 hours. Tier 6 is open-ended. Total approximate time to reach Tier 6: 15-30 hours depending on playstyle. The game does not end at Tier 6 -- it opens up.

**What changes at each tier** (besides audience size):

- **Tier 1 to 2**: Stakes matter. You can actually bomb in a way that costs you REP. The Laugh Graph becomes your best friend. Material reworking becomes essential -- you can't just write new jokes, you have to make the ones you have BETTER. Rival comics appear and compete for the same guest spots.
- **Tier 2 to 3**: The crowd diversifies. College shows have completely different compositions than club shows. Corporate gigs pay 3x but restrict your Edge axis (keep it below 4 or the booker never calls again). The Voice Identity system activates fully, and the player starts seeing career paths diverge based on their comedic identity.
- **Tier 3 to 4**: The headliner shift. You're no longer warming up someone else's crowd -- you're building your own. Fan acquisition and retention become explicit mechanics. The economy opens up (merch, podcast, touring). Agent relationship becomes critical -- a good agent means better gigs, but they take a cut.
- **Tier 4 to 5**: Media enters. Late-night sets are 5-minute performances with extremely specific requirements (Clean or mild Edge only, high Cleverness, the set must be self-contained with no callbacks to material the TV audience hasn't seen). Festival slots are industry showcases where a great set can jump you forward, and a bad one can stall you for months. The pressure ratchets.
- **Tier 5 to 6**: The special. The culminating performance. A 60-minute set performed at a specific venue, taped for distribution. The special requires a curated setlist of your best material, arranged with a narrative arc. The Crowd Engine runs at maximum complexity -- the audience is huge, diverse, and the stakes are existential. After the special, the game shifts into empire management: touring, development deals, and the question of what comes next.

---

## 4. Systems Interaction Map

Every system feeds into every other. Here's the full map.

```
BIT BUILDER -----> CROWD ENGINE
  (joke quality +     (audience reaction
   humor profile)      depends on joke fit)
       ^                      |
       |                      v
       |               LAUGH GRAPH
       |              (diagnostic data)
       |                      |
       +----------<-----------+
       (rework informed       |
        by graph data)        |
                              v
                        REP + CASH
                     (earned from sets)
                          |       |
            +-------------+       +----------+
            v                                v
     CAREER PROGRESSION                 ECONOMY
     (new venues, new                  (agent, merch,
      audience compositions,            podcast, touring)
      new stakes)                           |
            |                               |
            v                               v
      CROWD ENGINE                    VOICE IDENTITY
     (higher-tier venues =            (economy choices
      harder, more diverse             affect perceived
      audiences)                       authenticity)
            |                               |
            +-------------+-----------------+
                          |
                          v
                     THE SCENE
                 (rivals react to your
                  career moves, audience
                  overlap, material similarity)
                          |
                          v
                    GIG AVAILABILITY
                 (scene dynamics affect
                  which slots you can book)
                          |
                          v
                     BIT BUILDER
                (scene interactions generate
                 new component cards and
                 constrain material choices)
```

**Positive Feedback Loops** (snowball potential):
- Good jokes -> good crowd reactions -> high REP -> better venues -> bigger audiences -> more REP per set. This is the core growth engine.
- High Authenticity -> loyal fans -> consistent attendance -> stable REP income -> freedom to take creative risks.
- Strong Scene relationships -> collaboration -> shared audiences -> faster fan growth.

**Negative Feedback Loops** (rubber banding):
- Higher-tier venues have harder, more diverse audiences. You can't brute-force your way up with a narrow setlist. The game forces adaptation.
- FatigueModifier ensures longer sets are harder. You can't just add more jokes to compensate for weak material.
- Authenticity penalty for voice-shifting means rapid pivots have a real cost. You can't chase every trend.
- Material staleness: Jokes performed more than 5 times at the same venue tier lose 5% Quality per additional performance (audiences talk; material gets "known"). This forces constant Bit Builder engagement and prevents solved setlists.
- Rival comics who match your Voice Identity create audience competition -- if they're rising faster, your fan growth slows.

**Emergent Possibilities**:
- A player who focuses exclusively on Dark/Confrontational comedy builds a small but fiercely loyal cult following. They can't get the sitcom deal, but they can sell out 500-seat theaters in 15 cities and launch a podcast that outsells any of the mainstream comics. Different routes to the same tier.
- A player who steals material gets a short-term quality boost but risks scene-wide reputation damage when it's discovered. The risk/reward creates genuine moral decision points.
- A player who invests heavily in one rival relationship can ride the coattails of that rival's success -- touring together, benefiting from their audience bleed. But if the rival burns out or sells out, the player loses that infrastructure.

---

## 5. Progression Design

### Unlock Pacing

| Hours Played | What's New |
|:---:|---|
| 0-0.5 | Tutorial: Bit Builder basics, first joke assembly, apartment writing space |
| 0.5-1 | First open mic. Laugh Graph introduction. First crowd reactions. |
| 1-2 | First Rival encounter. Workshop mechanic unlocks (collaboration for new cards). Setlist building (3-5 jokes). |
| 2-3 | Tier 2 unlock. Real venues. Heckler system activates. Pivot Points introduced. Agent makes first contact. |
| 3-5 | Voice Identity tracker becomes visible. Player sees how their material choices shape their comedic identity. Cultural Moment system activates (trending topics generate new Premise cards). |
| 5-8 | Tier 3 unlock. College shows and corporate gigs introduce audience-specific constraints. Callback mechanic fully explained and encouraged (was available before but not spotlighted). |
| 8-12 | Tier 4 unlock. Headlining. Merch system. Podcast option. Touring. Economy complexity increases. Scene events become more dramatic (rivals blowing up, clubs closing). |
| 12-18 | Tier 5 unlock. Late-night TV sets. Festival circuit. Special taping preparation begins. Fan demographics become granular. The "do I stay true or go broad?" tension peaks. |
| 18-30 | Tier 6 unlock. The Special. Empire management. Legacy decisions. Endgame opens. |
| 30+ | Sandbox / Legacy mode. New challenges, different starting cities, different Voice commitments. |

### Difficulty Curve

The difficulty is stepped, not linear. Each tier transition is a significant jump:
- **Tier 1 to 2**: Audience expectations jump. You need jokes with Quality 40+ to get consistent laughs.
- **Tier 2 to 3**: Crowd diversity forces adaptation. A single setlist no longer works at every venue.
- **Tier 3 to 4**: Fan retention becomes a mechanic. You need new material regularly to keep fans engaged.
- **Tier 4 to 5**: Media appearances have strict requirements. The player must craft material specifically for TV constraints.
- **Tier 5 to 6**: The Special requires a 60-minute set with a narrative arc. This is the ultimate test of everything the player has learned.

The game never becomes "easy" at higher tiers because the Crowd Engine scales in complexity, material staleness forces constant iteration, and the Scene creates competitive pressure. At hour 20, a player who coasted to Tier 4 on a narrow Voice will feel the walls closing in as audiences demand more range. How does this feel at hour 20? It feels like the real game just started.

---

## 6. Economy Design

### Currencies

**REP (Reputation)**: The progression currency. Earned through performances. Spent to unlock tiers, access new venues, and attract agents. Cannot be purchased. Must be earned.

**CASH**: The operating currency. Earned through gig payouts, merch sales, podcast revenue, special deals. Spent on rent (yes, you can get evicted if you can't afford your apartment -- back to couch-surfing at the Tier 1 venue), workshop fees, travel, agent retainers, and production costs.

### REP Earnings by Venue Tier

| Tier | Base REP per Set | Quality Multiplier | Crowd Reaction Multiplier |
|:---:|:---:|---|---|
| 1 | 5 | Quality/100 (so a 50-quality average set = 0.5x = 2.5 REP) | Average ReactionScore * 2 (0-2x) |
| 2 | 15 | Same formula | Same formula |
| 3 | 40 | Same formula | Same formula |
| 4 | 100 | Same formula | Same formula |
| 5 | 250 | Same formula | Same formula |
| 6 | 500 | Same formula | Same formula |

**REP Earning Formula**:
```
REP_earned = BaseREP * (AvgJokeQuality / 100) * (AvgReactionScore * 2) * AuthenticityMultiplier * ViralBonus
```

- **AuthenticityMultiplier**: Described in Voice Identity section (0.4x to 1.4x).
- **ViralBonus**: If any joke in the set triggers a "viral moment" (at least one Podcast Listener or College Student cluster hits 0.90+ reaction), ViralBonus = 1.5x. Otherwise 1.0x.

A great set at a Tier 1 open mic: `5 * 0.7 * 1.6 * 1.1 * 1.0 = 6.16 REP`. Slow start.
A great set at a Tier 4 headliner: `100 * 0.8 * 1.7 * 1.2 * 1.5 = 244.8 REP`. Momentum.
A mediocre set at a Tier 5 theater: `250 * 0.5 * 0.8 * 0.9 * 1.0 = 90 REP`. Higher tier doesn't guarantee higher REP.

### CASH Payouts by Venue Tier

| Tier | Base Payout | Notes |
|:---:|:---:|---|
| 1 | $0-15 | Most open mics pay nothing. Some give a bar tab. |
| 2 | $25-75 | Guest spots. Inconsistent. Some are "exposure." |
| 3 | $100-400 | Feature spots. Corporate gigs pay $300-600 but restrict Edge. |
| 4 | $500-2,000 | Headlining. Consistent income. |
| 5 | $2,000-8,000 | Theater shows. Festival guarantees. Late-night appearance bonus $5,000. |
| 6 | $10,000-50,000+ | Specials ($50K-250K one-time). Arena tours ($15K-50K per show). |

### Agent System

Agents appear at Tier 2 and become essential by Tier 3.

| Agent Tier | Cut | What They Provide |
|---|:---:|---|
| **No Agent** | 0% | You book everything yourself. Limited to Tier 1-2 venues. |
| **Small Agent** | 10% | Access to Tier 3 venues. Basic gig pipeline (2-3 offers per week). |
| **Mid Agent** | 15% | Access to Tier 4 venues. Better gig pipeline (4-5 offers per week). Media connections. |
| **Top Agent** | 20% | Access to Tier 5-6 venues. Premium pipeline. Special deals. TV bookings. Festival invitations. |

Agents have their own relationship score (0-100). Below 30, they drop you. Above 70, they go to bat for you (better negotiation, more offers). Relationship is maintained by: performing well at booked gigs (+5 per successful set), taking their advice (+3), and staying active (+1 per week with at least 2 gigs). Relationship decreases by: bombing (-10), canceling gigs (-15), and going silent (-3 per inactive week).

### Secondary Revenue Streams (Tier 4+)

**Merch**: Unlocks at Tier 4. Passive income of `$FanCount * 0.05 * MerchQuality` per week. MerchQuality is 1-3 based on investment. Costs $500 to set up, $200/month to maintain.

**Podcast**: Unlocks at Tier 4. Weekly show. Revenue = `$ListenerCount * 0.01` per episode. Listeners grow based on your REP growth rate and guest quality (AI comic collaborators boost listener growth by 20% per appearance). Requires 2 hours of in-game weekly time (opportunity cost vs. writing/performing).

**Touring**: Unlocks at Tier 4. Multi-city runs. Revenue = sum of individual show payouts with a 1.3x touring bonus. Costs include travel ($200-$1,000 per city) and the opportunity cost of not being in your home scene for 2-4 in-game weeks.

**Special Deals**: Tier 5-6. One-time payouts. Netflix/HBO special: $50K-$250K depending on negotiation (agent relationship and REP affect the offer). Sitcom development deal: $25K upfront + $5K/week for the development period. These are major career milestones, not recurring income.

### Economic Pressure

The economy is designed to create meaningful resource tension at every tier:
- **Tier 1-2**: You're broke. Rent is $400/month. Gig income barely covers food. The pressure is survival. Writing is free; performing is free. The only cost is time.
- **Tier 3**: You can pay rent but you can't save. Workshop fees ($50-100), travel to gigs ($20-50), and the temptation to invest in better material through paid workshops creates spending decisions.
- **Tier 4**: Income stabilizes but expenses scale. Agent cut, merch setup, podcast production costs, touring expenses. The player feels the transition from "trying to survive" to "trying to grow."
- **Tier 5-6**: Money is abundant but the stakes are existential. A failed special costs months of momentum. A bad touring decision costs both money and scene presence. The economy shifts from "can I afford this?" to "is this the right investment of my time and brand?"

---

## 7. Risk Assessment

### Risk 1: The Bit Builder Feels Like a Spreadsheet

**The danger**: If assembling jokes feels like optimizing stat combinations rather than writing comedy, the core fantasy dies. The player wanted to feel like a comedian; instead they feel like a min-maxer.

**Mitigation**: Thematic tags on components. Every Premise card has a human-readable topic ("airport security," "dating apps," "my mother"). Every Punchline has a human-readable payoff ("the twist is that I was the problem all along"). The player is not combining numbers -- they're combining ideas that happen to have numbers underneath. The UI emphasizes the text, not the stats. The stats inform the Humor Profile and Quality score, but the player reads "Setup: My mother always said I'd amount to something" + "Punchline: She was wrong, but statistically so was she" and LAUGHS. If the components are well-written, the Bit Builder feels like joke writing, not data entry.

**Playtest priority**: HIGH. Test with non-gamers. Do they read the joke or the numbers?

### Risk 2: Crowd Engine Feels Random

**The danger**: If the player can't predict or understand why a joke bombed, the Laugh Graph is noise and the iteration loop breaks. The player shrugs and says "I guess audiences are random" and stops engaging with the system.

**Mitigation**: The Laugh Graph's per-segment breakdown is the key. It must be clear. "Comedy Nerds (35% of audience): ReactionScore 0.72 -- they loved the Cleverness. Date Night Couples (25% of audience): ReactionScore 0.22 -- Edge was too high for this segment." The player must be able to look at the data and say "I know what to change." Pre-show venue composition display must be prominent: before you book a gig, you see the expected crowd breakdown and their preference profiles. If the player chose to perform high-Edge material at a Date Night venue, the feedback should make it obvious that was the mismatch.

**Playtest priority**: VERY HIGH. The legibility of failure is the entire game.

### Risk 3: Solved Setlists

**The danger**: Players find one optimal setlist and repeat it forever. The game becomes rote.

**Mitigation**: Multiple layers.
1. Material staleness: -5% Quality per repeat at the same tier.
2. Dynamic crowd composition: +/-15% variance per show means no setlist is optimal every night.
3. Cultural Moments: Trending topics create relevance bonuses that shift weekly. Last week's perfect opener might be stale this week.
4. Rival material overlap: If a rival performs similar material at a bigger venue, your version gets the Derivative tag.
5. Tier transitions change audience composition entirely: the setlist that killed at Tier 2 clubs won't work at Tier 3 college shows.

**Playtest priority**: HIGH. Monitor if players rearrange setlists or just replay the same one.

### Risk 4: Voice Identity System Feels Punishing

**The danger**: Players feel trapped by their early Voice choices. They want to experiment but the Authenticity penalty is too harsh. They feel punished for being creative.

**Mitigation**: Authenticity recovery must be tunable. Current design: Authenticity recovers at 1 point per set that aligns with your current Voice. If it takes 20+ sets to recover from a creative experiment, that's too harsh. Consider: Authenticity penalty is front-loaded (large initial drop) but recovery is faster than accumulation. Going from 70 to 55 after 3 experimental sets, recovering to 65 after 5 aligned sets. The player feels the cost but isn't stuck in a hole. Additionally, certain career paths explicitly REWARD Voice shifts (the "reinvention" arc), giving players who want to experiment a narrative framework for doing so.

**Playtest priority**: MEDIUM-HIGH. Survey players: do you feel free to experiment?

### Risk 5: The Mid-Game Grind (Tier 3-4)

**The danger**: The early game is exciting (everything is new) and the late game is exciting (huge stakes, empire management). The mid-game -- where you're grinding feature spots and building a fan base -- could feel like a treadmill.

**Mitigation**: The Scene must carry the mid-game. Tier 3-4 is where rival dynamics peak. The player has enough presence to attract rivals and enough ambition to seek collaborators. Scene events should spike in frequency during this phase: a rival steals your material, a club owner offers you a residency, a comedy festival announces applications, a fellow comic has a breakdown. The mid-game should feel like a drama, not a grind. Mechanically, the Callback system reaches maturity here (enough jokes in the library to build complex callback chains), which adds strategic depth to the Bit Builder that wasn't available earlier.

**Playtest priority**: HIGH. Track session length and quit rates at Tier 3-4.

### Risk 6: Component Card Acquisition Feels Grindy

**The danger**: The player runs out of interesting component cards and the Bit Builder stagnates. Or they're flooded with cards and the selection is overwhelming.

**Mitigation**: Pacing targets are critical. 3-5 cards per in-game week in early career, tapering to 1-3 in late career. But late-career cards should be HIGHER quality and more specific -- they enable nuanced jokes that early cards can't. The library management UI needs a filter/sort system so 300+ cards don't feel like a mess. Cards should be categorizable by topic, by axis strength, and by component type. The player should feel like they're building a joke-writing toolkit, not drowning in clutter.

**Playtest priority**: MEDIUM. Track Bit Builder session times -- are they increasing (overwhelm) or decreasing (boredom)?

### Risk 7: The Economy Doesn't Matter

**The danger**: If REP is the only currency that matters and CASH has no teeth, the economy is decorative. The player ignores money and just chases REP.

**Mitigation**: Rent is real. If you can't pay rent, you lose your apartment and move to a shared space with fewer writing hours per week (reduced component card acquisition). Agent fees are mandatory -- no agent, no Tier 3+ venues. Touring costs money upfront before it pays off. The Special requires production investment ($5,000-20,000 depending on venue quality). CASH must create decision points: "I can afford the podcast OR the touring run, not both. Which grows my career faster?"

**Playtest priority**: MEDIUM. Track player cash balance curves. If everyone is always flush, the economy is too generous.

---

## 8. Open Questions for Playtesting

1. **Bit Builder component count**: Is six types (Premise, Setup, Misdirection, Punchline, Tag, Callback) the right number? Playtest with five (drop Misdirection, fold it into Setup) and compare satisfaction scores.

2. **Pivot Point count per set**: Currently undefined. Start with 2 Pivot Points per set at Tier 1, scaling to 4 at Tier 5. Test if this creates enough mid-set agency without making pre-set planning irrelevant.

3. **Audience cluster size**: Currently 2-6 people per cluster. Test with individual audience member simulation at small venues (Tier 1-2) vs. cluster simulation at large venues (Tier 4+). Does individual simulation add meaningful feedback or just noise?

4. **Material staleness rate**: -5% per repeat. Is this too aggressive? Test with -3% and -7% variants. The goal: players should WANT to write new material, not feel FORCED to.

5. **Callback chain depth**: How many callbacks-to-callbacks does the system support before the math gets absurd? Cap at 3 layers (joke A -> callback to A in joke B -> callback to B in joke C) or let it go deeper?

6. **Cultural Moment frequency**: How often should trending topics rotate? Weekly feels right for in-game time. Test if players engage with the system or ignore it.

7. **AI comedian count**: 15 at launch. Is that enough to make the scene feel alive? Too many to track? Test with 10 and 20.

8. **Session length**: Target is 30-60 minutes per session. Track actual session lengths. If players consistently play 90+ minutes, the session loop is too long (no natural stopping points). If they consistently play under 20 minutes, the engagement is too shallow.

9. **Voice Identity drift speed**: How fast should the Voice shift per performance? Too fast and it feels volatile. Too slow and it feels static. The current formula may need a damping factor for established voices (100+ performances should shift very slowly).

10. **Heckler frequency**: Too many hecklers and the game feels adversarial. Too few and an entire system goes unused. Test with 5%, 10%, and 15% heckler activation rates per set at Tier 2+ venues.

---

*This document was designed by REED. The game lives or dies on one question: does the 30-second loop -- assembling a joke in the Bit Builder, stepping on stage, hearing the crowd react -- feel like a creative act? Not a math problem. Not a slot machine. A creative act where the player MADE something and the world RESPONDED. If that loop sings, everything else is amplification. If it doesn't, no amount of career simulation saves it. Test the loop first. Test it with ten people. Watch their faces when the room laughs. That's your answer.*
