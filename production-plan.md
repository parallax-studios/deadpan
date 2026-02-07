# DEADPAN — Production Plan

**Producer**: CLOCK
**Project**: Stand-up Comedy Empire Simulation
**Status**: Production-ready — Greenlit for prototype build
**Timeline**: 18-24 months to 1.0 launch
**Team Size**: 8 core (prototype-to-EA), scale to 11 (post-EA to 1.0)
**Budget Philosophy**: Scope is the lever. Time is fixed. Quality is non-negotiable on the core loop.

---

## 1. Project Overview

### What We're Building

A stand-up comedy empire simulation where joke construction is a craft system, audiences are living ecosystems, and bombing hurts. The player builds jokes from modular components, performs them to reactive AI crowds, reads diagnostic feedback from the Laugh Graph, and iterates. The game lives or dies on one question: does the 30-second loop feel like creative work, not spreadsheet optimization?

Three months to answer that question. If the vertical slice doesn't sing, we cut or pivot. No heroics. No "it'll get better later."

### Scope Reality Check

**What we promised in the GDD**:
- 300+ component cards
- 9 audience archetypes
- 12 venue types
- 6 career tiers
- 15 AI comedians
- Voice Identity system
- Callback mechanics
- The Special (60-minute set endgame)

**What we're shipping at Early Access (Month 15)**:
- 200 component cards (Tier 1-4 content)
- 9 archetypes (all)
- 8 venues (Tier 1-4)
- 4 career tiers (0-3 complete, 4 feature-complete)
- 12 AI comedians (3 fully fleshed-out with arcs, 9 with basic behavior)
- Voice Identity system (functional, minimal UI)
- Callbacks (system works, limited content)
- The Special: NOT in Early Access — this is the 1.0 hook

**What we're cutting to hit the date**:
- Heckler Duels mini-game (becomes simple three-choice menu, not real-time)
- Comedy Crew system (post-1.0 expansion content)
- Podcast Empire (Tier 5-6 feature, deferred to 1.0)
- Writers' Room Mode (stretch goal, not launch)
- Legacy Mode (post-1.0 if the game succeeds)
- Multiplayer anything (post-1.0 if we're still alive)

The full GDD scope is 24 months. We're shipping a complete 4-tier game in 15 months, then adding Tier 5-6 in the next 3 months based on Early Access feedback. This is the plan.

### Success Criteria

**Prototype success (Month 3)**:
- 8 out of 10 external playtesters can explain why a joke succeeded or failed
- Average playtime: 45+ minutes (they want to keep building and performing)
- Zero confusion about the Bit Builder drag-drop flow

**Early Access success (Month 15-18)**:
- 500+ wishlists before launch
- 70%+ positive Steam reviews in first month
- 10+ hours average playtime (telemetry data)
- Active Discord community providing feedback

**1.0 success (Month 18-24)**:
- 80%+ positive Steam reviews
- 10K units sold in first month
- Median playtime: 20+ hours
- Profitable enough to fund Switch port

If we don't hit Early Access metrics, we reassess before investing in 1.0 content. If we don't hit 1.0 metrics, there's no Switch port. The milestones are checkpoints, not guarantees.

### Team Structure

**Core Team (8 people, Months 1-15)**:
- Lead Programmer (architecture, optimization, Crowd Engine)
- Gameplay Programmer (Bit Builder, career systems, Voice Identity)
- UI Programmer (UI Toolkit, Laugh Graph, all menus)
- Game Designer (systems design, balance, playtesting)
- Content Designer (component card writing, venue definitions)
- Technical Artist (UI art, VFX, shaders)
- 2D Artist (portraits, venue backgrounds, card art)
- Audio Designer (FMOD, crowd audio synthesis, music integration)

**Post-EA Additions (Months 15-24)**:
- QA Tester (full-time)
- Community Manager (part-time)
- Additional Content Designer (Tier 5-6 material)

**Producer Role (me)**: Milestone tracking, scope enforcement, risk management, team health monitoring. I'm the one who says "no" when the feature sounds cool but breaks the timeline. I'm also the one who green-lights cuts before they become emergencies.

---

## 2. Milestones: Prototype → Vertical Slice → Alpha → Beta → RC → Gold

### Milestone 0: Pre-Production (Month 0, 4 weeks)

**Goal**: Lock architecture, build production pipeline, onboard team.

**Deliverables**:
- Unity project setup (2023 LTS, Git repo, GitHub Actions CI)
- Core system scaffolding (BitBuilderSystem, CrowdEngine, LaughGraphSystem stubs)
- ScriptableObject data pipeline (component card templates, archetype templates)
- Custom Unity editor tools (Component Card Creator window)
- Team onboarding (everyone has read the GDD, tech doc, and this production plan)

**Exit Criteria**:
- All team members can build the Unity project locally
- First component card created via editor tool
- First ScriptableObject-based archetype defined
- Git workflow established (feature branches, code review process)

**Owner**: Lead Programmer
**Risk**: None. This is setup work.

---

### Milestone 1: Prototype (Months 1-3, 12 weeks)

**Goal**: Prove the 30-second loop works. Build joke → perform joke → see results → understand why.

**Deliverables**:

**Week 1-4: Bit Builder Foundation**
- Component card data model (Premise, Setup, Misdirection, Punchline types)
- 20 component cards (4 per type, hand-authored)
- Drag-and-drop UI (Unity UI Toolkit)
- Joke assembly logic (snap components together)
- Quality score calculation (Coherence + Surprise + Timing formula)
- Real-time quality display (color-coded 0-100 score)

**Week 5-8: Crowd Engine Core**
- Audience archetype data model (3 archetypes: Comedy Nerds, Date Night Couples, College Students)
- Crowd generation (20-person audience, clustered)
- Reaction calculation (dot product of joke profile vs archetype preferences)
- Reaction output (0.0-1.0 score per cluster, aggregate score)
- No audio yet — visual-only reactions (crowd sprite animations)

**Week 9-12: Performance Loop + Laugh Graph**
- Performance controller (sequence jokes, trigger Crowd Engine, collect results)
- Laugh Graph basic visualization (waveform showing aggregate reaction over time)
- Single venue (dive bar open mic, 20 people, 60% Comedy Nerds, 40% Date Night)
- One complete loop: Apartment (build joke) → Venue Selection → Stage (perform 3-5 jokes) → Post-Set Analysis (view Laugh Graph)

**Exit Criteria**:
- External playtest with 10 people (non-team)
- Playtest survey: "Did you understand why your jokes succeeded or failed?" — 8/10 say YES
- Average session time: 30+ minutes (if they quit earlier, the loop isn't sticky)
- No game-breaking bugs (crashes, soft-locks)

**Owner**: Entire team (this is all-hands)

**Risks**:
- **HIGH RISK**: Bit Builder feels like data entry, not creative work
  - **Mitigation**: Emphasize text over stats in UI. Add thematic icons to cards. Playtest with non-gamers.
  - **Contingency**: If playtest fails, we have 2 weeks to redesign UI before declaring failure. If it still doesn't work, we pivot or cancel.
- **VERY HIGH RISK**: Crowd Engine reactions feel random
  - **Mitigation**: Pre-show crowd composition display. Post-set per-segment breakdown. Clear tooltips on archetype preferences.
  - **Contingency**: If reactions aren't legible, add a "Prediction Mode" that shows expected reaction ranges before performing. This adds a safety net.

**Timeline Slack**: 1 week built in. If we're behind at Week 11, cut Tag component support (defer to Alpha). If still behind, cut third archetype (ship with 2).

---

### Milestone 2: Vertical Slice (Months 4-6, 12 weeks)

**Goal**: All five core systems functional. Career Tier 0-2 playable. Save/Load working.

**Deliverables**:

**Week 13-16: Expand Bit Builder**
- 80 component cards total (distributed across all types)
- Tag component support
- Callback component support (requires setlist history tracking)
- Component card unlock system (career progression gates)
- CSV import tool for batch card creation (designers work in spreadsheets)

**Week 17-20: Expand Crowd Engine**
- 9 audience archetypes (all from GDD)
- 5 venue types (Dive Bar, Comedy Club, Coffee Shop Open Mic, Small Theater, College Venue)
- Momentum system (reactions shift based on recent performance)
- Fatigue system (longer sets get harder)
- Spatial bleed (clusters influence adjacent clusters)
- Heckler check (probabilistic, no mini-game yet — just a negative event)

**Week 21-24: Voice Identity + Career + Save System**
- Voice Identity tracking (5 spectra, Authenticity score)
- Voice Identity UI (radar chart showing player's comedic identity)
- Career Manager (Tier 0-2 progression, REP/CASH economy)
- Venue unlock system (REP gates)
- Save/Load system (JSON serialization, 3 save slots, auto-save)
- Laugh Graph expanded (5 analysis views: Overview, Per-Segment, Pivot Analysis, Setlist Flow, Comparison)

**Exit Criteria**:
- Internal team playthrough: Tier 0 to Tier 2 in 2-3 hours, no critical bugs
- Save/Load works (save mid-session, close game, reopen, continue seamlessly)
- Laugh Graph provides actionable feedback (designers can diagnose why a joke bombed)
- Voice Identity system is visible and shifts based on material choices

**Owner**: Split responsibility (Gameplay Programmer owns Career/Voice, UI Programmer owns Laugh Graph, Lead owns Crowd Engine expansion)

**Risks**:
- **MEDIUM RISK**: Save system corrupts on edge cases
  - **Mitigation**: Unit tests for serialization. QA pass with intentional edge cases (save during performance, save with empty material library).
  - **Contingency**: If save corruption appears in playtesting, add redundant backup auto-saves (rolling 3-save system).
- **MEDIUM RISK**: Voice Identity feels meaningless
  - **Mitigation**: Career gating must be visible (certain venues require specific Voice profiles). UI must show Voice shift after every performance.
  - **Contingency**: If playtest feedback is "I don't care about Voice," reduce gating severity or make Voice shifts more dramatic (faster feedback).

**Timeline Slack**: 2 weeks built in. If behind at Week 22, cut Comparison view from Laugh Graph (nice-to-have). If still behind, cut Pivot Analysis view.

---

### Milestone 3: Alpha (Months 7-10, 16 weeks)

**Goal**: Tier 3-4 content. The Scene (AI comedians). Economy expanded. Mid-game loop feels engaging.

**Deliverables**:

**Week 25-28: Career Tier 3-4**
- 8 venues total (add 3 new Tier 3-4 venues)
- 200 component cards total (120 new cards)
- Agent system (agent relationship, agent cut from gigs, agent unlocks higher-tier venues)
- Merch system (passive income at Tier 4)
- Touring (multi-city gig sequences, optional)

**Week 29-34: The Scene (AI Comedians)**
- 12 AI comedian profiles (ScriptableObject definitions)
- AI comedian state machine (career progression, material generation, gig booking)
- Rival/collaborator relationship system (-100 to +100 scale)
- Scene events (rival steals material, collaborator offers podcast guest spot, club closes, festival announces)
- Material overlap detection (if AI comic performs similar joke at bigger venue first, player's version gets "Derivative" tag)

**Week 35-40: Mid-Game Tuning**
- Crowd Engine balance pass (tuning archetype preferences based on internal playtesting)
- Component card balance pass (identify underpowered/overpowered cards, adjust stats)
- Economy tuning (CASH flow, rent pressure, agent fees)
- UI polish pass (animations, transitions, screen juice)

**Exit Criteria**:
- Extended playtest (20 people, 6-8 hour target session)
- Playtest survey: "Did the mid-game feel engaging or repetitive?" — 70%+ say "engaging"
- AI comedians feel alive (playtesters mention rival names in feedback)
- No soft-locks, no critical bugs, stable framerate (60 FPS on mid-tier PC)

**Owner**: Gameplay Programmer (AI system), Content Designer (200 cards is a mountain of work), Game Designer (balance pass)

**Risks**:
- **HIGH RISK**: AI comedian system tanks performance
  - **Mitigation**: Scene simulation runs during "advance week" action, not real-time. Budget 200ms max for 12 AI sims.
  - **Contingency**: Reduce AI count to 10 if performance is unacceptable. The scene still feels alive with 10 comics.
- **MEDIUM RISK**: Mid-game grind feels repetitive
  - **Mitigation**: Scene events must fire frequently (1-2 per in-game week). Rival dynamics create drama.
  - **Contingency**: If playtesting reveals grind, increase REP earnings by 20% to accelerate progression. We'd rather players finish than quit.

**Timeline Slack**: 2 weeks built in. If behind at Week 38, reduce AI comedian count to 10 (cut 2 profiles). If still behind, defer Touring system to post-EA.

---

### Milestone 4: Beta (Months 11-14, 16 weeks)

**Goal**: Tier 4 complete. Audio/visual polish. Early Access launch prep.

**Deliverables**:

**Week 41-46: Audio Implementation**
- FMOD integration
- Procedural crowd audio system (granular laughter synthesis from 500+ samples)
- Venue-specific ambiance loops (6 unique venue soundscapes)
- Music integration (adaptive stems for apartment, green room, city, career screen)
- Performance state audio modulation (player breath, mic handling, nervous tics)

**Week 47-52: Visual Polish**
- Venue environment art (12 unique venue backgrounds)
- Character portraits (player + 12 AI comedians)
- Component card art (icons for 200 cards)
- UI animation pass (card drag/snap, napkin placement, graph rendering)
- VFX pass (spotlight effects, Laugh Graph glow, screen transitions)

**Week 53-56: Early Access Prep**
- Steam integration (Steamworks.NET: achievements, cloud saves, leaderboards)
- Telemetry pipeline (analytics events for Bit Builder usage, Laugh Graph views, setlist patterns)
- Tutorial sequence (onboarding for new players, skippable for returning players)
- Settings menu (audio/video options, accessibility features, keybinding)
- Early Access launch trailer (30-60 second trailer showing core loop)

**Exit Criteria**:
- Full Tier 0-4 playthrough (10-15 hours) is polished and stable
- Audio adds 50%+ to game feel (internal team consensus)
- Steam page is live with trailer, screenshots, wishlists tracking
- No critical bugs, 60 FPS stable on min-spec PC

**Owner**: Audio Designer (audio), Technical Artist + 2D Artist (visuals), UI Programmer (Steam integration)

**Risks**:
- **MEDIUM RISK**: Audio implementation takes longer than expected
  - **Mitigation**: FMOD is well-documented. Audio Designer has prior FMOD experience (if not, this is a hiring requirement).
  - **Contingency**: Ship EA with simplified crowd audio (pre-rendered samples, not procedural). Add procedural system in Month 16.
- **LOW RISK**: Wishlist count is below target (<500)
  - **Mitigation**: Start building audience 3 months before EA launch (Twitter, Reddit r/gamedev, r/tycoon, TikTok clips).
  - **Contingency**: Delay EA launch by 2-4 weeks to build more wishlists. Launching to an empty room is death.

**Timeline Slack**: 2 weeks built in. If behind at Week 54, defer leaderboards (nice-to-have). If still behind, ship without cloud saves (add post-launch).

---

### Milestone 5: Early Access Launch (Month 15)

**Goal**: Ship to Steam Early Access. Begin community feedback loop.

**Launch Checklist**:
- Steam page live with accurate description, screenshots, trailer
- Tier 1-4 content complete and polished
- Tier 5-6 feature-complete but content-light (visible in progression, not fully playable)
- Save/Load tested extensively (no corruption bugs)
- Performance stable (60 FPS on GTX 1060 equivalent)
- Tutorial skippable but functional
- Discord server active
- Launch day social media posts scheduled
- Press kit sent to 50+ indie game journalists/YouTubers

**Launch Week Activities**:
- Monitor Steam reviews (respond to critical bugs within 24 hours)
- Monitor Discord for feedback
- Hotfix patch within 72 hours if critical issues appear
- Community manager posts daily updates ("We hear you on X, investigating")

**Success Metrics (First Month)**:
- 70%+ positive reviews
- 500+ units sold
- Average playtime 8+ hours (telemetry)
- Active Discord (50+ daily active users)

**Owner**: Producer (that's me) + Community Manager

**Risks**:
- **HIGH RISK**: Launch day critical bugs
  - **Mitigation**: 2-week QA lockdown before launch (no new features, bug fixes only). Soak test on 10 different PC configurations.
  - **Contingency**: Delay launch by 1 week if critical bugs appear in final QA pass. Better to delay than launch broken.

---

### Milestone 6: Early Access → 1.0 (Months 16-18, 12 weeks)

**Goal**: Tier 5-6 content complete. Balance pass based on EA feedback. Polish. 1.0 launch.

**Deliverables**:

**Week 57-62: Tier 5-6 Content**
- 400+ component cards total (200 new cards for late-game)
- 12 venues total (4 new Tier 5-6 venues: theaters, festival tents, late-night studios)
- Podcast Empire system (Tier 5 unlock)
- Special taping sequence (60-minute set, narrative arc, final boss)
- Voice Identity gating (certain career paths require specific Voice profiles)

**Week 63-66: Balance Pass (Data-Driven)**
- Analyze telemetry from EA (which archetypes are too easy/hard? which venues are under-used?)
- Crowd Engine tuning (adjust archetype preferences, momentum curves, fatigue rates)
- Economy tuning (adjust REP costs, CASH flow, pacing)
- Component card balance (identify dead cards, buff/nerf)

**Week 67-68: 1.0 Polish + Launch Prep**
- Final bug fixing pass
- Performance optimization (hit framerate targets on min-spec)
- 1.0 launch trailer (extended, showcases full career arc)
- Press outreach (review copies to journalists/streamers)

**Exit Criteria**:
- Full playthrough (Tier 0 to Special) in 20-25 hours
- 80%+ positive reviews on Steam
- Stable performance (no crashes, 60 FPS on target hardware)

**Owner**: Game Designer (balance pass), Content Designer (200 new cards), Lead Programmer (optimization)

**Risks**:
- **MEDIUM RISK**: EA feedback reveals fundamental issues with Crowd Engine
  - **Mitigation**: Monthly balance patches during EA period. Communicate changes transparently.
  - **Contingency**: If Crowd Engine requires major redesign, delay 1.0 by 2-3 months. This is the core loop. It must work.

**Timeline Slack**: 2 weeks built in. If behind at Week 66, cut Podcast Empire (defer to post-1.0 DLC).

---

### Milestone 7: 1.0 Release (Month 18)

**Goal**: Exit Early Access. Full 1.0 launch.

**Launch Checklist**:
- Tier 5-6 complete
- Special taping sequence polished
- 400+ component cards
- All features from GDD implemented (except cut list)
- Performance optimized
- 1.0 trailer live
- Press coverage scheduled
- Community informed (exit announcement 2 weeks before)

**Launch Week Activities**:
- Same as EA launch (monitor reviews, Discord, hotfix readiness)
- Post-launch content roadmap announced (builds goodwill)

**Success Metrics (First Month)**:
- 80%+ positive reviews
- 10K units sold
- Median playtime 20+ hours
- Profitable (covers dev costs + funds Switch port)

---

### Milestone 8: Switch Port (Months 19-24, Optional)

**Goal**: Launch on Nintendo Switch (only if 1.0 is profitable).

**Deliverables**:
- Switch-optimized build (30 FPS stable, reduced crowd cluster count)
- Controller-native UI
- Nintendo certification submission
- eShop listing and trailer

**Exit Criteria**:
- Certification pass
- 5K units sold in first month (Switch market is different, lower expectations)

**Owner**: Lead Programmer (port), UI Programmer (controller UI)

**Risks**:
- **LOW RISK**: Certification failure
  - **Mitigation**: 2-week soak test on Switch dev kits before submission
  - **Contingency**: Delay Switch by 2-3 months if certification fails. PC is unaffected.

---

## 3. Sprint Plan (First 12 Weeks / Prototype Phase)

We're running 2-week sprints. Each sprint has clear deliverables. No epic user stories, no abstract goals. Concrete outputs only.

### Sprint 1 (Weeks 1-2): Bit Builder Foundation

| Task | Owner | Estimate | Dependency | Priority |
|------|-------|----------|------------|----------|
| Component card data model (ScriptableObject) | Lead Programmer | 1 day | None | P0 |
| Joke data model (assembly struct) | Lead Programmer | 1 day | Component card model | P0 |
| Quality calculator (Coherence + Surprise + Timing) | Gameplay Programmer | 3 days | Joke data model | P0 |
| Component Card Creator (Unity editor tool) | Lead Programmer | 2 days | Component card model | P1 |
| Write 20 component cards (4 per type) | Content Designer | 3 days | Card creator tool | P0 |
| Bit Builder UI (drag-drop placeholder) | UI Programmer | 4 days | None | P0 |
| Card library display (scrollable list) | UI Programmer | 2 days | Bit Builder UI | P1 |

**Sprint Goal**: End of Sprint 1, we can create component cards and see them in a UI list.

**Sprint Review**: Demo to team — drag a card, see it appear in the library. Quality score doesn't calculate yet, that's Sprint 2.

---

### Sprint 2 (Weeks 3-4): Bit Builder Assembly

| Task | Owner | Estimate | Dependency | Priority |
|------|-------|----------|------------|----------|
| Drag-and-drop logic (UI Toolkit drag handlers) | UI Programmer | 4 days | Bit Builder UI | P0 |
| Snap zones (component slots on assembly board) | UI Programmer | 2 days | Drag-and-drop logic | P0 |
| Joke assembly validation (require Premise+Setup+Misdirection+Punchline) | Gameplay Programmer | 1 day | Drag-and-drop logic | P0 |
| Quality score display (color-coded 0-100) | UI Programmer | 1 day | Quality calculator | P0 |
| Real-time quality update (recalc on card snap) | Gameplay Programmer | 1 day | Quality calculator | P1 |
| Card art (placeholder icons, 20 cards) | 2D Artist | 3 days | Component cards exist | P1 |

**Sprint Goal**: End of Sprint 2, we can build a complete joke and see its quality score.

**Sprint Review**: Demo to team — build a joke from 4 cards, see quality score appear and update live.

---

### Sprint 3 (Weeks 5-6): Crowd Engine Foundation

| Task | Owner | Estimate | Dependency | Priority |
|------|-------|----------|------------|----------|
| Audience archetype data model (ScriptableObject) | Lead Programmer | 1 day | None | P0 |
| Create 3 archetypes (Comedy Nerds, Date Night, College Students) | Game Designer | 1 day | Archetype model | P0 |
| Audience cluster struct | Lead Programmer | 1 day | Archetype model | P0 |
| Crowd generation logic (sample from archetype distribution) | Lead Programmer | 2 days | Cluster struct | P0 |
| Reaction calculation (dot product formula) | Lead Programmer | 2 days | Crowd generation | P0 |
| Reaction data struct (per-cluster + aggregate scores) | Lead Programmer | 1 day | Reaction calculation | P0 |
| Crowd sprite rendering (simple circle avatars) | Technical Artist | 3 days | Cluster struct | P1 |

**Sprint Goal**: End of Sprint 3, Crowd Engine can generate a 20-person audience and calculate reaction to a joke.

**Sprint Review**: Demo to team — generate crowd, feed it a joke, print reaction scores to console. No UI yet.

---

### Sprint 4 (Weeks 7-8): Crowd Engine Visualization

| Task | Owner | Estimate | Dependency | Priority |
|------|-------|----------|------------|----------|
| Crowd sprite animations (idle, laugh, disengage) | Technical Artist | 3 days | Crowd rendering | P0 |
| Reaction-to-animation mapping | Gameplay Programmer | 2 days | Crowd animations | P0 |
| Aggregate reaction display (simple UI bar) | UI Programmer | 1 day | Reaction calculation | P0 |
| Venue data model (ScriptableObject) | Lead Programmer | 1 day | None | P0 |
| Create 1 venue (Dive Bar Open Mic, 20 people, 60/40 split) | Game Designer | 1 day | Venue model | P0 |
| Crowd generation from venue config | Lead Programmer | 1 day | Venue model + crowd generation | P0 |

**Sprint Goal**: End of Sprint 4, we can see the crowd react visually to a joke.

**Sprint Review**: Demo to team — perform a joke, watch crowd sprites laugh or stay silent. Magic moment.

---

### Sprint 5 (Weeks 9-10): Performance Loop

| Task | Owner | Estimate | Dependency | Priority |
|------|-------|----------|------------|----------|
| Performance controller (sequence jokes, manage state) | Gameplay Programmer | 3 days | None | P0 |
| Setlist data model (list of JokeData) | Gameplay Programmer | 1 day | Joke data model | P0 |
| Setlist builder UI (drag jokes onto napkin) | UI Programmer | 3 days | Bit Builder UI | P0 |
| Venue selection UI (single venue button for now) | UI Programmer | 1 day | Venue model | P1 |
| Joke presentation sequence (display joke text, pause, trigger crowd reaction) | Gameplay Programmer | 2 days | Performance controller | P0 |
| Screen transitions (apartment → venue selection → stage) | UI Programmer | 2 days | None | P1 |

**Sprint Goal**: End of Sprint 5, we have a complete loop: build joke → add to setlist → select venue → perform.

**Sprint Review**: Demo to team — full loop playthrough. This is the first time the game feels like a game.

---

### Sprint 6 (Weeks 11-12): Laugh Graph + Prototype Polish

| Task | Owner | Estimate | Dependency | Priority |
|------|-------|----------|------------|----------|
| Laugh Graph data collection (track reactions per joke) | Gameplay Programmer | 1 day | Performance controller | P0 |
| Laugh Graph waveform rendering (UI Toolkit vector graphics) | UI Programmer | 3 days | Laugh Graph data | P0 |
| Post-set analysis screen (show waveform + joke labels) | UI Programmer | 2 days | Waveform rendering | P0 |
| Hover tooltips (show joke details on waveform hover) | UI Programmer | 1 day | Analysis screen | P1 |
| Apartment scene (placeholder background + corkboard) | 2D Artist | 2 days | None | P1 |
| Stage scene (placeholder background + spotlight) | 2D Artist | 2 days | None | P1 |
| Tutorial tooltips (explain Bit Builder, Crowd Engine, Laugh Graph) | Game Designer | 2 days | All systems exist | P1 |
| Bug fixing pass (crash fixes, soft-lock fixes) | Entire team | 2 days | All features complete | P0 |

**Sprint Goal**: End of Sprint 6, prototype is playable end-to-end with Laugh Graph feedback.

**Sprint Review**: Demo to external playtesters (10 people). This is the validation milestone.

---

## 4. Risk Register

| Risk | Likelihood | Impact | Mitigation | Contingency | Owner |
|------|------------|--------|------------|-------------|-------|
| **Bit Builder feels like spreadsheet** | High | Critical | Emphasize text over stats. Playtest with non-gamers. Add thematic icons. | If playtest fails: 2-week UI redesign. If still fails: pivot or cancel. | UI Programmer |
| **Crowd Engine reactions feel random** | High | Critical | Pre-show crowd display. Post-set per-segment breakdown. Clear tooltips. | Add "Prediction Mode" showing expected reactions before performing. | Lead Programmer |
| **Performance bottleneck (crowd sim)** | Medium | High | Burst-compiled jobs. Cluster-based simulation (max 500 clusters, not 1:1). | Reduce cluster count dynamically (250 on low-end PC, 150 on Switch). | Lead Programmer |
| **Late-game content starvation** | Medium | Medium | Target 500+ cards (not 300). Cultural Moments generate dynamic content. | Post-launch content DLCs ("Brooklyn Pack", "Dark Material Pack"). | Content Designer |
| **AI comedian sim tanks performance** | Medium | Medium | Scene sim runs during "advance week", not real-time. Budget 200ms max. | Reduce AI count from 15 to 10. Scene still feels alive. | Gameplay Programmer |
| **Mid-game grind feels repetitive** | Medium | High | Scene events fire frequently (1-2 per week). Rival dynamics create drama. | Increase REP earnings 20% to accelerate progression. | Game Designer |
| **Audio implementation delays** | Medium | Medium | FMOD is well-documented. Hire Audio Designer with FMOD experience. | Ship EA with simplified crowd audio (pre-rendered, not procedural). | Audio Designer |
| **Save system corruption** | Low | High | Unit tests for serialization. Extensive QA with edge cases. | Redundant auto-saves (rolling 3-save system). | Gameplay Programmer |
| **Switch certification failure** | Low | Medium | 2-week soak test on dev kits before submission. | Delay Switch by 2-3 months. PC unaffected. | Lead Programmer |
| **EA launch day critical bugs** | Low | Critical | 2-week QA lockdown before launch. Soak test on 10 PC configs. | Delay launch by 1 week if critical bugs found in final QA. | Producer |

---

## 5. Critical Path

The critical path is the sequence of tasks that determines the minimum project duration. Any delay on the critical path delays the entire project.

**Critical Path (Prototype Phase, Months 1-3)**:
```
Component Card Model → Joke Data Model → Quality Calculator → Bit Builder UI →
Drag-Drop Logic → Archetype Model → Crowd Generation → Reaction Calculation →
Crowd Rendering → Performance Controller → Laugh Graph → External Playtest
```

**Timeline**: 12 weeks. Zero slack. If any critical path task slips, the prototype slips.

**Critical Path (EA Launch, Months 1-15)**:
```
Prototype Success → Voice Identity System → Career Progression Tier 0-2 →
Save/Load → Tier 3-4 Content → AI Comedian System → Audio Implementation →
Visual Polish → Steam Integration → QA Lockdown → EA Launch
```

**Timeline**: 15 months. 4 weeks slack built in (distributed across milestones).

**What's NOT on the critical path**:
- Heckler Duels (cut to menu-based system)
- Podcast Empire (Tier 5-6 feature, deferred)
- Touring (optional feature, can be cut)
- Callback Tag animations (nice-to-have)
- Leaderboards (nice-to-have)

If we're behind schedule, we cut non-critical-path features before we extend the timeline.

---

## 6. Scope Management

**The Golden Rule**: We cut scope, not corners. A smaller, polished game beats a larger, broken game.

**Cut List (Pre-Approved)**:
- Heckler Duels → Simple menu (cut real-time mini-game)
- Comedy Crew system → Post-1.0
- Podcast Empire → Tier 5-6 only, cut if behind schedule
- Writers' Room Mode → Stretch goal
- Legacy Mode → Post-1.0
- Multiplayer → Post-1.0

**What We Do NOT Cut**:
- Bit Builder (core system)
- Crowd Engine (core system)
- Laugh Graph (core system)
- Voice Identity (strategic layer)
- Career progression Tier 0-4 (minimum viable game)
- Save/Load (table stakes)
- AI comedians (the scene is the soul)

**Scope Triggers** (automatic cuts if these conditions are met):
- If Prototype playtest fails at Month 3 → Reassess entire project
- If Alpha is 4+ weeks behind schedule → Cut Touring, reduce AI comedian count to 10
- If Beta is 4+ weeks behind schedule → Cut Podcast Empire, ship EA without Tier 5-6 preview
- If 1.0 is 4+ weeks behind schedule → Cut Podcast Empire permanently

**Producer's Authority**: I have authority to cut any non-core feature without team vote if it's blocking a milestone. The team can appeal, but the default is "cut first, discuss later."

---

## 7. Team Health and Sustainability

**No Crunch Policy**: Crunch is a management failure. We plan for 40-hour weeks. If we're consistently over 40 hours, we're over-scoped.

**Burnout Indicators**:
- Team member works 3+ weekends in a row
- Team member ships code without tests/review (rushing)
- Team member stops participating in standups/reviews
- Team member requests to switch tasks repeatedly (disengagement)

**Mitigation**:
- Weekly 1-on-1s with each team member (15 minutes, "how are you feeling?")
- Monthly team retrospectives (what's working, what's not)
- Slack time built into milestones (2-4 weeks per milestone)
- Cut scope before asking for overtime

**Prototype Phase Exception**: The first 3 months are high-intensity. This is expected. But we don't maintain that pace. After prototype validation, we shift to sustainable pacing.

---

## 8. Communication and Reporting

**Daily Standups** (15 minutes, async in Discord):
- What did you do yesterday?
- What are you doing today?
- Any blockers?

**Weekly Sprint Planning** (60 minutes, Mondays):
- Review last sprint deliverables
- Assign tasks for next sprint
- Identify blockers
- Update task board (Trello/Notion)

**Bi-Weekly Sprint Review** (60 minutes, Fridays):
- Demo completed work
- Playtest internally
- Collect feedback
- Identify bugs

**Monthly Milestone Review** (90 minutes):
- Assess milestone progress
- Update project timeline
- Identify risks
- Discuss scope adjustments

**Quarterly All-Hands** (2 hours):
- Review overall project health
- Share financial status (if relevant)
- Celebrate wins
- Discuss long-term vision

---

## 9. Success Metrics (Data-Driven)

**Prototype Phase (Month 3)**:
- External playtest: 8/10 understand why jokes succeed/fail
- Average session time: 30+ minutes
- Zero soft-locks or crashes

**Alpha Phase (Month 10)**:
- Extended playtest: 70%+ say mid-game is engaging
- Average session time: 6-8 hours
- Stable 60 FPS on mid-tier PC

**Beta Phase (Month 14)**:
- Full Tier 0-4 playthrough: 10-15 hours
- Audio adds 50%+ to game feel (team consensus)
- 500+ Steam wishlists

**Early Access Launch (Month 15)**:
- 70%+ positive reviews (first month)
- 500+ units sold (first month)
- Average playtime: 8+ hours (telemetry)

**1.0 Launch (Month 18)**:
- 80%+ positive reviews
- 10K units sold (first month)
- Median playtime: 20+ hours
- Profitable (covers dev costs + funds Switch port)

If we miss these metrics by >20%, we reassess before proceeding to the next phase.

---

## 10. Budget and Resource Allocation

**Team Costs (8 people, 15 months to EA)**:
- Average salary (indie rates): $60K/year per person
- Total team cost: $60K × 8 × 1.25 years = $600K

**Additional Costs**:
- Unity licenses (8 Pro licenses × $200/month × 15 months) = $24K
- FMOD licenses (indie tier, free)
- Software (Adobe CC, etc.): $3K
- Contractor music: $5K
- Contractor SFX: $3K
- Marketing (trailer, key art, PR): $15K
- Steam Direct fee: $100
- Misc (testing hardware, snacks): $5K

**Total Budget (EA Launch)**: $655K

**Revenue Targets**:
- Break-even: 10K units @ $20 = $200K gross, $140K after Steam cut, need 4.7x sales to break even on EA launch
- Realistic target: 5K units in EA first month, 20K units by 1.0 (Month 18) = $280K net → not profitable yet, but funds 1.0 development
- Success target: 50K units by end of Year 1 = $700K net → profitable, funds Switch port + DLC

**Risk**: If EA sells <2K units in first month, reassess 1.0 development. Pivot or cancel.

---

## 11. Closing Notes

This plan is a contract between the team and reality. We're building a game in 18-24 months. The scope is ambitious but achievable. The milestones are checkpoints, not guarantees. If the prototype doesn't work at Month 3, we pivot or cancel. If Early Access doesn't hit metrics, we reassess before investing in 1.0.

The critical path is the Bit Builder → Crowd Engine → Laugh Graph loop. Everything else is scaffolding. We ship the loop first, then we wrap a game around it.

We cut scope, not corners. A small, polished game beats a large, broken game. The cut list is pre-approved. If we're behind, we cut. No heroics. No "we'll just work weekends." Crunch is a failure of planning.

The team's health matters. Burnout ships bad games. We work 40-hour weeks. We build slack into the timeline. If we're consistently over 40 hours, we're over-scoped and we cut.

This is the plan. Now we execute.

What's the MVP? A 3-joke prototype that makes 8 out of 10 playtesters say "I get it."

Cut scope, not corners.

When is this actually shipping? Early Access in 15 months. 1.0 in 18 months. Switch in 24 months (if we're still alive).

What's the dependency? Prototype success. If Month 3 fails, nothing else matters.

Who's blocked? Nobody. That's my job.

---

**Document Version**: 1.0
**Author**: CLOCK (Producer)
**Last Updated**: 2026-02-07
**Next Review**: End of Prototype Phase (Month 3)
**Absolute File Path**: /Users/burcukose/git/project-draft/games/13-deadpan/production-plan.md

END DOCUMENT
