# DEADPAN — Release Plan Document

**Game**: DEADPAN — Stand-up Comedy Empire Simulation
**Release Manager**: SHIP
**Status**: Production Release Plan — Ready for Implementation
**Target Platforms**: PC (Steam Primary), Nintendo Switch (Secondary)
**Target Release**: Q4 2027 (Early Access Q2 2027)
**Document Version**: 1.0
**Last Updated**: 2026-02-07

---

## 1. Executive Summary

DEADPAN is launching into a blue ocean market with zero direct competition and two distinct audiences — tycoon sim players and comedy fans. This is an advantage and a vulnerability. The advantage is novelty. The vulnerability is that we have no proven path to follow. Launch day defines this game's entire trajectory.

This release plan accounts for:
- Two-phase launch (Early Access, then 1.0)
- Steam as primary platform with high community engagement requirements
- Switch port as secondary platform with separate certification path
- Content-driven marketing that generates shareable moments
- Post-launch balancing based on telemetry (Crowd Engine tuning is not guesswork)
- Rollback procedures for every critical system
- Age rating considerations for comedy content with Edge axis

The plan is checklist-driven. If it's not on the checklist, it doesn't happen. Launch day will be boring. That means we did our job.

---

## 2. Master Launch Checklist

### Phase 1: Pre-Production Complete (Month 0 — NOW)
- [x] Pitch document finalized
- [x] Game design document finalized
- [x] Technical architecture document finalized
- [ ] Release plan document finalized (this document)
- [ ] Art direction document finalized
- [ ] Sound design document finalized
- [ ] Project repository initialized
- [ ] Development team hired and onboarded
- [ ] Development timeline locked (18-24 month target)

### Phase 2: Vertical Slice (Months 1-3)
- [ ] Bit Builder prototype with 20 component cards
- [ ] Crowd Engine prototype with 3 archetypes, 1 venue
- [ ] Laugh Graph basic visualization
- [ ] One full performance loop functional
- [ ] External playtest with 10 testers
- [ ] Playtest feedback document created
- [ ] Steam partner account activated
- [ ] Steam app ID reserved
- [ ] Early wishlist landing page live (coming soon page)

### Phase 3: Core Systems Complete (Months 4-6)
- [ ] All five core systems functional (Bit Builder, Crowd Engine, Laugh Graph, Voice Identity, Career Manager)
- [ ] 80 component cards authored and balanced
- [ ] Save/Load system implemented and tested
- [ ] Tier 0-2 career progression complete
- [ ] Internal 2-hour playtest successful
- [ ] First trailer teaser (15-second GIF of Bit Builder + crowd reaction)
- [ ] Steam page draft prepared (store description, screenshots, video)
- [ ] Press kit v1 prepared
- [ ] Discord server launched
- [ ] Analytics pipeline implemented and tested

### Phase 4: Mid-Game Content (Months 7-10)
- [ ] Tier 3-4 career progression complete
- [ ] AI comedian system with 15 active comics
- [ ] Economy systems (agent, merch, cash flow) implemented
- [ ] 200 component cards total
- [ ] Callback system fully integrated
- [ ] 20-person playtest (8-hour session target)
- [ ] Steam page published (public)
- [ ] First full trailer (60-90 seconds)
- [ ] Press outreach begins (indie game sites, simulation game press)
- [ ] Wishlist campaign begins

### Phase 5: Late-Game and Polish (Months 11-14)
- [ ] Tier 5-6 career progression complete
- [ ] Special taping sequence implemented
- [ ] FMOD procedural crowd audio implemented
- [ ] UI polish pass (animations, transitions, juice)
- [ ] 300+ component cards total
- [ ] Cultural Moment system implemented
- [ ] Full playthrough test (Tier 0 to Special)
- [ ] Performance optimization pass (hit framerate targets)
- [ ] Steam achievements defined and implemented (minimum 20)
- [ ] Steam trading cards designed (minimum 5 base cards)
- [ ] Cloud save integration tested
- [ ] Age rating application submitted (ESRB, PEGI, IARC)

### Phase 6: Early Access Prep (Month 15)
- [ ] Early Access build feature-locked
- [ ] Tier 1-4 fully polished
- [ ] Tier 5-6 feature-complete (light on content)
- [ ] All critical bugs resolved (zero crash bugs, zero save corruption bugs)
- [ ] Steam Early Access page updated with EA timeline and roadmap
- [ ] Community feedback channels established (Discord, Steam forums)
- [ ] Telemetry dashboard operational
- [ ] Press review copies prepared (embargo: EA launch day)
- [ ] Launch trailer finalized
- [ ] Steam launch checklist complete (see Section 3.2)
- [ ] Early Access launch day plan created (hour-by-hour timeline)
- [ ] Rollback procedure tested
- [ ] Hotfix pipeline tested

### Phase 7: Early Access Launch (Month 15)
- [ ] EA build uploaded to Steam
- [ ] Launch day monitoring active (see Section 8)
- [ ] Press embargo lifts
- [ ] Social media launch campaign executes
- [ ] Team on-call for first 72 hours
- [ ] First patch prepared (Day 1 hotfix for any critical issues)
- [ ] Community manager monitoring Discord/Steam forums 24/7 (first week)

### Phase 8: Early Access Period (Months 15-18)
- [ ] Monthly content updates (new component card packs)
- [ ] Crowd Engine balance patches based on telemetry
- [ ] Community feedback integrated into development
- [ ] Bug fix patches as needed
- [ ] Tier 5-6 content completed
- [ ] 400+ component cards total
- [ ] Performance optimization continued
- [ ] 1.0 launch date announced (minimum 1 month notice)

### Phase 9: 1.0 Launch Prep (Months 17-18)
- [ ] 1.0 build feature-locked
- [ ] All EA feedback integrated
- [ ] Final Crowd Engine balance pass
- [ ] Final performance optimization pass
- [ ] Age rating received (ESRB, PEGI, IARC)
- [ ] Age rating content descriptors added to Steam page
- [ ] Full content review (all 400+ component cards reviewed for consistency)
- [ ] Press review copies sent (embargo: 1 week before launch)
- [ ] Launch trailer updated for 1.0
- [ ] Steam launch discount planned (10% launch week discount)
- [ ] 1.0 launch day plan created
- [ ] Post-launch content roadmap published

### Phase 10: 1.0 Launch (Month 18)
- [ ] 1.0 build uploaded to Steam
- [ ] Early Access tag removed
- [ ] Launch day monitoring active
- [ ] Press embargo lifts
- [ ] Launch discount goes live
- [ ] Team on-call for first 72 hours
- [ ] First post-launch patch prepared

### Phase 11: Switch Port Prep (Months 19-22)
- [ ] Switch devkit acquired
- [ ] Switch-optimized build started
- [ ] Performance profiling on real Switch hardware
- [ ] Controller-native UI implemented
- [ ] 30 FPS target validated
- [ ] Nintendo Developer Portal account activated
- [ ] Switch age rating application submitted (ESRB, PEGI)
- [ ] Lotcheck preparation documentation complete

### Phase 12: Switch Certification (Months 22-24)
- [ ] Switch build submitted to Nintendo Lotcheck
- [ ] Lotcheck feedback addressed
- [ ] Resubmission if needed
- [ ] Certification approval received
- [ ] eShop listing created
- [ ] Switch launch trailer created
- [ ] Switch press copies prepared
- [ ] Switch launch day plan created

### Phase 13: Switch Launch (Month 24)
- [ ] Switch build live on eShop
- [ ] Launch day monitoring active
- [ ] Cross-promotion with PC version
- [ ] Team on-call for first 72 hours

---

## 3. Build Pipeline

### 3.1 Build Pipeline Architecture

**Version Control**: Git + GitHub

**Branch Strategy**:
- `main`: Release-ready builds only. Every commit on main is shippable.
- `develop`: Active development. Daily commits. Automated builds.
- `early-access`: EA release branch. Hotfixes merged here, then to main.
- `feature/*`: Feature branches. Merged to develop via pull request.

**Automated Build Pipeline** (GitHub Actions):

```yaml
name: DEADPAN Build Pipeline

on:
  push:
    branches: [main, develop, early-access]
  pull_request:
    branches: [develop]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
      - name: Run unit tests (JokeQualityCalculator, ReactionCalculation)
      - name: Run integration tests (save/load, performance loop)

  build-windows:
    needs: test
    runs-on: windows-latest
    steps:
      - name: Checkout code
      - name: Build Windows x64 (Steam SDK included)
      - name: Upload artifact to Steam (internal beta branch)

  build-mac:
    needs: test
    runs-on: macos-latest
    steps:
      - name: Checkout code
      - name: Build macOS Universal
      - name: Upload artifact to Steam

  build-linux:
    needs: test
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
      - name: Build Linux x64
      - name: Upload artifact to Steam

  notify:
    needs: [build-windows, build-mac, build-linux]
    runs-on: ubuntu-latest
    steps:
      - name: Notify Discord channel (build success/failure)
```

**Build Cadence**:
- **Development builds**: Automated on every push to `develop`. Daily builds minimum.
- **Playtest builds**: Weekly manual trigger. Friday builds for weekend testing.
- **Release Candidate builds**: Manual trigger. Final testing before Steam upload.

### 3.2 Steam Build Upload Procedure

**Tools**: SteamCMD, Steamworks SDK

**Depot Structure**:
- Depot 1: Windows x64 binaries
- Depot 2: macOS Universal binaries
- Depot 3: Linux x64 binaries
- Depot 4: Shared content (data files, StreamingAssets)

**Upload Checklist** (every build):
1. [ ] Build passes all automated tests
2. [ ] Version number incremented in Unity project settings
3. [ ] Build notes documented (changelog.txt)
4. [ ] Windows build smoke-tested on clean VM (critical: test on machine WITHOUT Unity installed)
5. [ ] macOS build smoke-tested (if applicable)
6. [ ] Linux build smoke-tested (if applicable)
7. [ ] Save file compatibility tested (new build loads old saves)
8. [ ] SteamCMD upload script executed
9. [ ] Steam depot build marked as default for target branch (beta/EA/default)
10. [ ] Steam community announcement posted (if public build)
11. [ ] Discord announcement posted
12. [ ] Rollback procedure confirmed available (previous build retained on Steam)

**Steam Branch Strategy**:
- `internal-beta`: Daily builds. Developer access only.
- `playtest`: Weekly builds. Closed playtest group access.
- `early-access`: Early Access public build.
- `default`: 1.0 public release build.

**CRITICAL**: Every Steam upload MUST be smoke-tested on a clean machine (VM without Unity, without dev tools, no prior install). This is non-negotiable. "It works on my dev machine" is how you get 1-star reviews.

### 3.3 Build Versioning

**Format**: `MAJOR.MINOR.PATCH-LABEL`

Examples:
- `0.1.0-prototype`: Vertical slice prototype
- `0.3.0-dev`: Core systems development build
- `0.9.0-playtest`: Mid-game content playtest build
- `1.0.0-ea`: Early Access launch build
- `1.2.3-ea`: Early Access patch build
- `2.0.0`: 1.0 full release build
- `2.1.0`: Post-launch content update

**Versioning Rules**:
- MAJOR: Increments for EA launch (1.x.x) and 1.0 launch (2.x.x)
- MINOR: Increments for content updates (new tiers, new systems)
- PATCH: Increments for bug fixes and balance patches
- LABEL: `prototype`, `dev`, `playtest`, `ea`, or omitted for 1.0

**Where Version Appears**:
- Unity Project Settings (displayed in main menu)
- Steam build description
- Save file header (for migration logic)
- Analytics logs (for telemetry tracking)

### 3.4 Testing Procedure (Pre-Upload)

**Automated Tests** (run on every build):
- Unit tests for JokeQualityCalculator (50+ test cases covering edge cases)
- Unit tests for ReactionCalculationJob (validate formula accuracy)
- Integration test: Full performance loop (build joke, perform, verify REP/cash awarded)
- Integration test: Save/Load cycle (create save, load save, verify state)
- Performance test: 100-joke set with 500-person audience, must average < 16ms per frame

**Manual Tests** (run on RC builds):
- Clean machine install test (VM with no prior install, no Unity)
- Save file migration test (old save format loads correctly)
- Full playthrough smoke test (Tier 0 to Tier 2 in 1 hour, no crashes)
- Crowd Engine sanity test (perform same joke at 3 venues, reactions differ predictably)
- UI navigation test (keyboard-only, controller-only, mouse-only)
- Steam integration test (achievements unlock, cloud save syncs)

**Test Platforms** (minimum for PC launch):
- Windows 10 x64 (clean VM, min spec: GTX 1050, 8GB RAM, i5 processor)
- Windows 11 x64 (same spec)
- macOS Monterey (if macOS build shipping)
- Linux Ubuntu 22.04 (if Linux build shipping)

**Acceptance Criteria** (build cannot ship if any of these fail):
- Zero crash bugs in 2-hour playthrough
- Zero save corruption bugs
- Zero game-breaking progression blockers
- Framerate stable at 60 FPS on min-spec PC during performance sequences
- All Steam achievements unlock correctly
- Cloud save sync works correctly (tested with two machines)

---

## 4. Platform Configuration

### 4.1 Steamworks Configuration Checklist

**Store Page Configuration**:
- [ ] App name: "DEADPAN"
- [ ] Short description: 160 characters max, includes "X meets Y" hook
- [ ] Long description: Formatted with headers, bullet points, feature highlights
- [ ] About This Game section: 500-1000 words, covers core loop, unique mechanics, target audience
- [ ] System Requirements (Minimum and Recommended):
  - **Minimum**: Windows 10, GTX 1050 / Radeon RX 560, 8GB RAM, 2GB storage
  - **Recommended**: Windows 11, GTX 1660 / Radeon RX 5600, 16GB RAM, 2GB storage, SSD
- [ ] Languages supported: English (audio and interface)
- [ ] Store tags (20 tags max): Simulation, Tycoon, Comedy, Singleplayer, Management, Strategy, Indie, Character Customization, Choices Matter, Economy, Story Rich, Procedural Generation, Replayable, Atmospheric, Immersive Sim, Drama, Stylized, 2D, UI, Controller Support
- [ ] Categories: Single-player, Steam Achievements, Steam Cloud, Full Controller Support
- [ ] Age rating: ESRB: T (Teen), PEGI: 12, IARC: Teen (see Section 5)
- [ ] Content descriptors: Language, Mature Humor (based on Edge axis content)
- [ ] Pricing: $19.99 USD (Early Access), $24.99 USD (1.0)
- [ ] Regional pricing: Auto-convert from USD, manual review for major markets (EUR, GBP, JPY, AUD)

**Media Assets**:
- [ ] Header capsule image: 460x215 px
- [ ] Small capsule image: 231x87 px
- [ ] Main capsule image: 616x353 px
- [ ] Hero capsule image: 1920x622 px (appears on home page if featured)
- [ ] Library capsule: 600x900 px
- [ ] Library hero: 3840x1240 px
- [ ] Screenshots: Minimum 5, recommended 10. Format: 1920x1080 PNG. Show: Bit Builder, Crowd reactions, Laugh Graph, career screen, venue variety.
- [ ] Trailer: 60-90 seconds. Format: 1920x1080 MP4, H.264. Hook in first 5 seconds. Show core loop. End with release date.

**Achievements**:
- [ ] Minimum 20 achievements implemented
- [ ] Achievement names and descriptions written
- [ ] Achievement icons created (64x64 px, locked and unlocked states)
- [ ] Achievement rarity balanced (20% common, 50% medium, 30% rare)

Example achievements:
- "Open Mic Legend" — Perform 10 sets at open mics
- "Crowd Killer" — Achieve 0.85+ aggregate reaction score in a set
- "Callback Maestro" — Use 5 callbacks in a single set
- "Authentic Voice" — Reach 100 Authenticity
- "The Special" — Complete a Netflix/HBO special taping
- "Rivalry Resolved" — Improve relationship with a rival from -50 to +50

**Trading Cards**:
- [ ] Minimum 5 base cards (Steam requirement: 5-15)
- [ ] Card artwork created (unique art for each card)
- [ ] Badge levels designed (5 levels)
- [ ] Emoticons and profile backgrounds designed (optional but recommended)

Card themes:
- The Mic (iconic imagery)
- The Crowd (audience archetypes)
- The Brick Wall (comedy club aesthetic)
- The Napkin (setlist artifact)
- The Spotlight (performance moment)

**Steam Cloud Configuration**:
- [ ] Cloud save enabled
- [ ] Save file path configured: `Application.persistentDataPath/saves/`
- [ ] File size limit: 10MB per save (current save files < 1MB, plenty of headroom)
- [ ] Auto-upload on game exit
- [ ] Conflict resolution: Newest timestamp wins

**DLC/Season Pass Configuration** (post-1.0 consideration):
- [ ] DLC structure defined (component card packs, new cities)
- [ ] Pricing strategy defined ($4.99 per content pack)
- [ ] Release cadence defined (quarterly)

### 4.2 Nintendo Switch eShop Configuration Checklist

**eShop Listing** (configure via Nintendo Developer Portal):
- [ ] Game title: "DEADPAN"
- [ ] Software description: 500 characters max, covers core loop
- [ ] Key features: Bullet points (4-6), highlight unique mechanics
- [ ] Screenshots: Minimum 5, maximum 20. Format: 1280x720 PNG. Horizontal orientation.
- [ ] Video: 30-60 seconds. Format: MP4, H.264. Show core loop with controller input.
- [ ] Age rating: ESRB: T (Teen), PEGI: 12, IARC: Teen (must match PC rating)
- [ ] Content descriptors: Language, Mature Humor
- [ ] Pricing: $24.99 USD (launch price, matches PC 1.0 price)
- [ ] Regional pricing: Auto-convert, manual review for major markets
- [ ] Languages: English (interface and audio)
- [ ] Publisher name: [Studio Name]
- [ ] Developer name: [Studio Name]
- [ ] Release date: TBD (set after Lotcheck approval)

**Nintendo Lotcheck Submission**:
- [ ] Lotcheck submission form completed
- [ ] ROM submitted (must be final build, no placeholder content)
- [ ] Age rating certificate attached (ESRB/PEGI/IARC)
- [ ] User manual prepared (digital manual, PDF format)
- [ ] Legal text prepared (EULA, privacy policy)
- [ ] Third-party middleware list provided (Unity, FMOD, Steamworks.NET — note: Steamworks NOT used on Switch)
- [ ] Network features documented (none for DEADPAN)
- [ ] Save data size documented (< 10MB)
- [ ] Sleep/resume functionality tested (must resume within 3 seconds)
- [ ] Screenshots for Lotcheck review provided (all menus, all game states)

**Lotcheck Preparation** (technical requirements):
- [ ] No crashes in 72-hour soak test
- [ ] Framerate stable at 30 FPS minimum (60 FPS target)
- [ ] Sleep/resume works correctly (pause game, sleep console, resume, verify state)
- [ ] Home button functionality works (return to home, return to game, verify state)
- [ ] Controller support: Joy-Con (single and dual), Pro Controller
- [ ] No dev tools or debug strings in final build
- [ ] All text within safe area (overscan margins respected)
- [ ] Load times under 15 seconds for any screen transition
- [ ] Proper error messaging for save data issues (e.g., corrupted save shows user-friendly message)

**Lotcheck Rejection Risk Areas** (historical high-failure points):
- Sleep/resume edge cases (e.g., sleep during save operation)
- Controller disconnect handling (must not crash, must show reconnect prompt)
- Language/region settings edge cases (test with non-English system language)
- Save data corruption handling (must not brick console)
- Performance drops below 30 FPS (unacceptable, must fix before resubmission)

**Certification Timeline**:
- First submission to Lotcheck: 2-4 weeks for initial feedback
- Resubmission (if needed): 1-2 weeks for re-review
- Total time budget: 6-8 weeks from first submission to approval

---

## 5. Age Rating and Content Guidelines

### 5.1 Age Rating Strategy

**Target Rating**: ESRB: T (Teen), PEGI: 12, IARC: Teen

**Rationale**: The game's Edge axis allows for dark and provocative comedy content. Some component cards will include mature humor, references to adult themes, and potentially mild language. A Teen/12 rating gives creative freedom while maintaining broad accessibility.

**Rating Application Process**:

**IARC (International Age Rating Coalition)** — Primary method for digital distribution:
- [ ] IARC questionnaire completed via Nintendo Developer Portal (for Switch) or ESRB portal (for PC)
- [ ] Questionnaire answers:
  - Violence: None
  - Sexual content: Mild references (comedy context)
  - Language: Mild language (infrequent, non-sexual)
  - Controlled substances: References (comedy context, no promotion)
  - Gambling: None
  - Horror: None
  - User interaction: None (single-player only)
- [ ] IARC certificate received (usually within 24-48 hours)
- [ ] Certificate uploaded to Steam and Nintendo Developer Portal

**ESRB (Entertainment Software Rating Board)** — Required for physical Switch release (if applicable):
- [ ] ESRB application submitted (if physical release planned)
- [ ] Content video recorded (30-60 minutes of gameplay showing highest-maturity content)
- [ ] Content descriptor form completed
- [ ] Fee paid ($800 for digital-only, $4,000 for physical)
- [ ] Rating received (4-6 weeks)

**Content Descriptors Expected**:
- Language (for component cards with mild profanity)
- Mature Humor (for Edge axis content)
- Comic Mischief (for absurdist content)

### 5.2 Content Moderation Guidelines

**Component Card Content Rules** (enforced during content creation):

**Allowed**:
- Observational comedy (relationships, daily life, work)
- Absurdist humor (surreal scenarios, non-sequiturs)
- Dark humor (death, failure, existential dread — but not graphic)
- Political satire (but not real-world political figures or current events)
- Personal anecdotes (family, dating, embarrassment)
- Mild language (e.g., "damn," "hell," "ass")

**NOT Allowed** (T/12 rating limit):
- Strong language (F-word, C-word, R-word)
- Explicit sexual content or graphic descriptions
- Graphic violence or gore descriptions
- Hate speech or slurs (even in comedy context)
- Real-world political figures or events (legal/defamation risk)
- Promotion of illegal activity (drug use can be referenced, not promoted)

**Edge Axis Content Calibration**:
- Edge 0-3: Clean, family-friendly
- Edge 4-6: PG-13 equivalent, mild adult themes
- Edge 7-8: Teen-rated, dark humor, mature themes
- Edge 9-10: Pushes T/12 rating limit (careful review required)

**Content Review Process**:
- [ ] All component cards reviewed by lead designer
- [ ] All Edge 8+ cards reviewed by second designer
- [ ] All Edge 9-10 cards reviewed by external sensitivity reader (if budget allows)
- [ ] Any flagged cards revised or cut

**Cultural Sensitivity Considerations**:
- Avoid punching down (humor targets powerful, not vulnerable)
- Avoid stereotypes as punchlines
- Cultural references should be explanatory (not everyone gets every reference)
- Thematic tags help players avoid content they're uncomfortable with (future feature: content filter by theme)

### 5.3 Regional Compliance

**European Union (PEGI)**:
- PEGI 12 rating expected (same as Teen)
- GDPR compliance (if analytics collect any user data, even anonymized)
- Cookie consent if any web integration (Steam Workshop, if implemented)

**Germany (USK)**:
- PEGI rating generally accepted, but USK rating may be required for physical release
- Content restrictions: No glorification of violence (not applicable), no Nazi imagery (not applicable)

**Australia (ACB)**:
- M (Mature 15+) or MA15+ rating likely
- Australia has strict drug reference rules — review all substance-related component cards

**China (if considered)**:
- Extremely difficult market for comedy content (censorship unpredictable)
- Not recommended for initial release

**Japan (CERO)**:
- CERO B (12+) expected
- Localization required (future consideration, not launch)

---

## 6. Rollback and Hotfix Procedures

### 6.1 Rollback Procedure (Steam)

**When to Rollback**:
- Critical crash bug affecting > 10% of players
- Save corruption bug
- Game-breaking progression blocker
- Unintended exploit causing economy collapse
- Performance regression causing unplayable framerate

**Rollback Procedure** (execute within 2 hours of issue discovery):

1. [ ] **Incident Confirmation**: Team lead confirms rollback is necessary (not a minor bug)
2. [ ] **Steam Branch Rollback**:
   - Log into Steamworks Partner Portal
   - Navigate to Builds tab
   - Set previous stable build as default for public branch
   - Verify branch change propagated (check via SteamDB)
3. [ ] **Community Communication** (within 30 minutes of rollback):
   - Steam community announcement: "We've temporarily rolled back to the previous build due to [issue]. We're working on a fix and will re-release within [timeframe]."
   - Discord announcement (same message)
   - Twitter/social media post (same message)
4. [ ] **Root Cause Analysis**: Identify what caused the issue (code review, bug repro)
5. [ ] **Fix Implementation**: Patch the issue
6. [ ] **Testing**: Test fix on clean machine, verify save compatibility
7. [ ] **Re-Release**: Upload fixed build, set as default
8. [ ] **Post-Mortem**: Document what went wrong, update QA checklist to prevent recurrence

**Rollback Test** (pre-launch):
- [ ] Simulate rollback on internal-beta branch
- [ ] Verify players can load saves from rolled-back build
- [ ] Time the procedure (target: 2 hours from decision to rollback live)

### 6.2 Hotfix Pipeline

**Hotfix Criteria** (issues requiring immediate patch, not rollback):
- Non-critical crash affecting < 10% of players
- Balance issues (Crowd Engine over/under-tuned)
- Minor progression blockers (workaround exists)
- UI bugs (visual glitches, text errors)
- Achievement unlock issues

**Hotfix Procedure** (target: 24-48 hours from issue discovery to patch live):

1. [ ] **Issue Triage**: Confirm severity (hotfix vs. next regular patch)
2. [ ] **Branch Creation**: Create `hotfix/issue-description` branch from `main` or `early-access`
3. [ ] **Fix Implementation**: Minimal code change (hotfixes are surgical, not sweeping)
4. [ ] **Testing**: Test fix in isolation, test save compatibility, smoke test full loop
5. [ ] **Version Increment**: Increment PATCH version (e.g., 1.0.0-ea -> 1.0.1-ea)
6. [ ] **Build Upload**: Upload to Steam internal-beta branch
7. [ ] **Internal Verification**: Team tests hotfix build
8. [ ] **Promote to Public**: Set as default branch
9. [ ] **Community Communication**: Patch notes posted (Steam, Discord)
10. [ ] **Merge to Main**: Hotfix branch merged to main/early-access, then to develop

**Hotfix Communication Template**:

```
Patch 1.0.1-ea — Hotfix

Fixed:
- [Specific bug description]
- [Specific bug description]

Known Issues:
- [Any issues not addressed in this hotfix]

We're continuing to monitor [specific system] and will provide updates as needed.
```

**Hotfix Test** (pre-launch):
- [ ] Execute full hotfix procedure on internal-beta branch (practice run)
- [ ] Time the procedure (target: 24 hours from fix start to patch live)

### 6.3 Emergency Contacts and On-Call Rotation

**Launch Week On-Call Rotation** (Early Access launch, 1.0 launch, Switch launch):

| Role | Responsibility | Hours |
|------|----------------|-------|
| **Lead Programmer** | Critical bugs, crashes, technical issues | 24/7 first 72 hours, then 9AM-9PM week 1 |
| **Gameplay Programmer** | Crowd Engine issues, balance bugs | 9AM-9PM week 1 |
| **Community Manager** | Player communication, issue triage | 24/7 first 72 hours, then 9AM-9PM week 1 |
| **Release Manager (SHIP)** | Rollback decisions, hotfix coordination | 24/7 first 72 hours, then on-call week 1 |

**Communication Protocol**:
- **Player reports bug** -> Community Manager triages -> Logs in bug tracker
- **Critical bug confirmed** -> Community Manager pings on-call programmer + Release Manager
- **Team decides**: Rollback, hotfix, or defer to next patch
- **Community Manager posts update** within 2 hours of discovery

**Emergency Contact List**:
- [ ] All team leads have each other's phone numbers
- [ ] Discord emergency channel set up (phone notifications enabled)
- [ ] Steam partner support contact saved (for platform-level issues)

---

## 7. Launch Day Timeline

### 7.1 Early Access Launch Day (Target: 10AM PST / 1PM EST)

**T-7 Days**:
- [ ] Final EA build uploaded to Steam (default branch set to `early-access-launch`)
- [ ] Press embargo reminder sent to all review outlets
- [ ] Social media launch content scheduled (trailer, GIFs, screenshots)
- [ ] Discord announcement: "EA launches in 7 days"

**T-3 Days**:
- [ ] Launch discount configured in Steamworks (10% off, week 1 only)
- [ ] Steam announcement post scheduled ("Launching in 3 days")
- [ ] Team briefed on launch day protocol

**T-1 Day**:
- [ ] Final smoke test on public EA build (3 team members play for 2 hours each)
- [ ] On-call rotation confirmed
- [ ] Emergency contact list verified
- [ ] Launch day monitoring dashboard set up (Steam stats, Discord activity, social media mentions)

**T-0 (Launch Day) — Hour-by-Hour**:

**12:00 AM (midnight PST, T-10 hours)**:
- [ ] Team lead confirms: all systems green for launch

**8:00 AM (T-2 hours)**:
- [ ] Team online and in Discord war room channel
- [ ] Final build verification (download EA build from Steam, confirm it's correct version)
- [ ] Steam page final check (pricing, description, media all correct)

**9:00 AM (T-1 hour)**:
- [ ] Press embargo lifts (reviews go live)
- [ ] Monitor initial review scores (Metacritic, OpenCritic)
- [ ] Respond to any critical review issues (if reviewer hit a bug, verify if widespread)

**10:00 AM (LAUNCH)**:
- [ ] EA build goes live (default branch is public)
- [ ] Launch discount activates
- [ ] Launch trailer posted to YouTube, Twitter, Discord, Steam community
- [ ] "DEADPAN is now in Early Access" announcement post on Steam
- [ ] Discord announcement with launch trailer link
- [ ] Reddit post on r/tycoon, r/simulation, r/IndieGaming, r/pcgaming
- [ ] Press release sent to gaming press

**10:00 AM - 12:00 PM (First 2 Hours)**:
- [ ] Monitor Steam forums for bug reports
- [ ] Monitor Discord for player feedback
- [ ] Monitor Steam concurrent player count (target: 100+ in first hour)
- [ ] Monitor crash analytics (zero tolerance for crashes)
- [ ] Community Manager responding to player questions in real-time

**12:00 PM - 6:00 PM (Hours 2-8)**:
- [ ] Continue monitoring forums and Discord
- [ ] Triage any reported bugs (critical vs. minor)
- [ ] If critical bug found: initiate hotfix procedure
- [ ] Community Manager posts "First Hours Post-Mortem" update (thank players, acknowledge any issues, ETA on fixes)

**6:00 PM - 11:59 PM (Hours 8-14)**:
- [ ] Reduced monitoring (lead programmer on-call, community manager checking in every 2 hours)
- [ ] If major issues found: emergency team call
- [ ] End-of-day summary posted to Discord (concurrent players, sales estimate, bug status)

**T+1 Day**:
- [ ] Post-launch Day 1 debrief meeting (what went well, what went wrong)
- [ ] Patch planning (collect all reported bugs, prioritize for Day 3 patch)
- [ ] Community Manager posts "Day 1 Wrap-Up" update

**T+3 Days**:
- [ ] First patch deployed (bug fixes from first 72 hours)
- [ ] Patch notes posted

**T+7 Days**:
- [ ] Launch week retrospective (sales, reviews, player retention)
- [ ] Roadmap update (next content drop ETA)

### 7.2 1.0 Launch Day (Same structure as EA Launch, adjusted timeline)

**Differences from EA Launch**:
- Press embargo 1 week before launch (longer lead time for reviews)
- Launch discount: 10% off week 1, 20% off if player owns EA version (loyalty discount)
- Larger marketing push (more press outlets, paid ads if budget allows)
- "Leaving Early Access" announcement campaign (highlight what's new since EA)

### 7.3 Switch Launch Day (Same structure, platform-specific adjustments)

**Differences from PC Launch**:
- eShop goes live at 9AM PST (Nintendo's standard eShop update time)
- No Early Access (full 1.0 launch only)
- eShop launch trailer optimized for Switch audience
- Cross-promotion with PC version (bundle discount if player owns both)

---

## 8. Post-Launch Monitoring Plan

### 8.1 Key Metrics to Track (First 30 Days)

**Sales and Player Metrics** (Steam Dashboard, SteamDB):
- Units sold (daily)
- Concurrent players (peak and average)
- Refund rate (target: < 10%, danger zone: > 15%)
- Playtime average (target: 4+ hours in first session)
- Wishlist conversion rate (target: 15-20%)

**Community Metrics** (Discord, Steam Forums, Reddit):
- Discord member count (growth rate)
- Forum post volume (high volume = high engagement OR high frustration, triage sentiment)
- Reddit mentions and sentiment (use search alerts)
- Social media mentions and sentiment

**Technical Metrics** (Analytics Pipeline, Crash Reporting):
- Crash rate (target: < 0.1% of sessions)
- Save corruption rate (target: 0%, zero tolerance)
- Average session length (target: 45-90 minutes)
- Drop-off points (where do players quit? Tier 1? Tier 3? Indicates balance issue)
- Bit Builder usage patterns (which components are most/least used? Indicates balance issue)
- Crowd Engine balance (average reaction scores by venue tier — looking for outliers)

**Review Metrics** (Steam, Metacritic, OpenCritic):
- Steam review score (target: 80%+ positive)
- Metacritic score (target: 75+, if enough outlets review)
- Common positive mentions (what do players love?)
- Common negative mentions (what do players hate? Fix in next patch)

### 8.2 Monitoring Tools and Dashboard

**Steam Stats Dashboard**:
- Steamworks Partner Portal (sales, concurrent players, refunds)
- SteamDB (public stats, concurrent player graphs)

**Analytics Dashboard** (internal tool, see Technical Architecture doc Section 8.2):
- Web-based dashboard (Flask + Chart.js)
- Reads telemetry JSON logs from player builds
- Visualizes:
  - Component card usage (which cards are popular/ignored?)
  - Joke quality distribution (are players finding high-quality combinations?)
  - Crowd reaction distributions by venue (is any venue over/under-tuned?)
  - Laugh Graph patterns (where do sets typically peak/valley?)
  - Drop-off heatmap (at what career tier do players stop playing?)

**Crash Reporting**:
- Unity Cloud Diagnostics (or Sentry.io if budget allows)
- Automatic crash log upload
- Crash dashboard shows: frequency, platform, stack trace

**Community Monitoring**:
- Discord (manual monitoring by Community Manager)
- Steam Forums (manual monitoring, RSS feed alerts)
- Reddit (Google Alerts for "DEADPAN game", r/tycoon mentions)
- Twitter (TweetDeck column for "@gamename" and "DEADPAN game")

### 8.3 When to Act: Decision Triggers

**Immediate Action Required** (within 2 hours):
- Crash rate > 1% of sessions
- Save corruption reports (any number > 0)
- Refund rate > 20% in first 24 hours
- Steam review score drops below 60% positive
- Game-breaking progression blocker confirmed

**Action: Rollback or emergency hotfix**

**High Priority Action** (within 24 hours):
- Refund rate 10-20%
- Steam review score 60-79% positive
- Common negative review theme identified (e.g., "Crowd Engine feels random")
- Drop-off spike at specific tier (indicates balance issue)

**Action: Prioritize fix for next patch, post community update acknowledging issue**

**Medium Priority Action** (within 1 week):
- Refund rate < 10% but higher than expected
- Playtime average below target (< 2 hours first session)
- Specific component cards unused (indicates poor design or poor discoverability)
- Specific venue over/under-performing (Crowd Engine balance)

**Action: Include in next regular patch cycle**

**Low Priority / Monitoring** (track but no immediate action):
- Feature requests (log for future content updates)
- Minor UI complaints (quality-of-life improvements for future)
- Balance suggestions (collect data, validate with telemetry before acting)

### 8.4 Patch Cadence (Post-Launch)

**Early Access Period (Months 15-18)**:
- **Hotfixes**: As needed (critical bugs only)
- **Bug Fix Patches**: Weekly for first month, then bi-weekly
- **Content Updates**: Monthly (new component card packs, balance passes)
- **Major Updates**: Every 2-3 months (new tiers, new systems)

**Post-1.0 (Months 18+)**:
- **Hotfixes**: As needed (critical bugs only)
- **Bug Fix Patches**: Bi-weekly for first 2 months, then monthly
- **Content Updates**: Quarterly (DLC packs if successful)
- **Major Updates**: Annually (expansion-level content if wildly successful)

---

## 9. Marketing and Community Strategy (Release-Focused)

### 9.1 Pre-Launch Marketing Timeline

**Month -6 (Pre-EA)**:
- [ ] Steam page live (Coming Soon)
- [ ] First trailer released (15-second teaser)
- [ ] Wishlist campaign begins
- [ ] Press outreach begins (pitch to indie game sites, simulation game press)
- [ ] Reddit presence established (post dev blogs on r/tycoon, r/IndieGaming, r/gamedev)

**Month -3**:
- [ ] Full trailer released (60-90 seconds)
- [ ] Press preview builds sent to select outlets
- [ ] Discord server opened to public
- [ ] Weekly dev blog series begins (focused on core systems: Bit Builder, Crowd Engine, Voice Identity)

**Month -1**:
- [ ] EA launch date announced
- [ ] Press embargo date set (EA launch day)
- [ ] Final pre-launch trailer (focused on "EA launches [date]")
- [ ] Streamer outreach (send keys to comedy fans, tycoon game streamers)

**Week -1**:
- [ ] Daily countdown posts on social media
- [ ] "What is DEADPAN?" explainer thread on Twitter/Reddit
- [ ] Discord hype event (Q&A with dev team)

### 9.2 Launch Marketing

**EA Launch Day**:
- [ ] Launch trailer posted to YouTube, Twitter, Steam, Discord
- [ ] Press release sent to gaming press (IGN, PC Gamer, Polygon, Kotaku, RPS, Eurogamer)
- [ ] Reddit launch thread on r/tycoon, r/simulation, r/IndieGaming, r/pcgaming
- [ ] Discord launch announcement
- [ ] Steam community announcement

**Week 1**:
- [ ] Daily social media posts (GIFs of player-created jokes, Laugh Graph moments, funny reactions)
- [ ] Community spotlight (retweet/share player stories from Discord/Steam forums)
- [ ] Streamer key distribution (50-100 keys to comedy podcasters, tycoon game streamers)

**Month 1-3 (EA Period)**:
- [ ] Monthly dev blog (roadmap updates, behind-the-scenes)
- [ ] Community content showcases (best player-created setlists, funniest jokes)
- [ ] Patch highlight posts (every patch gets a "what's new" post)

### 9.3 The GIF Strategy

The core loop is inherently shareable. Every joke performance is a 10-second GIF waiting to happen.

**Shareable Moments**:
- Bit Builder: Dragging joke components onto a napkin (satisfying, tactile)
- Crowd Reaction: Watching the Laugh Meter spike from silence to eruption
- Laugh Graph: A wild waveform showing a set that bombed, recovered, killed
- Heckler Duel: A perfectly-timed comeback shutting down a heckler
- The Special: The climactic moment of a 60-minute set landing perfectly

**GIF Production Plan**:
- [ ] Create 20-30 pre-launch GIFs showcasing core loop moments
- [ ] Build in-game GIF export tool (press F9 to capture last 10 seconds as GIF, auto-save to desktop)
- [ ] Encourage players to share GIFs (Discord channel dedicated to "best moments")
- [ ] Retweet/share player GIFs on official social media

**Comedian Influencer Strategy** (high-risk, high-reward):
- [ ] Identify 5-10 working comedians with active social media presence (Marc Maron, Tig Notaro, Mike Birbiglia, Taylor Tomlinson, etc.)
- [ ] Send personalized press copies with note: "This game gets it. Would love your thoughts."
- [ ] If ANY comedian tweets "this game understands comedy," the conversion rate will spike

**Risk**: Comedians may ignore the game, or worse, criticize it publicly. Mitigation: Only approach after EA launch when we have positive reviews to point to.

---

## 10. Known Risks and Contingency Plans

### Risk 1: Crowd Engine Feels Random to Players (Severity: CRITICAL)

**Indicators**:
- Common negative review: "I don't understand why jokes bomb"
- High refund rate (> 15%)
- Low average playtime (< 2 hours)
- Telemetry shows players not iterating on jokes (they try once, give up)

**Contingency Plan**:
- Emergency Crowd Engine balance patch (increase legibility of Laugh Graph feedback)
- Add "Prediction Mode" to Bit Builder (show expected reaction before performing)
- Add tutorial pop-ups explaining crowd composition and preferences
- Community Manager posts "How to Read the Crowd" guide
- Consider short-term rollback to previous Crowd Engine tuning if change is too aggressive

**Prevention**:
- Extensive playtesting with non-gamers during development
- Clarity-focused UI design (Laugh Graph per-segment breakdown must be crystal clear)
- Pre-launch tutorial polish pass

### Risk 2: Component Card Content Misjudges Audience (Severity: HIGH)

**Indicators**:
- Reviews mention "offensive content" or "not funny"
- Age rating issues (content exceeds T/12 rating)
- Negative press coverage (content controversy)

**Contingency Plan**:
- Emergency content patch (remove flagged component cards, replace with alternatives)
- Public apology if content crosses a line
- Content review policy published (transparency about what's allowed/not allowed)
- Future content goes through external sensitivity review

**Prevention**:
- Content guidelines enforced during development (see Section 5.2)
- External sensitivity reader for Edge 9-10 content
- Pre-launch content review by diverse team members

### Risk 3: Mid-Game Grind Kills Retention (Severity: MEDIUM-HIGH)

**Indicators**:
- Telemetry shows drop-off spike at Tier 3-4
- Reviews mention "gets repetitive"
- Average playtime plateaus at 5-10 hours (players don't reach late-game)

**Contingency Plan**:
- Balance patch: Reduce REP requirements for Tier 4-5 unlock (faster progression)
- Content patch: Add mid-game scene events (more rival drama, more collaboration opportunities)
- Callback system tutorial (many players may not understand callbacks, mid-game is when they unlock value)
- Community Manager posts "Getting Past the Grind" guide

**Prevention**:
- Playtest mid-game extensively (20-person, 8-hour session target)
- Scene events spike in frequency at Tier 3-4 (per GDD Section 7 Risk Assessment)

### Risk 4: Technical Issues at Launch (Severity: MEDIUM)

**Indicators**:
- Crash rate > 1%
- Performance issues on min-spec PC
- Save corruption reports
- Steam integration broken (achievements not unlocking, cloud save not syncing)

**Contingency Plan**:
- Rollback procedure (see Section 6.1)
- Hotfix procedure (see Section 6.2)
- Public acknowledgment and ETA for fix
- Refund policy flexibility (offer refunds proactively if game is unplayable)

**Prevention**:
- Automated testing pipeline (see Section 3.1)
- Clean machine testing (see Section 3.2)
- Performance profiling on min-spec hardware
- Steam integration testing before every RC build

### Risk 5: Poor Launch Sales (Severity: MEDIUM)

**Indicators**:
- < 500 units sold in first week
- Wishlist conversion < 5%
- Low concurrent player count (< 50 in first week)

**Contingency Plan**:
- Post-launch marketing push (increase ad spend if budget allows)
- Price promotion (deeper discount, extend launch week discount to month 1)
- Press outreach intensifies (send keys to more outlets, including comedy press)
- Community content campaign (highlight player stories, GIFs, success stories)
- Evaluate if game is reaching target audience (are tycoon players finding it? are comedy fans finding it?)

**Prevention**:
- Wishlist campaign starts 6+ months before launch (target: 5K wishlists at EA launch)
- Press outreach to both gaming press AND comedy press
- GIF strategy (shareable content drives discovery)
- Streamer key distribution

### Risk 6: Switch Certification Fails (Severity: LOW-MEDIUM)

**Indicators**:
- Lotcheck rejection on first submission
- Performance issues on Switch hardware
- Sleep/resume bugs

**Contingency Plan**:
- Address Lotcheck feedback and resubmit (budget 2-4 weeks for fixes)
- Delay Switch launch if needed (PC launch unaffected)
- Transparent communication with Switch wishlist audience ("Switch version delayed to ensure quality")

**Prevention**:
- Extensive testing on real Switch hardware (not just Unity Editor)
- Lotcheck preparation checklist (see Section 4.2)
- Performance profiling on Switch (30 FPS minimum validated before submission)

---

## 11. Success Metrics and Launch Goals

### Early Access Launch Goals (Month 15)

**Sales Targets**:
- **Minimum Viable**: 1,000 units sold in first month (covers development cost of EA period)
- **Target**: 3,000 units sold in first month (indicates strong product-market fit)
- **Stretch**: 5,000+ units sold in first month (potential breakout hit)

**Community Targets**:
- **Wishlist Conversion**: 15-20% (industry average for indie sim games)
- **Steam Review Score**: 80%+ positive (Very Positive rating)
- **Refund Rate**: < 10% (industry average is 5-15%, aim for low end)
- **Discord Growth**: 500+ members in first month
- **Average Playtime**: 4+ hours in first session (indicates strong engagement)

**Technical Targets**:
- **Crash Rate**: < 0.1% of sessions
- **Save Corruption**: 0 reports
- **Performance**: 60 FPS stable on min-spec PC (validated by player telemetry)

### 1.0 Launch Goals (Month 18)

**Sales Targets**:
- **Minimum Viable**: 5,000 units sold in first month (post-EA launch)
- **Target**: 10,000 units sold in first month
- **Stretch**: 20,000+ units sold in first month

**Community Targets**:
- **Steam Review Score**: 85%+ positive (Overwhelmingly Positive rating)
- **Refund Rate**: < 8%
- **Discord Growth**: 2,000+ members total
- **Press Coverage**: 10+ major outlet reviews (IGN, PC Gamer, Polygon, etc.)

**Recognition Targets**:
- Steam "Featured" tag (editorial featuring)
- Steam "Top Seller" (even briefly)
- Positive mentions from working comedians (1+ comedian tweet = success)

### Switch Launch Goals (Month 24)

**Sales Targets**:
- **Minimum Viable**: 2,000 units sold in first month
- **Target**: 5,000 units sold in first month
- **Stretch**: 10,000+ units sold in first month

**Community Targets**:
- eShop user rating: 4.5/5 stars
- Cross-platform bundle sales (PC + Switch discount)

---

## 12. Final Pre-Launch Checklist (The Big One)

This is the master checklist. Every item must be checked before launch. If any item is unchecked, launch does not happen.

### Build Readiness
- [ ] Final build passes all automated tests
- [ ] Final build smoke-tested on clean VM (Windows 10, Windows 11)
- [ ] Final build tested on min-spec hardware (GTX 1050, 8GB RAM)
- [ ] Save file migration tested (old saves load correctly in new build)
- [ ] No critical bugs (zero crashes, zero save corruption, zero progression blockers)
- [ ] Performance validated (60 FPS stable on min-spec)
- [ ] Version number correct (matches marketing materials)

### Steam Configuration
- [ ] Steam app ID correct
- [ ] Store page complete (name, description, media, tags, categories, pricing)
- [ ] Age rating displayed correctly (ESRB: T, PEGI: 12)
- [ ] System requirements accurate
- [ ] Screenshots (minimum 5) uploaded
- [ ] Trailer uploaded
- [ ] Achievements configured (minimum 20)
- [ ] Trading cards configured (minimum 5)
- [ ] Cloud save enabled and tested
- [ ] Launch discount configured (10% off, week 1)
- [ ] Depot configuration correct (Windows, macOS, Linux)
- [ ] Build uploaded to default branch
- [ ] Build tested via Steam download (not local build)

### Marketing and Community
- [ ] Press embargo date set and communicated
- [ ] Press review copies sent (minimum 2 weeks before launch)
- [ ] Launch trailer finalized
- [ ] Social media content scheduled (launch day posts)
- [ ] Discord server ready (announcement channel, bug report channel, feedback channel)
- [ ] Reddit launch posts prepared
- [ ] Steam community announcement prepared
- [ ] Launch day timeline finalized (hour-by-hour plan)

### Team Readiness
- [ ] On-call rotation confirmed (first 72 hours)
- [ ] Emergency contact list verified
- [ ] Rollback procedure tested
- [ ] Hotfix procedure tested
- [ ] Monitoring dashboard set up
- [ ] Team briefed on launch day protocol

### Legal and Compliance
- [ ] Age rating certificate received (IARC)
- [ ] Age rating displayed on store page
- [ ] EULA prepared and displayed
- [ ] Privacy policy prepared (if analytics collect data)
- [ ] Third-party licenses documented (Unity, FMOD, middleware)

### Post-Launch Readiness
- [ ] First patch planned (Day 3-7, addresses first-week bugs)
- [ ] Community feedback tracking system ready (bug tracker, feature request board)
- [ ] Analytics dashboard operational
- [ ] Crash reporting configured

---

## 13. Post-Launch Content Roadmap (High-Level)

### Early Access Period (Months 15-18)

**Month 15** (EA Launch):
- Launch build: Tier 1-4 polished, Tier 5-6 feature-complete
- Week 1: Monitoring and hotfixes only
- Week 2-4: First patch (bug fixes from launch week)

**Month 16**:
- Content update: 50 new component cards (Brooklyn Pack — NYC-themed content)
- Balance patch: Crowd Engine tuning based on telemetry
- Quality-of-life: Setlist templates, material filtering improvements

**Month 17**:
- Content update: 50 new component cards (Dark Material Pack — high-Edge content)
- Feature addition: Heckler Duels (if scope allows)
- Tier 5-6 content expansion (more venues, more AI comedians)

**Month 18**:
- Final EA content update: Tier 5-6 polished, 400+ component cards total
- 1.0 launch announcement (date reveal, roadmap preview)
- Press preview build sent (1.0 embargo 1 week before launch)

### Post-1.0 (Months 18-24)

**Month 18** (1.0 Launch):
- Launch build: Full content, final balance
- Week 1-4: Monitoring, bug fixes, stability patches

**Month 19-21**:
- Quality-of-life updates (accessibility features, mod support)
- Seasonal content (holiday-themed component cards, optional)
- Switch port development begins

**Month 22-24**:
- Switch port certification and launch
- DLC planning (if sales support it): New Cities expansion, Writers' Room Mode

### Long-Term (Year 2+)

**If Successful** (> 50K units sold):
- Major expansion: New Cities (Austin, LA, Chicago each with unique venues/archetypes)
- New game mode: Writers' Room (TV writing career path)
- Multiplayer: Async comedy battles (build set, upload, compete on leaderboards)

**If Wildly Successful** (> 100K units sold):
- Sequel consideration: DEADPAN 2 with expanded systems, multiplayer focus
- Documentary Mode: Post-Special unlock showing career stats, Voice Identity evolution
- Physical release (limited run, specialty retailers)

---

## 14. Lessons from Past Launches (What Not to Do)

This section documents launch day failures from other projects. We learn from their mistakes.

### Case Study 1: "Cyberpunk 2077" — Performance Catastrophe

**What Happened**: Shipped with game-breaking performance issues on last-gen consoles. Refund rate spiked. PlayStation Store pulled the game. Reputation permanently damaged.

**Lesson**: Performance on min-spec hardware is non-negotiable. Test on real hardware, not just dev machines. If it doesn't run at acceptable framerate on min-spec, delay launch.

**DEADPAN Application**: All builds smoke-tested on min-spec PC (GTX 1050, 8GB RAM). Switch build tested on real hardware, not Unity Editor. 30 FPS minimum validated before certification submission.

### Case Study 2: "No Man's Sky" — Overpromised, Underdelivered

**What Happened**: Marketing promised features not in launch build. Review backlash. Years of free updates to rebuild trust.

**Lesson**: Market what's in the build, not what's planned. Early Access roadmap is a promise — deliver on it or communicate delays transparently.

**DEADPAN Application**: EA launch marketing explicitly states "Tier 1-4 polished, Tier 5-6 in development." Roadmap is conservative (under-promise, over-deliver). If feature slips, announce delay immediately.

### Case Study 3: "SimCity (2013)" — Always-Online Disaster

**What Happened**: Required always-online connection for single-player game. Servers crashed on launch day. Game unplayable for days. Refund requests flooded.

**Lesson**: Single-player games should not require online connectivity. Server dependency is a launch risk.

**DEADPAN Application**: Fully offline single-player. No server dependency. No launch day server risk. Cloud save is optional, not required.

### Case Study 4: "Anthem" — Content Starvation

**What Happened**: Shipped with strong core loop but insufficient endgame content. Players consumed all content in 20 hours, quit. Live service roadmap delayed. Game died.

**Lesson**: Tycoon/sim games live or die on content depth. Vertical slice must prove 20+ hour engagement, not just 2 hours.

**DEADPAN Application**: 400+ component cards at 1.0 launch. Callback system creates combinatorial depth. Cultural Moments generate dynamic content. Telemetry monitors content consumption rate. If players exhaust content faster than expected, accelerate DLC pipeline.

### Case Study 5: "Valve's Artifact" — Ignored Community Feedback

**What Happened**: Launched with monetization model community hated. Devs ignored feedback. Player count collapsed in weeks. Game went F2P, then died.

**Lesson**: Community feedback during EA is not optional noise — it's the product signal. Listen, acknowledge, act.

**DEADPAN Application**: Community Manager is first-class team member, not afterthought. Discord feedback is reviewed weekly. Monthly dev blogs show "we heard you, here's what we're changing." Telemetry validates subjective feedback (if players say "Tier 3 is too grindy" and telemetry shows drop-off spike at Tier 3, they're right).

---

## 15. Contact and Ownership

**Document Owner**: SHIP (Release Manager)

**Key Stakeholders**:
- **BYTE** (Lead Programmer): Build pipeline, technical readiness
- **REED** (Game Designer): Content completeness, balance validation
- **CLOCK** (Producer): Timeline enforcement, scope control
- **HYPE** (Marketing): Marketing and community strategy
- **CRASH** (QA Lead): Testing and quality validation

**Document Review Cadence**:
- **Monthly** during development (Months 1-14)
- **Weekly** during EA prep (Month 15)
- **Daily** during launch week
- **Quarterly** post-launch (Months 18+)

**Next Review Date**: Vertical Slice Playtest (Month 3) — validate Early Access timeline is achievable

---

## 16. Closing Notes from SHIP

This plan accounts for every scenario I've seen go wrong. Server crashes (not applicable — we're offline). Store page errors (checklist enforced). Review embargo breaks early (press communication protocol). Crash bugs on launch day (rollback procedure ready). Performance issues (tested on min-spec hardware). Content controversy (age rating and content guidelines enforced).

The plan is boring. That's the point. Launch day should be boring. If we execute this checklist, the only surprises will be positive ones — higher sales than expected, better reviews than expected, a comedian tweeting about the game.

The biggest risk is the Crowd Engine feeling opaque to players. We mitigate with aggressive feedback (Laugh Graph, crowd composition previews, post-set analysis). If players can't learn from failure, the loop dies and the game dies. Clarity is survival.

The second biggest risk is mid-game grind killing retention. We mitigate with scene events (rival drama, collaboration opportunities) and callback system depth. Telemetry will tell us if it's working. If Tier 3 drop-off spikes, we act immediately.

The third biggest risk is content starvation. 400+ component cards at launch. Cultural Moments generate dynamic Premise cards. Callback system creates combinatorial explosion. We're building a content engine, not a content library.

Early Access is not a beta test — it's a partnership with the community. They're co-designers. Their telemetry tunes the Crowd Engine. Their feedback shapes Tier 5-6 content. Their GIFs market the game. Treat them with respect and transparency.

This is a blue ocean product. There is no proven playbook. We're writing it as we go. The plan is flexible — if telemetry shows a system isn't working, we pivot. But we pivot deliberately, not reactively. Data informs decisions. Gut feelings are validated with telemetry.

Is it on the checklist? If yes, it happens. If no, it doesn't. Launch day is not the time for creative risks or last-minute features. Launch day is execution.

Test the build on a clean machine. Every. Single. Time.

What's the rollback plan? It's documented in Section 6.1. We've tested it. We can execute it in 2 hours.

When's the last commit before gold? It's the feature-lock milestone (Month 15 for EA, Month 18 for 1.0). After feature-lock, bugs only.

Who owns this step? Every checklist item has an owner (programmer, designer, community manager, release manager). No ambiguity.

First impressions are permanent. Launch day defines the game's trajectory. We get one shot. Make it boring. Make it clean. Make it shippable.

---

**END DOCUMENT**

**Document Version**: 1.0
**Last Updated**: 2026-02-07
**Next Review**: Vertical Slice Playtest (Month 3)
**Status**: READY FOR IMPLEMENTATION
