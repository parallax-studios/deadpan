# DEADPAN — QA Plan

**Game**: DEADPAN — Stand-up Comedy Empire Simulation
**QA Lead**: CRASH
**Status**: Pre-Production QA Framework
**Target Platforms**: PC (Steam Primary), Nintendo Switch (Secondary), Mobile (Stretch)
**Last Updated**: 2026-02-07

---

## 0. Executive Summary

DEADPAN is a systems-heavy simulation where player creativity meets deterministic AI. The entire game lives or dies on one question: **can the player understand WHY their joke bombed?**

If the Crowd Engine feels random, the loop is broken. If the Bit Builder feels like a spreadsheet, the fantasy is dead. If the Laugh Graph doesn't teach the player what to fix, we've built a game that punishes without educating.

This is not a game where "it works on my machine" is acceptable. The core loop must work for a non-gamer who loves comedy podcasts. It must work for a tycoon veteran who's never watched stand-up. It must work at hour 1 and at hour 100.

**What does "works" mean?**

"Works" means: I assembled a joke, performed it, read the Laugh Graph, and I know exactly what to change. Not "I think maybe." I KNOW.

That's the bar. Everything else is details.

---

## 1. Quality Gates (What Must Pass Before Shipping)

These are non-negotiable. If any gate fails, we do not ship.

### Gate 1: The Core Loop Clarity Test
**What**: 10 external playtesters (mix of gamers and comedy fans, no prior knowledge of the game).
**Test**: Build one joke. Perform it. Review the Laugh Graph. Answer: "Why did this joke succeed or fail?"
**Pass Criteria**: 8/10 can articulate the reason using the game's feedback systems.
**Failure Mode**: If players say "it felt random" or "I don't know," the Crowd Engine feedback is insufficient.
**Blocker**: Prototype does not advance to production until this passes.

### Gate 2: The 20-Hour Engagement Test
**What**: 5 playtesters play for 20 hours over 2 weeks.
**Test**: Reach Tier 3-4. Quit survey: "Did the mid-game feel like a grind?"
**Pass Criteria**: 4/5 say "No, the scene dynamics and rival arcs kept it interesting."
**Failure Mode**: If 3+ say "Yes, repetitive," the Scene AI or content variety is failing.
**Blocker**: Early Access does not launch until this passes.

### Gate 3: The Performance Budget Test
**What**: Automated performance test suite runs on min-spec PC, Switch dev kit, and target mobile device.
**Test**: Simulate a 60-minute set (15 jokes) with 500-person audience. Measure framerate stability.
**Pass Criteria**: PC = 60 FPS locked, Switch = 30 FPS minimum, Mobile = 30 FPS minimum.
**Failure Mode**: If any platform drops below target for more than 5% of the set, performance optimization is required.
**Blocker**: 1.0 release does not launch until this passes on all target platforms.

### Gate 4: The Save Corruption Test
**What**: 100 save/load cycles with active gameplay between each cycle.
**Test**: Create save. Play 10 minutes. Load save. Verify all state (material library, career tier, AI comedian relationships, Voice Identity).
**Pass Criteria**: 100/100 successful loads with zero data loss.
**Failure Mode**: Any save corruption is a CRITICAL bug. We do not ship with save corruption risk.
**Blocker**: No platform launches until this passes.

### Gate 5: The Voice Identity Transparency Test
**What**: 10 playtesters perform 20 sets across Tier 1-3, deliberately shifting their Voice.
**Test**: After each Voice shift, answer: "Do you understand why your Authenticity score changed?"
**Pass Criteria**: 9/10 can explain the Authenticity penalty using the game's feedback.
**Failure Mode**: If players feel punished without understanding why, the Voice Identity UI is failing.
**Blocker**: 1.0 release does not launch until this passes.

---

## 2. Test Plan by Feature Area

### 2.1 Bit Builder System

**Tested By**: QA + External Playtest
**Priority**: CRITICAL (core creative loop)

#### Test Cases

**TB-001: Component Card Drag and Drop**
- **Preconditions**: Bit Builder UI open, player has 20+ unlocked component cards.
- **Steps**:
  1. Drag Premise card to Premise slot.
  2. Drag Setup card to Setup slot.
  3. Drag Misdirection card to Misdirection slot.
  4. Drag Punchline card to Punchline slot.
  5. Observe real-time Humor Profile radar chart update.
  6. Observe real-time Quality Score update.
- **Expected**: Cards snap into slots smoothly. Humor Profile updates < 100ms. Quality Score recalculates < 1ms. No UI jank.
- **Severity**: CRITICAL

**TB-002: Joke Quality Calculation — Coherence**
- **Preconditions**: Access to component cards with known thematic tags.
- **Steps**:
  1. Build a joke where Premise and Setup share 2+ thematic tags (e.g., both tagged "family" and "technology").
  2. Note the Quality Score.
  3. Replace Setup with a card that shares zero thematic tags with Premise.
  4. Note the new Quality Score.
- **Expected**: Shared-tag joke has Coherence score 15-30. Zero-shared-tag joke has Coherence score 0-10. Quality Score drops significantly.
- **Severity**: HIGH

**TB-003: Joke Quality Calculation — Surprise**
- **Preconditions**: Access to component cards with diverse Humor Profiles.
- **Steps**:
  1. Build a joke where Misdirection has Absurdity=2, Punchline has Absurdity=9 (high delta).
  2. Note the Surprise score.
  3. Build a joke where Misdirection has Absurdity=5, Punchline has Absurdity=6 (low delta).
  4. Note the Surprise score.
- **Expected**: High-delta joke has Surprise score 20-30. Low-delta joke has Surprise score 0-10.
- **Severity**: HIGH

**TB-004: Joke Quality Calculation — Timing**
- **Preconditions**: Access to component cards with known word counts.
- **Steps**:
  1. Build a joke where Setup+Misdirection total 40 words, Punchline is 20 words (2:1 ratio).
  2. Note the Timing score.
  3. Build a joke where Setup+Misdirection total 10 words, Punchline is 30 words (1:3 ratio).
  4. Note the Timing score.
- **Expected**: 2:1 ratio joke has Timing score 15-20. 1:3 ratio joke has Timing score 0-10.
- **Severity**: HIGH

**TB-005: Callback System — Valid Target**
- **Preconditions**: Player has performed Joke A in a previous set (saved in material library).
- **Steps**:
  1. Build Joke B.
  2. Attach Callback component targeting Joke A.
  3. Observe Quality Score multiplier (should be 1.0x-1.5x).
  4. Perform setlist containing Joke A, then Joke B.
  5. Observe Laugh Graph — Joke B should receive Callback bonus if Joke A landed.
- **Expected**: Callback multiplier applied correctly. Laugh Graph shows elevated reaction for Joke B.
- **Severity**: HIGH

**TB-006: Tag System — Optional Component**
- **Preconditions**: Player has unlocked Tag component cards.
- **Steps**:
  1. Build a joke without a Tag. Note Quality Score.
  2. Attach a well-matched Tag (shares thematic tags with Punchline, higher Edge). Note Quality Score.
  3. Attach a mismatched Tag (no shared tags, lower Edge). Note Quality Score.
- **Expected**: Well-matched Tag adds 5-10 to Quality. Mismatched Tag subtracts 0-5.
- **Severity**: MEDIUM

**TB-007: Component Card Unlocking — Progression Gating**
- **Preconditions**: Player at Tier 1 with locked Tier 3 component cards.
- **Steps**:
  1. Attempt to use a locked component card.
  2. Advance to Tier 3.
  3. Verify previously locked cards are now available.
- **Expected**: Locked cards are visually grayed out and non-draggable. Unlocked cards are fully interactive.
- **Severity**: MEDIUM

**TB-008: Component Card CSV Import (Content Pipeline Tool)**
- **Preconditions**: Access to Unity Editor with Component Card Editor tool.
- **Steps**:
  1. Export 10 component cards to CSV.
  2. Modify CSV (change Cleverness value, add new thematic tag).
  3. Re-import CSV.
  4. Verify changes reflected in ScriptableObject assets.
- **Expected**: Import/export round-trips successfully. No data loss.
- **Severity**: MEDIUM (content creation blocker)

#### Edge Cases — Bit Builder

**EGB-001: Empty Joke Slot Performance Attempt**
- **Steps**: Leave Premise slot empty. Attempt to add joke to setlist.
- **Expected**: Error message: "Joke incomplete. All required components (Premise, Setup, Misdirection, Punchline) must be filled."
- **Severity**: MEDIUM

**EGB-002: Duplicate Component in Single Joke**
- **Steps**: Drag the same Punchline card into Punchline slot twice (if UI allows).
- **Expected**: Second drag either replaces first, or UI prevents duplicate placement.
- **Severity**: LOW

**EGB-003: Component Card with Missing Thematic Tags**
- **Steps**: Create a component card in editor with ThematicTags array = null. Attempt to use in Bit Builder.
- **Expected**: Game does not crash. Coherence calculation treats missing tags as empty array (score = 0).
- **Severity**: MEDIUM

**EGB-004: Joke Quality Calculation with Extreme Values**
- **Steps**: Build a joke where all components have Cleverness=10, Relatability=10, Edge=10, Absurdity=10, Physicality=10.
- **Expected**: Quality Score does not exceed 100. No overflow errors.
- **Severity**: HIGH

**EGB-005: Callback Chain Depth Limit**
- **Steps**: Build Joke A. Build Joke B with Callback to A. Build Joke C with Callback to B. Build Joke D with Callback to C.
- **Expected**: System handles up to 3-layer callback chains (as per GDD). 4th layer either disallowed or calculated correctly without stack overflow.
- **Severity**: MEDIUM

---

### 2.2 Crowd Engine System

**Tested By**: QA + Automated Tests
**Priority**: CRITICAL (core reactive loop)

#### Test Cases

**TC-001: Crowd Generation from Venue Config**
- **Preconditions**: VenueConfig ScriptableObject with defined archetype probabilities.
- **Steps**:
  1. Start performance at Venue A (e.g., "Dive Bar Open Mic" with 60% Fellow Comedians, 20% Regulars, 20% Random).
  2. Inspect generated crowd composition (via debug UI or logs).
  3. Repeat 10 times.
- **Expected**: Across 10 runs, average composition approximates venue distribution (+/- 15% as per GDD).
- **Severity**: CRITICAL

**TC-002: Reaction Calculation — Humor Profile Alignment**
- **Preconditions**: Joke with Cleverness=9, all other axes=3. Audience cluster with Comedy Nerds (Cleverness Pref=9).
- **Steps**:
  1. Perform joke to this audience.
  2. Observe per-cluster ReactionScore.
- **Expected**: Comedy Nerds cluster has ReactionScore > 0.6. Other archetypes (Date Night, etc.) have lower scores.
- **Severity**: CRITICAL

**TC-003: Momentum System — Building and Decaying**
- **Preconditions**: Fresh set with Momentum = 1.0.
- **Steps**:
  1. Perform 3 consecutive jokes with ReactionScore > 0.7 (strong laughs).
  2. Observe Momentum after each joke.
  3. Perform 2 consecutive jokes with ReactionScore < 0.3 (bombs).
  4. Observe Momentum decay.
- **Expected**: Momentum increases to ~1.3 after strong laughs. Momentum decreases to ~0.85 after bombs.
- **Severity**: HIGH

**TC-004: Fatigue Modifier — Long Set Penalty**
- **Preconditions**: Setlist with 15 jokes.
- **Steps**:
  1. Perform all 15 jokes (identical Quality and Humor Profile for consistency).
  2. Compare ReactionScore of Joke 1 vs. Joke 15.
- **Expected**: Joke 15 has ReactionScore approximately 22% lower than Joke 1 (15 jokes * 0.02 fatigue per joke = 0.78 multiplier).
- **Severity**: MEDIUM

**TC-005: Heckler Activation — Volatility and Low Reaction**
- **Preconditions**: Audience with Drunk Heckler archetype (Volatility=10).
- **Steps**:
  1. Perform a joke that the Heckler cluster dislikes (ReactionScore < 0.3).
  2. Observe heckler activation probability.
  3. Repeat 20 times.
- **Expected**: Heckler activates in 50-70% of cases (high Volatility * low reaction = high activation chance).
- **Severity**: MEDIUM

**TC-006: Spatial Bleed — Adjacent Cluster Influence**
- **Preconditions**: Audience with 2 clusters spatially adjacent.
- **Steps**:
  1. Perform a joke that Cluster A loves (ReactionScore = 0.9) and Cluster B is neutral on (ReactionScore = 0.5).
  2. Observe Cluster B's final reaction after bleed calculation.
- **Expected**: Cluster B's reaction increases by ~10% due to Cluster A's laughter bleed.
- **Severity**: LOW (can be disabled if perf cost is high)

**TC-007: Industry Scout Archetype — Viral Potential**
- **Preconditions**: Audience includes Industry Scout cluster (ViralPotential=6).
- **Steps**:
  1. Perform a joke that the Scout cluster rates highly (ReactionScore > 0.75).
  2. Observe post-set Career Manager REP calculation.
- **Expected**: If Scout cluster hits high reaction, REP includes ViralBonus multiplier (1.5x).
- **Severity**: MEDIUM

**TC-008: Crowd Engine Performance — 500 Clusters**
- **Preconditions**: Venue with max audience size (2000 people = ~500 clusters).
- **Steps**:
  1. Generate crowd.
  2. Perform 15-joke set.
  3. Measure per-joke evaluation time.
- **Expected**: Each joke evaluation completes in < 5ms. Total set framerate maintains 60 FPS on target PC spec.
- **Severity**: HIGH

#### Edge Cases — Crowd Engine

**EGC-001: Zero-Size Audience**
- **Steps**: Create VenueConfig with MinAudience=0, MaxAudience=0. Attempt performance.
- **Expected**: Game does not crash. Either venue is unselectable, or performance proceeds with "empty room" state (no reactions).
- **Severity**: HIGH

**EGC-002: Archetype Distribution Probabilities Sum > 1.0**
- **Steps**: Create VenueConfig where archetype probabilities sum to 1.5.
- **Expected**: Crowd generation normalizes probabilities (divides each by sum) or throws validation error in editor.
- **Severity**: MEDIUM

**EGC-003: Joke with All Humor Axes = 0**
- **Steps**: Create component cards with all axes = 0. Build joke. Perform to any audience.
- **Expected**: ReactionScore = very low (near 0) but game does not crash. Divide-by-zero protection in DotProduct calculation.
- **Severity**: MEDIUM

**EGC-004: Heckler Activation During Final Joke**
- **Steps**: Trigger heckler on the last joke of a set.
- **Expected**: Heckler interaction UI appears. Player can respond or ignore. Set ends cleanly after heckler resolution.
- **Severity**: MEDIUM

**EGC-005: Momentum Overflow — 10 Consecutive Eruptions**
- **Steps**: Engineer a scenario where 10 consecutive jokes hit ReactionScore > 0.95 (each adds 0.1 to Momentum).
- **Expected**: Momentum caps at reasonable value (e.g., 2.0x max) to prevent runaway feedback.
- **Severity**: LOW

**EGC-006: Fatigue Recovery via Tag**
- **Steps**: Perform 10 jokes. On Joke 11, use a Tag that successfully lands (ReactionScore > 0.7 for that cluster).
- **Expected**: Cluster's Fatigue increases by 0.05 (partial recovery as per GDD).
- **Severity**: LOW

---

### 2.3 Laugh Graph System

**Tested By**: QA + UX Playtest
**Priority**: CRITICAL (diagnostic feedback loop)

#### Test Cases

**TL-001: Real-Time Waveform Rendering**
- **Preconditions**: Performance in progress.
- **Steps**:
  1. Perform 5 jokes with varying ReactionScores (0.2, 0.5, 0.8, 0.3, 0.9).
  2. Observe real-time waveform at bottom of screen.
- **Expected**: Waveform shows 5 distinct peaks/valleys corresponding to reaction scores. Color shifts from blue (cold) to gold (hot) based on Momentum.
- **Severity**: CRITICAL

**TL-002: Post-Set Overview Tab**
- **Preconditions**: Completed set with 10 jokes.
- **Steps**:
  1. Open Laugh Graph analysis UI.
  2. Select "Overview" tab.
  3. Hover over each joke peak.
- **Expected**: Tooltip shows joke name, Quality/Surprise/Timing breakdown, and final ReactionScore.
- **Severity**: HIGH

**TL-003: Per-Segment Analysis Tab**
- **Preconditions**: Completed set with diverse audience (3+ archetypes).
- **Steps**:
  1. Open "Per-Segment" tab.
  2. Observe stacked area chart showing reactions by archetype.
  3. Identify which archetype loved/hated which joke.
- **Expected**: Chart clearly visualizes which audience segments responded to which jokes. Colorblind-friendly palette.
- **Severity**: HIGH

**TL-004: Pivot Analysis Tab — Counterfactual**
- **Preconditions**: Set where player used a Pivot Point to swap Joke A for Joke B.
- **Steps**:
  1. Open "Pivot Analysis" tab.
  2. Observe comparison: predicted performance of Joke A vs. actual performance of Joke B.
- **Expected**: Graph overlay shows both scenarios. Clear visual indication of whether pivot improved/worsened outcome.
- **Severity**: MEDIUM

**TL-005: Comparison Tab — Multi-Set Overlay**
- **Preconditions**: Performed same setlist at two different venues.
- **Steps**:
  1. Open "Comparison" tab.
  2. Select both sets.
  3. Observe overlaid waveforms.
- **Expected**: Player can visually compare how crowd composition affected performance.
- **Severity**: MEDIUM

**TL-006: Setlist Flow Tab — Energy Arc Visualization**
- **Preconditions**: Completed set with 12 jokes.
- **Steps**:
  1. Open "Setlist Flow" tab.
  2. Observe energy arc visualization (shows momentum build/break points).
- **Expected**: Clear visual of where momentum built, where it broke, where callbacks connected. "Kill chain" sequences highlighted.
- **Severity**: MEDIUM

#### Edge Cases — Laugh Graph

**EGL-001: Single-Joke Set**
- **Steps**: Perform a set with only 1 joke (edge case for open mic or tutorial).
- **Expected**: Laugh Graph renders a single data point. No division-by-zero errors in graph scaling.
- **Severity**: MEDIUM

**EGL-002: All Jokes Bomb (Flatline)**
- **Steps**: Perform a set where all ReactionScores < 0.2.
- **Expected**: Waveform is a near-flatline. Color remains blue (cold). Post-set analysis provides actionable feedback (e.g., "All archetypes preferred higher Relatability").
- **Severity**: HIGH

**EGL-003: All Jokes Erupt (Perfect Set)**
- **Steps**: Perform a set where all ReactionScores > 0.9.
- **Expected**: Waveform is a mountain range. Color is gold (hot). Post-set analysis highlights what worked (e.g., "High Cleverness resonated with Comedy Nerds").
- **Severity**: MEDIUM

**EGL-004: Laugh Graph Rendering Performance — 60-Minute Set**
- **Steps**: Perform maximum-length set (60 jokes for The Special).
- **Expected**: Post-set graph renders in < 100ms. UI remains responsive.
- **Severity**: MEDIUM

---

### 2.4 Voice Identity System

**Tested By**: QA + Playtest
**Priority**: HIGH (strategic meta-system)

#### Test Cases

**TV-001: Voice Identity Shift — Single Performance**
- **Preconditions**: Player Voice at neutral (all axes = 0). Audience size = 200.
- **Steps**:
  1. Perform a joke with Absurdity=9, all other axes=3. ReactionScore = 0.8.
  2. Observe Voice Identity shift.
- **Expected**: ObservationalAbsurdism axis shifts toward Absurdist (+0.05 to +0.15 based on formula). Other axes shift minimally.
- **Severity**: HIGH

**TV-002: Authenticity Increase — Aligned Material**
- **Preconditions**: Player Voice = Warm (+5), Clean (+4). Authenticity = 60.
- **Steps**:
  1. Perform 3 consecutive sets with material matching player Voice (Warm, Clean jokes).
  2. Observe Authenticity after each set.
- **Expected**: Authenticity increases by +1 per set, reaching 63.
- **Severity**: HIGH

**TV-003: Authenticity Penalty — Voice Deviation**
- **Preconditions**: Player Voice = Dark (+7), Confrontational (+6). Authenticity = 75.
- **Steps**:
  1. Perform 2 consecutive sets with Clean (+8), Warm (+7) material (4+ point deviation on two axes).
  2. Observe Authenticity after each set.
- **Expected**: Authenticity decreases by -3 to -5 per set, dropping to ~67-69.
- **Severity**: HIGH

**TV-004: Career Gating — Authenticity Minimum**
- **Preconditions**: Player Authenticity = 50. Career opportunity "HBO Special" requires Authenticity = 65.
- **Steps**:
  1. Attempt to unlock HBO Special.
- **Expected**: Opportunity is locked. UI message: "Requires Authenticity 65+. Current: 50."
- **Severity**: MEDIUM

**TV-005: Career Gating — Voice Requirements**
- **Preconditions**: Player Voice = Political (-6), Edge (+3). Career opportunity "Sitcom Deal" requires Warm (+5), Clean (+3).
- **Steps**:
  1. Attempt to unlock Sitcom Deal.
- **Expected**: Opportunity is locked. UI message: "Your comedy voice doesn't match this opportunity. Sitcom deals prefer Warm, Clean material."
- **Severity**: MEDIUM

**TV-006: Voice Identity UI — Visualization**
- **Preconditions**: Player has performed 20+ sets with varied material.
- **Steps**:
  1. Open Voice Identity screen.
  2. Observe five-axis visualization (radar chart or bar graph).
- **Expected**: Clear visual representation of current Voice position on each spectrum. Authenticity score prominently displayed.
- **Severity**: MEDIUM

#### Edge Cases — Voice Identity

**EGV-001: Authenticity Floor — Cannot Go Below 0**
- **Steps**: Engineer scenario where Authenticity penalty would drop below 0 (e.g., Authenticity=5, perform highly deviant material for -10 penalty).
- **Expected**: Authenticity clamps at 0. No negative values.
- **Severity**: LOW

**EGV-002: Authenticity Ceiling — Cannot Exceed 100**
- **Steps**: Engineer scenario where Authenticity would exceed 100 (e.g., Authenticity=98, perform highly aligned material for +5 bonus).
- **Expected**: Authenticity clamps at 100.
- **Severity**: LOW

**EGV-003: Voice Shift on Bombing**
- **Steps**: Perform a joke with high Absurdity to an audience that hates it (ReactionScore < 0.3).
- **Expected**: Voice shift still occurs but is reduced by reactionModifier (0.5x). Player's voice shifts less when material fails.
- **Severity**: MEDIUM

**EGV-004: Rapid Voice Oscillation — Exploit Check**
- **Steps**: Alternate between high-Dark and high-Clean material every set for 10 sets.
- **Expected**: Authenticity drops significantly (player is not committing to a voice). Voice position oscillates but trend toward neutral.
- **Severity**: MEDIUM

---

### 2.5 The Scene (AI Comedian System)

**Tested By**: QA + Long-Session Playtest
**Priority**: MEDIUM-HIGH (narrative/competitive layer)

#### Test Cases

**TS-001: AI Comedian Material Generation**
- **Preconditions**: AI comedian "Marcus" with SkillLevel=75, Voice=Absurdist/Dark.
- **Steps**:
  1. Simulate 1 in-game week.
  2. Inspect Marcus's material library.
- **Expected**: Marcus generates 0-2 new jokes (30% chance per week as per GDD). New jokes align with his Voice (high Absurdity, high Edge). Quality scores average 60-80 (skill-based variance).
- **Severity**: MEDIUM

**TS-002: Gig Competition — Player vs. AI**
- **Preconditions**: Player and AI comedian "Delia" both targeting same club regular spot.
- **Steps**:
  1. Check gig booking resolution.
- **Expected**: Booker picks based on REP (40%), relationship with booker (30%), Voice fit for venue (30%). Higher total score wins slot. Transparent feedback on why player won/lost.
- **Severity**: MEDIUM

**TS-003: Material Overlap Detection — Derivative Tag**
- **Preconditions**: Player has a joke with Humor Profile [Cleverness=7, Relatability=6, Edge=5, Absurdity=4, Physicality=3]. AI comedian "Alexis" performs a joke with profile [7, 6, 5, 4, 3] at a bigger venue first.
- **Steps**:
  1. Advance week (Scene simulation runs).
  2. Check player's joke for "Derivative" tag.
- **Expected**: Player's joke receives Derivative tag. Quality penalty -15 applied. Notification: "Alexis performed similar material at [Venue]. Your bit feels derivative."
- **Severity**: HIGH

**TS-004: Relationship Shift — Gig Bump**
- **Preconditions**: Player relationship with AI comedian "Ray" = 60 (friendly).
- **Steps**:
  1. Player books a gig, bumping Ray from the slot.
  2. Observe relationship change.
- **Expected**: Ray's relationship with player drops by -10 to -15.
- **Severity**: MEDIUM

**TS-005: Collaboration — Co-Writing Session**
- **Preconditions**: Player relationship with AI comedian "Delia" = 55+.
- **Steps**:
  1. Initiate collaboration "Co-Writing Session."
  2. Observe outcome.
- **Expected**: Both player and Delia receive 2-3 new component cards with shared thematic tags. Relationship increases by +5.
- **Severity**: MEDIUM

**TS-006: AI Career Arc — Flash in the Pan**
- **Preconditions**: AI comedian "Marcus" has Arc = "Flash in the Pan."
- **Steps**:
  1. Observe Marcus's career over 20 in-game weeks.
- **Expected**: Marcus rises rapidly (Tier 1 -> Tier 4 in 8-12 weeks), then plateaus or declines. Career events reflect arc (viral moment, then burnout).
- **Severity**: LOW

**TS-007: Scene Event — Comic Gets Cancelled**
- **Preconditions**: Mid-game (Tier 3+).
- **Steps**:
  1. Scene event triggers: "AI comedian [Name] has been cancelled due to [controversy]."
  2. Player presented with choice: Support them publicly (relationship +20, potential REP risk) or distance yourself (relationship -30, safe).
- **Expected**: Player choice affects relationship and potentially REP. Event creates narrative decision point.
- **Severity**: LOW

#### Edge Cases — The Scene

**EGS-001: All AI Comedians at Same Tier as Player**
- **Steps**: Engineer scenario where player and all 15 AI comedians reach Tier 4 simultaneously.
- **Expected**: Gig competition intensifies. No single AI monopolizes slots. Player still has viable booking options.
- **Severity**: LOW

**EGS-002: AI Comedian Relationship at -100 (Bitter Rival)**
- **Steps**: Engineer maximum rivalry (lose gigs to them, steal material, refuse collaboration).
- **Expected**: AI comedian actively targets player's gig slots. Fans trash player on social media (slight REP drain). Beating them at shared venue gives 1.5x REP bonus.
- **Severity**: LOW

**EGS-003: AI Comedian Relationship at +100 (Ride-or-Die)**
- **Steps**: Engineer maximum friendship (collaborate, support, share audiences).
- **Expected**: AI offers touring partnership (shared audience growth). Defends player during scene controversies. Collaboration unlocks exclusive component cards.
- **Severity**: LOW

**EGS-004: Scene Simulation Performance — 15 AI Comedians**
- **Steps**: Advance 1 in-game week with all 15 AI comedians active.
- **Expected**: Simulation completes in < 200ms. No framerate drop during week advance.
- **Severity**: MEDIUM

---

### 2.6 Career Progression and Economy

**Tested By**: QA + Balance Playtest
**Priority**: HIGH (player motivation and stakes)

#### Test Cases

**TE-001: Tier Unlock — REP Threshold**
- **Preconditions**: Player at Tier 1 with 99 REP (Tier 2 requires 100).
- **Steps**:
  1. Perform a set that awards 10 REP.
  2. Observe tier unlock notification.
- **Expected**: Tier 2 unlocks. New venues become available. UI notification: "You've reached Tier 2: Barker/Regular."
- **Severity**: HIGH

**TE-002: REP Earning Formula — Quality Modifier**
- **Preconditions**: Tier 2 venue (BaseREP=15). Player performs set with AvgJokeQuality=50.
- **Steps**:
  1. Perform set with avg ReactionScore = 0.8 (1.6x multiplier). Authenticity = 70 (1.1x multiplier). No viral moment.
  2. Calculate REP earned: 15 * 0.5 * 1.6 * 1.1 * 1.0 = 13.2 REP.
- **Expected**: REP awarded matches calculation (12-14 REP range acceptable due to rounding).
- **Severity**: MEDIUM

**TE-003: CASH Payout — Tier Scaling**
- **Preconditions**: Player performs at Tier 1 venue (payout $0-15), then Tier 3 venue (payout $100-400).
- **Steps**:
  1. Complete sets at both venues.
  2. Observe CASH earned.
- **Expected**: Tier 3 payout is 10-20x higher than Tier 1. Progression feels meaningful.
- **Severity**: MEDIUM

**TE-004: Rent Payment Failure — Eviction**
- **Preconditions**: Player CASH = $200. Rent due = $400.
- **Steps**:
  1. Advance to rent payment week.
  2. Fail to pay rent.
- **Expected**: Player loses apartment. Moves to shared space. Component card acquisition rate drops (-1 card per week). Notification: "You couldn't afford rent. You're crashing at Ray's place. Less time to write."
- **Severity**: MEDIUM

**TE-005: Agent Hiring — Cut and Benefits**
- **Preconditions**: Player at Tier 2 with no agent.
- **Steps**:
  1. Hire Small Agent (10% cut).
  2. Perform gig with $200 payout.
- **Expected**: Player receives $180 ($200 - 10%). Agent provides 2-3 gig offers per week (more than self-booking).
- **Severity**: MEDIUM

**TE-006: Agent Relationship — Dropping Player**
- **Preconditions**: Player has agent with relationship = 32.
- **Steps**:
  1. Bomb 2 consecutive gigs (relationship drops by -20 total).
  2. Advance week.
- **Expected**: Agent relationship drops to 12. Agent sends message: "This isn't working out. I'm dropping you." Player loses agent. Tier 3+ venues locked until new agent hired.
- **Severity**: MEDIUM

**TE-007: Merch System — Passive Income**
- **Preconditions**: Player unlocks Tier 4. FanCount = 1000. Merch setup complete (MerchQuality = 2).
- **Steps**:
  1. Advance 1 week.
  2. Observe merch income: $1000 * 0.05 * 2 = $100/week.
- **Expected**: CASH increases by ~$100 per week. Merch maintenance cost ($200/month) deducted monthly.
- **Severity**: LOW

**TE-008: Podcast Revenue — Listener Growth**
- **Preconditions**: Player launches podcast. Listeners = 5000. Releases 1 episode.
- **Steps**:
  1. Calculate revenue: $5000 * 0.01 = $50.
  2. Invite AI comedian guest (20% listener boost).
  3. Release second episode with 6000 listeners: $6000 * 0.01 = $60.
- **Expected**: Revenue scales with listener count. Guest appearances provide growth.
- **Severity**: LOW

#### Edge Cases — Economy

**EGE-001: Negative CASH Balance**
- **Steps**: Engineer scenario where expenses exceed income (rent + agent fees + travel > gig payouts).
- **Expected**: CASH can go negative. Player must take emergency gigs or sell assets (merch shutdown) to recover. Game does not soft-lock.
- **Severity**: HIGH

**EGE-002: REP Overflow — Maximum REP**
- **Steps**: Reach Tier 6 (requires 25,000 REP). Continue earning REP.
- **Expected**: REP continues to accumulate (no cap) or caps at reasonable value (e.g., 50,000). No overflow errors.
- **Severity**: LOW

**EGE-003: Agent Fees Exceed Gig Payout**
- **Steps**: Top Agent (20% cut) on a low-paying gig ($50).
- **Expected**: Agent takes $10, player receives $40. No negative payout.
- **Severity**: LOW

---

### 2.7 Save System

**Tested By**: QA + Automated Tests
**Priority**: CRITICAL (save corruption is unacceptable)

#### Test Cases

**TSS-001: Save Game — All State Preserved**
- **Preconditions**: Player at Tier 3, 50 jokes in library, 3 AI rivals, Voice Identity established.
- **Steps**:
  1. Save game to Slot 1.
  2. Quit game.
  3. Load game from Slot 1.
  4. Verify: Career tier, REP, CASH, material library, Voice Identity, AI comedian states, active scene events.
- **Expected**: All state matches pre-save exactly. Zero data loss.
- **Severity**: CRITICAL

**TSS-002: Auto-Save Trigger — Week Advance**
- **Preconditions**: Game running.
- **Steps**:
  1. Advance 1 in-game week.
  2. Check for auto-save file creation.
- **Expected**: Auto-save created in `saves/autosave_[timestamp].json`. Last 3 auto-saves preserved.
- **Severity**: HIGH

**TSS-003: Save File Versioning — Migration**
- **Preconditions**: Save file from older game version (e.g., v0.9.0).
- **Steps**:
  1. Load save in new version (e.g., v1.0.0).
- **Expected**: Migration logic updates save file format. Data preserved where possible. Incompatible fields filled with default values. Player notified: "Save file updated to new version."
- **Severity**: HIGH

**TSS-004: Multiple Save Slots — Isolation**
- **Preconditions**: Save to Slot 1 (NYC career). Save to Slot 2 (LA career).
- **Steps**:
  1. Load Slot 1.
  2. Verify NYC career data.
  3. Load Slot 2.
  4. Verify LA career data.
- **Expected**: Each slot is independent. No data bleed between slots.
- **Severity**: HIGH

**TSS-005: Save Corruption Recovery**
- **Steps**:
  1. Manually corrupt a save file (invalid JSON).
  2. Attempt to load.
- **Expected**: Game detects corruption. Error message: "Save file is corrupted. Load from auto-save or start new game?" Player can recover from last auto-save.
- **Severity**: CRITICAL

**TSS-006: Cloud Save Sync (Steam)**
- **Preconditions**: Steam Cloud enabled.
- **Steps**:
  1. Save game on PC A.
  2. Exit game. Steam uploads save to cloud.
  3. Launch game on PC B.
  4. Load save.
- **Expected**: Save downloaded from Steam Cloud. All state preserved across devices.
- **Severity**: MEDIUM

#### Edge Cases — Save System

**EGSS-001: Save During Performance**
- **Steps**: Trigger manual save while mid-set (joke 5 of 10).
- **Expected**: Save completes without interrupting performance. When loaded, player resumes at start of set (not mid-set).
- **Severity**: MEDIUM

**EGSS-002: Save with 500+ Jokes in Library**
- **Steps**: Reach late game with massive material library.
- **Expected**: Save file size < 5MB. Save/load completes in < 500ms. No performance degradation.
- **Severity**: MEDIUM

**EGSS-003: Load Save from Different Platform**
- **Steps**: Save on PC (Steam). Load on Switch.
- **Expected**: Save format is cross-platform compatible. State preserved. UI adjusts for platform (controller vs. mouse).
- **Severity**: LOW (if cross-platform saves are supported)

---

## 3. Performance and Platform Testing

### 3.1 Performance Benchmarks

**Tested On**: Min-spec PC, Target PC, Switch Dev Kit, Mobile (iPhone 13, Samsung Galaxy S21)

#### Benchmarks

**BP-001: Crowd Engine Evaluation — 500 Clusters**
- **Setup**: Tier 5 venue, 2000-person audience (500 clusters).
- **Test**: Perform 15-joke set. Measure per-joke evaluation time.
- **Target**: < 5ms per joke on PC. < 8ms on Switch. < 10ms on Mobile.
- **Blocker**: If target missed, reduce cluster count or optimize job parallelism.

**BP-002: UI Rendering — Bit Builder**
- **Setup**: Bit Builder open with 300 component cards unlocked.
- **Test**: Drag 10 cards in rapid succession. Measure frame time.
- **Target**: Maintains 60 FPS (< 16ms per frame) on PC. 30 FPS on Switch/Mobile.
- **Blocker**: If target missed, implement card virtualization (only render visible cards).

**BP-003: Laugh Graph Rendering — 60-Joke Set**
- **Setup**: Complete The Special (60 jokes).
- **Test**: Open post-set Laugh Graph analysis.
- **Target**: Graph renders in < 100ms. All 5 tabs navigable without lag.
- **Blocker**: If target missed, optimize vector path rendering.

**BP-004: Scene Simulation — 15 AI Comedians**
- **Setup**: Week advance with all AI active.
- **Test**: Measure simulation time.
- **Target**: < 200ms on PC. < 300ms on Switch.
- **Blocker**: If target missed, offload simulation to background thread.

**BP-005: Memory Usage — Late Game**
- **Setup**: Tier 6 player with 400 jokes, 15 AI comedians, full venue library unlocked.
- **Test**: Measure total RAM usage.
- **Target**: < 2GB on PC. < 1GB on Switch. < 512MB on Mobile.
- **Blocker**: If target exceeded, implement component card streaming (LRU cache).

**BP-006: Load Time — Save File**
- **Setup**: Save file with 500 jokes, Tier 6, full AI state.
- **Test**: Measure load time from file read to playable state.
- **Target**: < 3 seconds on PC. < 5 seconds on Switch. < 8 seconds on Mobile.
- **Blocker**: If target missed, implement asynchronous loading with progress bar.

### 3.2 Platform-Specific Testing

#### PC (Steam)

**TPC-001: Resolution Scaling**
- **Test**: Run game at 1920x1080, 2560x1440, 3840x2160.
- **Expected**: UI scales correctly. Text remains legible. No visual artifacts.

**TPC-002: Controller Support**
- **Test**: Navigate all UI screens with Xbox/PS controller.
- **Expected**: Full navigation possible. Button prompts update to match controller type.

**TPC-003: Steam Achievements**
- **Test**: Trigger achievement conditions (e.g., "Reach Tier 4").
- **Expected**: Steam achievement unlocks. Notification appears in-game and in Steam overlay.

**TPC-004: Steam Cloud Save**
- **Test**: See TSS-006.
- **Expected**: Saves sync across devices.

#### Nintendo Switch

**TSW-001: Handheld Mode**
- **Test**: Play in handheld mode (720p screen).
- **Expected**: UI text remains legible. Touch input disabled (buttons only).

**TSW-002: Docked Mode**
- **Test**: Play in docked mode (1080p TV).
- **Expected**: UI scales appropriately. No performance difference vs. handheld.

**TSW-003: Sleep/Resume**
- **Test**: Enter sleep mode mid-performance. Resume.
- **Expected**: Game state preserved. Performance resumes correctly. No crashes.

**TSW-004: Joy-Con Input**
- **Test**: Play with single Joy-Con, dual Joy-Con, Pro Controller.
- **Expected**: All control schemes functional. Button remapping works.

#### Mobile (iOS/Android) — If Shipped

**TMO-001: Touch Input — Bit Builder**
- **Test**: Drag component cards with touch.
- **Expected**: Larger touch targets (min 44x44 pixels). Smooth drag response.

**TMO-002: Portrait vs. Landscape**
- **Test**: Rotate device.
- **Expected**: UI adapts to orientation. Performance unaffected.

**TMO-003: Background/Foreground Transition**
- **Test**: Minimize app. Return to app.
- **Expected**: Game pauses when backgrounded. Resumes correctly. No state loss.

---

## 4. Evil Path Testing (Exploits and Edge Cases)

**Philosophy**: Players will do things we didn't expect. The "evil path" is what a speedrunner, griefer, or bored 12-year-old would try.

### Evil Path Test Cases

**EVIL-001: Infinite REP Loop — Replay Same Set**
- **Steps**: Find optimal setlist. Perform at same venue 100 times.
- **Expected**: Material staleness penalty (-5% Quality per repeat at same tier) prevents infinite farming. Player forced to write new material or move to new venue.
- **Severity**: HIGH

**EVIL-002: Voice Identity Whiplash**
- **Steps**: Alternate Dark/Clean material every set to confuse Voice Identity system.
- **Expected**: Authenticity tanks. Player locked out of career opportunities. System punishes inconsistency.
- **Severity**: MEDIUM

**EVIL-003: Agent Relationship Exploit**
- **Steps**: Tank agent relationship to -100. Drop agent. Hire new agent. Repeat.
- **Expected**: Agent availability is limited. After 3+ agent drops, new agents refuse to sign player or demand higher cuts (15% -> 25%). Reputation penalty.
- **Severity**: MEDIUM

**EVIL-004: Bankruptcy Lock**
- **Steps**: Spend all CASH. Take on maximum expenses (agent, rent, podcast, merch). Bomb all gigs (zero income).
- **Expected**: Player can take emergency gigs (low-paying but available). Can sell assets (merch shutdown refunds 50% setup cost). Game does NOT soft-lock.
- **Severity**: CRITICAL

**EVIL-005: Save Scum Gig Competition**
- **Steps**: Save before gig booking. If lose gig to AI rival, reload save and try again.
- **Expected**: RNG seed for gig competition is saved with game state. Reloading does not change outcome (deterministic). Save scumming ineffective.
- **Severity**: LOW

**EVIL-006: Minimum Viable Joke Spam**
- **Steps**: Build lowest-effort jokes (Quality score 10-15). Perform 100 of them to grind REP.
- **Expected**: Low Quality = low ReactionScore = minimal REP earned. 100 terrible sets earn less REP than 10 good sets. System punishes low-quality spam.
- **Severity**: MEDIUM

**EVIL-007: Heckler Ignore Spam**
- **Steps**: Ignore every heckler interaction to save Pivot Points.
- **Expected**: Ignored hecklers have 40% escalation chance. Repeated ignoring creates reputation penalty ("comic who can't handle hecklers"). Bookers notice.
- **Severity**: LOW

**EVIL-008: AI Rivalry Weaponization**
- **Steps**: Engineer maximum rivalry with all 15 AI comedians simultaneously.
- **Expected**: Gig competition becomes brutal but not impossible. Player can still book shows. Rival benefits (1.5x REP when beating them) offset difficulty.
- **Severity**: LOW

**EVIL-009: Callback Chain Infinite Loop**
- **Steps**: Build Joke A with Callback to itself.
- **Expected**: System detects circular reference. Callback invalid. UI error: "Callback cannot target itself."
- **Severity**: MEDIUM

**EVIL-010: Component Card Duplication**
- **Steps**: Attempt to duplicate unlocked component cards via save editing.
- **Expected**: Component card library is indexed by unique ID. Duplicate IDs ignored on load. Save validation detects tampering.
- **Severity**: LOW

---

## 5. Accessibility Testing

**Goal**: Ensure the game is playable by players with visual, auditory, motor, or cognitive disabilities.

### Accessibility Test Cases

**TA-001: Colorblind Mode — Laugh Graph**
- **Test**: Enable colorblind mode. View Laugh Graph.
- **Expected**: Waveform uses patterns (dots, dashes) in addition to color. Cold/hot states distinguishable without color perception.

**TA-002: Text Scaling**
- **Test**: Increase UI text size to 150%.
- **Expected**: All text remains legible. UI does not overlap or clip.

**TA-003: Screen Reader Support (PC)**
- **Test**: Enable Windows Narrator. Navigate Bit Builder UI.
- **Expected**: Component card names, Quality scores, and Humor Profile values read aloud. UI elements have accessible labels.

**TA-004: Controller-Only Navigation**
- **Test**: Play entire game without mouse/keyboard (PC) or touch (mobile).
- **Expected**: All UI screens navigable with controller. No mouse-only interactions.

**TA-005: Reduce Motion Option**
- **Test**: Enable "Reduce Motion" setting. Perform set.
- **Expected**: Camera shake, screen transitions, and animated UI effects reduced or disabled.

**TA-006: Subtitle Options (Audio Feedback)**
- **Test**: Enable subtitles. Play set with crowd reactions.
- **Expected**: Visual indicators for crowd laughter (e.g., "[Crowd: Big Laugh]") appear as subtitles.

---

## 6. Localization Testing (Post-1.0)

**Languages**: English (primary), French, German, Spanish (initial set).

### Localization Test Cases

**TLO-001: Component Card Text Translation**
- **Test**: Switch language to French. View component cards.
- **Expected**: All card text translated. Thematic tags localized. Jokes remain culturally coherent (not literal translations).

**TLO-002: UI Text Overflow**
- **Test**: Switch to German (longest language). View all UI screens.
- **Expected**: Text does not overflow containers. UI layout adjusts for longer strings.

**TLO-003: Cultural Adaptation — Jokes**
- **Test**: Review component cards in Spanish.
- **Expected**: Jokes adapted for cultural context (e.g., US-specific references replaced with local equivalents).

---

## 7. Regression Checklist (Post-Fix Verification)

After any bug fix, run this checklist to ensure the fix didn't break existing functionality.

### Regression Tests

**RG-001: Core Loop Functional**
- **Test**: Build joke. Perform. View Laugh Graph. Iterate.
- **Expected**: No crashes. Feedback systems operational.

**RG-002: Save/Load Still Works**
- **Test**: Save game. Quit. Load game.
- **Expected**: All state preserved.

**RG-003: Performance Unchanged**
- **Test**: Run BP-001 (Crowd Engine benchmark).
- **Expected**: Performance within target.

**RG-004: Voice Identity Tracking Active**
- **Test**: Perform 3 sets. Check Voice shift.
- **Expected**: Voice updates correctly.

**RG-005: AI Comedian Scene Still Simulating**
- **Test**: Advance 5 weeks. Check AI career changes.
- **Expected**: AI comedians generate material, book gigs, progress careers.

---

## 8. Known Issues and Risk Areas

These are the systems most likely to break. Monitor closely.

### High-Risk Systems

**HR-001: Crowd Engine Reaction Calculation**
- **Why**: Complex formula with many variables (Momentum, Fatigue, Bleed, Volatility). Easy to introduce edge cases.
- **Watch For**: Division by zero, overflow, unexpected NaN values.
- **Mitigation**: Unit tests for all formulas. Automated test suite with edge case inputs.

**HR-002: Save System JSON Serialization**
- **Why**: Large, nested data structures. Version migration logic.
- **Watch For**: Null reference exceptions on load. Missing fields after version update.
- **Mitigation**: Extensive save/load testing. Version migration automated tests.

**HR-003: Voice Identity Drift Speed**
- **Why**: Formula balancing is subjective. "Feels right" is hard to quantify.
- **Watch For**: Player complaints that Voice shifts too fast or too slow. Authenticity penalties feel unfair.
- **Mitigation**: Playtest feedback. Tunable config values. A/B testing.

**HR-004: AI Material Overlap Detection**
- **Why**: Euclidean distance threshold for "similarity" is arbitrary. False positives/negatives likely.
- **Watch For**: Player reports "I didn't steal this bit." Or: "This AI clearly stole my bit but no penalty."
- **Mitigation**: Tunable similarity threshold. Telemetry on Derivative tag frequency.

**HR-005: Material Staleness Penalty**
- **Why**: -5% per repeat could be too harsh or too lenient depending on playstyle.
- **Watch For**: Players complain about forced material churn. Or: Players abuse repeat sets.
- **Mitigation**: Tunable penalty rate. Playtest data on avg set repeat count.

---

## 9. Bug Severity Definitions

**CRITICAL**: Game-breaking. Crashes, save corruption, progression blockers. Ship-stopper.
**HIGH**: Major feature broken. Core loop disrupted. Severely impacts player experience.
**MEDIUM**: Feature works but not as intended. Workarounds exist. Annoying but not blocking.
**LOW**: Cosmetic, edge case, or minor inconvenience. Polish-level issue.

---

## 10. Testing Schedule (Development Milestones)

### Milestone 1: Vertical Slice (Month 3)
- **Focus**: Core loop clarity. Bit Builder feel. Crowd Engine legibility.
- **Tests**: TB-001 to TB-008, TC-001 to TC-003, TL-001 to TL-003.
- **External Playtest**: 10 people. Gate 1 must pass.

### Milestone 2: Core Systems (Month 6)
- **Focus**: All 5 core systems functional. Save/Load stable.
- **Tests**: Full test plan for Bit Builder, Crowd Engine, Laugh Graph, Voice Identity, Save System.
- **Internal Playtest**: 2-hour sessions. No game-breaking bugs.

### Milestone 3: Mid-Game Content (Month 10)
- **Focus**: The Scene, economy, career progression Tier 3-4.
- **Tests**: TS-001 to TS-007, TE-001 to TE-008, Evil Path tests.
- **External Playtest**: 20 people, 8-hour sessions. Gate 2 must pass.

### Milestone 4: Late-Game and Polish (Month 14)
- **Focus**: Tier 5-6, The Special, audio/visual polish, performance.
- **Tests**: Full performance benchmarks, platform testing (PC + Switch).
- **Internal Playtest**: Full playthrough (Tier 0 to Special).

### Milestone 5: Early Access Launch (Month 15)
- **Focus**: Stability. Community feedback pipeline.
- **Tests**: All CRITICAL and HIGH severity bugs resolved. Gate 3 (performance) and Gate 4 (save corruption) must pass.
- **Post-Launch**: Monitor crash reports, telemetry, player feedback. Hotfix critical issues within 48 hours.

### Milestone 6: 1.0 Release (Month 18)
- **Focus**: Final content, balance, optimization.
- **Tests**: Gate 5 (Voice Identity transparency) must pass. Full regression suite. Accessibility testing.
- **Pre-Launch**: 2-week code freeze. Final QA pass. Zero CRITICAL bugs.

### Milestone 7: Switch Port (Month 24)
- **Focus**: Platform certification.
- **Tests**: Full platform-specific test suite (TSW-001 to TSW-004). Performance benchmarks on real hardware.
- **Certification**: Submit to Nintendo. 2-week soak test before submission.

---

## 11. QA Team and Tools

### Team Structure

**QA Lead**: 1 (CRASH)
**QA Testers**: 2 (Months 1-15), 3 (Months 15-24)
**External Playtesters**: 10-20 per milestone

### Tools

**Bug Tracking**: Jira or Linear
**Test Case Management**: TestRail or spreadsheet
**Automated Testing**: Unity Test Framework for unit tests
**Performance Profiling**: Unity Profiler + custom in-game overlay
**Analytics**: Custom JSON event logging + Python dashboard
**Version Control**: Git (QA branch for test builds)

---

## 12. What Does "Ship-Ready" Mean?

Ship-ready means:

1. **Gate 1 (Core Loop Clarity) passed**: Players understand why jokes succeed/fail.
2. **Gate 3 (Performance Budget) passed**: Framerate targets met on all platforms.
3. **Gate 4 (Save Corruption) passed**: 100/100 save/load cycles successful.
4. **Zero CRITICAL bugs**: No crashes, no save corruption, no progression blockers.
5. **< 5 HIGH bugs**: All high-severity issues either fixed or have documented workarounds.
6. **Accessibility baseline met**: Colorblind mode, text scaling, controller navigation functional.
7. **Regression suite passed**: All core systems operational after final code freeze.

Ship-ready does NOT mean perfect. It means the game delivers on its core promise — the player can build jokes, perform them, and learn from the results — without technical failures destroying that experience.

---

## 13. Post-Launch Support Plan

### Hotfix Window (Weeks 1-4 Post-Launch)

**Priority**: CRITICAL bugs only.
**Response Time**: 24 hours for crash bugs, 48 hours for save corruption.
**Deployment**: Steam hotfix branch -> main. Switch certification for critical fixes only.

### Patch Cadence (Months 1-6 Post-Launch)

**Monthly patches**: Address HIGH and MEDIUM bugs, balance tuning based on telemetry.
**Community feedback integration**: Top 5 requested features/fixes prioritized.
**Balance updates**: Crowd Engine tuning, Voice Identity drift speed, material staleness penalty.

### Content Updates (Months 6-18 Post-Launch)

**DLC packs**: New component cards, new venues, new AI comedian profiles.
**Feature expansions**: Heckler Duels, Writers' Room Mode, Legacy Mode (if successful).

---

## 14. Final Notes from CRASH

This QA plan is a living document. It will change as the game changes. But the core principle does not change: **the player must understand why they failed.**

If we ship a game where the player says "I don't know what I did wrong," we have failed. Full stop.

The Crowd Engine is the highest-risk system. It is also the most important. We will spend 50% of our QA resources on Crowd Engine testing and balancing. If it feels random, the game is broken.

Save corruption is unacceptable. We do not ship with save bugs. We do not patch save bugs. We prevent them. 100 save/load cycles, zero failures, or we do not ship.

Performance targets are not negotiable. 60 FPS on PC, 30 FPS on Switch. If we can't hit those, we cut features or reduce scope. We do not ship a slideshow.

The "evil path" tests are not optional. Players will find every exploit, every edge case, every way to break the systems we built. We find them first.

Where's the regression test? Every fix gets a regression test. If we fixed it once, we test it forever. No backsliding.

What happens if the player does THIS? That's the question I ask for every feature. What if they do the opposite of what we expect? What if they spam the same input 1000 times? What if they leave it idle for an hour? What if they alt-tab mid-performance? What if they pull the power cable during a save? We test the chaos.

Define "works." "Works" is not "it compiled." "Works" is "the player can achieve their goal without the game lying to them." The Laugh Graph works if the player can diagnose their failure. The Bit Builder works if assembling a joke feels creative, not clerical. The Voice Identity system works if the player feels the consequences of their choices, not the randomness of a black box.

We are not the enemy of shipping. We are the enemy of shipping broken.

Let's ship something that respects the player's time, their intelligence, and their trust. Let's ship something that works.

---

**Document Version**: 1.0
**Next Review**: Post-Vertical Slice Playtest (Month 3)
**Owner**: CRASH — QA Lead

END DOCUMENT
