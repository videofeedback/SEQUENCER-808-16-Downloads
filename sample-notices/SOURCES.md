# Factory TR-808 recordings

Recorded by Michael Fischer / Technopolis, September 8, 1994. The original notes describe recordings made directly from an actual Roland TR-808's individual outputs, at 16-bit / 44.1 kHz, with individual hits selected and edited by the original author. They are hardware recordings, not synthesized emulations or samples of another drum machine.

Source mirror: https://github.com/fluid-music/open-drums/tree/475cc3314fe06f6d1af02e9790ad9707c1f2b26b/tr-808

Original source identified by that mirror: http://machines.hyperreal.org/categories/drum-machines/TR-808/samples/

The original author's free-sample statement is preserved in `TR808-original-notes.txt`. The mirror's attribution and licensing description are retained in `upstream-README.md`, and its package metadata declares ISC in `upstream-package.json`. These third-party recordings have separate provenance from the plugin code; this project does not assert a new CC0 dedication over them.

All 16 WAV files are byte-for-byte copies of the pinned source, with SHA-256 hashes in `manifest.json`. No trimming, normalization, EQ, compression, saturation, effects, or pitch shifting has been applied by this project. The recording author's original editing is part of the source material.

Bass drum, snare, toms, congas, cymbal, and open hi-hat use the hardware's middle control settings (the 50 suffix). Rim shot, clap, cowbell, closed hi-hat, claves and maracas use their single recordings. No tuned/processed derivative files from the source repository are used.

With neutral controls (Tone 0%, Tuning 0 semitones, Decay 100%), playback only scales amplitude for the level controls and Rack's audio voltage convention. When Rack's sample rate differs from 44.1 kHz, interpolation preserves the original playback duration and pitch. Version 2.2 adds optional per-lane tone filtering, pitch adjustment by resampling, and a decay envelope during playback; these never modify the source WAV files. The optional accent boost and hi-hat choke are disabled by default.
