*Ormer Modular · made in Guernsey*

# FLUKE

USER MANUAL · VCV RACK · v2.0.0 · 12 HP

Fluke is a sibling to Shoal, Ormer Modular's generative melody sequencer, and a lot smaller. It is a CV generator with **eight tracks of ever-changing random voltage**. When something sounds right you **catch** it, and the last stretch that played becomes a loop. A **MUTATE** knob then decides how much that loop drifts each time round, from perfectly still to slowly wandering. Each track has its own style of randomness, plus Chance, Rate, Direction, Slide and Quantise, with the key set per track or for the whole module. Everything is on a 12 HP panel with a small screen and a single encoder. Turn the encoder to pick a track, click and hold to go into its settings, turn to scroll them, click to edit a value, double-click to finish, and click and hold again to come back out. Prefer a mouse to a knob? Every setting is also in the right-click menu.

## The panel

Everything below is at its default setting. Fluke comes in two panels, silver and black: Rack picks one from its own dark-panel setting, and you can force either from the module's right-click menu.

- **CATCH** (Light button, latching): Turns the last Length steps that played into this track's loop. Press again to release it. Lit while caught, dipping at the start of each pass. Dark while the track is free. Also picks this track on the screen.
- **MUTATE** (Knob · 0–100% · default 0): How much a caught loop changes each time round: at 0% it repeats exactly, at 100% every step is replaced every pass. Does nothing to a free track. Also picks this track on the screen.
- **CV** (CV output): This track's random voltage, one new value per step, within the track's Range. Held between steps, and glided if Slide is up. The small light beside it follows the voltage.
- **GATE** (Gate output): A 10 V gate on every step that passes the track's Chance, for as long as Gate length says. The small light beside it is lit while the gate is high.
- **CLOCK** (Clock input): Each rising edge (above about 1 V) is one beat. With a cable in, the internal clock stands down and the screen shows the incoming BPM. Without one, the internal clock runs at the BPM setting.
- **RESET** (Trigger input): A rising edge (above about 1 V) restarts every track from the beginning of its pass on the next clock pulse.
- **CATCH ALL** (Light button): Catches every track that is still free. If every track is already caught, releases them all.
- **CATCH ALL** (Trigger input): A rising edge (above about 2 V) does exactly what the CATCH ALL button does.
- **ENCODER** (Encoder): Turn to pick a track (the ninth stop is GLOBAL). Click and hold to go into its settings, and again to come out. Inside, turn to scroll, click to edit, turn to change, double-click to finish. Turn quickly for bigger steps on the wide settings. Every setting is also in the right-click menu.
- **THE SCREEN** (Display): Shows the selected track, whether it is caught or free, the setting being edited and its value, and the track's last 32 steps (or its caught loop, in amber, with a white bar on the step playing). After a minute untouched it becomes a night sea where each firing track makes a ripple. The right-click menu sets or turns off the screensaver.

## Catching a loop

Every track is a source of random voltage. On each clock pulse (scaled by the track's Rate) it picks a new value in the style you chose, sends it to its **CV** output, and sends a gate to its **GATE** output if the step passes Chance. The track remembers what it played: the last 64 steps, together with which of them fired.

CLOCK → RATE → STYLE (random value) → CHANCE → RANGE · QUANTISE · SLIDE → CV · GATE

### CATCH turns what just played into a loop

Press a track's **CATCH** button and the last **Length** steps that played become that track's loop (the default Length is 16 steps; at most 64). The button lights. From then on the track plays the loop instead of choosing new values. The first time round it plays exactly what you caught. Press the button again to **release** it, and the track goes back to throwing fresh values.

If a track hasn't played anything yet there is nothing to catch, and the button stays dark.

### MUTATE: how much the loop changes each time round

At the end of every pass of a caught loop, each step is replaced by a fresh value in the track's style with a probability set by the track's **MUTATE** knob, and a fresh Chance roll comes with it. At **0%** the loop repeats exactly, however long it runs. At **100%** every step is replaced every pass, so it behaves like a free track. In between, the loop slowly wanders. MUTATE works on caught loops only.

### What stays live on a caught loop

A loop stores the values and which steps fired, not the voltages. So **Range, Quantise, Scale, Root, Slide, Chance, Rate and Direction** all keep working on a caught loop, and the loop at fixed settings repeats exactly. Re-quantise a caught loop into another key, or shrink its Range, and the same pattern comes out transformed.

### CATCH ALL

The **CATCH ALL** button catches every track that is still free. If every track is already caught, it releases them all. A trigger into the CATCH ALL jack does the same.

### Chance, and why a missed step holds

A step that misses its Chance is **skipped**: it sends no gate and the CV **holds** its previous value. This is deliberate, so a note's release tail never changes pitch under it. The missed step is still recorded with its roll, so a caught loop keeps its rhythm of hits and misses.

### Breathe: whole passes of silence

At the end of each pass, a track rests for the whole next pass with a probability set by **Breathe**: no gates, and the CV holds. It lets a loop drop out and come back.

## The screen and encoder

Nearly every setting lives on the screen, which you work with the encoder (the large knob). There are two levels, and one gesture moves between them: **click and hold** the encoder (about half a second, without turning it).

1. **Select.** Turn the encoder to pick a track. The ninth stop after track 8 is **GLOBAL**, the settings that belong to the whole module. The screen shows the track, whether it is caught or free, its style, rate and length, and its last 32 steps.
2. **Click and hold to go in.** A thin amber line grows along the top of the screen while you hold (about half a second), and the settings open when it reaches the end. Now turn to scroll through the settings (the screen shows the group, the setting's name and where you are in the list). **Click** to edit: the value turns amber and underlined. Turn to change it, then **double-click** to finish. A single click while editing does nothing, so a click that lands late can never throw you out of the edit.
3. **Click and hold again to come back out** to Select. Holding does nothing while you are editing a value: double-click first.

Touching a track's CATCH button or MUTATE knob also picks that track on the screen. The encoder remembers where you were in each list. Settings that run from 0 to 100% (Chance, Slide, Breathe, Gate length), BPM and Length move one step at a time, and in bigger steps (5, or 4 for Length, 5 for BPM) when you turn quickly.

### What the screen shows

The top line shows where you are (`SELECT`, `TRK 3` or `GLOBAL`) and whether the track is `CAUGHT` or `FREE`. Below it are the style, rate and length (or, inside the settings, the group and setting name and your place in the list), and the big line is the value. Along the bottom are 32 bars. On a free track they are the last 32 steps that played. On a caught track they are the loop, in amber, with a white bar on the step playing now.

### Start-up and the screensaver

When Fluke loads, the FLUKE wordmark builds on the screen and dissolves. After a minute without a touch (the right-click menu can turn this off or make it five minutes) the screen becomes a small scene: a whale's tail rising from a night sea. Each track that fires opens a ripple on the water at its own place along the surface (a caught loop's ripple is brighter), and any firing makes the tail dip and throw a few drops. The first turn or click of the encoder only wakes the screen and changes nothing. Touching a CATCH button or MUTATE knob wakes it too, and does its usual job.

## Track settings

Pick a track, click and hold, and these are the settings, in the order you meet them. Each track has its own set. Defaults are shown in brackets.

| Group | Setting | What it does |
|---|---|---|
| RANDOM | Style (Open) | The kind of randomness the track throws, free and in mutations. Seven styles, below. |
| RANDOM | Chance (100%) | 0 to 100%. The chance a step fires. A step that misses sends no gate and the CV holds. It stays live on a caught loop. |
| PLAY | Rate (x1) | 29 steps from /64 to x64. How fast the track steps against the clock. x1 is one step per clock pulse; /4 is one step every four pulses; x2 is two steps per pulse. Table below. |
| PLAY | Swing (0%) | 0 to 50%. Holds back every second step of the track by this share of a step, for swung hats and late ghost kicks. 0% is straight, about 33% is a triplet feel and 50% is dotted. It follows the track's own Rate, and RESET puts the next step back on the beat. Other tracks are untouched, so a kick can stay straight while a hat swings. |
| PLAY | Length (16) | 1 to 64 steps. How many steps CATCH grabs, and so how long the loop is. |
| PLAY | Direction (Forwards) | The order a caught loop plays its steps in. Fifteen directions, below. |
| PLAY | Breathe (0%) | 0 to 100%. The chance, at the end of each pass, that the next whole pass rests. |
| OUTPUT | Range (0 to 5V) | The size and polarity of the CV, in one setting: 0 to 1V · 0 to 2V · 0 to 3V · 0 to 5V (default) · 0 to 10V · ±1V · ±2V · ±3V · ±5V · ±10V. Unipolar ranges run from 0 V up; the ± ranges swing both ways about 0 V. |
| OUTPUT | Slide (0%) | 0 to 100%. How much of each step is spent gliding to the new value. At 0% the CV jumps; at 100% it glides all the way, step to step. |
| OUTPUT | Quantise (Off) | Snaps the CV to the track's scale and root, before any Slide. Off, the CV is continuous. |
| OUTPUT | Scale (Global) | Global, or one of 13 scales for this track alone. Global follows the module's Scale in the Global settings. |
| OUTPUT | Root (Global) | Global, or C to B for this track alone. Global follows the module's Root. |

The scales are: Chromatic · Major · Natural minor · Harmonic minor · Dorian · Phrygian · Lydian · Mixolydian · Major pent · Minor pent · Blues · Hirajoshi · In-Sen. A note halfway between two scale notes snaps down.

### Styles

A style is the shape of the randomness: how the values are spread across the track's Range.

| Style | What it throws |
|---|---|
| Open (default) | Every value in the range is equally likely. The plainest randomness. |
| Midwater | Values gather around the middle of the range, and the extremes are rare. |
| Shallows | Leans low: most values sit near the bottom, with now and then a middle one. |
| Squall | Mostly calm and low, with sudden gusts. |
| Tide | Rising and falling runs: three to six steps climb towards a new level, then turn and fall back. |
| Current | A smooth wander. Each value is a small move from the one before. |
| Deep | A slow, layered wander: long rolling movements with smaller ripples riding on them. |

### Directions

Direction decides the order a **caught** loop plays its steps in. A free track picks a new random value every step, so its order doesn't matter.

| Direction | Order a caught loop plays in |
|---|---|
| Forwards (default) | Step 1 to the last step, in order. |
| Reverse | The last step back to step 1. |
| Pendulum | Forwards, then back, turning round at each end (the end steps play twice). |
| Random | Any step each time, so repeats and gaps are possible. |
| Drunk | A stagger: half the time one step forward, a quarter of the time the same step again, a quarter of the time one step back. |
| Pong | Forwards, then back, bouncing off each end without repeating the end steps. |
| Tide | Forwards, but the values shift one step along every pass, so the notes slide against the rhythm of hits. |
| Shuffle | Every step once per pass, in a shuffled order that changes each pass. |
| Pools | Circles a pool of three or four steps for a while, then moves to another place in the loop. |
| Stride | Two ahead, one back: 1, 3, 2, 4, 3, 5 and so on. A pass takes twice as many steps. |
| Gravity | Moves forwards, but each step has a chance of snapping back to step 1. |
| Converge | Folds in from both ends: first, last, second, second to last, and so on to the middle. |
| Diverge | Unfolds from the middle out to both ends. |
| Skitter | Random, but never the same step twice in a row. |
| Anchor | Step 1 between every other step: 1, 2, 1, 3, 1, 4 and so on. A pedal note with excursions. |

### Rate

The clock is one pulse per beat (see Global settings). Rate multiplies or divides that for each track, so tracks can run against each other.

| # | Rate |
|---|---|
| 1 | /64 |
| 2 | /32 |
| 3 | /16 |
| 4 | /8 |
| 5 | /7 |
| 6 | /6 |
| 7 | /5.3 |
| 8 | /5 |
| 9 | /4 |
| 10 | /3 |
| 11 | /2.6 |
| 12 | /2 |
| 13 | /1.5 |
| 14 | x1 (default) |
| 15 | x1.25 |

| # | Rate |
|---|---|
| 16 | x1.3 |
| 17 | x1.5 |
| 18 | x2 |
| 19 | x2.6 |
| 20 | x3 |
| 21 | x4 |
| 22 | x5 |
| 23 | x5.3 |
| 24 | x6 |
| 25 | x7 |
| 26 | x8 |
| 27 | x16 |
| 28 | x32 |
| 29 | x64 |

## Global settings

Pick **GLOBAL** (the stop after track 8), click and hold, and these are the settings.

| Group | Setting | What it does |
|---|---|---|
| CLOCK | BPM (120) | 20 to 300. The internal clock's tempo, used when nothing is patched into CLOCK. With a clock patched in, the screen shows the incoming clock's tempo instead, to one decimal and marked EXT, and BPM can't be edited. Each incoming pulse counts as one beat, the same as the internal clock. |
| CLOCK | Run (On) | Starts and stops the clock. Off, no track steps. |
| CLOCK | Freeze (Off) | Nothing advances: every CV holds its value and sounding gates stay as they are. |
| KEY | Scale (Natural minor) | The scale Quantise snaps to on every track whose Scale is set to Global. |
| KEY | Root (C) | The key note of that scale, for every track whose Root is set to Global. |
| GATE | Gate length (50%) | 5 to 100%. How long every gate stays high, as a share of the step. |

> **One key or eight.** Leave every track on Global and the whole module plays in one key: change Scale and Root once. Set a track's own Scale or Root and it goes its own way, for a bass in minor pentatonic under a lead in the full minor scale, or a drone a fifth away.

## Patching

| Jack | Type | Notes |
|---|---|---|
| CLOCK | clock in | Each rising edge (above about 1 V) is one beat. With a cable in, the internal clock stands down and the screen shows the incoming BPM. Without one, the internal clock runs at the BPM setting. A clock that sends several pulses per beat reads as a faster tempo: use each track's Rate to divide it. |
| RESET | trigger in | A rising edge (above about 1 V) restarts every track from the beginning of its pass on the next clock pulse. |
| CATCH ALL | trigger in, and button | Catches every free track; if all are caught, releases them all. A rising edge above about 2 V does the same as the button. |
| CV 1 to 8 | CV out | The track's random voltage, one new value per step: 0 V up to the track's Range, or ± the Range for the bipolar settings. Held between steps (and glided, if Slide is up). |
| GATE 1 to 8 | gate out | 10 V gate on every step that passes Chance, as long as Gate length says. A resting track sends none. |

> **Not polyphonic.** Every output is a single channel. Each track has a small light by its CV jack that follows the voltage, and another by its GATE jack that is lit while the gate is high.

## Right-click menu

Every setting is in the right-click menu too, so you can use the encoder or not. The menu works on the track the screen is on. Choose a track from **Track** at the top (or touch its CATCH or MUTATE, or turn the encoder), then open the menu: that track's settings are listed first, then the module's. Percentages and numbers are sliders (drag, or click or right-click a slider and type a value, then Enter).

| Item | Choices | What it does |
|---|---|---|
| Track | Track 1 to Track 8 | Which track the settings below belong to. The screen follows. |
| Copy track · Paste onto | Track 1 to 8 · All other tracks | Copy the selected track's settings, MUTATE and (if it is caught) its loop, then paste them onto any other track, or onto all of the others. A pasted free track becomes free; a pasted caught track becomes caught with the same loop. |
| Caught | on · off | The track's CATCH button. |
| Mutate | 0 to 100% | The track's MUTATE knob. |
| Style · Chance · Rate · Swing · Length · Direction · Breathe | as in Track settings | The track's settings, with the same ranges. |
| Range · Slide · Quantise · Scale · Root | as in Track settings | The track's output settings. Scale and Root can be Global. |
| BPM · Run · Freeze | as in Global settings | With a clock patched in, BPM is set by it and the menu says so. |
| Key: Scale · Key: Root | 13 scales · C to B | The module's key, for every track whose Scale or Root is Global. |
| Gate length | 5 to 100% | How long every gate stays high, as a share of the step. |
| Panel | Follow Rack setting · Silver · Black | Forces the silver or the black panel for this module. The jacks and screws change with it. The choice is saved with the patch. By default the panel follows Rack's **View > Use dark panels if available**. |
| Screensaver | Off · After 1 minute · After 5 minutes | How long the screen waits, untouched, before showing the whale's tail. Default after 1 minute. Saved with the patch. |

The patch saves every setting, and each caught track's loop, so a patch reopens exactly as you left it.

## Installing

Fluke is sold through the VCV Library, for Mac (Apple Silicon or Intel), Windows and Linux.

1. Add Fluke to your account on its VCV Library page.
2. In Rack, log in from the **Library** menu and choose **Library > Update all**. Rack downloads Fluke and any other plugins you own.
3. Restart Rack if it asks you to, then add **Fluke** from the module browser, under Ormer Modular.

Fluke needs Rack 2.

## Troubleshooting

**Nothing is moving.**

Fluke needs a clock to step: patch one into CLOCK, or unplug it to use the internal clock. Check **Run** and **Freeze** in the Global settings: Run should be On and Freeze Off.

**CATCH won't light.**

A track can only catch what it has played. Wait for it to step at least once. If the track's Rate is slow, that can take a while.

**The loop never changes.**

MUTATE at 0% repeats the loop exactly. Turn the track's MUTATE up. MUTATE does nothing to a free track.

**A gate is missing, and the CV didn't change.**

That step missed its Chance (or the track is resting through a Breathe pass). A missed step holds the CV on purpose.

**I can't change BPM.**

A clock is patched into CLOCK and sets the tempo. The screen shows its BPM and marks it EXT. Unpatch it to edit BPM.

**The tempo reads as a multiple of what I expect.**

Fluke counts each incoming pulse as one beat. A clock that sends 4 or 24 pulses per beat reads 4 or 24 times too fast: set each track's Rate to /4 or /24 to bring them back to a beat.

**The screen shows a tail on the sea and the encoder won't change anything.**

That is the screensaver. The first turn or click wakes the screen and does nothing else. Turn it off or lengthen it in the right-click menu.

**The notes aren't in my key.**

Quantise must be On for the track. Then check the track's Scale and Root: if they're on Global, the Global Scale and Root decide.

**The panel won't change colour.**

Use the module's right-click **Panel** menu. If it is set to Follow Rack setting, Rack's **View > Use dark panels if available** decides.

## Specifications

| Format | Rack 2 · 12 HP | Not polyphonic. Silver and black panels. |
|---|---|---|
| Tracks | 8 | Each with its own style, Chance, Rate, Swing, Length, Direction, Breathe, Range, Slide, Quantise, Scale and Root; a CATCH button and a MUTATE knob |
| Loops | 1 to 64 steps | Values and hit pattern stored per step; each track remembers its last 64 steps |
| Styles | 7 | Open · Midwater · Shallows · Squall · Tide · Current · Deep |
| Rates | 29 | /64 to x64 |
| Directions | 15 | Forwards to Anchor |
| Scales | 13 | Chromatic and twelve more, with any of 12 roots |
| CV out | 8 jacks | 0 to 1, 2, 3, 5 or 10 V, or ± 1, 2, 3, 5 or 10 V |
| Gate out | 8 jacks | 10 V, 5 to 100% of the step |
| Clock | 20 to 300 BPM | internal, or one pulse per beat from the CLOCK jack |
| Platforms | Mac · Windows · Linux | Apple Silicon and Intel Macs |

Fluke's engine is original. It uses no third-party DSP. Fluke is closed-source and proprietary.

Fluke for VCV Rack · Ormer Modular · made in Guernsey

catch it
