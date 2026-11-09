<p align="center"><img src="docs/images/fluke-banner.svg" alt="Fluke by Ormer Modular" width="100%"></p>

<p align="center">
<img src="https://img.shields.io/badge/licence-proprietary-lightgrey" alt="licence: proprietary">
<img src="https://img.shields.io/badge/platform-disting%20NT-e2a24a" alt="platform: disting NT">
<img src="https://img.shields.io/badge/firmware-1.19%2B-blue" alt="minimum firmware 1.19">
<img src="https://img.shields.io/badge/GUID-Fluk-lightgrey" alt="GUID: Fluk">
</p>

<p align="center"><em>Eight tracks of random CV. Catch what you like and it becomes a loop.</em></p>

# Fluke

Fluke is a sibling to Shoal, Ormer Modular's generative melody sequencer, and a lot smaller. It is a CV
generator with eight tracks of ever-changing random voltage. When something sounds right you catch it, and the
last stretch that played becomes a loop. A Mutate setting then decides how much that loop drifts each time round,
from perfectly still to slowly wandering.

Each track has its own style of randomness, plus Chance, Rate, Swing, Direction, Slide and Quantise, with the key
set per track or for the whole algorithm. Every track can run from the global clock or from a clock of its own, and
can send its notes as MIDI as well as CV and gates.

On the disting NT, three pots edit the picked track, the centre pot push turns the page, the left pot push catches
and the right pot push catches all. Everything else is an ordinary parameter, so it maps to CV, MIDI or I²C like any
other.

<p align="center"><a href="https://ormermodular.github.io/fluke/nt/">disting NT manual</a></p>

## Installing

Fluke for the disting NT is free and needs [firmware 1.19 or newer](https://www.expert-sleepers.co.uk/distingNTfirmwareupdates.html).

1. Download `fluke-plugin.zip` from the [latest release](https://github.com/ormermodular/fluke/releases/latest).
2. Unzip it at the root of the disting NT SD card. It installs `fluke.o` at `/programs/plug-ins/ormermodular/fluke.o`.
3. Restart the module or remount the card, then add Fluke.

## Credits

Thanks to the disting NT testers for their time and ideas, and to Expert Sleepers for the disting NT and its plug-in API.

## Licence

Proprietary. Fluke is closed-source software, free to use with the disting NT. See [LICENSE](LICENSE). Made in Guernsey.
