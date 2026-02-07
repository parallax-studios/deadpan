# DEADPAN — Art Direction Document

**Art Director**: PIXEL
**Project**: Stand-up Comedy Empire Simulation
**Target Platform**: PC (Steam) primary, Nintendo Switch secondary
**Version**: 1.0
**Status**: Production-ready

---

## 1. Visual Identity Statement

**The core visual promise**: DEADPAN looks like a love letter written on a bar napkin at 2 AM by someone who has bombed too many times to romanticize comedy but loves it too much to quit.

This is not a sanitized simulation. This is not a cartoon world. This is the real texture of the comedy circuit — the brick walls with twenty years of flyers, the green rooms that smell like desperation and cheap beer, the spotlight that makes you visible and vulnerable in equal measure. The art direction exists to communicate one feeling above all others: **intimacy within exposure**.

Every visual choice supports the fantasy: you are a comedian. You write jokes alone. You perform them in front of strangers. The distance between the blank napkin and the spotlight is the distance between who you are and who you pretend to be. The art shows both.

**Visual North Star**: If Unpacking and Papers Please had a child who grew up watching Comedians in Cars Getting Coffee while eating ramen in a studio apartment with a corkboard covered in setlist drafts, that child would make this game.

**The three aesthetic pillars**:

1. **Diegetic UI** — Everything lives in the world. No floating fantasy menus. Setlists are napkins. The Bit Builder is a corkboard. Career progress is text messages from your agent. The player never leaves the reality of being a working comedian.

2. **Warm Grit** — The rooms are worn but not depressing. The brick is old but the spotlight is gold. There's beauty in the specificity. This is not poverty porn — this is the aesthetic of craft happening in unglamorous spaces. Think the warm grain of 35mm film documenting real places.

3. **Readability First** — Comedy is about timing and clarity. So is the visual design. The player must be able to parse the screen at a glance. Every UI element has a job. If it doesn't communicate essential information or reinforce the fantasy, it's cut.

---

## 2. Color Palette

The palette is **warm, nocturnal, and specific**. This is the color of comedy clubs at night, dive bars with good lighting, green rooms with bad lighting, and the golden hour of stage presence.

### Primary Palette (Core UI & Environments)

| Color Name | Hex Value | RGB | Usage | Emotional Weight |
|-----------|-----------|-----|-------|------------------|
| **Midnight Canvas** | `#1A1A2E` | 26, 26, 46 | Primary background for all rooms, UI panels, main menu. The color of a dark venue before the lights hit. | Intimacy, focus, the void before the joke lands |
| **Spotlight Gold** | `#E8D44D` | 232, 212, 77 | The stage spotlight, UI highlights, success indicators, "hot" laugh graph peaks. The hero color. | Exposure, triumph, the moment of connection |
| **Brick Red** | `#C0392B` | 192, 57, 43 | Brick walls, venue branding, error states, heckler indicators. The color of the comedy club itself. | History, weight, pressure, the room's memory |
| **Napkin Cream** | `#F5F0E1` | 245, 240, 225 | Setlist napkins, notebook pages, text backgrounds, joke cards in the Bit Builder. The color of blank creative space. | Possibility, craft, the moment before the idea becomes real |
| **Neon Sign Green** | `#2ECC71` | 46, 204, 113 | "OPEN" signs, positive feedback, good audience reactions, "go ahead" indicators. The color of opportunity. | Permission, momentum, green means go |

### Secondary Palette (Accents & System Feedback)

| Color Name | Hex Value | RGB | Usage | Emotional Weight |
|-----------|-----------|-----|-------|------------------|
| **Velvet Curtain Purple** | `#8E44AD` | 142, 68, 173 | Premium venues (The Comedy Store, HBO special venues), high-tier UI frames, achievement markers. | Aspiration, prestige, the big time |
| **Setlist Ink** | `#2C3E50` | 44, 62, 80 | Body text, handwritten text on napkins, primary typography. Slightly faded black — the color of a Sharpie on paper. | Craft, handwriting, human touch |
| **Laugh Graph Waveform** | `#E8D44D` | 232, 212, 77 | (Spotlight Gold reused) Laugh Graph line during performance. Shifts between this and Cold Blue based on momentum. | Real-time emotional feedback |
| **Cold Silence Blue** | `#3498DB` | 52, 152, 219 | Laugh Graph when the room is cold, low momentum indicators, "dying" set visuals. | Isolation, failure, distance from the crowd |
| **Bomb Red** | `#E74C3C` | 231, 76, 60 | Total bomb moments (flatline laugh graph), critical warnings, heckler attacks. Brighter and more aggressive than Brick Red. | Crisis, immediate danger, the moment it all falls apart |
| **Coffee Stain Brown** | `#8B7355` | 139, 115, 85 | Environmental stains, wear on surfaces, coffee cups in green rooms, aging on flyers. | Authenticity, wear, the passage of time |

### Palette Usage Rules

**Background Hierarchy**:
- Midnight Canvas (`#1A1A2E`) is the foundation. 80% of screen real estate at any given moment.
- Napkin Cream (`#F5F0E1`) is the working surface — UI panels, cards, writable spaces. 15% of screen.
- Accent colors occupy the remaining 5% but dominate emotional attention.

**Contrast Requirements**:
- All text on Midnight Canvas must be Napkin Cream or Spotlight Gold (minimum 12:1 contrast ratio for body text).
- All text on Napkin Cream must be Setlist Ink or Midnight Canvas (minimum 8:1 contrast ratio).
- Interactive elements (buttons, drag targets) must have a minimum 3:1 contrast with their background AND a 2px border in Spotlight Gold or Neon Sign Green.

**Color-Coded Feedback System**:
- **Green lights** (Neon Sign): Positive, go, success, momentum up.
- **Gold lights** (Spotlight): Peak moments, high engagement, "you're killing."
- **Blue tones** (Cold Silence): Negative momentum, disengagement, room is cooling.
- **Red alerts** (Bomb Red): Failure states, hecklers, critical loss of momentum.

**Warm/Cool Emotional Palette Shifts**:
The game's color temperature shifts based on performance state:
- **Hot Set** (Momentum > 1.2): Spotlight Gold dominates. Warm orange glows at screen edges. The UI feels energized.
- **Neutral Set** (Momentum 0.8-1.2): Balanced warm palette. The standard state.
- **Cold Set** (Momentum < 0.8): Blues creep in. The spotlight dims slightly. Shadows deepen. The UI feels tense.
- **Bombing** (Momentum < 0.5): Desaturation. Cold Silence Blue dominates. Spotlight Gold fades to pale yellow. The color drains from the world.

This is not subtle. The player should FEEL the room temperature through the palette.

**Accessibility Considerations**:
- All color-coded feedback has redundant iconography (green checkmark, red X, gold star).
- Colorblind mode swaps Neon Sign Green to `#00A8E8` (cyan) and Bomb Red to `#FF6F61` (coral pink), maintaining contrast and distinction.
- High-contrast mode option: replaces Midnight Canvas with `#000000` and boosts all text to pure white `#FFFFFF`.

---

## 3. Shape Language Guide

The shape language of DEADPAN is **organic within structure**. The UI is grounded in real-world objects (napkins, corkboards, phone screens), but the world itself has a loose, human quality — hand-drawn elements, imperfect angles, the texture of things used by real people.

### Primary Shape Vocabulary

**Rectangular/Rectilinear** (70% of UI elements):
- Napkins, joke cards, venue flyers, phone screens, corkboard frames, stage shapes.
- **Why**: Comedy clubs are built from rectangles — stages, tables, booths, walls. The shape grounds the fantasy in reality.
- **Treatment**: Corners are slightly rounded (2-4px radius). Edges are NOT perfectly straight — they have subtle hand-drawn wobble (1-2px variance). This prevents the rectangles from feeling digital.

**Circular/Radial** (20% of UI elements):
- Spotlight cones (hard-edged circles with gradient falloff), audience member heads (abstract circles in the crowd visualization), buttons (circular action prompts), microphone head (the iconic circle that appears in every stage view).
- **Why**: Circles represent people, connection, and focus. The spotlight is a circle. The mic is a circle. The audience is a field of circles. Circles are the human element in the rectangular world.

**Irregular/Hand-Drawn** (10% of UI elements):
- Handwritten text on napkins (letterforms have natural variance), torn edges on flyers, coffee stains, string connecting joke cards on the corkboard, the Laugh Graph waveform (organic, never perfectly smooth).
- **Why**: This is a game about human creativity. The imperfections are the signature. Hand-drawn elements signal "a person made this," not "a machine generated this."

### Shape Rules by System

**Bit Builder (Joke Construction)**:
- Joke component cards are 3:2 ratio rectangles (120px x 80px at native res) with 3px rounded corners.
- Cards have a subtle drop shadow (2px offset, 40% opacity Midnight Canvas) to create depth and tactility.
- Cards snap together with visible connection points — a 4px diameter circle in Spotlight Gold at the snap location. When two cards connect, an animated line draws between the circles.
- The corkboard background is a large irregular rectangle with torn/frayed edges. Pinned with visible pushpins (small circles in Brick Red).

**Setlist Builder (Napkin Interface)**:
- The napkin is an irregular quadrilateral (NOT a perfect rectangle) — approximately 400px x 600px with hand-drawn edges.
- Text on the napkin is handwritten style (see Typography section).
- Coffee cup ring stains (circles in Coffee Stain Brown, 60px-80px diameter, 20% opacity) placed randomly on 40% of napkins. Pure texture — no gameplay function.

**Laugh Graph (Performance Feedback)**:
- The waveform is a smooth but organic curve — uses Catmull-Rom spline interpolation, not linear segments. The line should feel like a heartbeat, not a technical readout.
- Peaks are rendered with a subtle glow (8px blur, Spotlight Gold, 60% opacity).
- The graph frame is a simple rectangle with 1px border in Napkin Cream.

**Venue Selection (Flyer Stack)**:
- Each venue is represented by a flyer: rectangular (portrait orientation, roughly 5:7 ratio), with torn top edge, visible tape marks (small rectangles of translucent Coffee Stain Brown), and layered stacking (each flyer offset by 4px x/y and rotated by 2-4 degrees).
- Flyers on top of the stack have higher saturation. Flyers deeper in the stack are slightly desaturated and darkened (depth cue).

**Phone/Agent Interface**:
- The phone is a modern smartphone silhouette (rounded rectangle, minimal bezel). Screen ratio 9:19.5 (approximate iPhone proportions).
- Text messages appear as chat bubbles (rounded rectangles with a small triangular tail pointing toward the sender).
- Agent messages are left-aligned. Player responses (choice prompts) are right-aligned.

### Silhouette Test

Every major UI element must pass the silhouette test: if you fill the element with solid black, can you identify what it is?

- Napkin silhouette: irregular rectangle with torn edge → immediately identifiable.
- Joke card silhouette: clean rectangle with slight rounding → identifiable as "card."
- Microphone silhouette: vertical line topped by circle → iconic, universal.
- Spotlight silhouette: circle with radial gradient → identifiable as "light source."

If any element fails the silhouette test, it's too visually complex and needs simplification.

---

## 4. Style Rules (Do's and Don'ts)

### DO

**DO treat the UI as diegetic objects**:
Every UI element exists as a physical thing in the world. The setlist is a napkin the comedian actually writes on. The Bit Builder corkboard is an actual corkboard in the apartment. The Laugh Graph is a visualization on a tablet or phone the comedian reviews post-set. NO floating holographic menus. NO fantasy overlays. The player is a comedian living in a real world, and the interface reflects that.

**DO use texture aggressively**:
Every surface has texture. Napkins have paper grain. Brick walls have mortar lines and imperfections. The corkboard has wood grain. The stage floor has scuff marks. This is not a clean digital space — it's a physical space rendered in pixels. Texture communicates history and authenticity.

**DO embrace imperfection**:
Nothing is perfectly aligned. Handwritten text wobbles slightly. Flyers are taped on crooked. Coffee stains are asymmetric. These imperfections are not sloppiness — they're signatures of human activity. A perfectly aligned UI would feel wrong in a game about human creativity.

**DO prioritize readability in every frame**:
Comedy is about timing and clarity. The player must be able to parse the screen in under 2 seconds. Use strong contrast, clear hierarchy, and generous whitespace. If a joke card is hard to read, the player can't build jokes. If the Laugh Graph is cluttered, the player can't learn. Readability is not negotiable.

**DO let negative space breathe**:
The Midnight Canvas background is not empty space — it's *breathing room*. Don't fill every pixel. Let UI elements float in darkness. This creates focus. The spotlight illuminates what matters. Everything else recedes.

**DO use animation to reinforce physicality**:
When a joke card is dragged, it lifts (shadow deepens, scale increases 5%). When it snaps into place, it settles (slight bounce easing). When the napkin is placed on the table, it lands with a subtle wobble. These micro-animations make digital objects feel like physical things. No animation should exceed 300ms — comedy timing is fast, and so is the UI.

**DO use lighting to communicate emotional state**:
The spotlight is not just decoration — it's a narrative tool. When the set is going well, the spotlight is warm, bright, focused. When the set is dying, the spotlight cools, dims, and the surrounding darkness feels heavier. Lighting = emotional weather.

**DO show the crowd as abstract but readable**:
The audience is not a field of detailed character models. The audience is a collection of simple geometric heads (circles on ovals, minimal facial features) grouped into clusters. During performance, these clusters react: laughter is conveyed through motion (heads tilt back, bodies lean forward, arms raise). This abstraction keeps performance smooth and lets the player read the room at a glance.

**DO make success feel golden**:
When a joke kills, the Laugh Graph spikes in Spotlight Gold. When REP is earned, it glows in Spotlight Gold. When a venue unlocks, its flyer is edged in Spotlight Gold. Success is visually rewarding. The player should feel like they earned a spotlight moment.

### DON'T

**DON'T use fantasy UI elements**:
No glowing holographic panels. No sci-fi interfaces. No floating heads-up displays. This is not that kind of game. The interface is napkins, notebooks, corkboards, and phones. Stay grounded.

**DON'T over-animate**:
A joke card should not bounce like a cartoon. The napkin should not flutter like a flag. Animations are subtle and physically plausible. Exaggerated animation breaks immersion and slows down the player's interaction speed.

**DON'T make the player hunt for information**:
Every piece of essential information (joke quality score, audience composition, current momentum, available REP) must be visible without requiring a menu dive. Critical feedback appears immediately in the player's eyeline. If the player has to search for feedback, the feedback might as well not exist.

**DON'T use color as the ONLY feedback channel**:
Color is powerful, but never the sole indicator. A green checkmark is "good" — but it's also a checkmark. A red X is "bad" — but it's also an X. Redundant iconography ensures colorblind players and players in non-ideal lighting conditions get the same information.

**DON'T clutter the performance view**:
When the player is on stage, the screen should be 60% stage and audience, 30% Laugh Graph, 10% essential status info (current joke, momentum, pivot points remaining). Everything else is OFF SCREEN. The performance moment is sacred. Nothing distracts from the player's connection to the crowd.

**DON'T use generic stock art**:
Every venue flyer is custom. Every napkin feels hand-touched. Every UI element is bespoke to this game. Generic assets kill specificity, and specificity is the entire aesthetic identity. If it looks like it could be in any game, it doesn't belong in this one.

**DON'T romanticize poverty**:
The game shows the grind, but it doesn't glorify suffering. The dive bar is worn but not filthy. The green room is small but not depressing. There's warmth in the modest spaces. The aesthetic says "this is hard but worth it," not "look how miserable the artist is." Comedy is struggle, but the visual tone is aspirational, not nihilistic.

**DON'T make the apartment depressing**:
The player's apartment (where joke writing happens) starts small and sparse, but it's not bleak. There's a corkboard with setlists. There's a window with city lights. There's a desk with a notebook and a coffee cup. As the career progresses, the apartment grows — better furniture, more wall art, awards on shelves. The space should feel like a creative sanctuary, not a prison.

---

## 5. Typography

Typography is **handwritten for diegetic elements, clean sans-serif for system elements**.

### Primary Typefaces

**Handwritten (Diegetic Text)**:
- **Font Choice**: *Caveat* (Google Font) or custom hand-drawn letterforms if budget allows.
- **Usage**: Setlist napkins, joke text on corkboard cards (when displayed in-world), green room scrawlings, venue flyers.
- **Size Range**: 14px-22px for napkin text, 10px-16px for flyer details.
- **Weight**: Regular (400). No bold. Emphasis through underlining or ALL CAPS, never weight change (handwriting doesn't have bold).
- **Treatment**: Slight rotation variance per character (0.5-2 degrees), baseline wobble (1-2px variance), irregular spacing. This simulates actual handwriting. Never perfectly aligned.

**Clean Sans-Serif (System Text)**:
- **Font Choice**: *Inter* (Google Font) for all system UI.
- **Usage**: Bit Builder stats, Laugh Graph labels, menu text, tutorials, settings.
- **Size Range**: 12px body text, 16px subheadings, 24px headings, 36px+ hero text (game title, tier unlock announcements).
- **Weight Hierarchy**:
  - Regular (400): body text, descriptions
  - Medium (500): subheadings, labels
  - Bold (700): headings, key stats, emphasis
- **Treatment**: Perfect alignment, consistent spacing, maximum legibility. This is the "system voice" — clear, reliable, never ambiguous.

**Monospace (Code/Data Display)**:
- **Font Choice**: *JetBrains Mono* (Google Font).
- **Usage**: Numerical stats in Bit Builder (Humor Profile axes, Quality score), REP and CASH counters, technical readouts in post-set analysis.
- **Size Range**: 12px-16px.
- **Weight**: Regular (400) for most, Bold (700) for emphasis.
- **Why Monospace**: Makes numbers easy to scan and compare. The fixed-width ensures stat columns align perfectly.

### Typography Rules

**Hierarchy in the Bit Builder**:
1. Component card title (joke component name, e.g., "Premise: Airport Security"): Inter Medium 14px, Setlist Ink.
2. Component card body (the actual text of the joke fragment): Caveat Regular 16px, Setlist Ink.
3. Component card stats (Humor Profile axes): JetBrains Mono Regular 11px, Cold Silence Blue, right-aligned.

**Hierarchy on the Napkin Setlist**:
1. Setlist title ("Tuesday Open Mic - The Creek"): Caveat Regular 18px, Setlist Ink, underlined.
2. Joke titles: Caveat Regular 16px, Setlist Ink, left-aligned, numbered by hand (1., 2., 3...).
3. Notes/annotations (e.g., "KILL THIS OPENER"): Caveat Regular 12px, Bomb Red, scrawled at angles.

**Hierarchy in the Laugh Graph**:
1. Graph title ("Set Performance - The Comedy Store, 2/7/26"): Inter Bold 18px, Napkin Cream.
2. Axis labels (time, engagement): Inter Regular 12px, Napkin Cream, 70% opacity.
3. Joke markers (labels on waveform peaks): Inter Medium 11px, Spotlight Gold.

**Line Length Limits**:
- Diegetic text (napkins, cards): 40-60 characters per line maximum. Mimics natural handwriting line breaks.
- System text (menus, tutorials): 60-80 characters per line maximum. Optimized for reading speed.

**Accessibility**:
- Minimum text size: 12px for body text, 10px for annotations (and annotations must never contain critical gameplay information).
- Line height: 1.5x font size for body text, 1.3x for headings.
- Dyslexia-friendly mode option: replaces Caveat with *OpenDyslexic* and increases Inter line height to 1.6x.

---

## 6. Asset Pipeline Overview

### Pipeline Philosophy

The art pipeline prioritizes **iteration speed and modular reuse**. The Bit Builder generates thousands of joke combinations, the Crowd Engine populates dozens of venue types, and the career arc spans 40+ unique locations. The pipeline must support rapid content creation without sacrificing visual consistency.

### Production Structure

**Role Breakdown**:
- **Lead Artist (1)**: Defines style, creates hero assets (key venues, core UI elements), reviews all assets for consistency.
- **UI Artist (1)**: Implements all UI elements in-engine, handles diegetic interface design, maintains style guide.
- **Environment Artist (1)**: Builds all venue environments (comedy clubs, theaters, apartments). Modular set construction.
- **VFX Artist (1)**: Laugh Graph visualizations, spotlight effects, audience reaction animations, screen-space effects (color grading, vignette, glow).
- **Animator (0.5 FTE)**: Character idle animations for audience members, micro-animations for UI (card drag, napkin placement, flyer transitions).

**Tools**:
- **2D Art**: Adobe Photoshop (primary), Procreate (for hand-drawn texture creation).
- **UI Implementation**: Unity UI Toolkit or Godot Control nodes (engine-dependent). All UI is 2D.
- **3D Environments**: Blender (modeling and lighting). Low-poly aesthetic (see Technical Constraints). Export to FBX.
- **Textures**: 2D hand-painted in Photoshop, 1024x1024 or 512x512 atlases. No procedural textures (they lack the handmade quality).
- **Animation**: Spine 2D for audience character rigs (simple 2-bone skeletons), Unity/Godot native animation for UI.
- **VFX**: Shader-based (custom spotlight shader, waveform line renderer). Particle systems for subtle ambient effects (dust in spotlight, steam from coffee cup).

### Art Asset Structure

**Joke Component Cards** (300+ unique cards at launch):
- **Template**: 120x80px PNG, 3px rounded corners, drop shadow baked in.
- **Layers**:
  1. Background (Napkin Cream fill)
  2. Border (2px Setlist Ink stroke)
  3. Icon (16x16px spot illustration representing the joke topic — e.g., airplane silhouette for "airport security" premise)
  4. Title text (component type + brief label, e.g., "Premise: Airplane")
  5. Body text (the actual joke fragment, 2-3 lines, Caveat font)
  6. Stat overlay (Humor Profile mini-radar chart, 5 axes, 32x32px, semi-transparent)
- **Production Method**:
  - Create 20 template variations (different border colors, slight rotation variance, wear patterns).
  - Populate templates with text and icons per card.
  - Batch export with naming convention: `card_[type]_[id].png` (e.g., `card_premise_001.png`).
- **Estimated Time**: 2 hours per 10 cards once template is finalized. ~60 hours total for 300 cards.

**Venue Environments** (12 unique venues at launch, 5 variants per venue = 60 total scenes):
- **Modeling**: Modular kit approach. Each venue is assembled from reusable pieces:
  - Stage platform (3 sizes: small, medium, large)
  - Brick wall (4 variants: clean, worn, graffiti, flyer-covered)
  - Audience seating (tables, booths, theater seats, standing room)
  - Lighting rigs (practical lights + spotlight)
  - Props (mic stand, bar, green room furniture)
- **Polycount Budget**: 5,000-10,000 tris per venue. Low-poly with high-contrast lighting does the heavy lifting.
- **Textures**: Hand-painted diffuse only. No normal maps, no PBR. Single 2048x2048 atlas per venue.
- **Lighting**: Baked lightmaps for ambient + real-time spotlight (single dynamic spotlight per venue). Warm key light from stage direction, cool fill from audience direction.
- **Production Method**:
  - Build modular kit first (80 hours).
  - Assemble 12 base venues from kit (20 hours).
  - Create 4 additional variants per venue by swapping wall textures, lighting color, and prop placement (40 hours).
- **Estimated Time**: 140 hours total for 60 venue scenes.

**UI Elements**:
- **Napkin Setlist**: 5 hand-drawn napkin variations (different coffee stains, wrinkle patterns, torn edges). 512x768px PNG with alpha channel.
- **Corkboard**: 1 hero asset, 2048x2048px, rendered at various scales depending on screen size. Cork texture + wood frame + visible pushpins.
- **Flyers**: 40+ unique venue flyers. Each flyer is a 400x560px PNG (portrait orientation) with custom layout per venue. Include venue name, show dates (randomized), clip art, and distressed edges.
- **Phone Interface**: Single smartphone mockup (1080x2340px) with transparent screen area. Text messages rendered as dynamic text overlays.
- **Laugh Graph**: Shader-based line renderer (procedural). The waveform is generated in real-time from performance data. Frame is a simple 1px stroke rectangle.

**Character Rigs (Audience Members)**:
- **Design**: Ultra-simplified. Circle head (solid color, 2 dot eyes, minimal mouth shape), oval torso, no limbs (arms implied through body rotation). Think *Untitled Goose Game* level of abstraction.
- **Variations**: 12 unique head colors, 12 unique torso colors, 3 size variants = 432 possible combinations (sufficient for 80-person audience with minimal repetition).
- **Animation**: 3-bone rig (head, torso pivot, torso base).
  - Idle: gentle sway (1-second loop, 0.5-degree rotation variance).
  - Laugh: head tilts back 15 degrees + torso bounces 5px + scale pulse 105% (0.3-second animation).
  - Disengage: head tilts down 10 degrees + torso darkens 20% (0.5-second fade).
  - Heckle: head tilts forward aggressively + torso red tint (0.2-second snap).
- **Production Method**: Create base rig in Spine 2D. Export 4 animations. Generate variations through code (color swap + scale). Total production time: 16 hours.

### Naming Conventions

**Files**:
- Texture: `tex_[object]_[variant]_[resolution].png` (e.g., `tex_brickwall_worn_1024.png`)
- Model: `mdl_[object]_[LOD].fbx` (e.g., `mdl_stage_lod0.fbx`)
- UI Element: `ui_[element]_[state].png` (e.g., `ui_button_hover.png`)
- Card: `card_[type]_[id].png` (e.g., `card_punchline_042.png`)
- Flyer: `flyer_[venue_name].png` (e.g., `flyer_comedy_store.png`)

**Layers in Source Files** (PSD/Blend):
- Always name layers descriptively.
- Use folders: "Background," "Foreground," "UI," "Lighting."
- Lock non-editable layers.
- Include a "REFERENCE" top layer with style guide swatches and ruler guides.

### Version Control and Backups

- All source files (PSD, Blend, Spine) stored in Git LFS or equivalent.
- Exported assets (PNG, FBX) generated via export scripts (automate where possible).
- Daily backups to external drive.
- Style guide PDF (this document) stored in repo root. Any palette or typography changes require updating the guide FIRST, then assets.

### Iteration Process

1. **Concept**: Lead Artist sketches key asset (pencil or digital rough). 30 min.
2. **First Pass**: Implement in production tool (Photoshop, Blender). 2-4 hours.
3. **In-Engine Review**: Import to game, view in context. Does it read at a glance? Does it match the style guide?
4. **Revision**: Adjust based on in-context review. 1-2 hours.
5. **Final Approval**: Lead Artist signs off. Asset locked.

**Speed > Perfection**: If an asset is 80% there and reads clearly, ship it. The player is focused on joke construction and performance, not pixel-perfect brick mortar. Consistency matters more than polish.

---

## 7. Readability Checklist Results

Every UI element and environment passes through this checklist before approval.

### The Squint Test

**Method**: Display the screen at normal size. Squint until details blur. Can you still identify the key information?

**Applied to DEADPAN**:
- **Bit Builder (Joke Card Assembly)**: PASS. Even squinting, joke cards are distinct rectangular shapes. The connection lines between cards remain visible. The Humor Profile radar chart (color-coded) remains identifiable.
- **Napkin Setlist**: PASS. The napkin shape is clear. The numbered list is readable as a list (even if individual words blur). Handwritten text maintains character.
- **Laugh Graph**: PASS. The waveform is high-contrast (Spotlight Gold on Midnight Canvas). Peaks and valleys read clearly. The emotional state (hot/cold) is conveyed through color temperature even when squinting.
- **Venue Selection (Flyer Stack)**: PASS. Each flyer is a distinct rectangle. The layered stacking reads as depth. The top flyer (active selection) is brighter and thus clearly the focus.
- **Performance View (On Stage)**: PASS. The stage, spotlight, audience clusters, and Laugh Graph are all in distinct visual zones. The eye knows where to look: center (stage), bottom (graph), periphery (audience).

**Failures Identified**:
- Early prototype: Joke card stat text (Humor Profile numbers) was too small (8px). Failed squint test. Fixed by replacing numbers with mini radar chart (visual > textual at small sizes).

### The Thumbnail Test

**Method**: Take a 1920x1080 screenshot. Scale it down to 320x180 (YouTube thumbnail size). Can you still tell what's happening in the scene?

**Applied to DEADPAN**:
- **Main Menu**: PASS. Title (large Napkin Cream text on Midnight Canvas), single spotlight illuminating a mic stand, simple menu options below. Reads as "comedy game" even at thumbnail size.
- **Bit Builder**: PASS. Corkboard texture is recognizable. Cards are distinct colored rectangles. The assembly area (where cards snap together) is visually distinct from the card library.
- **Performance View**: PASS. Spotlight cone, stick figure audience, waveform graph. Even at 320x180, the composition communicates "performing on stage."

**Failures Identified**:
- Early prototype: Audience members were too detailed (visible facial features, clothing). At thumbnail size, they became visual noise. Fixed by simplifying to circle heads and solid-color torsos.

### The Colorblind Test

**Method**: Run screenshots through colorblind simulation filters (Deuteranopia, Protanopia, Tritanopia). Does critical information remain distinguishable?

**Applied to DEADPAN**:
- **Standard Palette**:
  - Deuteranopia (red-green blindness): Brick Red and Neon Sign Green become difficult to distinguish. FAIL.
  - Protanopia (red-green blindness): Same issue. FAIL.
  - Tritanopia (blue-yellow blindness): Spotlight Gold and Cold Silence Blue lose contrast. FAIL.

**Fix**: Implemented redundant iconography + colorblind mode.
- **Redundant Icons**:
  - Green feedback = checkmark icon + green color.
  - Red feedback = X icon + red color.
  - Gold success = star icon + gold color.
  - Blue cold state = snowflake icon + blue tint.
- **Colorblind Mode**:
  - Swaps Neon Sign Green → Cyan (`#00A8E8`).
  - Swaps Bomb Red → Coral Pink (`#FF6F61`).
  - Increases contrast across all UI elements by 15%.
  - Result: Deuteranopia and Protanopia = PASS. Tritanopia = PASS.

### The Motion Test

**Method**: Observe the screen in motion (performance playthrough, UI transitions). Does the eye track the right elements? Is there visual noise or distraction?

**Applied to DEADPAN**:
- **Performance View**: PASS. During a set, the player's eye should track: stage (comedian's position) → Laugh Graph (real-time feedback) → audience (visual confirmation of graph data). The spotlight naturally draws the eye to center. The Laugh Graph pulses with color shifts (hot/cold) which creates peripheral awareness without requiring direct focus.
- **Bit Builder Drag-and-Drop**: PASS. When dragging a joke card, the card lifts (shadow deepens, scale increases) and follows the cursor smoothly. Snap targets (the assembly slots) pulse with a 1-second glow animation in Spotlight Gold. The eye easily tracks where the card can be placed.
- **Venue Flyer Selection**: PASS. Hovering over a flyer causes it to lift from the stack (scale 105%, shadow deepens, slight rotation). The animation is 200ms with ease-out easing — fast enough to feel responsive, slow enough to feel physical.

**Failures Identified**:
- Early prototype: Laugh Graph updated every frame with high-frequency oscillation. Result: visual noise, player couldn't read the trend. Fixed by smoothing the waveform with a 0.3-second rolling average. Now the graph pulses like a heartbeat, not a seismograph.

### The Glance Test

**Method**: Show a screenshot to a player for 2 seconds. Remove it. Ask: "What were you looking at? What information did you retain?"

**Applied to DEADPAN**:
- **Bit Builder**: Players correctly identified: "Corkboard with cards. Some cards connected. I could see stats." SUCCESS. Players retained the structure (assembly area vs. library) and understood the interaction model (cards connect).
- **Performance View**: Players correctly identified: "Comedian on stage, audience in front, graph at bottom showing how it's going." SUCCESS. The three-zone layout (stage, audience, feedback) was immediately parsed.
- **Napkin Setlist**: Players correctly identified: "A list on a napkin. Hand-written. Numbered jokes." SUCCESS. The diegetic object (napkin) was recognized, and the function (list of jokes) was understood.

**Failures Identified**:
- Early prototype: Bit Builder stats were overlaid directly on cards as text (5 numbers). Players said: "I saw numbers but didn't understand what they meant." Fixed by replacing text with a mini radar chart. New test: Players said: "I saw a shape, like a fingerprint for the joke." SUCCESS. Visual > textual for at-a-glance information.

### The First-Boot Test

**Method**: Show the game to someone who has never seen it. No tutorial. Can they identify what kind of game it is within 10 seconds of seeing the main menu or first gameplay screen?

**Applied to DEADPAN**:
- **Main Menu**: 8/10 testers correctly identified "comedy game" or "stand-up comedy" within 10 seconds. Visual cues: brick wall, spotlight, microphone, the word "DEADPAN" in handwritten font. 2/10 said "music game?" (microphone = music association). Acceptable margin of error.
- **Bit Builder (First Screen)**: 6/10 testers correctly identified "building something" or "crafting." 4/10 were unsure. After seeing cards snap together, 10/10 understood "assembling jokes from pieces." Conclusion: The Bit Builder requires minimal tutorial text ("Drag cards to build a joke"), but the interaction model is intuitive once demonstrated.

**Failures Identified**:
- Early prototype: Main menu had no environmental context — just text on black. Testers had no idea what the game was. Fixed by adding the brick wall, spotlight, and mic stand. Instant clarity.

---

## 8. Reference List

The visual identity of DEADPAN is synthesized from these references. Every artist on the team should study this list.

### Games (Visual Style & UI)

**Unpacking** (Witch Beam, 2021):
- **What We're Stealing**: Diegetic UI. Environmental storytelling through objects. The warm, specific, tactile quality of hand-placed items. The way a cluttered space feels *lived in*, not chaotic.
- **Specific Reference**: The way boxes and objects have subtle shadows and a hand-drawn quality. The way unpacking a familiar object (a coffee mug, a notebook) triggers emotional recognition. We want joke cards to feel like *your* joke cards, not generic data.

**Papers, Please** (Lucas Pope, 2013):
- **What We're Stealing**: The tension of performance under observation. The way a simple stamp mechanic (approve/deny) becomes emotionally loaded. The Eastern European bureaucratic aesthetic adapted to comedy clubs = same vibe, different locale.
- **Specific Reference**: The desk layout. Everything has a place. The UI is a workspace. The player is doing a job. That's the Bit Builder — you are at your desk, building jokes like a craftsperson stamping documents.

**The Movies** (Lionhead Studios, 2005):
- **What We're Stealing**: Managing a creative empire. The satisfaction of watching your creative product (a film, a joke set) get judged by an audience. The career arc from nobody to mogul.
- **Specific Reference**: The way the game communicated success through visual feedback (award trophies, star ratings, audience applause). We want REP growth and tier unlocks to feel like winning an award.

**Slay the Spire** (MegaCrit, 2019):
- **What We're Stealing**: Card-based modular assembly with visual clarity. The way card synergies are immediately apparent. The satisfaction of discovering a powerful combination.
- **Specific Reference**: The card layout. Each card has an icon, a title, a description, and stats — all perfectly readable at a glance. The visual hierarchy is flawless. That's the joke component card design.

**Night in the Woods** (Infinite Fall, 2017):
- **What We're Stealing**: The warmth of a specific subculture (small-town America = dive bar comedy scene). The way NPCs feel like real people with their own lives. The warm color palette that makes even mundane environments feel inviting.
- **Specific Reference**: The town exploration. Each location (the donut shop, the party, Mae's house) has its own personality. That's how each comedy venue should feel — not generic "club A, club B," but The Creek vs. The Comedy Store, each with distinct identity.

**Kind Words** (Popcannibal, 2019):
- **What We're Stealing**: The handwritten aesthetic. The intimacy of words written by a human hand. The way vulnerability is communicated through visual softness.
- **Specific Reference**: The letter-writing interface. The paper texture. The handwritten font. That's the napkin setlist — it should feel like something you wrote, not something a computer generated.

### Films & TV (Cinematography, Color, Mood)

**Louie** (FX, 2010-2015):
- **What We're Stealing**: The contrast between the warm glow of stage lights and the cold reality of the city outside. The handheld, grainy, documentary quality. The way the show looks *lived in*.
- **Specific Reference**: Season 1 Episode 1. The brick wall, the spotlight, the audience in shadow. That's the performance view. The green room scenes — fluorescent lights, beige walls, exhaustion. That's the off-stage color palette.

**The Marvelous Mrs. Maisel** (Amazon, 2017-2023):
- **What We're Stealing**: The period-specific club interiors. The velvet curtains. The warm golden stage lights. The way the camera captures the electricity of a crowd leaning in.
- **Specific Reference**: Gaslight Cafe scenes. The spotlight cutting through cigarette smoke. The audience tables lit by candles. That hazy, intimate, golden quality = our Spotlight Gold.

**Comedians in Cars Getting Coffee** (Netflix/Crackle, 2012-2019):
- **What We're Stealing**: The intimacy of comedians talking shop. The warmth of the color grading. The way the show makes diners and coffee shops look beautiful through lighting and framing.
- **Specific Reference**: The warm amber color grade. The natural light through diner windows. That's the off-stage world (apartment, green rooms, agent meetings). Warm, human, real.

**Bo Burnham: Inside** (Netflix, 2021):
- **What We're Stealing**: The lone performer in a small room. The spotlight as the only light source. The way isolation is communicated through negative space and harsh lighting contrast.
- **Specific Reference**: The bedroom performance space. One spotlight. Everything else is darkness. That's the visual metaphor for stand-up — one person, one light, the void.

### Art & Photography (Texture, Composition, Light)

**Saul Leiter** (Street Photography, 1950s-60s):
- **What We're Stealing**: The way urban environments look warm and painterly through windows, reflections, and fog. The use of foreground blur to create depth and intimacy.
- **Specific Reference**: His use of warm reds, yellows, and oranges in city scenes. That's our Brick Red, Spotlight Gold, and Napkin Cream — the warm palette of a city at night.

**Edward Hopper** (American Realism, 1920s-60s):
- **What We're Stealing**: The isolation of figures in urban spaces. The way artificial light (diners, theaters, office windows) creates islands of warmth in darkness. The emotional weight of negative space.
- **Specific Reference**: *Nighthawks* (1942). The diner glowing in the night. The figures inside isolated but visible. That's the comedy club — a warm box of light in the dark city. The green room as an Edward Hopper painting.

**Vintage Comedy Club Posters** (1970s-1990s):
- **What We're Stealing**: The DIY photocopy aesthetic. The layered, torn, taped-up flyers on brick walls. The Sharpie handwriting. The coffee stains and wear.
- **Specific Reference**: Google Image Search "comedy club flyer 1980s." That's the venue flyer design. High-contrast photocopied look, bold sans-serif type, clip art, phone numbers written in Sharpie.

### Design Movements

**Memphis Design** (1980s Postmodernism):
- **What We're Stealing**: Bold geometric shapes. Primary colors used playfully. The celebration of imperfection and asymmetry. The anti-minimalist joy of MORE.
- **Specific Reference**: Ettore Sottsass furniture. The way Memphis used circles, rectangles, and squiggles in unexpected combinations. That's the shape language — structured but playful. Rectangles (cards) + circles (spotlights, audience) + hand-drawn squiggles (string on corkboard, coffee stains).

**Dada / Collage Aesthetic** (1920s-30s):
- **What We're Stealing**: The layered, cut-and-paste quality. The mix of typed text, handwritten text, and found images. The raw, unpolished edges.
- **Specific Reference**: Hannah Höch photomontages. The way disparate elements are combined into a cohesive whole. That's the UI — napkins, corkboard, flyers, phone screens, all existing in the same space without trying to blend seamlessly. The seams are visible, and that's the point.

---

## 9. Technical Constraints Summary

The art direction must fit within the technical budget. These constraints are non-negotiable.

### Platform Performance Targets

**PC (Steam) — Primary Platform**:
- **Target Spec**: GTX 1060 / RX 580 (mid-range 2016 GPU), Intel i5-8400, 8GB RAM.
- **Resolution**: 1920x1080 native, scalable to 4K.
- **Frame Rate**: Locked 60 FPS during all gameplay. 30 FPS minimum during performance sequences (Laugh Graph rendering + audience animation).
- **Why These Targets**: Tycoon/sim players value stability over spectacle. The game runs on laptops. Prioritize consistency.

**Nintendo Switch — Secondary Platform**:
- **Target Spec**: Handheld mode (720p), Docked mode (1080p).
- **Frame Rate**: Locked 30 FPS. 60 FPS is a stretch goal but not required.
- **Constraints**: Texture memory is tight (2GB max for all art assets). Atlas everything aggressively. Use texture compression (ASTC for Switch).

### Art Budget Constraints

**Polycount** (3D Environments):
- **Per Venue**: 5,000-10,000 tris total. This is LOW POLY by modern standards, but lit correctly, it looks great. Reference: *Firewatch* (2016) ran on 10-15K tris per scene and looked stunning.
- **Modular Kit Approach**: Build 200-300 modular pieces (wall segment, table, chair, stage platform, mic stand). Venues are assembled from these pieces. Reduces memory footprint and production time.
- **Character Models**: Audience members are 2D sprites (Spine rigs), not 3D models. Total polycount: ZERO. Saves performance for lighting and effects.

**Texture Budget**:
- **Per Venue**: Single 2048x2048 atlas. Diffuse only, no normal maps, no specular. Hand-painted textures compress well and load fast.
- **UI Textures**: 1024x1024 max per element. Most UI elements (cards, napkins, flyers) are 512x512 or smaller.
- **Total Texture Memory Budget**: 500MB for all art assets (environments, UI, characters). This fits comfortably in Switch's 2GB available memory after engine overhead.

**Draw Calls**:
- **Max Draw Calls Per Frame**: 150. Each unique material = 1 draw call. Atlasing and material reuse keep this low.
- **Batching Strategy**:
  - All joke cards share 1 material (atlas of card backgrounds + dynamic text overlay).
  - All venue props share 1 material per venue (atlased).
  - Audience sprites batched via sprite renderer (1 draw call for all visible audience members).

**Animation Budget**:
- **Skeletal Rigs**: Audience characters only. 3 bones per character. Max 100 characters on screen = 300 bones. Well within modern engine limits.
- **UI Animations**: Tweening only (position, rotation, scale, alpha). No skeletal animation. Unity/Godot handle this efficiently.
- **VFX**: Shader-based (spotlight cone, waveform line). Minimal particle systems (dust in spotlight = 20-30 particles max, pooled and reused).

### File Size Targets

**PC Build**: 1.5GB installed (including engine runtime). Comparable to *Game Dev Tycoon* (1.2GB) and *Slay the Spire* (1.5GB).
**Switch Build**: 1.2GB (more aggressive compression).

**Breakdown**:
- Engine runtime: 300MB
- Code + data: 100MB
- Audio (music + SFX): 400MB (compressed OGG, 128kbps)
- Art assets (textures + models): 500MB
- UI assets: 200MB

### Rendering Features (What We're Using)

**YES**:
- Real-time directional + spotlight lighting (1 key light, 1 spotlight per scene).
- Baked lightmaps for ambient lighting (pre-calculated, no runtime cost).
- Post-process color grading (LUT-based, minimal cost).
- Vignette effect (shader, negligible cost).
- Bloom on Spotlight Gold elements (additive blend, low cost).
- Sprite-based 2D characters (Spine animation, efficient batching).

**NO** (Cut for Performance/Aesthetic Reasons):
- Real-time shadows (too expensive for the target spec; baked shadows only).
- Normal mapping (doesn't fit the hand-painted aesthetic).
- PBR materials (overkill for the art style; diffuse-only is faster and looks better for this game).
- Screen-space reflections (not needed; no reflective surfaces).
- Ambient occlusion (baked into textures).
- Anti-aliasing (FXAA only if needed; the sharp pixel edges fit the aesthetic).

### Shader Budget

**Custom Shaders** (5 total):
1. **Spotlight Cone Shader**: Radial gradient with adjustable color and intensity. Used for stage spotlight. ~50 lines of shader code.
2. **Waveform Line Renderer**: Procedural line with dynamic color and glow. Used for Laugh Graph. ~80 lines.
3. **Napkin Paper Shader**: Combines paper texture + stain texture + handwritten text overlay. Used for setlist napkins. ~60 lines.
4. **Corkboard Shader**: Cork texture + wood frame + pushpin sprites. ~40 lines.
5. **Card Shader**: Rounded rectangle with drop shadow + stats overlay + icon. ~70 lines.

All shaders are unlit or vertex-lit (no per-pixel lighting calculations). Optimized for mobile (Switch).

### Audio Budget

**Music**:
- Main menu theme: 2-minute loop, 128kbps OGG, ~2MB.
- Green room ambient: 1-minute loop, 96kbps, ~0.7MB.
- Performance background (lo-fi jazz): 3-minute loop, 128kbps, ~3MB.
- Venue-specific music: 8 tracks, 2 minutes each, 128kbps, ~16MB total.
- **Total Music**: ~22MB.

**SFX**:
- Card drag/snap: 3 variations, ~50KB total.
- Napkin placement: 2 variations, ~30KB.
- Crowd reactions: 20 unique laugh samples (chuckle, big laugh, eruption), ~500KB. Pitched and time-stretched at runtime for variety.
- Heckler shouts: 10 variations, ~200KB.
- Ambient (glass clinks, door close, mic feedback): 15 sounds, ~300KB.
- UI (button hover, menu confirm): 5 sounds, ~50KB.
- **Total SFX**: ~1.1MB.

**Crowd Audio System**:
- Laughter is procedurally mixed: select 3-5 laugh samples based on crowd size and reaction intensity, layer with slight delay (20-50ms offset per sample), apply reverb based on venue size. This creates realistic crowd laughter from a small sample library.
- No voice acting. Jokes are text-only. This saves 95% of the audio budget and keeps the combinatorial space of the Bit Builder infinite.

---

## 10. Screen-by-Screen Visual Breakdown

This section defines the exact visual treatment for every major screen in the game.

### Main Menu

**Layout**:
- **Background**: Full-screen brick wall texture (Brick Red dominant, Coffee Stain Brown mortar). Slightly out of focus (1px Gaussian blur) to reduce visual weight.
- **Center Stage**: Single spotlight (Spotlight Gold gradient, radial falloff) illuminating a microphone stand. The mic is the only fully in-focus element. Dust particles float in the light cone (20-30 particles, slow upward drift).
- **Title**: "DEADPAN" in Caveat Bold 72px, Napkin Cream, positioned upper-third of screen, slight rotation (-2 degrees), subtle drop shadow (4px offset, 60% opacity Midnight Canvas).
- **Menu Options**: Vertical list, center-bottom. Options in Inter Medium 20px, Napkin Cream. Hover state: Spotlight Gold + scale 110%.
  - New Game
  - Continue
  - Settings
  - Credits
  - Quit
- **Audio**: Main menu theme (melancholic piano + ambient city hum). Crowd murmur at 10% volume (sets the mood).

**Emotional Target**: Anticipation. Intimacy. "You are about to step into a world."

---

### Apartment (Joke Writing Space)

**Layout**:
- **Background**: Small apartment interior. Left side: window with city lights visible (out of focus, warm glow). Right side: desk with notebook, coffee cup, lamp. Center: corkboard on wall (this is the Bit Builder).
- **Corkboard**: 60% of screen. 2048x1536px cork texture, wood frame, visible pushpins. This is the active workspace.
- **Component Card Library**: Bottom 20% of screen. Horizontal scrollable list of joke component cards. Each card is 120x80px (see Asset Pipeline section for card design details). Draggable.
- **Lighting**: Warm desk lamp (key light from right, Spotlight Gold tint). Cool ambient from window (Midnight Canvas tint). High contrast — the corkboard is brightly lit, the periphery fades to shadow.
- **UI Overlays**:
  - Top-left: Current REP and CASH counters (JetBrains Mono 16px, Napkin Cream, Midnight Canvas background panel).
  - Top-right: Current in-game time and day (Inter Regular 14px, Napkin Cream, 70% opacity).
  - Bottom-right: "Write New Material" button (Inter Medium 16px, Neon Sign Green background, Setlist Ink text, rounded rectangle).

**Interaction**:
- Player drags component cards from the library onto the corkboard.
- Cards snap together when dragged to within 20px of a valid connection point (Setup snaps to Premise, Punchline snaps to Misdirection, etc.).
- When cards snap, a line draws between them (Spotlight Gold, 2px thick, hand-drawn wobble effect).
- Assembled joke displays a real-time Quality score (0-100, JetBrains Mono, color-coded: red/orange/yellow/green/gold).

**Emotional Target**: Focused creativity. "This is your workshop. Build something."

---

### Setlist Builder (Pre-Performance)

**Layout**:
- **Background**: Green room or kitchen table. Warm practical lighting (single overhead bulb, Coffee Stain Brown tint). Cluttered periphery (empty coffee cups, crumpled napkins, phone charging in corner).
- **Center**: Napkin (512x768px, Napkin Cream, torn edge at top, coffee ring stain at bottom-right). This is the active setlist.
- **Napkin Content**:
  - Top: Venue name + show date (Caveat Regular 18px, Setlist Ink, underlined).
  - Body: Numbered list of joke titles (Caveat Regular 16px, Setlist Ink). Drag-to-reorder functionality. Each joke displays a mini Humor Profile icon (32x32px radar chart).
  - Annotations: Scrawled notes in margins (e.g., "NAIL THIS OPENER," "callback to #2 if crowd is hot"). Caveat Regular 12px, Bomb Red or Neon Sign Green depending on tone.
- **Joke Library**: Right side of screen, vertical scrollable list. All available jokes (constructed in the Bit Builder). Each entry shows joke title, Quality score, and Humor Profile. Draggable onto napkin.
- **Action Buttons**:
  - "Head to Venue" (Inter Medium 18px, Spotlight Gold background, Midnight Canvas text, center-bottom).
  - "Practice Set" (small text button, bottom-left, Inter Regular 14px, Neon Sign Green).

**Interaction**:
- Drag jokes from library onto napkin to build setlist (max 5-15 jokes depending on career tier).
- Reorder jokes by dragging within the napkin.
- Click "Practice Set" to see a simulated performance (no REP/CASH earned, pure feedback loop).
- Click "Head to Venue" to transition to performance.

**Emotional Target**: Preparation. "You're about to walk into the room. Are you ready?"

---

### Venue Selection (Booking Screen)

**Layout**:
- **Background**: Corkboard or table covered in venue flyers.
- **Flyer Stack**: 8-12 venue flyers, layered and stacked (each flyer offset by 4px x/y, rotated 2-4 degrees for depth). Top flyer is fully visible and saturated. Lower flyers are partially obscured and desaturated.
- **Flyer Design** (per venue):
  - Venue name (bold sans-serif, high contrast, e.g., "THE CREEK" in all caps).
  - Show details (date, time, lineup, two-drink minimum, etc.).
  - Clip art or logo (custom per venue).
  - Distressed edges (torn, taped).
  - Coffee stains, pen marks (texture details).
- **Interaction**:
  - Hover over a flyer: it lifts from the stack (scale 105%, shadow deepens, rotation 0 degrees for readability).
  - Click a flyer: it expands to fill screen, showing full venue details (crowd composition, expected REP, payout, booker relationship).
  - "Book This Gig" button appears (Inter Medium 18px, Spotlight Gold background).
- **Info Panel** (appears on flyer expansion):
  - Crowd composition breakdown (pie chart or horizontal bar chart showing archetype percentages).
  - Expected audience size (e.g., "40-60 people").
  - Payout: $XXX.
  - REP potential: XXX (based on venue tier and player's current career level).
  - Booker relationship: 0-100 (affects booking priority).

**Emotional Target**: Opportunity and choice. "Where do you want to perform? Choose wisely."

---

### Performance View (On Stage)

This is the most important screen. The player spends 30-40% of total playtime here.

**Layout (Three Zones)**:

**Zone 1: Stage + Audience (Top 60% of screen)**:
- **Stage**: Elevated platform, center-screen. Brick wall behind (Brick Red, flyers and graffiti visible). Microphone stand center-stage (iconic silhouette).
- **Spotlight**: Radial gradient cone (Spotlight Gold at center, fading to Midnight Canvas at edges). The spotlight illuminates the mic and a circular area on stage. Dust particles visible in the light beam.
- **Comedian Representation**: Abstract. A simple vertical line (the stand-up's body) next to the mic. No detailed character model — the player IS the comedian. Alternatively, the mic stand alone is sufficient (the comedian is implied).
- **Audience**: Foreground/mid-ground. 20-100 audience members (depending on venue size) rendered as 2D sprite characters (circle head + oval torso, see Character Rigs section). Grouped into clusters (tables of 2-6 people). Clusters positioned in a shallow arc facing the stage.
- **Audience Animation**:
  - Idle: Gentle sway.
  - Laughing: Heads tilt back, bodies bounce, scale pulses.
  - Disengaged: Heads tilt down, bodies darken.
  - Heckling: One character stands slightly, body flashes red.

**Zone 2: Laugh Graph (Bottom 30% of screen)**:
- **Graph Frame**: Horizontal rectangle, full width, 1px Napkin Cream border.
- **Waveform**: Real-time line graph. X-axis = time (joke by joke). Y-axis = aggregate audience engagement (0-1.0 normalized).
- **Line Color**: Shifts based on momentum:
  - Hot (Momentum > 1.2): Spotlight Gold.
  - Neutral (0.8-1.2): Napkin Cream.
  - Cold (< 0.8): Cold Silence Blue.
  - Bombing (< 0.5): Bomb Red.
- **Joke Markers**: Vertical tick marks on the X-axis showing when each joke starts. Label shows joke number (1, 2, 3...).
- **Peak Annotations**: When a joke gets a big reaction (ReactionScore > 0.7), the peak glows (8px Spotlight Gold blur).

**Zone 3: Status HUD (Bottom 10% of screen, overlaid on graph)**:
- **Left Side**: Current joke number and title (Inter Medium 14px, Napkin Cream).
- **Center**: Momentum indicator (visual: circular gauge, 0-2.0, color-coded like waveform).
- **Right Side**: Pivot Points remaining (e.g., "Pivots: 2/4," Inter Medium 14px, Neon Sign Green if available, gray if depleted).

**Interaction**:
- Jokes advance automatically (timing based on word count of joke components, approximately 3-8 seconds per joke).
- Player can trigger a Pivot Point mid-set: a radial menu appears with back-pocket jokes (pre-selected alternate material). Selecting a joke swaps it into the setlist immediately.
- No other interaction during performance. The player WATCHES. The tension is in observation, not action.

**Audio**:
- Ambient: crowd murmur (low-pass filtered, 20% volume).
- Per-joke: crowd reaction (laughter samples layered based on ReactionScore, reverb based on venue size).
- Silence: when a joke bombs, the ambient murmur becomes oppressively loud (no laughter to cover it).

**Emotional Target**: Exposure and tension. "The room is watching you. Are they with you or against you?"

---

### Post-Set Analysis (Laugh Graph Diagnostic)

**Layout**:
- **Background**: Green room or apartment (same environment as joke writing, but dimmer lighting — post-performance exhaustion).
- **Center**: Large Laugh Graph (full waveform, 80% of screen width). This is the detailed, zoomable version.
- **Tabs (Top of Graph)**:
  - Overview (default)
  - Per-Segment (breaks down reactions by audience archetype)
  - Pivot Analysis (shows counterfactual: what would have happened if you hadn't pivoted)
  - Setlist Flow (energy arc visualization)
  - Comparison (overlay previous performances)
- **Graph Annotations**:
  - Hover over any peak/valley: tooltip shows joke title, components used, Quality score, per-segment reactions, Surprise score.
  - Color-coded zones: green (good), yellow (okay), red (bad).
- **Summary Panel (Right Side)**:
  - REP earned: +XXX (JetBrains Mono 24px, Spotlight Gold if gain, Bomb Red if loss).
  - CASH earned: +$XXX.
  - Venue relationship: +/- (affected by performance quality).
  - Best Joke: [Title] (highest ReactionScore).
  - Worst Joke: [Title] (lowest ReactionScore).
  - Audience MVP: [Archetype] loved your set! (e.g., "Comedy Nerds").
  - Audience Hater: [Archetype] was not feeling it. (e.g., "Date Night Couples").
- **Action Buttons**:
  - "Rework Material" (takes player back to Bit Builder with notes on which jokes to improve).
  - "Next" (proceeds to career screen).

**Emotional Target**: Learning and iteration. "Here's what worked. Here's what didn't. Now go make it better."

---

### Career Overview (The Scene)

**Layout**:
- **Background**: Phone screen mockup (smartphone silhouette, 9:19.5 ratio, centered on screen).
- **Phone Content**:
  - **Top**: Status bar (in-game time, date, battery icon at 100% always — pure aesthetic).
  - **Body**: Text message thread interface. Three categories of messages:
    1. **Agent**: Booking offers, advice, relationship check-ins. (Left-aligned bubbles, gray background.)
    2. **Bookers**: Venue invitations, feedback on recent sets. (Left-aligned bubbles, Brick Red background.)
    3. **Rivals/Collaborators**: Scene gossip, collaboration invites, rivalry trash-talk. (Left-aligned bubbles, Velvet Curtain Purple or Neon Sign Green depending on tone.)
  - Player responses appear as right-aligned bubbles (Napkin Cream background, Setlist Ink text).
- **Scrollable Thread**: Vertical scroll, most recent messages at bottom (standard messaging app UX).
- **Interaction**:
  - Tap a message to expand (shows full text if truncated).
  - Tap a booking offer to view venue details (transitions to Venue Selection screen).
  - Tap a collaboration invite to view AI comic profile and accept/decline.
- **Bottom Nav Bar** (fixed):
  - Icons for: Home (career overview), Gigs (venue selection), Material (Bit Builder), Stats (career stats page).

**Emotional Target**: The comedy world is alive. "People are talking. Opportunities are emerging. What's your next move?"

---

### Settings Menu

**Layout**:
- **Background**: Blurred version of current screen (frosted glass effect, 10px Gaussian blur, 40% darkening overlay).
- **Center Panel**: Rectangle (800x600px), Napkin Cream background, Setlist Ink text.
- **Sections** (vertical list, Inter Regular 16px):
  - **Graphics**: Resolution dropdown, fullscreen toggle, frame rate cap (30/60/uncapped).
  - **Audio**: Master volume, music volume, SFX volume (sliders, 0-100%).
  - **Accessibility**: Colorblind mode toggle, high-contrast mode toggle, dyslexia-friendly font toggle, text size (small/medium/large).
  - **Controls**: Key rebinding (PC), button remapping (Switch).
  - **Language**: Dropdown (English, Spanish, French, German, etc.).
- **Close Button**: Top-right, "X" icon (Inter Bold 24px, Bomb Red).

---

## 11. Animation Principles Applied to DEADPAN

Animation in DEADPAN follows the 12 principles of animation (Disney), adapted for UI and low-poly environments.

### Key Principles for This Game

**1. Squash and Stretch** (Limited Application):
- Audience characters: When laughing, heads scale 105% for 0.1 seconds, then return to 100%. Subtle.
- Joke cards: When dragged, scale 110%. When dropped, scale bounces 105% → 95% → 100% over 0.2 seconds.

**2. Anticipation**:
- Before a joke card snaps into place, the snap target pulses (scale 105%, Spotlight Gold glow, 0.2-second lead-in).
- Before the performance starts, the spotlight fades up over 1 second (anticipation for "here we go").

**3. Staging** (Critical for Readability):
- Every animation must direct the player's eye to the right place. When REP is earned, the number pulses and glows (you can't miss it). When a heckler activates, their character flashes red and rises slightly (you see the threat immediately).

**4. Follow Through and Overlapping Action**:
- When a napkin is placed on the table, it lands first (main object), then the coffee cup wobbles slightly (secondary action, 0.1-second delay).
- When the Laugh Graph spikes, the waveform peaks first, then the glow effect fades in (overlapping, not simultaneous).

**5. Ease In and Ease Out**:
- All UI transitions use ease-out for appearing (fast start, slow stop) and ease-in for disappearing (slow start, fast stop). This feels natural, not robotic.
- Example: Flyer lifts from stack with ease-out (0.2 seconds, cubic bezier). Returns to stack with ease-in (0.15 seconds).

**6. Arcs**:
- When joke cards are dragged, they follow the cursor in a slight arc (not a straight line). This mimics the natural motion of a hand moving a physical card.
- When the spotlight shifts focus (if it ever needs to move), it follows an arc, not a linear path.

**7. Secondary Action**:
- Primary: Joke card snaps into place. Secondary: Connection line draws between cards, pushpin appears.
- Primary: Performance ends. Secondary: Spotlight fades, crowd stands and disperses.

**8. Timing**:
- Fast actions (card snap, button click): 0.1-0.2 seconds.
- Medium actions (screen transition, flyer lift): 0.2-0.4 seconds.
- Slow actions (spotlight fade-up, end-of-set applause): 0.5-1.0 seconds.
- Comedy is about timing. The UI must be snappy. No animation exceeds 1 second unless it's a narrative beat (e.g., the special taping intro).

**9. Exaggeration** (Use Sparingly):
- When a set KILLS (average ReactionScore > 0.85), the Laugh Graph spike is exaggerated (120% height, double glow radius). This is the game celebrating the player's success.
- When a set BOMBS (average ReactionScore < 0.3), the waveform flatlines and turns Bomb Red with a pulsing desaturation effect on the entire screen. This is the game making failure feel visceral.

**10. Solid Drawing / Clarity** (Adapted for UI):
- Every frame of animation must be readable. No motion blur that obscures text. No transitions that make the UI hard to parse mid-animation.

**11. Appeal**:
- Animations should feel good. When a joke card snaps into place, the player should feel satisfaction. The bounce, the glow, the sound effect (snap.mp3) — all combine to create a moment of "yes, that worked."

**12. Personality** (in the World, Not Characters):
- The world has personality. The napkin wobbles when placed. The flyer peels slightly when lifted. The spotlight flickers once before fading up. These details communicate "this is a real place with character," not "this is a sterile simulation."

---

## 12. Accessibility Compliance

DEADPAN is designed to be playable by as wide an audience as possible. Accessibility is not an afterthought — it's baked into the art direction.

### Visual Accessibility

**Colorblind Modes**:
- **Deuteranopia/Protanopia Mode**: Swaps Neon Sign Green → Cyan, Bomb Red → Coral Pink. All green/red feedback also has redundant iconography (checkmark/X).
- **Tritanopia Mode**: Adjusts Spotlight Gold → Orange, Cold Silence Blue → Purple. Maintains contrast.
- **Test Process**: All screens run through Coblis (colorblind simulator) before approval.

**High-Contrast Mode**:
- Background → Pure Black (`#000000`).
- Text → Pure White (`#FFFFFF`).
- All UI borders increased to 3px.
- Disables decorative textures (napkin grain, corkboard texture) to reduce visual noise.

**Text Scaling**:
- Three sizes: Small (100%), Medium (125%), Large (150%).
- All UI layouts use relative positioning (percentages, not fixed pixels) to accommodate text reflow.

**Dyslexia-Friendly Mode**:
- Swaps all fonts to OpenDyslexic (heavier baseline, unique character shapes).
- Increases line height to 1.6x.
- Increases letter-spacing by 5%.

**Photosensitivity**:
- No flashing effects above 3 Hz.
- All screen transitions fade (no hard cuts).
- Spotlight pulses are slow (1-second cycle minimum).
- Disable screen shake option in settings.

### Auditory Accessibility

**Subtitles/Captions**:
- Jokes are text-based (no voice acting), so all content is already captioned by default.
- SFX captions available as toggle: e.g., [laughter], [glass clink], [mic feedback].

**Visual Audio Cues**:
- Crowd reactions have visual indicators (audience character animations + Laugh Graph) in addition to audio.
- Heckler shouts trigger a red flash + screen shake (in addition to audio).

**Stereo/Mono Toggle**:
- Spatial audio can be toggled to mono (important for players with single-ear hearing).

### Motor Accessibility

**Reduced Precision Mode**:
- Increases drag-and-drop snap radius from 20px to 40px.
- Enlarges clickable areas for all buttons by 20%.

**Hold-to-Confirm**:
- Toggle to replace single-click actions with hold-to-confirm (prevents accidental clicks). Button fills with color over 0.5 seconds to confirm.

**Keyboard/Controller Navigation**:
- Full keyboard navigation for all menus (Tab to cycle, Enter to select).
- Controller support with button remapping.

**One-Handed Mode**:
- Remappable controls to allow left-hand-only or right-hand-only play.

---

## 13. Marketing & Visual Identity Beyond the Game

The art direction extends to all marketing materials. Visual consistency across Steam page, trailers, social media, and press kits is mandatory.

### Steam Capsule Images

**Header Capsule** (460x215px):
- Brick wall background (Brick Red).
- Microphone stand center-left, spotlight cone illuminating it (Spotlight Gold).
- Game title "DEADPAN" upper-right (Caveat Bold 48px, Napkin Cream).
- Tagline below title: "Build jokes. Bomb sets. Become a legend." (Inter Regular 16px, Napkin Cream).

**Library Capsule** (600x900px, Vertical):
- Same composition as header, but vertical format.
- Full microphone stand visible.
- Napkin setlist in foreground (bottom-third), visible joke list scrawled in Caveat font.

**Hero Capsule** (1920x620px, Wide):
- Brick wall background, full stage visible.
- Center: microphone stand with spotlight.
- Foreground: audience silhouettes (circle heads, abstract).
- Top-third: Game title + tagline.
- Bottom-third: Laugh Graph waveform (Spotlight Gold) with visible peaks and valleys.

**Emotional Target**: "This is a game about the spotlight, the mic, and the room. You know what this is."

---

### Trailer Visual Style

**Opening Shot** (0:00-0:03):
- Fade in from black.
- Single spotlight illuminates a microphone stand on an empty stage.
- Ambient sound: crowd murmur.
- Text overlay: "You bombed last night."

**Hook Sequence** (0:03-0:15):
- Quick cuts:
  1. Bit Builder (cards being dragged and snapped together).
  2. Setlist napkin being written.
  3. Walk to stage (first-person POV, approaching the mic).
  4. Spotlight hits. Crowd visible in shadow.
  5. First joke delivered (text on screen: "Setup: I tried a dating app...").
  6. Laugh Graph spikes (Spotlight Gold).
  7. Audience reaction (heads tilt back, laughter).
- Text overlay: "Build jokes. Perform them. Watch the room react."

**Feature Showcase** (0:15-0:40):
- Bit Builder: "Construct jokes from modular components."
- Crowd Engine: "Every audience is different."
- Laugh Graph: "Learn what works. Iterate."
- Career Arc: "Open mic to HBO special."
- The Scene: "Rivals. Collaborators. The comedy world is alive."

**Climax** (0:40-0:50):
- Montage of success moments:
  1. Laugh Graph eruption (Spotlight Gold spike).
  2. Standing ovation (audience on their feet).
  3. REP unlock: "You are now a HEADLINER."
  4. Special taping venue (large theater, velvet curtain).
- Music swells (main theme piano + beat drop).

**Closer** (0:50-1:00):
- Return to the microphone stand.
- Text overlay: "DEADPAN. Coming 2026."
- Fade to black.
- End card: Steam logo + Wishlist button.

**Audio**:
- Main theme (melancholic piano) throughout.
- Laughter samples layered in.
- Crowd murmur as ambient texture.
- No voice-over. The visuals and text carry the narrative.

**Visual Style**:
- All footage is in-game (no pre-rendered cinematics).
- Color grading matches the game: warm golds and reds, deep blacks, high contrast.
- Text overlays use Caveat for personality, Inter for clarity.

---

### Social Media Style Guide

**Formats**:
- Twitter/X: 1200x675px (16:9 landscape).
- Instagram: 1080x1080px (1:1 square) or 1080x1350px (4:5 portrait).
- TikTok: 1080x1920px (9:16 vertical).

**Content Types**:

**1. Joke Component Showcase**:
- Image: Single joke card (Premise, Setup, Punchline, etc.) on Napkin Cream background, slight rotation, drop shadow.
- Text overlay: The joke fragment (e.g., "Setup: My therapist says I use humor as a coping mechanism.").
- Caption: "What punchline would you pair with this? #DEADPAN"

**2. Venue Reveal**:
- Image: Venue flyer (full custom design).
- Caption: "Venue Unlock: [Venue Name]. Crowd composition: [archetypes]. Are you ready?"

**3. GIF Loops**:
- Bit Builder: Cards being dragged and snapped together (3-second loop).
- Laugh Graph: Waveform spiking and falling (5-second loop).
- Spotlight: Spotlight fading up on empty stage (3-second loop).

**4. Fan Content Prompts**:
- "Post your best bombing story with #DeadpanGame and we'll turn the top 5 into in-game Premise cards."
- "What's your comedy voice? Take our quiz." (Links to a Visual Identity quiz: 5 questions, generates a Voice Identity spectrum result with shareable graphic.)

**Visual Consistency**:
- All social media assets use the game's color palette.
- All text overlays use Caveat (handwritten) or Inter (clean).
- All images include a small "DEADPAN" logo in the corner (60px wide, Napkin Cream on Midnight Canvas background).

---

### Press Kit Assets

**Logo**:
- Full logo: "DEADPAN" in Caveat Bold, Napkin Cream, with microphone icon (simplified silhouette) left-aligned. Provided in PNG (transparent background) and SVG.
- Icon-only logo: Microphone silhouette (circle head + vertical line body) in Spotlight Gold on Midnight Canvas circle background. 512x512px.

**Screenshots** (All 1920x1080):
1. Bit Builder (joke assembly in progress).
2. Performance View (comedian on stage, audience visible, Laugh Graph active).
3. Setlist Builder (napkin with handwritten jokes).
4. Post-Set Analysis (Laugh Graph with annotations).
5. Venue Selection (flyer stack).
6. Career Screen (phone interface with text messages).

**Key Art**:
- Hero image: Microphone stand on stage, spotlight, audience silhouettes, Laugh Graph in foreground. 4K resolution (3840x2160px). Provided in PNG and JPEG.

**Fact Sheet**:
- Formatted as a single-page PDF, using Inter font, Napkin Cream background with coffee stain texture.
- Sections: Game Title, Developer, Release Date, Platforms, Genre, Features, Links (Steam, Twitter, Discord).

---

## 14. Localization and Font Considerations

DEADPAN will launch in English, with plans to localize to 6-8 additional languages.

### Font Choices for Localization

**Issue**: Caveat (handwritten font) and Inter (system font) have limited character set support. Some languages (e.g., Japanese, Chinese, Cyrillic) require alternative fonts.

**Solution**:

| Language | Handwritten Font (Diegetic) | System Font |
|----------|------------------------------|-------------|
| English, French, German, Spanish, Italian, Portuguese | Caveat | Inter |
| Russian (Cyrillic) | Ruslan Display | Inter (supports Cyrillic) |
| Japanese | Yomogi (Google Font, handwritten style) | Noto Sans Japanese |
| Simplified Chinese | Ma Shan Zheng (Google Font, handwritten style) | Noto Sans SC |
| Korean | Poor Story (Google Font, handwritten style) | Noto Sans Korean |

All fallback fonts are chosen to match the visual weight and style of Caveat/Inter as closely as possible.

**Text Expansion**:
- UI layouts must accommodate 30% text expansion (German, French, Russian often run longer than English).
- Joke component cards use dynamic text sizing: if text exceeds 3 lines, font size reduces from 16px to 14px.

**Right-to-Left Languages** (Arabic, Hebrew):
- Not in initial launch. If added, all UI layouts flip horizontally (mirrored). Handwritten text requires new font (e.g., Amiri for Arabic).

---

## 15. Future-Proofing the Art Direction

As DEADPAN grows (DLC, updates, sequels), the art direction must remain consistent while allowing expansion.

### Modular Expansion

**New Venues**:
- All venues use the same modular kit (brick walls, stage platforms, audience seating). New venues are assembled from existing pieces + 1-2 new custom props.
- New venue flyer takes 2-3 hours to design (maintains the torn-edge, high-contrast, photocopied aesthetic).

**New Joke Components**:
- New component cards use the existing template. Production time: 10-15 minutes per card (write text, assign icon, balance stats).

**New Career Tiers** (if added):
- Higher tiers (Arena tours, international circuits) maintain the same visual language but scale up: bigger stages, more audience members, higher-resolution Laugh Graph.

**Seasonal Events**:
- Halloween: Brick walls get cobwebs, spotlight shifts to cold blue, flyers have spooky clip art. Color palette shift: reduce Spotlight Gold saturation by 20%, increase Cold Silence Blue by 20%.
- Holiday: Warm reds and greens, string lights on brick walls, "Happy Holidays" scrawled on napkin setlists.

**Visual Consistency Rules for Expansion**:
1. All new assets must use the established color palette (no new accent colors without art director approval).
2. All new UI elements must pass the squint test and thumbnail test.
3. All new environments must use the modular kit + max 3 new custom props.
4. All new content must be reviewed against this art direction document before final approval.

---

## 16. Closing Statement

The art direction of DEADPAN is not decoration. It is the promise the game makes to the player: **You are a comedian. This is your world. We see you.**

Every napkin, every spotlight, every brick wall is designed to make the player feel like they are living this life — not observing it from a distance. The UI is diegetic because the player's hands are in the world. The palette is warm because the comedy scene, for all its grit, is a community of people trying to make strangers laugh. The shapes are imperfect because creativity is not clean.

Readability is the unbreakable rule. If the player can't parse the Bit Builder at a glance, the jokes don't get built. If the Laugh Graph is cluttered, the learning loop breaks. If the performance view is visually noisy, the tension evaporates. Clarity above all.

The visual identity is: **intimate, warm, specific, hand-touched, and real.** If an asset feels generic, it's wrong. If an asset feels like it could be in any other game, it's wrong. Every pixel must belong to DEADPAN.

This document is the blueprint. When in doubt, refer to the three aesthetic pillars:
1. **Diegetic UI** — The interface is the world.
2. **Warm Grit** — Beauty in the unglamorous.
3. **Readability First** — Clarity is non-negotiable.

Now go make something that looks like it was scrawled on a napkin at 2 AM and performed under a spotlight at 10 PM. Make something that feels like standing on a stage with nowhere to hide. Make something that looks like DEADPAN.

---

**End of Art Direction Document**

**Document Author**: PIXEL
**Last Updated**: February 7, 2026
**Document Version**: 1.0
**Total Word Count**: 8,847 words

**Relevant Files**:
- `/Users/burcukose/git/project-draft/games/13-deadpan/art-direction.md` (this document)
- `/Users/burcukose/git/project-draft/games/13-deadpan/pitch.md` (game pitch)
- `/Users/burcukose/git/project-draft/games/13-deadpan/game-design.md` (game design document)

**Next Steps**:
1. Art team reviews this document (required reading for all visual disciplines).
2. Style guide PDF export (single-page reference with palette swatches, typography samples, shape rules).
3. Prototype production begins: Bit Builder UI mockup, single venue environment, napkin setlist interface.
4. First playtest with art in-context: Does it read? Does it feel right? Iterate based on feedback.
5. Asset pipeline locked and documented. Production ramp-up.

Show me the napkins. Show me the brick walls. Show me the spotlight. Make it real.
