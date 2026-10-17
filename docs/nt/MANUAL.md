*Ormer Modular · made in Guernsey*

# FLUKE

USER MANUAL · EXPERT SLEEPERS DISTING NT · v1.0.0 · FREE

Fluke is a sibling to Shoal, Ormer Modular's generative melody sequencer, and a lot smaller. It is a CV generator with **eight tracks of ever-changing random voltage**. When something sounds right you **catch** it, and the last stretch that played becomes a loop. A **Mutate** setting then decides how much that loop drifts each time round, from perfectly still to slowly wandering. Each track has its own style of randomness, plus Chance, Rate, Direction, Slide and Quantise, with the key set per track or for the whole algorithm. On the disting NT it takes three pots and two pushes: **three pots** for the track's settings, **the left pot push to catch** and **the right pot push to catch all**. Everything else is an ordinary parameter, so it can be mapped to CV, MIDI or I²C like any other. Fluke also sends MIDI notes, and can be clocked from MIDI.

## The screen

Fluke replaces the usual parameter line with its own screen: a whale's tail rising from a night sea. Each track that fires opens a ripple on the water (a caught loop's ripple is brighter), and any firing makes the tail dip and throw a few drops.

- **Top left:** the picked track, and `CAUGHT` when it has a loop. Under it, for three seconds after you turn a pot, the name and value of the setting you moved. It fades away when you stop turning.
- **Top, right of centre:** what the two pot pushes do right now. `PUSH L: CATCH` or `RELEASE` for the picked track, `R: CATCH ALL` or `RELEASE ALL` for every track.
- **Top right:** the tempo (`120 BPM`), or `EXT` when a clock cable sets it, or `MIDI` when it follows MIDI clock.
- **Bottom:** the name of what each of the three pots does on this page, each with a small level bar, and four dots for the page you are on.

## Controls

Fluke uses as little of the disting NT's own controls as it can. Buttons 1 to 4 and the left encoder push do their usual jobs, so you can always get out or into the parameter list.

| Control | On the Fluke screen |
|---|---|
| Three pots | Edit three settings of the picked track. Which three depends on the page. |
| Centre pot push | Next page of three settings (four pages, then back to the first). |
| Left pot push | **Catch** the picked track, or release it. The same as the track's `Caught` parameter. |
| Right pot push | **Catch all**: catches every track that is still free. If all are caught, releases them all. The same as the `Catch all` parameter. |
| Encoders (turn) and right encoder push | Do nothing here, so they cannot change a setting you cannot see. Press button 2 for the parameter list, where they work as normal. |
| Buttons 1 to 4, left encoder push | The disting NT's own: menu, parameters, help and shift. |

### The four pot pages

| Page | Left pot | Centre pot | Right pot |
|---|---|---|---|
| 1 | TRACK | MUTATE | CHANCE |
| 2 | SLIDE | RATE | LENGTH |
| 3 | SWING | STYLE | DIRECTION |
| 4 | BREATHE | RANGE | SCALE |

**TRACK** picks which of the eight tracks the other pots and the screen are on. It is the `Track` parameter, so you can also set it from the parameter list or map it to CV.

> **Pots pick up where the setting is.** When you change page, or pick another track, the pots do nothing until your hand reaches the setting's current value, and then they take over. That is the disting NT's own pick-up behaviour, so nothing jumps.

Everything not on a pot page (Quantise, Root, the Global key, Clock source, Run, Freeze, Gate length, MIDI and the routing) is in the parameter list: press button 2.

## Catching a loop

Every track is a source of random voltage. On each clock pulse (scaled by the track's Rate) it picks a new value in the style you chose, sends it to its CV output, and sends a gate to its gate output if the step passes Chance. The track remembers what it played: the last 64 steps, together with which of them fired.

CLOCK → RATE → STYLE (random value) → CHANCE → RANGE · QUANTISE · SLIDE → CV · GATE

### Catch turns what just played into a loop

Push the **left pot** and the last **Length** steps that played become the picked track's loop (the default Length is 16 steps; at most 64). The screen says `CAUGHT`. From then on the track plays the loop instead of choosing new values. The first time round it plays exactly what you caught. Push again to **release** it, and the track goes back to throwing fresh values.

If a track hasn't played anything yet there is nothing to catch, and the push does nothing.

### Mutate: how much the loop changes each time round

At the end of every pass of a caught loop, each step is replaced by a fresh value in the track's style with a probability set by the track's **Mutate**, and a fresh Chance roll comes with it. At **0%** the loop repeats exactly, however long it runs. At **100%** every step is replaced every pass, so it behaves like a free track. In between, the loop slowly wanders. Mutate works on caught loops only.

### What stays live on a caught loop

A loop stores the values and which steps fired, not the voltages. So **Range, Quantise, Scale, Root, Slide, Chance, Rate and Direction** all keep working on a caught loop, and the loop at fixed settings repeats exactly. Re-quantise a caught loop into another key, or shrink its Range, and the same pattern comes out transformed.

### Catch all

The **right pot push**, the `Catch all` parameter, or a trigger into the `Catch all input` catches every track that is still free. If every track is already caught, it releases them all.

### Chance, and why a missed step holds

A step that misses its Chance is **skipped**: it sends no gate and the CV **holds** its previous value. This is deliberate, so a note's release tail never changes pitch under it. The missed step is still recorded with its roll, so a caught loop keeps its rhythm of hits and misses.

### Breathe: whole passes of silence

At the end of each pass, a track rests for the whole next pass with a probability set by **Breathe**: no gates, and the CV holds. It lets a loop drop out and come back.

## Track parameters

There is a parameter page for each track (`Track 1` to `Track 8`), and every parameter on it is prefixed with the track, such as `T3: Rate`. Each track has its own set. Defaults are shown in brackets.

| Parameter | What it does |
|---|---|
| Caught (Off) | On while the track plays a caught loop. Turn it On to catch, Off to release. Map it to a gate or a button to catch from a patch. A catch with nothing played yet turns itself back Off. |
| Mutate (0%) | 0 to 100%. How much a caught loop changes each time round. |
| Style (Open) | The kind of randomness the track throws, free and in mutations. Seven styles, below. |
| Chance (100%) | 0 to 100%. The chance a step fires. A step that misses sends no gate and the CV holds. It stays live on a caught loop. |
| Rate (x1) | 29 steps from /64 to x64. How fast the track steps against the clock. x1 is one step per clock pulse; /4 is one step every four pulses; x2 is two steps per pulse. Table below. |
| Swing (0%) | 0 to 50%. Holds back every second step of the track by this share of a step, for swung hats and late ghost kicks. 0% is straight, about 33% is a triplet feel and 50% is dotted. It follows the track's own Rate, and a reset puts the next step back on the beat. Other tracks are untouched. |
| Length (16) | 1 to 64 steps. How many steps a catch grabs, and so how long the loop is. |
| Direction (Forwards) | The order a caught loop plays its steps in. Fifteen directions, below. |
| Breathe (0%) | 0 to 100%. The chance, at the end of each pass, that the next whole pass rests. |
| Range (0 to 5V) | The size and polarity of the CV, in one setting: 0 to 1V · 0 to 2V · 0 to 3V · 0 to 5V (default) · 0 to 10V · ±1V · ±2V · ±3V · ±5V · ±10V. Unipolar ranges run from 0 V up; the ± ranges swing both ways about 0 V. |
| Slide (0%) | 0 to 100%. How much of each step is spent gliding to the new value. At 0% the CV jumps; at 100% it glides all the way, step to step. |
| Quantise (Off) | Snaps the CV to the track's scale and root, before any Slide. Off, the CV is continuous. |
| Scale (Global) | Global, or one of 13 scales for this track alone. Global follows the algorithm's Scale on the Global page. |
| Root (Global) | Global, or C to B for this track alone. Global follows the algorithm's Root. |
| CV out, CV out mode | The bus the track's CV goes to (None by default), and whether it replaces what is on the bus (the default) or adds to it. |
| Gate out, Gate out mode | The same for the track's gate. |
| MIDI channel (0) | 0 (off) or 1 to 16. The channel this track sends MIDI notes on. See MIDI. |

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

The clock is one pulse per beat (see Global parameters). Rate multiplies or divides that for each track, so tracks can run against each other.

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

## Global parameters

These are on the `Global` page.

| Parameter | What it does |
|---|---|
| Track (1) | 1 to 8. The track the pots and the screen are on. |
| Catch all (Off) | A momentary action: setting it to Go catches every free track (or releases all, if all are caught) and it returns to Off by itself. This is what the right pot push does. It can be mapped. |
| Clock source (Internal) | Internal, External or MIDI. Internal uses the BPM below. External steps on each rising edge of the clock input. MIDI follows incoming MIDI clock. |
| BPM (120) | 20 to 300. The internal clock's tempo. Each pulse of an external clock counts as one beat, the same as the internal clock. |
| Run (On) | Starts and stops the clock. Off, no track steps. |
| Freeze (Off) | Nothing advances: every CV holds its value and sounding gates stay as they are. |
| Scale (Natural minor) | The scale Quantise snaps to on every track whose Scale is Global. |
| Root (C) | The key note of that scale, for every track whose Root is Global. |
| Gate length (50%) | 5 to 100%. How long every gate stays high, as a share of the step. |
| Gate level (5 V) | 1 to 10 V. The height of every gate. |
| Clock input (1) | The bus an external clock arrives on. |
| Reset input (None) | The bus a reset trigger arrives on. A rising edge restarts every track from the beginning of its pass on the next clock pulse. |
| Catch all input (None) | The bus a trigger arrives on to do what Catch all does. |
| MIDI dest, MIDI velocity, MIDI note at 0V | See MIDI. |

> **One key or eight.** Leave every track on Global and the whole algorithm plays in one key: change Scale and Root once. Set a track's own Scale or Root and it goes its own way, for a bass in minor pentatonic under a lead in the full minor scale, or a drone a fifth away.

## MIDI

### Note out

Each track can send its notes as MIDI. Set the track's **MIDI channel** to 1 to 16; at **0**, the default, the track sends none. The notes of a track are sent as:

- **Pitch:** `MIDI note at 0V` (default 36, C2) plus the track's CV in semitones, at one volt per octave, rounded to the nearest note. Quantise a track and it sends notes of its scale.
- **Start and end:** a note starts on every step that fires, at the value the CV is moving to (so Slide does not smear the pitch), and ends when the track's gate falls. MIDI timing is always the audible gate.
- **One note at a time per track.** Changing the track's channel or the destination while a note is sounding ends it first.
- **Velocity and destination** are shared by all tracks: `MIDI velocity` (1 to 127, default 100) and `MIDI dest`, which can be any mix of the breakout, the select bus, USB and the disting NT's own internal MIDI (to play another algorithm, such as Poly FM, from Fluke). The default is the breakout.

### Clock in

Set **Clock source** to **MIDI** and Fluke follows incoming MIDI clock: 24 clocks make one beat, one x1 step. **Start** restarts every track from its first step, **Stop** holds the clock and **Continue** carries on from where it stopped.

## Routing

Each track has a **CV out** and a **Gate out**. They start on **None**, so a track touches no bus until you give it one.

| Output | What it carries |
|---|---|
| CV out (1 to 8) | The track's random voltage, one new value per step: 0 V up to the track's Range, or ± the Range for the bipolar settings. Held between steps (and glided, if Slide is up). |
| Gate out (1 to 8) | A gate on every step that passes Chance, at the Gate level (default 5 V) for as long as Gate length says. A resting track sends none. |

Each output has a mode: **Replace** (the default) writes the track's signal to the bus, and **Add** sums it onto whatever is already there.

## Presets

A preset saves every parameter, and each caught track's loop with its hit pattern, so a preset reloads exactly as you left it. **Caught** is a parameter, so a preset, or a mapped CV, can catch and release a track.

## Installing

Fluke is free. It needs **disting NT firmware 1.19 or later**.

1. Copy `fluke.o` to the `programs/plug-ins` folder on the disting NT's SD card.
2. Put the card back and start the disting NT (or rescan the plug-ins).
3. Add **Fluke** to a preset: it is in the algorithm list under its name.

## Troubleshooting

**Nothing is moving.**

Fluke needs a clock to step. Check **Clock source**: Internal needs nothing; External needs a clock on the Clock input bus; MIDI needs MIDI clock and a Start. Also check **Run** is On and **Freeze** is Off.

**I hear or see nothing from a track.**

A track's CV out and Gate out start on None. Give each a bus on its track page.

**Pushing the left pot does nothing.**

A track can only catch what it has played. Wait for it to step at least once. If the track's Rate is slow, that can take a while.

**The loop never changes.**

Mutate at 0% repeats the loop exactly. Turn the track's Mutate up. Mutate does nothing to a free track.

**A gate is missing, and the CV didn't change.**

That step missed its Chance (or the track is resting through a Breathe pass). A missed step holds the CV on purpose.

**The pots don't respond after I change page or track.**

They pick up where the setting is: move the pot past the setting's current value and it takes over.

**The encoders do nothing.**

On the Fluke screen they are switched off, so they can't change a setting you can't see. Press button 2 for the parameter list, where they work as usual.

**The notes aren't in my key.**

Quantise must be On for the track. Then check the track's Scale and Root: if they're on Global, the Global Scale and Root decide.

**No MIDI comes out.**

Set the track's MIDI channel above 0, and check MIDI dest isn't None.

## Specifications

| Format | disting NT algorithm | Firmware 1.19 or later. Free. |
|---|---|---|
| Tracks | 8 | Each with its own style, Chance, Rate, Swing, Length, Direction, Breathe, Range, Slide, Quantise, Scale, Root, Mutate, Caught and MIDI channel |
| Loops | 1 to 64 steps | Values and hit pattern stored per step; each track remembers its last 64 steps; saved in presets |
| Styles | 7 | Open · Midwater · Shallows · Squall · Tide · Current · Deep |
| Rates | 29 | /64 to x64 |
| Directions | 15 | Forwards to Anchor |
| Scales | 13 | Chromatic and twelve more, with any of 12 roots |
| CV outputs | 8, on any buses | 0 to 1, 2, 3, 5 or 10 V, or ± 1, 2, 3, 5 or 10 V |
| Gate outputs | 8, on any buses | 1 to 10 V, 5 to 100% of the step |
| Clock | 20 to 300 BPM | internal, one pulse per beat from a bus, or MIDI clock |
| MIDI | note out per track | 16 channels; any of breakout, select bus, USB and internal |

Fluke's engine is original. It uses no third-party DSP.

Fluke for the disting NT · Ormer Modular · made in Guernsey

catch it
