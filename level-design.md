# DEADPAN — Level Design Document

*Written by GRID, Level Designer*
*Where does the player LOOK? What's the pacing here? Every room teaches something.*

---

## 1. DESIGN PHILOSOPHY

### The Core Spatial Truth

In Deadpan, the "levels" are performance venues. Each venue is a lesson in spatial pressure, audience psychology, and emotional pacing. The player doesn't traverse physical space — they traverse ATTENTION SPACE. The critical path isn't "how do I get from A to B?" It's "how do I get from a cold room to a hot room?" The sightlines aren't literal — they're the invisible geometry of who's watching whom, who influences whom, and where the energy flows.

**Every room teaches something**:
- The dive bar open mic teaches SURVIVAL under indifference
- The comedy club teaches FLOW under scrutiny
- The green room teaches VULNERABILITY under fluorescents
- The theater teaches PACING under expectation
- The late-night studio teaches CONTROL under production

The player moves through these spaces not by walking, but by EARNING ACCESS. Each venue is a tier gate, a difficulty spike, and an emotional beat. The level design challenge is making each space feel spatially and emotionally DISTINCT — not just through art, but through the MECHANICS of how audiences behave in that geometry.

### Spatial Design Principles for Performance Spaces

1. **Proximity determines intimacy**. Small rooms create intimacy (15 people, eye contact possible). Large rooms create spectacle (2,000 people, anonymous mass). The player must FEEL the difference in how they perform.

2. **Sightlines are bidirectional**. The player sees the audience. The audience sees the player. But more importantly: audience members see EACH OTHER. A laughing table makes adjacent tables more likely to laugh (social proof). A walking-out couple makes nearby clusters disengage. The spatial arrangement of the audience affects behavior.

3. **The green room is the decompression chamber**. Every venue has one. It's the space between performances where the REAL emotional content lives. The green room's spatial design (cramped vs. spacious, private vs. communal) determines the social dynamics.

4. **Entry and exit paths tell stories**. How does the player get to the stage? Through the crowd (vulnerable, exposed)? From backstage (separated, elevated)? The approach to the mic is a breadcrumb trail of mounting pressure.

5. **The spotlight is the eye of the storm**. Once the player is on stage, the space contracts to a cone of light. The vast room becomes irrelevant. The player's focus narrows to the mic, the Laugh Graph, and the faces in the first three rows. This narrowing must be FELT spatially.

---

## 2. VENUE TAXONOMY — THE PROGRESSION LADDER

Each tier represents a distinct spatial challenge and emotional lesson.

### TIER 0: THE APARTMENT (Tutorial Space)

**Purpose**: Teach the Bit Builder without performance pressure. The safe space.

**Emotional Beat**: Rebuilding belief after bombing. Intimacy with self.

**Spatial Layout**:
```
+------------------+
|   [WINDOW]       |
|                  |
|  [DESK]          |  <- Bit Builder interface lives here
|   - Corkboard    |
|   - Napkins      |
|                  |
|      [COUCH]     |  <- Rest/reflection space
|                  |
|  [KITCHENETTE]   |
+--------+---------+
         |
    [DOOR to world]
```

**Flow**: Player begins at desk. Camera tight, claustrophobic. The room is small but YOURS. No audience. No pressure. Just you and the components. The window shows the city at night — other lights, other lives, other stages. The visual breadcrumb: the world is out there. You're not ready yet. But you will be.

**Pacing Curve**: FLAT. This is the zero-energy baseline. The player should feel the ABSENCE of performance pressure, which makes the first open mic entrance feel like stepping off a cliff.

**Metrics to Track**:
- Time spent in Bit Builder (should be 3-5 minutes)
- Number of jokes assembled before first venue unlock (target: 2-3)
- Tutorial completion rate

**Difficulty Note**: No difficulty. This is the breathing room before the plunge.

---

### TIER 1: THE DIVE BAR OPEN MIC (Democracy Room)

**Purpose**: Teach that SURVIVAL is success. Teach reading a hostile/indifferent room. Teach that silence is louder than you think.

**Emotional Beat**: Terror and exhilaration. The first time you make a stranger laugh is electric. The first time you bomb is devastating.

**Spatial Layout (Top-Down)**:
```
    [DOOR—ENTRANCE]
          |
    +-----+----------------------+
    |  REGULARS    REGULARS     |
    |   (bar)       (bar)        |
    |                            |
    |  [TABLE]    [TABLE]        |
    |   Date       Drunk          |
    |                            |
    |        [STAGE CORNER]      |
    |         * MIC              |  <- Clip light above
    |         (no elevation)     |
    |                            |
    | [TABLE]           [TABLE]  |
    | Comics            Comics   |
    | waiting           waiting  |
    |                            |
    |              [BATHROOMS]   |  <- Stage is NEAR bathrooms
    +----------------------------+
```

**Flow Diagram**:
- **Entry**: Player enters through main door. Crosses the entire room to reach stage corner. EXPOSED walk. Every eye on you (the ones that care).
- **Approach**: No backstage. You stand by the comics' tables until your name is called, then walk 15 feet to the mic. That 15 feet is the longest distance in comedy.
- **Performance Zone**: Corner stage. No elevation. You're AT audience level. Eye contact is unavoidable with front tables. The Regulars at the bar aren't even facing you — they're watching the game on TV.
- **Exit**: Walk back through the room. If you killed, it's a victory lap. If you bombed, it's a walk of shame.

**Pacing Curve**:
```
Tension
   ^
 8 |                    *peak: 1st punchline
 7 |                   /|\
 6 |                  / | \
 5 |      *approach  /  |  \  *aftermath
 4 |     /          /   |   \
 3 |    /          /    |    \___
 2 |___/          /     |        \___
 1 |_____________/      |            \____
   +-----|-----|-----|-----|-----|-----|----> Time
      Entry  Walk   Mic   Perform  Off   Exit
              up          (3-5min) stage
```

**Encounter Breakdown**:

| Encounter | What | Where | Why |
|-----------|------|-------|-----|
| **The Walk** | Cross the room to the stage | Entry → Stage | Tests courage. Every eye on you. Breadcrumb: the mic glows under clip light. |
| **The Mic Grab** | Touch the mic, adjust stand | Stage corner | Ritual. Grounding moment. Player takes ownership of space. |
| **Set: Joke 1** | First joke delivery | Stage | Cold open. Room is neutral. This joke determines Momentum. |
| **Set: Joke 2-4** | Core material | Stage | Momentum builds or dies here. Crowd Engine fully active. |
| **Set: Pivot Point** | Mid-set decision | Stage | If bombing, can swap upcoming bit. Tests real-time reading. |
| **Set: Closer** | Final joke | Stage | Last impression. Shape of Laugh Graph's ending. |
| **The Walk Back** | Return to comics' table | Stage → Table | Emotional decompression. Delia may or may not look up. |

**Breadcrumbing Strategy**:
- **Visual**: Clip light above stage corner is the ONLY bright spot in a dim bar. Player's eye is drawn there immediately.
- **Audio**: Muffled conversation. Clink of glasses. Low-energy ambiance. When the MC says your name, the audio dips slightly — the room's attention shifts.
- **Social**: Other comics wait at tables. Their body language (phone-checking, notebook-writing) signals this is routine for them, terrifying for you.
- **Mechanical**: Tutorial prompts appear as napkin notes in the HUD. "You're third up. That's a good slot — warm but not late."

**Difficulty Considerations**:

| Factor | Setting | Impact |
|--------|---------|--------|
| Audience Patience | Low (3/10) | Faster loss of Momentum if jokes don't land |
| Crowd Composition Variance | High (+/- 15%) | Each night feels different |
| Heckler Risk | 5% per set | Low but present. Keeps player alert. |
| Material Staleness Penalty | None | First-time venue. Everything is fresh. |

**Playtesting Metrics**:
- **First set completion rate** (target: 95%+)
- **Time to first laugh** (should be within first 2 jokes)
- **Bomb rate on first attempt** (expect 40-50% — this is intended)
- **Return rate after first bomb** (target: 80%+; if lower, emotional recovery pacing is too harsh)

**Variants**:
- **Tuesday 8 PM Open Mic**: 60% comics, 20% regulars, 20% random. Toughest crowd. Best learning environment.
- **Friday 10 PM Open Mic**: 40% comics, 30% date night, 30% college. Easier crowd, more chaotic energy.
- **Sunday Afternoon**: 50% comics, 30% casuals, 20% tourists. Weird energy. Everything feels slightly wrong. Advanced difficulty.

---

### TIER 2: THE COMEDY CLUB — GUEST SPOT (Politics Room)

**Purpose**: Teach that RELATIONSHIPS matter as much as material. Teach the booker gate. Teach the two-drink minimum audience (slightly drunk, slightly generous, slightly unpredictable).

**Emotional Beat**: Pride and pressure. You're in a REAL room. This is Joan's domain. The brick wall has history.

**Spatial Layout (Top-Down)**:
```
         [LOBBY/ENTRANCE]
                |
    +-----------+-----------------+
    |                             |
    |  [STAGE - ELEVATED 18"]     |  <- Brick wall backdrop
    |     * MIC  (spotlight)      |
    |     [STOOL] [MIC STAND]     |
    |                             |
    |   TABLE  TABLE  TABLE       |  <- First 3 rows
    |   TABLE  TABLE  TABLE       |     (6-top tables)
    |   TABLE  TABLE  TABLE       |
    |                             |
    |         [AISLE]             |
    |                             |
    |   TABLE  TABLE  TABLE       |  <- Back rows
    |   TABLE  TABLE  TABLE       |
    |                             |
    |        [BAR - rear]         |  <- Regulars hang here
    |                             |
    +----+-------------------+----+
         |                   |
    [GREEN ROOM]         [BATHROOMS]
```

**Green Room (Critical Space)**:
```
+------------------------+
| [MIRROR w/ dead bulbs] |
|                        |
|    [COUCH - sagging]   | <- Where comics wait
|                        |
| [WHITEBOARD - setlist] | <- Tonight's order
|    1. Sarah (MC)       |    in dry-erase
|    2. PLAYER           |
|    3. Delia            |
|    4. Marcus (closer)  |
|                        |
|  [DOOR to STAGE]       | <- Tape over latch
|  (taped latch)         |
+------------------------+
```

**Flow Diagram**:
```
Entry (lobby)
    → Green Room (wait, anxiety builds)
    → Hear MC through wall (muffled, anticipation)
    → MC calls your name
    → Door to stage (tape over latch — ritual detail)
    → Stage (elevated, spotlight hits, 60-80 people watching)
    → Perform (5-7 minutes, Crowd Engine at medium complexity)
    → Exit to green room (Delia is next, she's watching her phone)
    → Post-set analysis (Laugh Graph review, Joan's face when you passed her)
```

**Pacing Curve**:
```
Tension
   ^
10 |                        * CLOSER (joke 6-7)
 9 |                       /|
 8 |                   *  / |
 7 |                  /| /  |
 6 |      *GREEN     / |/   |      *aftermath
 5 |     / ROOM     /  *    |     /
 4 |    /  wait    /  PIVOT |    /
 3 |   /          /         |   /
 2 |  /     *WALK          |  /
 1 |_/_____ /TO STAGE      | /
   +-----|-----|-----|-----|-----|-----|--> Time
      Arrive  Wait  Approach Perform  Off  Review
      Green   (hear (spotlight (5-7   Stage
      Room    MC)   hits)     min)
```

**Encounter Breakdown**:

| Encounter | What | Where | Why |
|-----------|------|-------|-----|
| **Green Room Entry** | Meet other comics on the lineup | Green room | Social dynamics. Delia is here. Marcus might be. Relationships begin. |
| **The Wait** | Hear the MC and opener through the wall | Green room couch | Tension builds. Anticipation. Audio cue: muffled punchlines, crowd laughter. |
| **The Call** | MC says your name | Through wall → door | Point of no return. Door opens, light spills in, ambiance swells. |
| **Stage Entrance** | Walk from door to mic, 12 feet | Backstage → Stage | EXPOSED. Spotlight follows you. Applause (polite). You're elevated now. |
| **Set: Opening** | First 2 jokes | Center stage | Win the room or lose it. Momentum starts here. |
| **Set: Core (jokes 3-5)** | Main material | Center stage | Build energy. Callbacks start to activate here if used. |
| **Set: Pivot Moment** | Adjust based on crowd read | Center stage | 2 Pivot Points available. Use or hold. |
| **Set: Closer** | Final joke(s) | Center stage | Exit impression. Applause curve determines REP multiplier. |
| **Exit** | Walk off stage to green room | Stage → Green room | Emotional release. Delia is up next. She doesn't say "good set" but she nods. That's enough. |
| **Joan's Read** | Booker watches from back of room | Bar area (invisible to player during set) | Post-set, if player did well, Joan catches their eye. No words. The nod is the currency. |

**Breadcrumbing Strategy**:
- **Visual**: Spotlight on stage is the anchor. Player's eye goes there. The brick wall is iconic — this is a REAL comedy room.
- **Audio**: Layered soundscape. Green room: quiet murmur, nervous energy. Stage: spotlight hum, mic feedback briefly, then clarity. Crowd: glass clinks, low conversation that STOPS when you start.
- **Social**: Whiteboard in green room shows the order. Seeing your name in dry-erase marker between established comics is the breadcrumb: you belong here now.
- **Mechanical**: REP unlock notification appears post-set if you hit the threshold. "Joan noticed. You're eligible for a regular spot."

**Difficulty Considerations**:

| Factor | Setting | Impact |
|--------|---------|--------|
| Audience Patience | Medium (5/10) | Two-drink minimum makes them generous but distractible |
| Crowd Composition | 30% Comedy Nerds, 25% Date Night, 20% Regulars, 15% Casuals, 10% Fellow Comics | More complex reads. Can't please everyone. |
| Heckler Risk | 10% per set | Drunk Hecklers appear. Acknowledge/Ignore/Engage mechanics activate. |
| Material Staleness | -5% Quality per repeat at same venue | Forces iteration. Can't coast on one setlist. |
| Booker Relationship Gate | Joan's approval required for regular spot | Relational pressure. Performance alone isn't enough. |

**Playtesting Metrics**:
- **Green room immersion time** (should linger 30-60 seconds before stage call)
- **Pivot Point usage rate** (target: 60% of players use at least 1)
- **Post-set Laugh Graph review time** (if < 20 seconds, players aren't engaging with diagnostic layer)
- **Repeat booking rate** (players should return to this venue 4-6 times before tier unlock)

**Variants**:
- **Tuesday Guest Spot**: Smaller crowd (30-50), more comics in audience. Tougher. Lower payout but better learning.
- **Friday Headliner Night**: You're opening for a bigger name. Crowd of 70-90. They're here for the headliner, not you. Tough warm-up challenge.
- **Saturday Prime Slot**: Best crowd composition. 80-100 people. High energy. This is the "if you're going to record a set for a clip, do it here" slot.

---

### TIER 3: THE COLLEGE SHOW / CORPORATE GIG (Constraint Rooms)

**Purpose**: Teach that AUDIENCE MATTERS MORE THAN SKILL. The same setlist that killed at the club will bomb at the college and get you fired at the corporate gig. Teach adaptation. Teach constraint (corporate = low Edge allowed).

**Emotional Beat**: Cognitive dissonance. "I'm good at this. Why isn't it working?" The lesson: comedy is situational.

**Spatial Layout: College Show (Cafeteria/Event Space)**:
```
    [MAKESHIFT STAGE - floor level, no elevation]
           * MIC (on stand, wobbly)

     [CROWD - standing/sitting on floor]
     O O O O O O O O    <- Front (engaged)
     O O O O O O O O
     O O O   O O O O    <- Middle (distracted)
         O O   O O
     O     O O     O    <- Back (phones out)

    [DOORS - back, people wander in/out]
```

**Spatial Layout: Corporate Gig (Hotel Conference Room)**:
```
    +---------------------------------+
    |  [PROJECTOR SCREEN]             |  <- Corporate branding
    |                                 |
    |    [SMALL STAGE - 12" riser]    |
    |         * MIC                   |
    |                                 |
    |  [TABLES - 8-top rounds]        |
    |   TABLE    TABLE    TABLE       |  <- Dinner service
    |   TABLE    TABLE    TABLE       |     (clinking plates)
    |                                 |
    |  [EXECUTIVE TABLE - front]      |  <- Booker sits here
    |                                 |
    |        [BAR - side]             |
    +---------------------------------+
```

**Flow Differences**:

**College**:
- No green room. You wait in a hallway or a corner.
- Stage is floor-level. You're AT the audience, not above them.
- Audience is fluid — people arrive late, leave early, stand in back on phones.
- Energy is CHAOTIC. High Volatility. They'll erupt or they'll ignore you. No middle ground.

**Corporate**:
- You're introduced by the VP of Marketing who makes an unfunny joke first (kills your Momentum before you start).
- Audience is captive but disengaged. They're here for the free dinner.
- HARD CONSTRAINT: Edge must stay below 4 or the booker cuts your set and you lose the gig fee.
- Crowd is older, more Date Night and Industry types. Low tolerance for absurdity.

**Pacing Curve — College Show**:
```
Tension
   ^
 9 |              * IF you win them
 8 |             /|\ (eruption possible)
 7 |            / | \
 6 |           /  |  \
 5 |      ____/   |   \
 4 |     /        |    \___
 3 |    /     *PIVOT
 2 |___/     (adjust or die)
 1 |_____________________________
   +-----|-----|-----|-----|------> Time
      Start  Joke2  Mid   Closer
      (cold) (test) (decide) (?)
```

**Pacing Curve — Corporate Gig**:
```
Tension
   ^
 6 |        *peak (IF you stay safe)
 5 |       /|\
 4 |      / | \____
 3 |_____/  |      \_____ (never hot, never cold)
 2 |        |
 1 |________|_____________
   +-----|-----|-----|-----> Time
      Intro  Setup  Safe  End
      (VP)   (polite) material
```

**Encounter Breakdown — College Show**:

| Encounter | What | Where | Why |
|-----------|------|-------|-----|
| **No Green Room** | Wait in hallway, hear crowd noise | Backstage area | Disorientation. This isn't a comedy venue. It's borrowed space. |
| **Chaotic Entry** | Walk through crowd to "stage" | Crowd → Stage | Exposed. Some students cheer (your friends?). Most don't look up. |
| **Cold Open** | First joke to test temperature | Floor-level stage | CRITICAL. If this doesn't land, the room never warms. |
| **The Wanderers** | Students walk in late, leave early | Throughout set | Distraction. Tests focus. Momentum bleeds from movement. |
| **Pivot or Die** | Mid-set read: are they with you? | 3 minutes in | If not, swap to high-Energy, high-Physicality material. Absurdity works here. |
| **The Eruption (if earned)** | Room goes HOT | Final 2 minutes | College crowds erupt harder than any other venue. The high is higher. |

**Breadcrumbing Strategy**:
- **Visual**: College = phones out, backlit faces in the dark. That's your visual enemy. When phones go DOWN, you're winning.
- **Audio**: College = chaotic. Conversation DURING your set. You have to cut through noise. Corporate = clinking silverware. You perform over dinner.
- **Mechanical**: Pre-gig briefing for corporate shows: "Keep it PG-13. The CMO is in the front row." This constraint appears as a HUD element during set.

**Difficulty Considerations**:

| Factor | College Show | Corporate Gig |
|--------|--------------|---------------|
| Patience | Very Low (2/10) | Medium (5/10) but disengaged |
| Constraint | None (go wild) | HARD Edge cap at 4 |
| Volatility | Very High | Low (polite applause even if not funny) |
| Payout | Low ($100-200) | High ($400-600) |
| Reputation Risk | Medium (bad set just fades) | High (booker blacklists you) |

**Playtesting Metrics**:
- **Constraint adherence rate** (corporate: do players respect the Edge cap or test it?)
- **Setlist adaptation rate** (do players rebuild setlists per venue type or try to force the same material?)
- **Frustration-quit rate** (if > 15% after college/corporate intro, the difficulty spike is too steep)

---

### TIER 4: THE THEATER — HEADLINER (Expectation Room)

**Purpose**: Teach that SCALE changes everything. Teach that intimacy is impossible at 500+ people. Teach that audiences arrive with EXPECTATIONS (they bought tickets to see YOU), and expectations are pressure.

**Emotional Beat**: Power and loneliness. You're the headliner. The room is yours. But the stage is far from the audience, and the connection is different. Colder. More transactional.

**Spatial Layout (Top-Down)**:
```
                    [STAGE - elevated 4 feet]
                        * MIC (pro setup)
                     [STOOL] [WATER]
                     [MONITOR speakers]

    [FRONT ROWS - seats 1-5]
     S S S S S S S S S S S S S S S S S S S S
     S S S S S S S S S S S S S S S S S S S S
     S S S S S S S S S S S S S S S S S S S S

            [AISLE]

    [MID ROWS - seats 6-15]
     S S S S S S S S S S S S S S S S S S S S
     S S S S S S S S S S S S S S S S S S S S
     [continues for 10 rows]

    [BACK ROWS - seats 16-20]
     S S S S S S S S S S S S S S S S S S S S
     S S S S S S S S S S S S S S S S S S S S

    [BALCONY - optional, adds 200 seats]

    [BOOTH - sound/lighting]  [LOBBY/BAR - rear]
```

**Flow Diagram**:
```
Backstage green room (PRIVATE, clean, professional)
    → Pre-show ritual (check setlist, drink water, hear crowd murmur)
    → Introduction (MC hypes you, crowd applause builds)
    → Stage entrance (through curtain or from wings, BIG moment)
    → Walk to mic (12-foot walk, applause continues, spotlight tracks you)
    → Grab mic, let applause die, START
    → 45-60 minute set (longest yet, FatigueModifier kicks in hard)
    → Standing ovation (if earned) or polite applause (if not)
    → Exit (curtain call, offstage, green room alone)
    → Post-show (fans? Agent? Empty room?)
```

**Pacing Curve**:
```
Tension/Energy
   ^
10 |                                    * CLOSER
 9 |                                   /|
 8 |                    *ACT 2 PEAK  / |
 7 |                   /|           /  |
 6 |         *ACT 1   / |          /   |
 5 |        /  PEAK  /  |         /    |
 4 |   ____/        /   | *VALLEY/     |
 3 |  /            /    |/             |
 2 | /OPENER      /  TRANSITION       |
 1 |/____________/______________________|
   +-----|-----|-----|-----|-----|-------> Time
      0-5   10-15  20-25  30-40  45-60min
     (cold) (build)(breath)(build)(peak)

   <- ACT 1 -> <TRANS> <- ACT 2 -> <CLOSER>
```

**Encounter Breakdown**:

| Encounter | What | Where | Why |
|-----------|------|-------|-----|
| **Private Green Room** | Pre-show alone time | Backstage | Contrast to dive bar chaos. You're alone with your thoughts. Pressure builds. |
| **The Introduction** | MC hypes you to 500 people | Offstage (hear through monitor) | Anticipation. Applause builds. You hear your name echoing. |
| **Grand Entrance** | Walk through curtain to center stage | Wings → Center | MOMENT. Applause peaks. Spotlight hits. This is what "making it" looks like. |
| **Act 1 (0-20 min)** | Opening material, build rapport | Stage | Win the room. Establish Voice. Plant callback seeds. |
| **Transition (20-25 min)** | Energy valley, intentional breath | Stage | Pacing lesson. You can't be at 10/10 for 60 min. Give them a moment. Tell a story. |
| **Act 2 (25-45 min)** | Core material, callbacks activate | Stage | Payoff planted setups. Momentum builds. FatigueModifier is real now. |
| **Closer (45-60 min)** | Best material, final callback chain | Stage | Leave them wanting more. Standing ovation or polite applause — the Laugh Graph tells the truth. |
| **Exit & Aftermath** | Offstage, green room, alone or with agent | Backstage | Emotional reckoning. Did you deliver? Empty room or crowded room — which feels lonelier? |

**Breadcrumbing Strategy**:
- **Visual**: The curtain. The stage lights cutting through dark. The EMPTY seats before the show (shown briefly) vs. the FULL room when you enter.
- **Audio**: Crowd murmur is LOUD. 500 people sound like an ocean. The quiet AFTER applause dies is the loneliest sound.
- **Mechanical**: Setlist for theater shows requires STRUCTURE. The game hints: "Your setlist needs an arc. Arrange jokes with pacing in mind."

**Difficulty Considerations**:

| Factor | Setting | Impact |
|--------|---------|--------|
| Set Length | 45-60 minutes | FatigueModifier at max. Late jokes need to be STRONG. |
| Audience Expectation | High | They paid $30-50. They know your hits. Playing only new material is risky. |
| Crowd Composition | Mixed, skewed toward fans of your Voice | Less diversity = easier to read, but expectations are higher. |
| Callback Complexity | High (15+ jokes to reference) | Mastery test. Can you build a callback chain across 60 minutes? |
| Agent Pressure | Present | Agent watches. Bad show affects future bookings. |

**Playtesting Metrics**:
- **Set completion rate** (60-min sets are LONG; do players maintain engagement?)
- **Pacing arc adherence** (do players structure sets with energy valleys or try to stay hot the whole time?)
- **Callback usage depth** (are players building 3-layer callback chains?)
- **Post-show emotional resonance** (survey: "How did the empty green room afterward feel?")

---

### TIER 5: LATE-NIGHT TV STUDIO (Control Room)

**Purpose**: Teach that CONSTRAINTS can suffocate. Teach the difference between performing for a room and performing for a CAMERA. Teach that "making it" sometimes means giving up control.

**Emotional Beat**: Vertigo. This is the dream. The set goes well. And it feels... hollow. The room is sterile. The audience is coached. You're a product, not a person.

**Spatial Layout (Side View)**:
```
    [CAMERAS - 3 positions]
       CAM1   CAM2   CAM3
         \     |     /
          \    |    /
           \   |   /
         [STAGE - elevated, polished]
              * MIC (fixed position)
           [MARK on floor - don't move]

    [AUDIENCE - tiered seating, 100 people]
     FRONT [warmup comedian got them laughing already]
     ROW 2 [selected for demographics]
     ROW 3 [told when to applaud]

    [PRODUCTION BOOTH - above and behind]
     [DIRECTOR] [PRODUCERS] [NETWORK EXEC]
```

**Flow Diagram**:
```
Green room (network TV sterile, catering, other guests)
    → Pre-show briefing ("5 minutes. Clean. Don't mention [list]. Hit your mark.")
    → Wait in wings (hear house band, hear host intro)
    → Stage entrance (walk to mark, hit mark EXACTLY, smile for Camera 2)
    → 5-minute set (NO pivot points, NO improvisation, stick to approved material)
    → Applause (coached, loud, indistinguishable from real)
    → Handshake with host (if time allows, often cut)
    → Exit (walk off, set is OVER, no green room decompression)
    → Watch playback on monitor backstage (is that you? it doesn't feel like you)
```

**Pacing Curve**:
```
Tension
   ^
 7 |           * PUNCHLINE 3-4
 6 |          /|\
 5 |      ___/ | \___
 4 |     /     |     \
 3 |____/   CONTROLLED  \____
 2 |       ENERGY
 1 |_________________________
   +-----|-----|-----|------> Time
      0-1   2-3   4-5  (min)
    (intro)(build)(close)

  NOTE: Pacing curve is FLAT compared to live rooms.
        The energy is manufactured, not earned.
```

**Encounter Breakdown**:

| Encounter | What | Where | Why |
|-----------|------|-------|-----|
| **The Briefing** | Producer lists restrictions | Green room | "Don't say X, Y, Z. Keep it PG. 5 minutes EXACTLY. Don't go long." |
| **The Mark** | Tape on stage floor, hit it exactly | Stage wings → Mark | Loss of freedom. You can't move. The camera frame is the prison. |
| **Coached Applause** | Audience applauds on cue, not on content | Stage | Dissonance. Are they laughing at the joke or the APPLAUSE sign? |
| **The 5-Minute Limit** | Set must be TIGHT, no pivot, no flex | Stage | Ultimate constraint. The set is a locked sequence. |
| **The Playback** | Watch yourself on monitor | Backstage after | Uncanny valley. That's you, but it's NOT you. The camera smoothed you into someone else. |

**Breadcrumbing Strategy**:
- **Visual**: Everything is TOO clean. Too bright. The mark on the floor is bright RED tape. The cameras are the dominant presence, not the audience.
- **Audio**: House band sting after each punchline (whether it landed or not). Coached laughter has a different SOUND — it starts on cue, stops on cue.
- **Mechanical**: Material selection screen for this gig has a FILTER: "Edge < 3, Absurdity < 6, Self-contained (no callbacks)." The player must BUILD a set for TV.

**Difficulty Considerations**:

| Factor | Setting | Impact |
|--------|---------|--------|
| Time Constraint | HARD 5-minute limit | Going long = cut off mid-joke, career damage. |
| Material Constraints | Clean, self-contained, no callbacks | Must rebuild setlist. Your best material may not qualify. |
| Audience Read | IMPOSSIBLE | They're coached. The Laugh Graph is semi-randomized. You can't trust it. |
| Career Impact | HIGH | Success here opens doors. Failure closes them. |
| Emotional Payoff | LOW | The set goes well and you feel... nothing. |

**Playtesting Metrics**:
- **Material rebuilding rate** (do players UNDERSTAND they can't use their normal setlist?)
- **Time limit violations** (if > 25%, the 5-min constraint isn't clear enough)
- **Emotional response survey** ("Did this feel like a victory?" Target: 30-40% say NO. The dissonance is intended.)

---

### TIER 6: THE SPECIAL — 60-MINUTE THEATER TAPING (Legacy Room)

**Purpose**: The culmination. Teach that the ultimate test is YOURSELF. The crowd is large, the stakes are existential, but the real question is: did you make the thing you needed to make?

**Emotional Beat**: The same terror as the first open mic. The same question: *Am I funny?* But now the room is 1,500 people and three cameras and a Netflix logo and it STILL comes down to whether you can make strangers feel something.

**Spatial Layout**:
```
                  [STAGE - professional, elevated]
                       * MIC (wireless option)
                    [STOOL] [WATER] [MONITOR]
                    [CAMERAS - 4 angles]

    [ORCHESTRA SEATING - 800 seats]
     S S S S S S S S S S S S S S S S S S S S S S S S
     S S S S S S S S S S S S S S S S S S S S S S S S
     [rows continue]

    [MEZZANINE - 400 seats]

    [BALCONY - 300 seats]

    [BOOTH - recording/mixing]

    [GREEN ROOM - backstage, ALONE or with support]
```

**Flow Diagram**:
```
Week before: Setlist construction (60-min arc, choose from your library, arrange with narrative intent)
    ↓
Day of: Theater walkthrough (see the empty room, the scale, the cameras)
    ↓
Green room: Alone with the setlist napkin, the same ritual as the first open mic
    ↓
Hear the crowd: 1,500 people. Ocean sound.
    ↓
Introduction: MC hypes. Applause builds.
    ↓
Walk to stage: Longest walk. Same as the dive bar, but the stakes are existential.
    ↓
60-minute set:
    - Act 1 (0-20 min): Win the room, establish voice
    - Act 2 (20-40 min): Core material, callback chains
    - Act 3 (40-60 min): Deeper, riskier, the material that MATTERS
    ↓
Closer: The last joke you'll tell as this version of yourself
    ↓
Applause: Standing ovation or not. The Laugh Graph has a shape. That shape is your legacy.
    ↓
Offstage: Empty green room. Sit on the couch. Stare at the napkin setlist. Was it worth it?
```

**Pacing Curve — The Special**:
```
Tension/Energy
   ^
10 |                                          * FINAL MOMENT
 9 |                                         /|
 8 |                      * ACT 2 PEAK      / |
 7 |                     /|                /  |
 6 |       * ACT 1      / |      * ACT 3  /   |
 5 |      /  PEAK      /  |     /  DEPTH /    |
 4 | ____/            /   |____/        /     |
 3 | /               /    TRANSITION   /      |
 2 |/ OPENER        /                 /       |
 1 |/______________/________________/________|
   +-----|-----|-----|-----|-----|-----|-------> Time
      0-10  15-20  25-30  35-40  45-50  55-60min

   The curve must have VALLEYS (intentional breaths) and PEAKS (earned climaxes).
   A flat curve = exhausting. A random curve = incoherent.
   This is the mastery test.
```

**Encounter Breakdown**:

| Encounter | What | Where | Why |
|-----------|------|-------|-----|
| **Setlist Construction** | Pre-show: build the 60-min arc | Apartment/Green Room | Strategic depth. Choose material. Arrange with intent. This IS the game. |
| **Theater Walkthrough** | See the empty venue before the show | Stage, day before | Perspective. The room is VAST. Tomorrow it will be full. |
| **Green Room Ritual** | Alone with napkin setlist, same as open mic | Backstage, 30 min before | Full circle. Same fear, same spark. |
| **The Walk** | Entrance to stage, 1,500 people watching | Wings → Center | The culmination of every walk before this. |
| **Act 1: Establish** | Opening 20 minutes | Stage | Win them. Prove you belong here. |
| **Act 2: Deliver** | Core material, callbacks chain | Stage | Give them what they came for. |
| **Act 3: Risk** | Deep material, the stuff that scares you | Stage | The material that defines you. Not the crowd-pleasers — the TRUTH. |
| **The Closer** | Final joke, final callback, final moment | Stage | The last thing they'll remember. Choose wisely. |
| **Aftermath** | Green room, alone, napkin in hand | Backstage | The question isn't "did they like it?" It's "did I make what I needed to make?" |

**Breadcrumbing Strategy**:
- **Visual**: The empty theater during walkthrough. The FULL theater on show night. The napkin setlist — the same napkin UI from the first open mic.
- **Audio**: The ocean of 1,500 people. The silence when you ask for it. The eruption when you earn it.
- **Mechanical**: Setlist builder for the special has a NARRATIVE ARC requirement. "Your set needs Act 1, Act 2, Act 3 structure. Arrange accordingly."

**Difficulty Considerations**:

| Factor | Setting | Impact |
|--------|---------|--------|
| Set Length | 60 minutes | MAXIMUM FatigueModifier. Late material needs to be exceptional. |
| Audience Size | 1,500 | Massive crowd. Social proof Bleed effect is STRONG. Win them early or lose them fast. |
| Career Stakes | MAXIMUM | This is your legacy moment. Success = empire. Failure = stall. |
| Emotional Stakes | MAXIMUM | The real test isn't the crowd. It's whether you stayed true to your Voice. |
| Authenticity Pressure | If Authenticity < 60, the set feels hollow even if the numbers are good | Mechanical reinforcement of theme. |

**Playtesting Metrics**:
- **Setlist construction time** (should be 10-15 minutes; this is a BIG decision)
- **Arc adherence** (do players structure Act 1/2/3 or just stack their best material?)
- **Authenticity score at time of special** (track correlation between Authenticity and player satisfaction)
- **Post-special survey** ("Was this the set you needed to make?" Target: 70%+ say YES, regardless of Laugh Graph outcome.)

---

## 3. THE GREEN ROOM — THE EMOTIONAL HUB

The green room is not a level. It's the SPACE BETWEEN levels. It's where the emotional core of Deadpan lives.

### Spatial Design Principles for Green Rooms

Every venue's green room tells a story:

**Dive Bar**: No green room. You wait in the corner by the comics' table. The lack of privacy is the point.

**Comedy Club**: Cramped, sagging couch, dead bulbs, whiteboard with dry-erase ghosts of old setlists. The space is SHARED. Other comics are always there. Conversations happen in fragments.

**Theater**: Private green room. Clean. Professional. EMPTY. The loneliness of success.

**Late-Night Studio**: Network TV sterile. Catering table. Other guests (actors, musicians). You don't belong here and you know it.

**Special Taping**: Your own green room. Too much space. Too much quiet. Just you and the napkin.

### Green Room as Emotional Pacing

The green room is the BREATH between performances. The pacing rhythm of Deadpan is:

```
Anticipation (green room) → Tension (stage) → Release (Laugh Graph) → Reflection (green room)
```

The player should WANT to return to the green room after a set. It's the decompression. The space where Delia might nod, where Marcus might congratulate or compete, where Pete might say something that reframes everything.

### Green Room Encounters (Tier 2+)

| Character | Trigger | Dialogue/Event | Impact |
|-----------|---------|----------------|--------|
| **Delia** | After a good set | She doesn't say "good set." She says, "That callback in the fifth bit — where'd you get that?" | Validation from the toughest critic. |
| **Marcus** | After his set goes viral | He's on his phone, reading comments, half-present. "Did you see the numbers?" | Contrast: his success feels empty. |
| **Pete** | After you bomb | He's sitting in the corner. Doesn't look up. After a beat: "You coming back next week?" | The question is the mentorship. |
| **Alexis** | After she performs | Reviewing her Laugh Graph on a tablet. "Segment 3 underperformed. I think it's the Misdirection timing." | She treats it like data. You treat it like art. Both are valid. |
| **Ray** | Unpredictable | Sometimes brilliant, sometimes erratic. Might be writing furiously, might be staring at the wall. | Reminder that comedy costs. |

---

## 4. LEVEL PROGRESSION FLOW — THE LADDER

The player climbs the ladder by EARNING ACCESS, not by walking to a new zone.

### Unlock Gates

| Tier | Unlock Condition | What Opens | Why This Gate Matters |
|------|------------------|------------|----------------------|
| 0→1 | Tutorial complete | Dive bar open mics | First real performance. Terror and exhilaration. |
| 1→2 | 100 REP + Joan's approval | Comedy club guest spots | Relationship gate. Performance alone isn't enough. |
| 2→3 | 500 REP + Agent contact | College/Corporate gigs | Constraint introduction. Same skill, different contexts. |
| 3→4 | 2,000 REP + Fan base threshold | Headlining, theaters | Scale shift. Intimacy becomes impossible. |
| 4→5 | 8,000 REP + Media appearance offer | Late-night TV, festivals | Control loss. The dream is hollow. |
| 5→6 | 25,000 REP + Authenticity > 60 | Special taping opportunity | Legacy moment. Did you stay true? |

### Difficulty Curve Across Tiers

```
Difficulty
   ^
10 |                              * SPECIAL (Tier 6)
 9 |                             /
 8 |                    * TV    /
 7 |                   (Tier 5)/
 6 |              *THEATER     /
 5 |             (Tier 4)     /
 4 |        *CONSTRAINT      /
 3 |       (Tier 3)         /
 2 |    *CLUB              /
 1 | *(Tier 2)            /
 0 |*DIVE                /
   |__________________ /____________> Time
    Tier 1   2    3    4    5    6

The curve is STEPPED, not smooth. Each tier transition is a shock.
```

---

## 5. SPATIAL STORYTELLING — ENVIRONMENTAL DETAILS

Every venue has **diegetic UI elements** that tell stories:

### The Dive Bar Open Mic
- Flyers on the wall: old comedy shows, some comics' names crossed out (they quit? moved? died?).
- Setlist on a napkin, scrawled in pen.
- Mic stand leans slightly left (always has, always will).
- Regulars' drinks: same glass, same position, every night.

### The Comedy Club
- Brick wall has LAYERS of flyers, half-torn, palimpsest of history.
- Green room whiteboard: ghosts of old setlists in faded dry-erase.
- Couch canyon in the middle from ten years of comics sitting, sinking.
- Tape over door latch (nobody remembers who put it there; everyone respects it).

### The Theater
- Empty seats before the show (shown in walkthrough) vs. FULL room (1,500 people, ocean sound).
- Private green room mirror: clean, well-lit, reflects the question "who are you?"
- Napkin setlist on the counter, same UI as the dive bar. Full circle.

### The Late-Night Studio
- Mark on floor (RED tape, impossible to miss, impossible to ignore).
- Cameras as dominant presence (audience is secondary).
- Green room catering table (network logo on napkins, everything branded, nothing personal).

---

## 6. BREADCRUMBING STRATEGIES ACROSS ALL VENUES

### Visual Breadcrumbs
- **Spotlight = goal**. Where the light is brightest, that's where you're going.
- **Audience body language**. Phones down = winning. Arms crossed = losing. Leaning forward = hooked.
- **Green room whiteboard**. Your name in the setlist order = you belong here now.

### Audio Breadcrumbs
- **Crowd murmur volume**. Loud murmur before you start = anticipation. Quiet murmur during your set = disengagement.
- **Laughter SHAPE**. Short burst = chuckle. Sustained wave = big laugh. ERUPTION = the room broke.
- **Silence**. The absence of sound is the loudest feedback. The player must FEEL silence.

### Social Breadcrumbs
- **Character presence**. Delia in the green room = she's watching. Pete at the back of the dive bar = he's listening.
- **Relationship shifts**. Joan's nod after a good set. Marcus's absence after your viral moment. Ray's manic energy before a great set.

### Mechanical Breadcrumbs
- **Laugh Graph color shift**. Blue (cold) → Gold (hot). The player learns to READ the graph like a heartbeat monitor.
- **REP unlock notifications**. "Joan noticed." "Agent interested." "Festival invite unlocked." Progression = story.
- **Voice Identity tracker**. The five spectra shift as you perform. The player SEES who they're becoming.

---

## 7. DIFFICULTY VARIANTS & OPTIONAL CHALLENGES

### Hard Mode — "The Purist Run"
- Authenticity must stay above 75 at all times.
- No corporate gigs (Edge constraint too restrictive).
- Special must be 100% new material (no greatest hits).
- **Reward**: "Artistic Integrity" achievement + Pete's final monologue unlocks.

### Speed Run — "The Grind"
- Reach Tier 6 in minimum in-game weeks.
- Forces optimization over exploration.
- **Risk**: Low Authenticity, hollow victory.

### Chaos Mode — "The Ray Santos Path"
- All material must have Edge > 7 or Absurdity > 7.
- High-risk, high-reward. Polarizing crowds.
- **Outcome**: Cult following or burnout.

### Legacy Mode
- Start new playthrough in a world shaped by your previous comedian's career.
- Previous character is now a LEGEND (or cautionary tale) in the scene.
- Your old material exists in the culture (risk of "Derivative" tag).

---

## 8. PLAYTESTING PRIORITIES — WHAT TO MEASURE

### Spatial Comprehension
- **Do players understand WHERE to look?** (Spotlight, Laugh Graph, audience body language)
- **Do players feel CONFINED or ELEVATED by stage geometry?** (Dive bar floor-level vs. theater elevation)

### Emotional Pacing
- **Do players DREAD the walk to the mic?** (If not, the anticipation build is too weak.)
- **Do players NEED the green room after a set?** (If they skip it, the emotional release isn't working.)
- **Do players feel DIFFERENT at Tier 1 vs. Tier 6?** (Same fear, different scale = full circle.)

### Difficulty Curves
- **Bomb rate per tier** (Target: Tier 1 = 40%, Tier 2 = 30%, Tier 3 = 35% [constraint shock], Tier 4 = 20%, Tier 5 = 25% [control shock], Tier 6 = 15%)
- **Frustration-quit rate** (If > 20% at any tier, that tier's difficulty spike is too harsh.)
- **Repeat venue rate** (Players should return to each venue type 3-5 times before tier unlock. If < 2, progression is too fast.)

### Breadcrumb Legibility
- **Time to first Laugh Graph review** (Should happen within 30 seconds post-set. If not, the diagnostic value isn't clear.)
- **Agent mechanic discovery rate** (If < 80% discover agent system by Tier 3, the unlock isn't signposted well enough.)
- **Voice Identity awareness** (Survey: "Do you understand your comedic Voice?" Target: 90%+ YES by Tier 3.)

---

## 9. ACCESSIBILITY & SCALABILITY NOTES

### For Players Who Struggle with Performance Anxiety
- **Practice Mode**: Perform to an EMPTY room (just you, the Bit Builder, and the stage). No Crowd Engine. No stakes. Build confidence.
- **Narrator Mode**: Optional voice-over (Pete's voice?) that provides gentle commentary and encouragement.

### For Players Who Want Pure Optimization
- **Metrics Dashboard**: Unlock after first Special. Shows lifetime stats, optimal setlist configurations, Voice Identity min-maxing paths.
- **Crowd Composition Simulator**: Test setlists against hypothetical audience makeups before booking gigs.

### For Players Who Want Pure Story
- **Story Mode**: Reduced Crowd Engine complexity. Laugh Graph still exists but is more forgiving. Focus on character relationships and narrative beats over mechanical mastery.

---

## 10. FINAL SPATIAL PHILOSOPHY

Where does the player LOOK?

**At the dive bar**: They look at the mic. The clip light. The only bright thing in a dark room.

**At the club**: They look at the brick wall. The history. The whiteboard with their name on it.

**In the green room**: They look at the other comics. Delia's silence. Marcus's phone. Pete's absence or presence.

**At the theater**: They look at the SCALE. The empty seats that will be full. The cameras that will record this forever.

**On stage**: They look at the Laugh Graph. The waveform. The heartbeat of the room. The only truth.

**After the special**: They look at the napkin. The setlist. The same napkin from the first open mic. Full circle.

What's the pacing here?

Anticipation → Terror → Performance → Release → Reflection. Every venue. Every set. The rhythm never changes. Only the stakes.

Every room teaches something.

**The dive bar teaches**: You are alone, and that's okay. Survive.

**The club teaches**: You are not alone. Navigate. Build relationships. Earn respect.

**The college/corporate teaches**: Context is everything. Adapt or die.

**The theater teaches**: Scale changes intimacy. You can't see their faces anymore. The connection is different.

**The TV studio teaches**: Control is an illusion. The dream is hollow.

**The special teaches**: The question was never "can I make it?" The question was always "what do I make when I get there?"

---

## CLOSING NOTE — FROM GRID'S DESK

Every level is a stage. Every stage is a test. But the test isn't "are you funny?" The test is "can you read the room, manage the energy, build the pacing arc, and make strangers feel something in a space that doesn't owe you anything?"

The dive bar is a chokepoint: pass through or quit. The club is a flow lesson: navigate relationships, earn your spot. The theater is a scale shock: intimacy becomes impossible, connection becomes transactional. The TV studio is a constraint prison: lose control, gain exposure. The special is the final exam: everything you've learned, 60 minutes, one chance.

Where does the player LOOK? At the light. Always the light. The spotlight, the Laugh Graph glow, the green room mirror, the exit sign when it's time to leave.

What's the pacing? Terror, breath, terror, breath, terror, breath. The rhythm of live performance. The rhythm of a life in comedy.

Every room teaches something. The player who learns every lesson — survival, flow, adaptation, scale, control, authenticity — doesn't just make it. They BECOME it.

Walk the level. Time it. Watch someone else play it. Where do they get lost? Where do they feel small? Where do they feel powerful? Those moments are the design.

The level isn't the geometry. The level is the FEELING of standing in the light and trying to make strangers laugh. Build the feeling. The geometry follows.

---

*GRID — Level Designer*
*"Every room is a lesson, every corridor is pacing, every vista is a reward."*
