# DEADPAN — Sound Design Document

**Sound Designer & Composer**: ECHO
**Status**: Production-ready sound design document
**Target Platforms**: PC (Steam), Nintendo Switch, Mobile (iPad)

---

## 1. Sonic Identity Statement

**DEADPAN sounds like the room you're trying to win.**

Every comedy club has a frequency. Not the frequency of laughter — the frequency of *waiting to laugh*. The hum of a neon sign filtering through brick and drywall. The clink of ice in a glass held by someone deciding whether you're funny. The friction of a dozen conversations dissolving as the spotlight hits. That pre-laugh silence — charged, dangerous, alive — is the keynote of this game.

Audio IS game feel. In DEADPAN, you don't just see the audience react. You *hear* the room temperature change. A cold room has weight, texture, resonance. A hot room vibrates. The difference between bombing and killing is sonic before it's visual. Close your eyes during a set and you'll know exactly how you're doing. That's the design target.

The soundscape is diegetic, intimate, reactive. Every sound belongs to the comedy world. No orchestral swells. No generic UI blips. If a sound doesn't exist in a green room, a dive bar, or a theater at 11 PM on a Tuesday, it doesn't exist in this game.

**Core sonic principles:**

1. **The room is an instrument.** Ambiance shifts dynamically based on crowd state. A disengaged crowd sounds different than a primed crowd. The same venue at Tier 1 and Tier 4 has different acoustic character.

2. **Silence is a sound design choice.** In comedy, silence is the worst sound. The game weaponizes it. A bombed joke is followed by 2.4 seconds of suffocating quiet — long enough to feel it in your chest.

3. **Laughter is a spectrum, not a binary.** Polite chuckles, explosive cackles, surprised gasps, groans, the rolling wave of a room losing it — each has distinct sonic texture. The Laugh Meter is visual, but the audio tells you *why* they're laughing.

4. **Performance is performative.** The player character's voice during sets is deliberately lo-fi, filtered through a stage mic. It's not clean studio VO. It's a human being in a room with an SM58 and bad monitoring. You hear the proximity effect when they lean in. You hear the plosives they didn't control. You hear the nerves.

5. **The city breathes around you.** Between sets, the game world has ambient life. Late-night traffic. Muffled comedy from the next room. The hiss of a radiator. A siren three blocks over. The soundscape says: this world exists when you're not performing. You're one comedian in a city full of rooms.

---

## 2. Sonic Palette

**Warm, gritty, hyper-specific.**

The palette is built from three sonic layers, each with its own production philosophy:

### 2.1 The Room (Foundation Layer)

The physical acoustic space. Every venue has a unique IR (impulse response) that defines its reverb character, frequency response, and spatial signature.

**Sonic characteristics:**
- **Dive Bar Open Mic**: Boxy, dark, 200-600 Hz mud, short RT60 (0.4s), lots of mid-frequency clutter from HVAC and kitchen bleed, slight room modes at 120 Hz and 340 Hz. Intimate but messy. Think: The Creek and The Cave (Queens), The Slipper Room (Lower East Side). Dry as hell. No natural reverb. Every laugh is direct, unforgiving.

- **Comedy Club (Tier 2-4)**: Mid-sized brick room, 0.9-1.2s RT60, warm low-mid buildup (150-400 Hz from bodies and upholstery), slight high-frequency roll-off above 8 kHz. The room "holds" laughter — a good laugh sustains for 1.2-2 seconds after the initial trigger. Think: The Comedy Cellar, The Comedy Store Main Room, Cap City Comedy Club. The sound wraps around you.

- **Theater (Tier 5-6)**: Large acoustic space, 1.6-2.1s RT60, balanced frequency response, pronounced early reflections (40-80ms), diffuse late reverb. Laughter becomes orchestral here — individual voices blur into a collective roar. Think: Beacon Theatre, The Wilbur, Town Hall. The room amplifies momentum. When it's hot, it's a cathedral of noise.

**Production approach:**
Record/synthesize unique IRs for 8-10 key venues. Use convolution reverb to place all diegetic sound (laughter, crowd murmur, stage audio) within each venue's acoustic signature. The player should be able to close their eyes and distinguish a dive bar from a theater by reverb alone.

**Reference tracks:**
- The ambient room tone from *Seinfeld* (the Comedy Cellar has a sound)
- The acoustic space in *The Comedian* (2016 film) — you hear the room's personality
- The dry, claustrophobic club sound in *Louie* (Season 1, Episode 1) — no reverb, all proximity

### 2.2 The Crowd (Dynamic Layer)

The living, reactive audience. Laughter is the melody. Murmur is the bassline. Silence is the rest.

**Sonic characteristics:**

Laughter taxonomy (mapped to Crowd Engine reaction tiers):

| Reaction Tier | Sonic Description | Frequency Range | Dynamic Range | Duration |
|---|---|---|---|---|
| **Silence** (0.0-0.15) | Ambient room tone only. Coughs. Glass clinks. Someone shifting in their seat. The absence is the sound. | 80-4000 Hz (room noise) | -50 to -35 dBFS | N/A |
| **Polite Smile** (0.16-0.30) | Nasal exhales. Single "heh" vocalizations. No sustained phonation. Tight, controlled, socially obligatory. | 400-2500 Hz | -40 to -30 dBFS | 0.3-0.6s |
| **Chuckle** (0.31-0.50) | Short burst laughter. "Ha" or "huh" with slight pitch variation. Still controlled. Individual voices distinguishable. | 250-3500 Hz | -32 to -20 dBFS | 0.6-1.2s |
| **Solid Laugh** (0.51-0.70) | Full phonated laughter. "Ha-ha-ha" with rhythmic pulsing. Voices start to blend. The room "agrees." | 150-5000 Hz | -25 to -15 dBFS | 1.2-2.0s |
| **Big Laugh** (0.71-0.85) | Explosive, involuntary. High-frequency bursts (sharp intakes, shrieks), full-body engagement, clapping starts to emerge. Slight chaotic phasing as laugh timing desynchs across the room. | 120-8000 Hz | -18 to -8 dBFS | 2.0-3.5s |
| **Eruption** (0.86-0.95) | The room breaks. Overlapping laughter creates dense texture, harmonic buildup in 200-600 Hz from collective vocal energy, clapping becomes rhythmic, some people gasping for air (audible inhales). Peak emotional release. | 80-12000 Hz | -12 to -3 dBFS | 3.5-6.0s |
| **Standing Ovation** (0.96-1.0) | Laughter + sustained applause + vocal whoops. Laughter decays but applause sustains. The room is ON FIRE. This is the sound of victory. | 60-16000 Hz (full spectrum) | -8 to 0 dBFS | 6.0-12.0s (applause sustains longer than laugh) |

**Crowd murmur states** (ambient bed beneath laughter):

- **Disengaged** (Momentum < 0.7): Quiet conversations, glasses clinking, chairs creaking, phones buzzing (subtle). Attention is diffuse. You're fighting for focus. High-frequency content above 4 kHz (whispers, silverware).

- **Primed** (Momentum 0.7-1.0): Conversation drops, bodies lean forward, ambient noise floor drops -6 dB. The room is LISTENING. Only essential sounds remain (breathing, fabric rustle).

- **Hot** (Momentum 1.0-1.5): Post-laugh ambient hum — residual vocal energy, people catching their breath, excited murmurs between jokes. The room vibrates. Low-frequency bloom at 150-300 Hz from collective body presence.

**Heckler audio:**
Distinct from laughter. Aggressive, pointed vocal interruptions from a localized spatial position (stereo or surround placement). Male and female heckler voice variants with varying drunkenness (slurred timing, pitch instability). Cuts through ambient mix at -10 to -5 dBFS — loud enough to *feel* like a violation of the performance space.

**Production approach:**
Record modular laughter samples (individual laughs, small group laughs, large group laughs) across demographic types. Build a granular laughter synthesizer that blends samples based on:
- Crowd size (determines density)
- Reaction tier (determines intensity)
- Archetype composition (Comedy Nerds laugh differently than Bachelor Parties — nerds are nasal, tight, high-frequency; bachelor parties are loud, open, low-frequency)
- Venue acoustics (convolve output through venue IR)
- Momentum state (adds low-frequency energy to hot crowds)

The synthesizer output should be non-repetitive across hundreds of sets. No two laughs sound identical.

**Reference tracks:**
- Live audience recordings from *Kill Tony* podcast (real, unpolished, reactive laughter with full dynamic range)
- The crowd sound design in *The Marvelous Mrs. Maisel* (especially Gaslight Café scenes — intimate crowd dynamics)
- Actual comedy club ambiance field recordings (The Comedy Store green room documentary has incredible room tone)

### 2.3 The Human (Narrative Layer)

The player character's voice, breath, mic handling, nervous tics. The body betrays performance anxiety. The audio reflects it.

**Sonic characteristics:**

**Player voice during performance:**
- Filtered through SM58 dynamic mic model (presence peak at 4-5 kHz, proximity bass boost below 200 Hz when close, roll-off above 12 kHz)
- Subtle compression (4:1 ratio, fast attack) to mimic house PA system
- Room acoustics applied (early reflections from stage monitors, reverb tail from venue IR)
- Performance state affects delivery:
  - **Confident state** (3+ consecutive solid laughs): Voice is relaxed, timing is controlled, breaths are inaudible, mic technique is clean
  - **Nervous state** (opening of set, post-bomb): Voice has slight tremor (1-3 Hz LFO on pitch), faster speech rate, audible inhales, occasional mic plosives (uncontrolled plosive bursts at 80-150 Hz), longer pauses
  - **Bombing state** (2+ consecutive silence reactions): Voice becomes quieter (player is shrinking), speech rushes (desperate pacing), mouth clicks audible (dry mouth from adrenaline), mic handling noise (grip shifts from tension)

**Player breath:**
The space between jokes. Audible on stage mic during silence. Deep breath before setlist closer. Exhale after a bomb. The breath tells the emotional story the joke can't.

**Footsteps and stage movement:**
Footsteps on stage (wood creak for small clubs, muted thud for carpeted theaters). Mic stand adjustment (metal clink, slight feedback whine if handled poorly). Cable drag across floor. These are subtle but they ground the player in the physical space.

**Production approach:**
Modular VO system with performance state parameters. Record player dialogue in two emotional states (confident, nervous). Layer breath samples (calm, anxious, post-exertion) that trigger based on performance context. Mic handling foley recorded from actual stage mics.

**Reference tracks:**
- Stand-up specials recorded in single takes with minimal mixing: *Bill Burr: Paper Tiger* (you hear the room, the mic, the breathing)
- The vocal intimacy of *Bo Burnham: Inside* (especially the whispered moments — proximity, breath, vulnerability)
- Any live comedy album from the 70s-80s (George Carlin, Richard Pryor) where the recording is "too close" — you hear EVERYTHING

---

## 3. SFX List (Organized by Category)

All SFX are diegetic. If it doesn't exist in the comedy world, it doesn't exist in the game.

### 3.1 UI / Meta Sounds

**Design philosophy:** UI sounds are physical interactions with objects in the comedy world. No beeps. No whooshes. Everything is tactile.

| SFX Name | Description | Trigger | Sonic Character |
|---|---|---|---|
| **Napkin_SetlistWrite_01-08** | Pen scratching on napkin as setlist is written | Dragging joke into setlist slot | Dry, fibrous, intimate. Ballpoint on paper napkin. Close-mic'd. Slight pressure variation between strokes. 300-2500 Hz. |
| **CardSnap_BitBuilder_01-05** | Component card snapping into joke slot | Connecting Premise/Setup/Punchline in Bit Builder | Index card being placed on corkboard with slight adhesive stick. Papery impact + subtle friction. 500-4000 Hz transient. |
| **CorkboardPin_01-03** | Pushpin securing card to board | Confirming joke assembly | Metal pin pressing through paper into cork. Short metallic "tink" (8-12 kHz) + dull thud (200-600 Hz). |
| **PhoneBuzz_Notification_01-10** | Phone vibration for texts/notifications | Agent messages, rival updates, gig offers | iPhone vibration motor on wood table. Buzzy, sustained (0.4s), 150-400 Hz rattle. Variations for different table surfaces. |
| **PhoneSwipe_01-05** | Touch interaction with phone UI | Navigating career screen, reading messages | Finger sliding on glass with subtle squeaky friction. 2-6 kHz. Very quiet (-40 dBFS). |
| **NotebookPage_Turn_01-06** | Page turning in writing notebook | Navigating joke library | Thick paper page turn. Slightly muffled (notebook is closed partway). 400-3000 Hz rustle. |
| **NotebookPage_Rip_01-03** | Tearing page from notebook | Discarding/reworking joke | Paper tear with fibrous separation. Starts at 600 Hz, descends to 200 Hz as tear completes. Cathartic. |
| **PenClick_01-04** | Ballpoint pen clicking | Selecting joke component for editing | Classic pen click mechanism. Sharp transient (4-8 kHz) + spring resonance (1.2 kHz). |
| **Lighter_Flick_01-05** | Cigarette lighter flick (green room idle animation) | Ambient green room activity | Zippo-style lighter. Flint strike (broadband noise burst) + gas ignition (low whoosh at 80-300 Hz). |
| **CoffeeMug_Pickup_01-04** | Mug lifted from table | Idle/transition animation | Ceramic mug on wood table. Slight scrape (friction at 800-2000 Hz) + weight shift (low thud 100-250 Hz). |
| **CoffeeSip_01-05** | Drinking coffee | Player idle action in green room | Liquid sip + swallow. Intimate, close perspective. 200-1500 Hz wet mouth sounds (subtle, not gross). |
| **GreenRoomDoor_Open_01-03** | Green room door opening | Transitioning from green room to stage | Old door hinge creak (rusty, 400-1200 Hz sweep) + door hitting doorstop (dull thud 80-200 Hz). |
| **GreenRoomDoor_Close_01-03** | Green room door closing | Returning from stage | Door close with latch click (2-5 kHz metallic snap) + muffled thud from door seal. |
| **Barstool_Creak_01-06** | Barstool movement | Sitting in green room, adjusting on stage | Wood/metal stool creak. Weight shift causes slow pitch bend (200-600 Hz). Sustained (0.6-1.2s). |
| **Spotlight_On_01-02** | Stage spotlight turning on | Start of performance | Electrical relay click (4 kHz transient) + halogen bulb warm-up hum (120 Hz + harmonics at 240/360/480 Hz, fades in over 0.8s). |
| **Spotlight_Off_01-02** | Stage spotlight turning off | End of performance | Relay click + descending hum (120 Hz fading out over 1.2s). Slight bulb filament "tick" as it cools (random transients 2-6 kHz). |
| **Microphone_Feedback_Short_01-04** | Brief mic feedback spike | Mic handling error during nervous performance state | Sharp, pure tone (varies: 800 Hz, 1.2 kHz, 2.5 kHz, 4 kHz) lasting 0.2-0.5s. Cuts through mix at -8 dBFS. Painful. |
| **Microphone_Tap_01-03** | Tapping mic to test | Pre-set mic check animation | Low-frequency thud (80-150 Hz) + slight distortion from proximity effect. "Is this thing on?" |
| **Applause_Sustained_Small_01-03** | Small crowd applause (20-80 people) | Post-set success at Tier 1-2 venues | Rhythmic clapping, slightly uncoordinated (50-80 BPM variance). Full spectrum but concentrated 800-4000 Hz. Decays naturally after 3-6s. |
| **Applause_Sustained_Large_01-03** | Large crowd applause (200-2000+ people) | Post-set success at Tier 4-6 venues | Dense, massive clapping with low-frequency body (200-600 Hz from collective movement). Full spectrum wash. Sustains 8-15s. |
| **WalkOut_FootstepsReceding_01-03** | Audience member walking out mid-set | Crowd member leaves during bomb | Footsteps moving away (descending volume + increasing high-frequency roll-off for distance), chair scrape, door open/close. Spatially positioned. Devastating. |

**Total UI/Meta SFX**: 87 individual samples (with variations)

### 3.2 Venue Ambiance (Looping Beds)

Each venue has a unique ambient soundscape that loops seamlessly, providing the acoustic foundation for all performances.

| Venue Type | Ambiance Description | Frequency Content | Dynamic Range | Loop Length |
|---|---|---|---|---|
| **DiveBar_Ambiance_Loop** | HVAC hum, muffled kitchen clatter, street traffic bleed through walls, occasional glass clink, low conversation murmur from bar area, neon sign buzz | 60-4000 Hz, concentrated 80-800 Hz | -45 to -30 dBFS | 120s |
| **ComedyClub_Ambiance_Loop** | Crowd pre-show murmur (50-150 people), bar service (distant), HVAC (subtle), occasional laugh from previous set bleed | 80-6000 Hz, vocal range 200-2500 Hz prominent | -40 to -25 dBFS | 180s |
| **Theater_Ambiance_Loop** | Large room tone (reverb tail constant presence), audience settling (programs rustling, seats creaking), very subtle HVAC, distant lobby activity | 40-8000 Hz, diffuse and spacious | -50 to -35 dBFS | 240s |
| **OpenMic_CoffeeShop_Ambiance** | Espresso machine (steam bursts, grinder), conversation murmur, acoustic guitar tuning (someone waiting their turn), door chime | 100-8000 Hz, broadband noise from machines | -42 to -28 dBFS | 90s |
| **GreenRoom_Ambiance_Loop** | Muffled stage audio through wall (voices intelligible but low-passed at 800 Hz), radiator hiss, fluorescent light buzz (120 Hz hum + 7 kHz whine), distant city ambiance through window | 60-8000 Hz, heavy low-mid presence | -48 to -32 dBFS | 150s |
| **City_Exterior_Night_Loop** | Late-night traffic (distant), siren (occasional, 1-2 per loop), wind through alley, steam vent, muffled music from adjacent bar, footsteps on wet pavement | 40-10000 Hz, low-frequency traffic rumble 60-200 Hz | -50 to -30 dBFS | 180s |

**Ambiance layering system:**
Each venue ambiance has three layers:
1. **Static bed** (constant room tone, HVAC, venue-specific signature sounds)
2. **Dynamic layer** (crowd murmur that shifts based on Momentum state, adjusted in real-time)
3. **Event layer** (one-shot sounds that trigger randomly: glass clink every 8-15s, door open/close, cough, chair creak)

Layers are mixed based on game state. During performance, Static + Dynamic dominate. During green room scenes, all three layers active with Event layer more prominent (the world feels more alive when you're NOT performing).

**Total Ambiance Assets**: 6 looping beds (each with 3-layer stems) = 18 files + 40 one-shot event sounds

### 3.3 Laughter & Crowd Reactions

The most critical SFX category. These are modular samples that feed the granular laughter synthesizer.

**Sample library structure:**

| Sample Category | Count | Description |
|---|---|---|
| **Individual_Laugh_Chuckle_Male** | 50 | Single male chuckles, varying ages and vocal qualities |
| **Individual_Laugh_Chuckle_Female** | 50 | Single female chuckles, varying ages and vocal qualities |
| **Individual_Laugh_Full_Male** | 60 | Full "ha-ha-ha" male laughter, 1-3 second duration |
| **Individual_Laugh_Full_Female** | 60 | Full female laughter, 1-3 second duration |
| **Individual_Laugh_Explosive_Male** | 30 | Uncontrolled, loud male laughter with snorts/gasps |
| **Individual_Laugh_Explosive_Female** | 30 | Uncontrolled, loud female laughter with snorts/gasps |
| **Group_Laugh_Small_3-5ppl** | 40 | Small group laughter (captures natural timing variation) |
| **Group_Laugh_Medium_10-20ppl** | 30 | Medium group laughter (starts to blend into collective) |
| **Group_Laugh_Large_50+ppl** | 20 | Large group laughter (full texture, harmonic buildup) |
| **Crowd_Groan_Collective** | 15 | Audience groaning at a bad pun or dark joke (reaction, not rejection) |
| **Crowd_Gasp_Surprise** | 12 | Sharp collective inhale after shocking punchline |
| **Crowd_Awkward_Silence_RT** | 8 | Room tone captures during silence — you hear the LACK of reaction |
| **Applause_Clap_Single** | 40 | Individual hand claps for building applause textures |
| **Applause_Rhythmic_Slow** | 10 | Slow clap (can be mocking or genuine based on context) |
| **Whoop_Celebration_Male** | 20 | Vocal whoops and celebration shouts (male) |
| **Whoop_Celebration_Female** | 20 | Vocal whoops and celebration shouts (female) |

**Total Laughter/Reaction Samples**: 495 individual files

**Granular synthesis approach:**
The Crowd Engine requests a laughter output based on:
- Reaction tier (0.0-1.0 scale)
- Crowd size (8-3000 people)
- Archetype composition (different archetypes = different laugh timbres)
- Venue acoustics (IR applied to output)

The synthesizer:
1. Selects 3-12 individual laugh samples (count scales with crowd size)
2. Randomly time-offsets each sample by 0-300ms (natural desynchronization)
3. Adjusts pitch of each sample by -8% to +8% (prevents robotic uniformity)
4. Adjusts gain of each sample based on archetype preferences (Comedy Nerds laugh quieter than Bachelor Parties)
5. Blends group laugh samples underneath for density (if crowd size > 30)
6. Convolves output through venue IR
7. Applies Momentum-based EQ (hot crowds get +3 dB low-frequency boost at 150-300 Hz)

Result: Every laugh is unique. No repetition fatigue.

### 3.4 Performance Vocal & Foley

Player character sounds during performance.

| SFX Name | Description | Trigger | Sonic Character |
|---|---|---|---|
| **Breath_Inhale_Calm_01-10** | Calm breathing between jokes | Performance state: confident | Nasal inhale, subtle, 200-4000 Hz, -35 dBFS |
| **Breath_Inhale_Nervous_01-10** | Anxious breathing | Performance state: nervous | Sharper, faster inhale with slight tremor, 300-6000 Hz, -30 dBFS |
| **Breath_Exhale_Relief_01-06** | Exhale after big laugh | Post-eruption reaction | Long, relaxed exhale, 150-3000 Hz, -32 dBFS |
| **Breath_Exhale_Defeat_01-06** | Exhale after bomb | Post-silence reaction | Short, deflated exhale with slight vocal fry, 100-2000 Hz, -28 dBFS |
| **MouthClick_Dry_01-08** | Dry mouth click | Performance state: bombing | High-frequency mouth noise, 4-10 kHz, -25 dBFS, intimate and uncomfortable |
| **Swallow_Nervous_01-05** | Audible swallow | Performance state: nervous, pre-punchline | Wet throat sound, 200-2000 Hz, -30 dBFS |
| **Footstep_Stage_Wood_01-08** | Footsteps on stage | Player movement during set | Wood creak, 200-800 Hz, slight resonance, -28 dBFS |
| **Footstep_Stage_Carpet_01-08** | Footsteps on carpeted stage | Player movement during set (theaters) | Muffled thud, 100-600 Hz, -32 dBFS |
| **MicStand_Adjust_01-04** | Adjusting mic stand height | Pre-set preparation | Metal sleeve friction (600-3000 Hz) + locking clamp click (4 kHz transient) |
| **MicStand_Bump_01-03** | Accidentally bumping mic stand | Performance error during nervous state | Low-frequency thud (80-200 Hz) through mic + slight feedback whine (varies) |
| **Cable_Drag_01-04** | Mic cable dragging on floor | Player movement with handheld mic | Fabric/rubber scrape on wood/carpet, 150-1500 Hz, subtle |

**Total Performance Vocal/Foley SFX**: 73 individual samples

### 3.5 Environmental & Scene Transition

Sounds that establish place and transition between game states.

| SFX Name | Description | Context |
|---|---|---|
| **Taxi_Horn_Distant_01-05** | Car horn, distant | City exterior transition |
| **Subway_Rumble_Pass_01-03** | Subway passing underground | City exterior (NYC-specific) |
| **Rain_Light_OnWindow_Loop** | Light rain on window | Green room ambient (weather variant) |
| **Siren_Police_Distant_01-04** | Police siren fading past | City exterior night |
| **Bar_Crowd_Walla_Interior** | Bar crowd ambiance | Venue lobby, pre/post-show |
| **Jukebox_MuffledMusic_01-03** | Muffled jukebox from adjacent room | Dive bar venues (low-passed music, 200-2500 Hz) |
| **Kitchen_Clatter_Distant** | Restaurant kitchen sounds | Dive bar venues with food service |
| **Cash_Register_Ding_01-02** | Cash register | Bar transactions (ambient detail) |
| **Door_Exterior_Heavy_Open/Close** | Venue exterior door | Entering/exiting venue |
| **Stairs_Creak_Ascend/Descend** | Staircase to basement club | Specific venue transitions (The Cellar, etc.) |

**Total Environmental SFX**: 35 individual samples

---

**TOTAL SFX COUNT: 808 individual samples + 18 ambiance loops**

---

## 4. Music Brief

### 4.1 Style & Emotional Intent

DEADPAN's music is not a soundtrack. It's the city's exhale. The score lives in the moments between performances — the green room at 1 AM, the apartment at sunrise after a great set, the long subway ride home after bombing. The music is *reflective, melancholic, intimate, and unflinchingly human*.

**Core musical identity:**
Late-night jazz piano meets lo-fi hip-hop beats meets the quiet hum of a city that never sleeps but sometimes pauses to breathe. Think Vince Guaraldi's *A Charlie Brown Christmas* played through a cassette deck in a Brooklyn apartment. Think the introspective warmth of Mac DeMarco's chord progressions. Think the nocturnal drift of Nujabes. The music understands that comedy is a lonely craft practiced in rooms full of people.

**Instrumentation:**
- **Primary**: Piano (upright, slightly out of tune, recorded close with felt hammers audible), electric piano (Rhodes, warm and chorused), synthesizer pads (analog, slightly detuned, Juno-60 character)
- **Secondary**: Upright bass (acoustic, played with fingers, intimate proximity), brushed drums (jazz kit, very light touch, more texture than rhythm), field recordings (vinyl crackle, rain, distant traffic, train rumble — used as texture beds)
- **Accent**: Muted trumpet (Harmon mute, Miles Davis-esque), tenor saxophone (breathy, late-night blue), electric guitar (clean Fender tone with spring reverb, occasional chords, never shredding)
- **Forbidden**: Orchestral strings (too cinematic), aggressive electronic production (too modern/sterile), vocals (the player's internal voice is the only voice that matters), anything that feels "epic" (comedy is not epic; comedy is small and sharp)

**Tonal palette:**
- **Harmony**: Jazz-influenced (7th chords, 9th chords, occasional modal ambiguity), major keys with melancholic color tones (major 7th, added 6th), minor keys that feel searching rather than sad
- **Rhythm**: Slow to mid-tempo (65-95 BPM), swing feel or straight feel depending on context, emphasis on space and breath between phrases
- **Melody**: Simple, singable, slightly fragmented (phrases that trail off, questions without answers), often centered in the mid-register (comfortable, conversational range)
- **Production**: Lo-fi aesthetic (vinyl crackle, tape saturation, slight wow/flutter, room tone audible), mono or narrow stereo field for intimacy, dynamic range preserved (no brick-wall limiting — the music breathes)

**Musical references:**
- *Vince Guaraldi Trio* — "Cast Your Fate to the Wind" (the piano tone, the rhythmic space)
- *Nujabes* — "Feather" (the lo-fi warmth, the melancholic hope)
- *Mac DeMarco* — "Chamber of Reflection" (the synth pads, the introspective drift)
- *Bill Evans Trio* — "Peace Piece" (the harmonic suspension, the patience)
- *Mort Garson* — "Plantasia" (the analog synth character, the oddly comforting strangeness)
- *Cowboy Bebop OST* — "Rain" (the late-night jazz melancholy)

### 4.2 Adaptive Music System

The music responds to game state, emotional context, and player progression. It is never static.

**Music Zones & Emotional States:**

| Zone | Emotional State | Musical Character | Adaptive Parameters |
|---|---|---|---|
| **Main Menu** | Contemplative, open | Solo piano, slow tempo (68 BPM), open 5th intervals, no drums. The question: "Do I still have it?" | Static. Loops seamlessly. 3:20 duration. |
| **Apartment (Writing)** | Intimate, focused | Piano + subtle synth pad, field recordings (rain or city ambiance), no drums. Creative solitude. | Volume decreases slightly when Bit Builder is active (focus cue). Tempo imperceptibly slows to 62 BPM when player has been idle >30s (fatigue cue). |
| **Green Room (Pre-Show)** | Anticipation, nerves | Electric piano + brushed drums (entering on loop 2), upright bass (subtle), muted trumpet (occasional melodic phrase). The tension builds. | Drum presence increases as showtime approaches. Final 60 seconds before stage: high-pass filter sweeps upward from 200 Hz to 800 Hz, creating tension. Cuts to silence 3 seconds before stage transition. |
| **Green Room (Post-Show, Success)** | Relief, euphoria | Rhodes piano + upright bass, drums (light swing feel), major key, slightly faster tempo (82 BPM). The exhale. | Melody is more present, harmonies are richer (added 9th chords). If player achieved Eruption-level reactions during set, saxophone enters with a warm countermelody on loop 3. |
| **Green Room (Post-Show, Bomb)** | Defeat, isolation | Solo piano, minor key, slower tempo (58 BPM), long silences between phrases. The longest walk. | Extended silence after final phrase (8 seconds before loop). Reverb tail is longer (3.5s), creating emptiness. If player bombed badly (avg reaction < 0.2), piano tone is slightly detuned (+8 cents), creating unease. |
| **City Exterior (Night)** | Wandering, searching | Full ensemble (piano, bass, drums, synth pad), medium tempo (75 BPM), drifting between major and minor. The city as companion. | Layers in: Bass and drums fade in after 30s, synth pad enters at 60s, creating a sense of journey. If player is walking after a success, occasional trumpet flourishes. If walking after failure, no trumpet — just rhythm section. |
| **Career Screen (Mid-Tier)** | Ambition, momentum | Electric piano + bass + light drums, steady tempo (80 BPM), driving but not aggressive. The climb. | If player's REP is increasing session-over-session, add melodic motif (4-note phrase) that repeats on loop 2. If REP is stagnant, motif doesn't appear — the music feels aimless. |
| **Career Screen (Late-Tier)** | Reflection, stakes | Full ensemble + field recordings (vinyl crackle, distant laughter from archival comedy recordings). The question shifts from "Can I make it?" to "What does 'making it' mean?" | Harmony becomes more complex (sus chords, modal mixture). Tempo slightly slower (72 BPM). If player has high Authenticity (>75), the melody is confident, resolved. If low Authenticity (<40), the melody is fragmented, unresolved. |
| **The Special (Setup/Performance)** | Existential focus | Silence, then minimal piano (single-note pulse), then gradually building ensemble. This is the test. | Music begins 60 seconds before performance. Sparse, tense. As the set progresses and reactions are positive, layers add: bass at 25% setlist completion, drums at 50%, full ensemble at 75%. If bombing, layers never arrive — just the pulse remains. If crushing, final joke is followed by music swelling into the post-show cue. |
| **Ending (Victory)** | Bittersweet triumph | Full ensemble, major key, warm and resolved but not triumphant. The player made it. Now what? | Melody resolves on tonic but harmony includes a suspended 4th — the resolution is real but the question remains. 4:40 duration with a long reverb tail (6 seconds). Field recordings of distant applause and city ambiance fade in under the final chord. |
| **Ending (Artistic Path)** | Integrity, solitude | Solo piano, minor key that shifts to major in the final 8 bars. The player chose authenticity over empire. The resolution is internal. | Slow tempo (60 BPM). Melody is simple and singable — a lullaby for the lonely artist. Final chord is a major 7th (hopeful but unresolved). 3:50 duration. |

**Transition Logic:**

Music crossfades between zones using beat-matched transitions (if rhythmic) or reverb-tail blends (if ambient). Transition duration: 4-8 seconds. No hard cuts unless dramatically necessary (e.g., the silence before stepping on stage).

**Dynamic Layering System:**

Each music zone is composed of 3-5 stems:
1. **Foundation** (piano or bass, always present)
2. **Harmony** (synth pads, additional keys, conditional)
3. **Rhythm** (drums, conditional based on emotional state)
4. **Melody** (trumpet, sax, lead voice, conditional based on player success/state)
5. **Texture** (field recordings, vinyl crackle, ambient bleed, always subtle)

Stems are mixed in real-time based on adaptive parameters. The player never hears the same mix twice.

**Total Music Track Count:**
- 12 primary zone cues (3-5 stems each = 48 stem files)
- 8 transition stingers (short musical phrases for moments like tier unlock, rival encounter, viral moment)
- 2 endings (4 stems each = 8 stem files)

**Total Music Assets: 64 files (42 minutes of unique music content)**

### 4.3 Musical Motifs & Themes

**The Player's Theme (4-note motif):**
A simple ascending phrase: `D - F - A - C` (Dm7 arpeggio). Appears across multiple zones in different harmonic contexts. In the apartment, it's tender and searching. In the career screen, it's driving and hopeful. In the ending, it's resolved and reflective. The motif is the player's internal voice — it evolves as they evolve.

**The City's Theme (2-bar chord progression):**
`Fmaj7 - G7 - Am7 - Em7` (I - II - iii - vii in F major). Represents the comedy world — impermanent, cyclical, always in motion. Appears in city exterior cues and career screen music. The progression never resolves to tonic — it cycles endlessly, just like the grind.

**The Moment Theme (stinger):**
A single suspended chord (Dsus4) that blooms and decays. Plays when the player achieves a major milestone: first headliner slot, viral moment, special announcement, tier unlock. Duration: 4.5 seconds with long reverb tail. The sound of a door opening.

---

## 5. Adaptive Audio System Design

The audio engine is the invisible director, conducting the soundscape in response to gameplay.

### 5.1 Real-Time Laughter Synthesis

**System: Granular Laughter Engine (GLE)**

**Inputs (from Crowd Engine):**
- Reaction tier per audience cluster (0.0-1.0 float)
- Audience cluster size (int)
- Archetype ID per cluster (enum: Comedy Nerds, Date Night, Bachelor Parties, etc.)
- Venue ID (enum)
- Momentum state (float, 0.0-2.0)
- Fatigue state per cluster (float, 0.0-1.0)

**Processing:**
1. For each cluster:
   - Map Reaction Tier to laughter sample pool (Silence, Chuckle, Solid Laugh, etc.)
   - Sample count = f(cluster_size): 8 people = 2-3 samples, 50 people = 6-10 samples, 200+ people = 8-12 samples + group samples
   - Select samples from pool randomly (weighted by Archetype preferences)
   - Apply per-sample randomization: time offset (0-300ms), pitch shift (-8% to +8%), gain adjust (-6 dB to +3 dB)
   - Blend group laugh samples underneath (if cluster size > 30)
2. Convolve cluster output through venue IR (based on Venue ID)
3. Apply Momentum-based EQ:
   - If Momentum > 1.0 (hot crowd): +3 dB shelf boost at 150-300 Hz
   - If Momentum < 0.7 (cold crowd): -2 dB at 200-500 Hz (thin out the low-end warmth)
4. Apply Fatigue-based high-frequency roll-off:
   - Fatigue < 0.8: -1 dB per 0.1 fatigue decrease above 4 kHz (tired crowds lose energy in laugh overtones)
5. Spatialize cluster audio based on venue seating map (stereo or 5.1 surround)
6. Sum all cluster outputs, apply final limiter (ceiling at -1 dBFS), output to mix

**Performance target:** <5ms latency from Crowd Engine reaction trigger to audio output. The laughter must feel *instant*.

**Fallback:** If GLE fails or CPU budget exceeded, fallback to pre-rendered laughter samples (less variety, no synthesis). Graceful degradation.

### 5.2 Ambiance State Machine

**System: Dynamic Ambiance Mixer (DAM)**

**States:**
- **Venue_Idle** (venue ambiance, pre-show)
- **Venue_Primed** (crowd attention focused, murmur drops)
- **Venue_Hot** (post-laugh ambient hum, high energy)
- **Venue_Cold** (disengaged, murmur increases, ambient noise clutter)
- **GreenRoom_Alone** (solo ambiance, intimate)
- **GreenRoom_Busy** (multiple comics, higher activity)
- **City_Exterior**

**Transitions triggered by:**
- Game state change (entering/exiting venue, starting/ending set)
- Momentum state change (Crowd Engine passes threshold)
- Scene population (number of AI comedians in green room)

**Mixing logic per state:**

| State | Static Bed Volume | Dynamic Layer Volume | Event Layer Frequency |
|---|---|---|---|
| **Venue_Idle** | -18 dBFS | -22 dBFS (moderate murmur) | 1 event per 6-12s |
| **Venue_Primed** | -18 dBFS | -28 dBFS (murmur drops) | 1 event per 15-25s |
| **Venue_Hot** | -18 dBFS | -20 dBFS (excited hum) | 1 event per 5-10s |
| **Venue_Cold** | -18 dBFS | -16 dBFS (louder murmur, distraction) | 1 event per 4-8s |
| **GreenRoom_Alone** | -20 dBFS | N/A | 1 event per 20-40s |
| **GreenRoom_Busy** | -20 dBFS | -24 dBFS (conversation bleed) | 1 event per 8-15s |
| **City_Exterior** | -22 dBFS | -26 dBFS (distant activity) | 1 event per 10-20s |

**Crossfade duration:** 3-5 seconds between states (smooth, no jarring cuts).

### 5.3 Performance Anxiety Audio Modulation

**System: Player State Audio Filter (PSAF)**

Modulates player voice and breath based on performance state.

**Performance States:**
- **Confident** (3+ consecutive reactions >0.5)
- **Neutral** (default)
- **Nervous** (set opening, or post-bomb recovery)
- **Bombing** (2+ consecutive reactions <0.2)

**Audio modulation per state:**

| State | Voice Pitch | Voice Tremor (LFO) | Breath Rate | Breath Volume | Mic Handling Noise |
|---|---|---|---|---|---|
| **Confident** | Baseline (0 cents) | None | 12 breaths/min | -38 dBFS | Rare (5% chance per phrase) |
| **Neutral** | Baseline | None | 14 breaths/min | -35 dBFS | Occasional (10% chance) |
| **Nervous** | +2 cents (slight tension) | 1.5 Hz, ±3 cents | 18 breaths/min | -30 dBFS | Frequent (20% chance) |
| **Bombing** | -3 cents (shrinking) | 2.5 Hz, ±5 cents | 22 breaths/min (rapid) | -28 dBFS (audible panic) | Very frequent (35% chance) |

**Breath samples** are dynamically selected from the appropriate pool (calm, nervous, anxious) and inserted into pauses between joke delivery. Timing is procedural based on speech pacing.

**Mic handling noise** (plosives, stand bumps, cable drag) triggers probabilistically based on state. The player physically manifests nervousness through audio artifacts.

### 5.4 Music Mixing & Priority System

**Mix Hierarchy** (see Section 6 for full details), but music-specific ducking:

**Music volume modulation:**
- **During performance:** Music is silent (no score during sets — the crowd is the music)
- **Pre-performance (final 60s):** Music builds tension, then cuts to silence 3s before stage
- **Post-performance:** Music fades in over 4s, reaches full volume after 8s
- **Apartment/Green Room:** Music is present but mixed at -24 to -18 dBFS (background, not foreground)
- **Career Screen:** Music is more prominent, -18 to -12 dBFS
- **Key narrative moments (tier unlock, special announcement):** Music foreground, -12 to -6 dBFS, all other audio ducks -8 dB

**Adaptive mixing:**
If player is idle in apartment for >90 seconds, music volume increases +4 dB and frequency content shifts (slight high-pass filter at 150 Hz lifts, allowing bass to bloom). This creates a subtle "lean in" effect — the music is waiting with you.

### 5.5 Spatial Audio Design

**Stereo Implementation (Primary Platform: PC/Switch):**

Audience clusters are positioned in the stereo field based on venue seating layout:
- Small venues (Tier 1-2): Narrow stereo image (70% center, 30% L/R spread). Intimate, direct.
- Medium venues (Tier 3-4): Moderate spread (50% center, 50% L/R). Balanced.
- Large venues (Tier 5-6): Wide spread (30% center, 70% L/R). Immersive, enveloping.

Hecklers are hard-panned to L or R based on their table position. The spatial violation is part of the impact — they're not just loud, they're *over there*, disrupting the center-stage symmetry.

Footsteps, mic handling, and breath are centered (player POV).

Ambiance is stereo-wide with slight decorrelation (0-20ms delay between L/R channels for spaciousness).

**5.1 Surround Implementation (Stretch Goal):**

If budget and platform support:
- Audience laughter uses full 5.1 field (clusters spatially positioned based on seating)
- Ambiance uses surrounds for immersion (HVAC, distant stage audio in rears)
- Music remains stereo (L/R front channels only)
- Player voice/breath/foley centered (front center channel)

**Binaural Implementation (Mobile/Headphone Players):**

HRTF processing applied to audience clusters and ambiance for headphone users. Creates 3D spatial positioning without surround hardware. Critical for mobile platform where headphone use is assumed.

---

## 6. Mix Hierarchy

Audio priority system ensuring clarity and emotional impact.

### 6.1 The Frequency Spectrum Map

Every sound has a home frequency. Overlaps are minimized through surgical EQ and dynamic ducking.

| Frequency Range | Primary Occupants | Mixing Strategy |
|---|---|---|
| **Sub-bass (20-60 Hz)** | Venue room tone, large crowd low-frequency body, music bass (upright bass) | Sparse. Only present in large venues (Tier 4+). Music bass is sidechain-compressed slightly when crowd eruptions occur (-2 dB duck). |
| **Bass (60-250 Hz)** | Crowd murmur body, piano low register, footsteps, door thuds, audience movement | Controlled. Crowd murmur is high-passed at 80 Hz (except Tier 5+ venues). Music low-mids duck -3 dB during crowd laughter to prevent mud. |
| **Low-mids (250-600 Hz)** | Laughter fundamental range, male voice, piano mid-register, Rhodes, upright bass mid-range | THIS IS THE COMBAT ZONE. Laughter takes priority always. Music is notched -4 dB at 350-500 Hz during performances. Player voice is boosted +2 dB at 400 Hz (presence) to cut through. |
| **Mids (600-2500 Hz)** | Laughter overtones, female voice, player breath, piano upper-mid, synth pads, most UI sounds (pen scratch, card snap) | CLARITY RANGE. Laughter and player voice dominate. Music pads are rolled off -3 dB at 1-2 kHz during sets. UI sounds are mixed at -32 to -25 dBFS to remain audible but non-intrusive. |
| **Upper-mids (2.5-6 kHz)** | Laughter brightness, sibilance, high-frequency laugh bursts (shrieks, gasps), cymbal brushes, mouth clicks | PRESENCE AND EMOTION. High reactions (Eruption-tier) have significant energy here. Music trumpet/sax lives here but is mixed quietly (-28 dBFS) to avoid conflict. Mouth clicks during bombing are mixed louder (-25 dBFS) — discomfort is intentional. |
| **Highs (6-12 kHz)** | Applause transients, glass clinks, pen clicks, mic feedback, field recording air/crackle, synth shimmer | AIR AND SPACE. Sparse but essential for realism. Ambiance event sounds (glass clink, chair creak) occupy this range and are mixed at -38 to -30 dBFS. Feedback spikes cut through at -8 dBFS (intentionally jarring). |
| **Ultra-highs (12-20 kHz)** | Vinyl crackle texture, air conditioner hiss, distant cymbal shimmer | TEXTURE ONLY. Mixed at -45 to -35 dBFS. Subliminal. Creates "analog warmth" without cluttering. |

### 6.2 Priority Tiers (Real-Time Ducking System)

When the mix gets crowded, the priority system determines what ducks.

**Priority Tier 1 (NEVER ducks):**
- Player dialogue (joke delivery during performance)
- Heckler audio (must cut through — it's a violation)
- Critical UI audio (mic feedback, phone notification for agent call, tier unlock stinger)

**Priority Tier 2 (Ducks only for Tier 1):**
- Audience laughter (Solid Laugh or higher reactions)
- Applause
- Player breath and vocal foley

**Priority Tier 3 (Ducks for Tier 1 & 2):**
- Audience laughter (Polite Smile, Chuckle-tier reactions)
- Crowd murmur (Dynamic layer)
- Music (all stems)

**Priority Tier 4 (Ducks for all above):**
- Ambiance (Static bed and Event layers)
- Field recording textures
- Distant environmental sounds (traffic, sirens, kitchen clatter)

**Ducking implementation:**
Sidechain compression with fast attack (5-10ms), medium release (200-400ms). Duck amount:
- Tier 3 ducks -6 dB when Tier 1 active, -4 dB when Tier 2 active
- Tier 4 ducks -8 dB when Tier 1 active, -6 dB when Tier 2 active, -3 dB when Tier 3 active

**Example scenario:**
Player delivers punchline (Tier 1) -> Crowd erupts with laughter (Tier 2) -> Music ducks -4 dB, ambiance ducks -6 dB -> Laughter sustains -> Player exhales in relief (Tier 2) -> Music remains ducked until laughter decays -> 400ms later, music and ambiance return to full volume.

Result: Every sound has space. The mix never turns to mush.

### 6.3 Dynamic Range Philosophy

**DEADPAN preserves dynamic range. No brick-wall limiting. The silences are as loud as the screams.**

Target loudness: **-18 LUFS integrated** (quiet by modern game standards — intentional)

Peak ceiling: **-1 dBFS true peak** (prevent clipping but allow transients to punch)

Why? Comedy is about contrast. A joke lands because the silence before it was *silent*. If the mix is constantly dense and loud, the silence has no weight. The player must feel the discomfort of a quiet room, and the euphoria of a room that breaks. Dynamic range is the emotional range.

**Loudness by context:**
- **Performance ambiance (crowd waiting):** -40 to -30 LUFS (quiet, tense)
- **Solid laugh:** -25 to -18 LUFS (present, satisfying)
- **Eruption:** -15 to -8 LUFS (overwhelming, cathartic)
- **Silence (post-bomb):** -55 to -45 LUFS (just room tone — the void)
- **Music (apartment/green room):** -24 to -18 LUFS (background presence)
- **Music (career screen, key moments):** -18 to -12 LUFS (foreground, intentional)

**Mastering chain (final output):**
1. Surgical EQ (high-pass at 30 Hz, remove sub-rumble)
2. Multiband compression (gentle, 2:1 ratio, transparent glue)
3. Limiter (ceiling at -1 dBFS, 0.5ms attack, 50ms release, catch peaks only)
4. Dither (16-bit or 24-bit depending on platform)

No loudness war. The game breathes.

---

## 7. Implementation Plan & Technical Requirements

### 7.1 Audio Middleware

**Recommended: FMOD Studio**

Why FMOD?
- Robust real-time parameter system (essential for adaptive music stems and laughter synthesis)
- Built-in convolution reverb (venue IRs)
- Granular synthesis support (laughter engine)
- Excellent Unity/Unreal integration (likely engines for this project)
- Snapshot system (perfect for mix priority/ducking)
- Low CPU overhead (critical for 800+ SFX and real-time synthesis)

**Alternative: Wwise**

Viable if team has existing Wwise pipeline. Offers similar features but steeper learning curve. FMOD is preferred for indie/mid-tier budget.

**Fallback: Engine-native audio (Unity AudioMixer, Unreal MetaSounds)**

Possible but limits adaptive complexity. Not recommended unless budget is severely constrained.

### 7.2 Audio Implementation Architecture

**FMOD Event Structure:**

```
DEADPAN_Master.fspro
│
├── SFX/
│   ├── UI/
│   │   ├── Napkin_SetlistWrite (multi-sample event, random select)
│   │   ├── CardSnap_BitBuilder (multi-sample event, random select)
│   │   └── ... (all UI SFX as individual events)
│   ├── Ambiance/
│   │   ├── DiveBar_Ambiance (3-layer event: Static, Dynamic, Event)
│   │   ├── ComedyClub_Ambiance (3-layer event)
│   │   └── ... (all venue ambiances with parameter-controlled layers)
│   ├── Crowd/
│   │   ├── Laughter_Synthesis (granular event, see below)
│   │   ├── Applause_Build (layered event, scales with crowd size)
│   │   └── Heckler_Shout (multi-sample event, spatialized)
│   ├── Performance/
│   │   ├── Player_Voice (filtered, processed, state-modulated)
│   │   ├── Player_Breath (state-driven sample pool selection)
│   │   └── ... (all performance foley)
│   └── Environment/
│       └── ... (all environmental one-shots)
│
├── Music/
│   ├── MainMenu (looping, static)
│   ├── Apartment_Writing (4-stem event: Piano, Pad, Field Recordings, Bass)
│   ├── GreenRoom_PreShow (5-stem event, tension-building parameters)
│   ├── GreenRoom_PostShow_Success (4-stem event, REP gain parameter)
│   ├── GreenRoom_PostShow_Bomb (2-stem event, detuned parameter)
│   ├── City_Exterior (4-stem event, success state parameter)
│   ├── Career_MidTier (4-stem event, REP momentum parameter)
│   ├── Career_LateTier (5-stem event, Authenticity parameter)
│   ├── TheSpecial_Setup (5-stem event, setlist progress parameter)
│   ├── Ending_Victory (4-stem event)
│   └── Ending_Artistic (2-stem event)
│
└── Master Bus/
    ├── Snapshots/
    │   ├── Performance_Active (ducks music, foregrounds crowd)
    │   ├── GreenRoom_Idle (balanced mix)
    │   ├── CareerScreen_Focus (foregrounds music)
    │   └── Narrative_Moment (foregrounds music, ducks ambiance)
    └── Buses/
        ├── SFX_Bus (all SFX, master volume control)
        ├── Ambiance_Bus (all ambiance loops, Priority Tier 4 ducking)
        ├── Crowd_Bus (laughter/reactions, Priority Tier 2)
        ├── UI_Bus (UI sounds, Priority Tier 1-3 mixed)
        └── Music_Bus (all music, Priority Tier 3 ducking)
```

**Laughter_Synthesis Event (detailed breakdown):**

This is the most complex audio event in the game.

**Parameters (driven by Crowd Engine):**
- `ReactionTier` (float, 0.0-1.0) — maps to laughter intensity
- `CrowdSize` (int, 8-3000) — determines sample count and group layer blend
- `ArchetypeID` (int enum, 0-8) — modulates sample pool weighting and EQ
- `VenueID` (int enum, 0-9) — selects convolution IR
- `Momentum` (float, 0.0-2.0) — modulates low-frequency EQ boost
- `Fatigue` (float, 0.0-1.0) — modulates high-frequency roll-off

**Event structure:**
1. **Sample Layer** (granular sampler):
   - Programmer Instrument loads sample pool based on `ReactionTier` (e.g., tier 0.5-0.7 loads "Solid Laugh" pool)
   - Sample count = `min(12, max(2, CrowdSize / 10))`
   - Each sample: random time offset (0-300ms), random pitch (-8% to +8%), random gain (-6 to +3 dB)
   - `ArchetypeID` modulates sample pool weighting (e.g., Bachelor Parties favor explosive laughs, Comedy Nerds favor tight chuckles)
2. **Group Layer** (if `CrowdSize` > 30):
   - Loads group laugh samples (Small, Medium, or Large based on `CrowdSize`)
   - Blends underneath Sample Layer at -8 dB
3. **Convolution IR** (based on `VenueID`):
   - Sample + Group output routed through convolution reverb
   - IR is preloaded per venue
4. **Momentum EQ** (based on `Momentum`):
   - If `Momentum` > 1.0: +3 dB shelf boost at 150-300 Hz
   - If `Momentum` < 0.7: -2 dB at 200-500 Hz
5. **Fatigue High-Freq Roll-Off** (based on `Fatigue`):
   - `Fatigue` < 0.8: low-pass filter at `8000 - (1.0 - Fatigue) * 2000 Hz`
   - Example: Fatigue 0.6 = low-pass at 7200 Hz
6. **Spatialization**:
   - 3D positional audio based on audience cluster position in venue seating map
   - Stereo spread or 5.1 surround depending on platform

**Output:** Unique, reactive laughter every time.

### 7.3 Audio Budget & Optimization

**Platform Target: PC (Steam) / Nintendo Switch**

| Resource | Budget (PC) | Budget (Switch) | Notes |
|---|---|---|---|
| **Total Audio Asset Size** | 1.2 GB uncompressed | 800 MB uncompressed | Switch uses more aggressive Vorbis compression (Q5 vs Q7) |
| **Compressed Disk Size** | ~350 MB (Vorbis Q7, 44.1 kHz) | ~200 MB (Vorbis Q5, 44.1 kHz) | Acceptable for download size |
| **Memory Footprint (Loaded)** | 120-180 MB | 80-120 MB | Streaming used for ambiance/music, SFX preloaded |
| **Concurrent Voice Count** | 64 voices | 48 voices | Granular laughter can spike to 20-30 voices during Eruption reactions |
| **CPU Budget (Audio)** | <8% (on mid-tier PC, i5 equivalent) | <10% (Switch docked mode) | FMOD is efficient; real-time synthesis is the primary load |
| **Convolution Reverb Instances** | 2 simultaneous | 1 simultaneous | Venue IR on crowd/ambiance. Player voice uses algorithmic reverb (cheaper). |

**Optimization strategies:**
- **SFX streaming:** Only UI and performance foley are preloaded. Ambiance loops stream from disk (minimal memory hit).
- **Music streaming:** All music stems stream. No music is preloaded.
- **Laughter synthesis voice management:** Cap at 12 simultaneous granular voices per Eruption. If CPU spikes, reduce to 8 and increase group layer blend (quality degradation is minor).
- **Distance culling:** Audience clusters >20m from player (in large venues) have their laughter volume reduced by -12 dB and sample count halved.
- **Dynamic voice stealing:** Lowest-priority sounds (Tier 4 ambiance event layer) are voice-stolen if voice count exceeds budget.

### 7.4 Pipeline & Workflow

**Audio production pipeline:**

1. **SFX Recording/Sourcing (Weeks 1-4)**
   - Record custom foley (napkin writing, card snaps, mic handling, footsteps, door creaks)
   - License/record laughter samples (casting call for diverse laugh recordings, 10-15 participants)
   - Record venue ambiances (field recording sessions at 3-5 comedy clubs in LA/NYC)
   - Source UI sounds from library + custom recording

2. **SFX Editing & Processing (Weeks 5-8)**
   - Edit all samples to spec (trim, normalize, noise reduction, EQ)
   - Organize into FMOD-ready folder structure
   - Generate metadata spreadsheet (filename, category, frequency range, suggested mix level)

3. **Music Composition & Production (Weeks 1-12, parallel track)**
   - Compose all 12 primary zone cues (piano sketches first, full production second)
   - Record live instruments where possible (upright bass, piano, trumpet — budget permitting)
   - Produce stems for each cue (isolated instrument layers)
   - Export stems as 24-bit WAV, 48 kHz (downsample to 44.1 kHz on import to FMOD)

4. **FMOD Implementation (Weeks 9-14)**
   - Build FMOD project structure (events, buses, snapshots)
   - Implement all SFX events with appropriate randomization/variations
   - Implement adaptive music events with stem layering and parameter control
   - Implement Laughter_Synthesis event (most complex, requires iteration)
   - Implement convolution reverb system with venue IRs

5. **Integration with Game Code (Weeks 15-18)**
   - Integrate FMOD with Unity/Unreal (depending on engine choice)
   - Hook Crowd Engine outputs to Laughter_Synthesis parameters
   - Hook performance state system to Player_Voice/Breath modulation
   - Hook music zone transitions to game state changes
   - Implement mix snapshot triggers (performance start/end, menu transitions)

6. **Mixing & Balancing (Weeks 19-22)**
   - Playtest with sound designer present
   - Balance all SFX levels relative to each other
   - Tune ducking/priority system (adjust sidechain thresholds and duck amounts)
   - Tune laughter synthesis parameters (archetype weighting, momentum EQ curves)
   - Master final output chain (EQ, compression, limiter)

7. **Optimization & Polish (Weeks 23-24)**
   - Profile CPU/memory usage on target platforms
   - Optimize voice counts, reduce sample rates where inaudible (e.g., sub-bass ambiance can be 22 kHz)
   - Compress audio assets (Vorbis Q7 for PC, Q5 for Switch)
   - Final QA pass (check for pops, clicks, clipping, missing audio triggers)

**Team requirements:**
- **1 Sound Designer/Composer** (full-time, 24 weeks) — ideally ECHO, but realistically: someone with comedy world knowledge and adaptive audio experience
- **1 Audio Programmer** (half-time, weeks 15-24) — for FMOD integration and laughter synthesis system
- **Contract VO talent** (1 week) — for player character VO (if needed; may be text-only joke delivery with implied voice)
- **Contract musicians** (1-2 weeks) — upright bass, trumpet, live piano recording (budget permitting; can use samples if budget tight)

### 7.5 Testing & Iteration Targets

**Audio Playtesting Priorities:**

1. **Laughter Legibility Test** (Week 16-17):
   - Playtest: Can the player distinguish between reaction tiers by audio alone (eyes closed)?
   - Success metric: 80% accuracy identifying Silence, Chuckle, Solid Laugh, Eruption
   - If failure: Increase dynamic range between tiers, add more distinct sonic markers (e.g., applause triggers earlier in Big Laugh tier)

2. **Mix Clarity Test** (Week 20):
   - Playtest: Can the player hear all critical audio (joke delivery, laughter, hecklers, UI feedback) during dense moments (Eruption + heckler + UI notification)?
   - Success metric: No reports of "I couldn't hear X"
   - If failure: Adjust ducking curves, increase priority tier separation

3. **Emotional Resonance Test** (Week 21):
   - Playtest: Does the audio make bombing *feel* bad and killing *feel* good?
   - Success metric: Qualitative feedback from playtesters ("the silence after bombing was brutal," "the eruption gave me chills")
   - If failure: Extend silence duration post-bomb, increase dynamic range of Eruption, add more low-frequency weight to hot crowds

4. **Music Integration Test** (Week 22):
   - Playtest: Does the music enhance the emotional context without distracting?
   - Success metric: Players don't consciously notice music shifts, but report emotional shifts ("the green room felt sad after I bombed")
   - If failure: Music is too loud or too present — reduce volume, increase subtlety of adaptive parameters

5. **Performance Anxiety Test** (Week 23):
   - Playtest: Does the player voice modulation (breath, tremor, mic handling) communicate nervousness?
   - Success metric: Players report "I could hear myself getting nervous" without being told the system exists
   - If failure: Increase modulation intensity (louder breaths, more tremor), make mic handling noise more frequent

---

## 8. Silence Map

**Silence is a sound design choice. This is where and why silence is weaponized.**

### 8.1 Critical Silence Moments

**1. Post-Bomb Silence (The Void)**

**Context:** Player delivers punchline. Crowd reaction tier < 0.15 (Silence).

**Duration:** 2.4 seconds

**Audio content:** Pure venue room tone (HVAC hum, distant ambient bleed, occasional glass clink or cough). No laughter. No murmur. The absence is deafening.

**Mix:** All Priority Tier 3 and 4 audio ducks -12 dB. Music is already absent during performance. Only room tone and player breath remain.

**Why:** Comedy is the only art form where silence is failure. The player must FEEL the silence in their chest. 2.4 seconds is long enough to be agonizing without breaking pacing. This is the worst sound in the game, and it should be.

**Iteration note:** If playtest feedback says "the silence is too long," do NOT shorten it. The discomfort is the point. If players are complaining, the design is working.

---

**2. Pre-Stage Silence (The Breath Before the Plunge)**

**Context:** Final 3 seconds before stepping on stage. Music has been building tension in the green room, then cuts.

**Duration:** 3.0 seconds

**Audio content:** Single deep player inhale (0.8s), held breath (1.5s), quiet exhale (0.7s). Distant muffled crowd murmur through walls. No music. No movement. Just breath.

**Mix:** All audio except player breath and distant murmur is muted.

**Why:** The transition from preparation to performance is existential. The silence is the moment of commitment. The player is about to be seen. The breath grounds them in their body.

**Reference:** The silence before Mitch Hedberg stepped on stage (archival recordings) — you can hear him breathing, gathering himself. That vulnerability is the target.

---

**3. Setlist Closer Pause (The Final Gambit)**

**Context:** Player is about to deliver the final punchline of their set. The entire performance hinges on this moment.

**Duration:** 1.2 seconds (shorter than post-bomb silence, but pregnant with potential)

**Audio content:** Crowd is primed (low ambient murmur, bodies leaning forward). Player breath (audible inhale). Silence. Then: punchline delivery.

**Mix:** Dynamic crowd layer drops -10 dB. Static ambiance bed remains. Player breath is prominent (-28 dBFS).

**Why:** The setup-to-punchline transition is the hinge of joke structure. The pause creates anticipation. If the punchline lands, the contrast between silence and eruption is MASSIVE. If it bombs, the silence extends into the Void.

**Iteration note:** This silence should be *tense*, not empty. The crowd is waiting. The air is charged. Slight low-frequency rumble (60-100 Hz at -50 dBFS) under the silence to create subliminal pressure.

---

**4. Tier Unlock Moment (The Pause Before the Door Opens)**

**Context:** Player has just earned enough REP to unlock a new career tier. Notification appears.

**Duration:** 0.8 seconds

**Audio content:** All audio fades out over 0.8s. Silence. Then: The Moment Theme stinger (suspended chord) blooms.

**Why:** The silence creates space for the moment to land. The tier unlock is a major milestone. Rushing into the stinger without silence diminishes the impact. The pause says: "Stop. This matters."

---

**5. The Special — Pre-Performance Silence (Existential Stillness)**

**Context:** The player is backstage before performing their 60-minute special. This is the culmination of their career. The screen fades to black.

**Duration:** 4.5 seconds (the longest silence in the game)

**Audio content:** Absolute silence for 2.0 seconds. Then: distant crowd murmur fades in (very quiet, -45 dBFS). Then: single piano note (Dsus4, the Player's Theme suspended) holds underneath as the screen fades back in and the spotlight hits.

**Why:** This is the loneliest moment in comedy. The player has spent 20-30 hours getting here. The silence acknowledges the weight. Then the piano reminds them: *You've been here before. You know what to do.* The silence is not the Void — it's the space before creation.

**Reference:** The opening of *Bo Burnham: Inside* — the silence before the first word carries the entire emotional arc of the special.

---

### 8.2 Micro-Silences (Structural Silence)

**Between Jokes (Pacing Silence):**

Every joke in a setlist is followed by 0.3-0.8 seconds of silence (depending on laughter duration) before the next joke setup begins. This is the structural silence of standup. The silence is NOT empty — it's filled with decaying laughter, crowd murmur, and player breath. But the player's voice stops. The silence is rhythmic. Without it, the set becomes a wall of words and loses cadence.

**Implementation:** Automated in setlist playback. Silence duration = `0.3 + (ReactionScore * 0.5)` seconds. Strong reactions earn longer pauses (the crowd needs time to recover). Weak reactions get short pauses (the player rushes forward, trying to recover momentum).

---

**Post-Applause Silence (Resolution):**

After a successful set, applause sustains for 6-12 seconds, then decays naturally. As it fades, there's a 1.5-second silence before the post-show music fades in. This silence is the exhale. The performance is over. The player survived. The silence acknowledges: *It's done.*

---

**Green Room Idle Silence:**

If the player sits idle in the green room (no input for 45+ seconds), the ambient event layer stops triggering. Only the static bed (muffled stage audio, radiator hiss) remains. The silence is not total, but it's noticeably quieter. The world is waiting for the player to move. The silence communicates: *What are you waiting for?*

---

### 8.3 Silence as Contrast (The Reset)

Silence is the baseline that makes laughter register as LOUD. Every Eruption-tier reaction is preceded by relative quiet (either a pause in the set or a low-reaction previous joke). The contrast is the impact.

**Audio design principle:** If the mix is constantly "full," the player becomes numb. Laughter at -15 LUFS only feels overwhelming if the preceding audio was -40 LUFS. The silence (or near-silence) is the setup. The laughter is the punchline.

**Iteration target:** The dynamic range between the quietest moment in a set (post-bomb silence) and the loudest moment (Eruption) should be at least 40 dB. That's the range of human emotion.

---

## 9. Accessibility Considerations

Audio accessibility is not optional.

### 9.1 Visual Audio Indicators

For players who are deaf or hard of hearing, critical audio cues must have visual equivalents.

**Visual indicators required:**

| Audio Cue | Visual Indicator |
|---|---|
| **Laughter (all tiers)** | Laugh Meter waveform (already exists in design). Color-coded by reaction tier. |
| **Heckler shout** | Red exclamation mark icon appears at the spatial position of the heckler (L/R screen edge). Text subtitle: "[HECKLER]: Get off the stage!" |
| **Applause** | Clapping hand icons animate around screen edges. Intensity scales with applause volume. |
| **Phone notification (agent, gig offer)** | Phone screen lights up with visible notification banner. Vibration can be represented by brief screen shake (2-3 frames). |
| **Mic feedback** | Visual glitch effect (screen flash, slight distortion) + "FEEDBACK" text appears briefly. |
| **Door open/close** | Door animation in environment (already exists visually). |
| **Footsteps (player/NPC)** | Subtle dust particle puff on each footstep impact. |

**Subtitle system:**
- All player dialogue (joke delivery) is subtitled with color-coded speaker tags
- Crowd reactions are subtitled as group behaviors: "[LAUGHTER]", "[CHUCKLES]", "[SILENCE]", "[APPLAUSE]"
- Hecklers are subtitled with spatial indicator: "[HECKLER - LEFT]: You suck!"
- Background ambiance is NOT subtitled (would clutter UI)

### 9.2 Audio Customization Options

**Settings menu audio options:**

| Setting | Range | Default | Purpose |
|---|---|---|---|
| **Master Volume** | 0-100% | 80% | Overall output level |
| **SFX Volume** | 0-100% | 90% | All sound effects (crowd, UI, foley) |
| **Music Volume** | 0-100% | 70% | All music tracks |
| **Ambiance Volume** | 0-100% | 60% | All looping ambiance beds |
| **Crowd Volume** | 0-100% | 100% | Laughter/applause/reactions (subset of SFX) |
| **UI Audio Volume** | 0-100% | 80% | UI sounds (pen scratch, card snap, phone buzz) |
| **Dynamic Range** | Compressed / Normal / Wide | Normal | Adjusts final limiter. "Compressed" reduces dynamic range for players in noisy environments or using low-quality speakers. "Wide" preserves full dynamic range for headphone/studio monitor users. |
| **Crowd Density** | Low / Medium / High | High | Adjusts granular laughter voice count. Low = 4 max voices (less CPU, less dense). High = 12 max voices. For performance or preference. |
| **Music Adaptive Layers** | On / Off | On | Allows players to disable adaptive music stem changes if they find it distracting. Music plays full mix always if disabled. |

### 9.3 Photosensitivity (Audio-Driven Visuals)

If any visual effects are triggered by audio (e.g., screen flash on mic feedback, Laugh Meter waveform intensity), provide option to disable or reduce intensity in accessibility settings. This is standard practice.

---

## 10. Final Notes & Production Philosophy

**This soundscape is not decoration. It is architecture.**

Every sound in DEADPAN exists to answer one question: *How does this room feel?* A cold room feels different than a hot room. A dive bar feels different than a theater. Bombing feels different than killing. The audio is the tactile surface of the emotional experience.

**Listen to the space between.**

Comedy is not the jokes. Comedy is the room's reaction to the jokes. The laughter is the feedback loop. The silence is the stakes. The breath is the humanity. The audio design must make the player feel like they are standing in that spotlight, in that room, with those people, in that moment. If the audio achieves that, the game works. If it doesn't, no amount of visual polish saves it.

**Close your eyes. What do you hear?**

If the answer is "I hear a game," the design has failed. If the answer is "I hear a comedy club at 11 PM on a Tuesday, and I'm about to go on stage, and I'm terrified," the design has succeeded.

**Audio IS game feel.**

The difference between a joke that lands and a joke that dies is audible before it's visible. The laughter graph shows you the data, but the audio makes you *feel* it. The player should be able to close their eyes during a set and know exactly how they're doing. That's the bar.

**The mic is the loneliest place on earth.**

And the sound design must make the player understand why.

---

**End of document.**

**Estimated total word count: ~9,800 words**

**Document status:** Production-ready. All systems specified. Ready for audio team allocation and FMOD implementation.

**Next steps:**
1. Approve sound design direction and budget
2. Allocate audio team (1 sound designer/composer + 0.5 audio programmer)
3. Begin SFX recording and music composition (Week 1)
4. Prototype Laughter_Synthesis event in FMOD (Week 10 — critical path item)
5. First audio playtest with vertical slice build (Week 17)

---

**Listen. The room is waiting.**
