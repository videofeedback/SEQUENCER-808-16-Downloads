# SEQUENCER 808-16 — sample-library drum machine

Version 2.10.2 for VCV Rack 2 / macOS ARM64 and Windows x64. Both use the same shared content; see [installation](INSTALLATION.md), [Mac guide](MACOS.md), [Windows guide](WINDOWS.md) and [content inventory](CONTENT.md). An original TR-808-inspired step sequencer with a recorded TR-808 factory library and importable sample libraries. No other drum modules are required. Not affiliated with Roland.

The plugin and module now appear as **SEQUENCER 808-16**. Internal plugin/model IDs, sample-library folders and preset formats retain their original identifiers so existing patches and presets continue to load.

**Free of charge under the [proprietary freeware license](LICENSE.txt).** Code reuse and redistribution require permission. See [installation and troubleshooting](INSTALLATION.md) for the manual installer and the four complete examples. This plugin is distributed independently of the VCV Library. Support: [admin@comfycode.ai](mailto:admin@comfycode.ai).

## Choose an example workflow

Open [the illustrated workflow guide](examples/SEQUENCER-808-16/START%20HERE.html) for screenshots, zoomable close-ups, all 16 sound recipes, saving instructions, four matched patches and audio previews.

- **01–02 Sequencer:** pre-processed TR-808 samples in a two-row drum machine, with all 16 mute/solo controls.
- **03–04 Modular:** original recordings with visible, named VCF/Percall/dry-wet chains in four rows.
- Each workflow has a basic 110 BPM groove and a 118 BPM looping song: A×2, B×2, C×2, I×1.

All sample assets are embedded. Use Clocked RUN to start; save the entire .vcv patch to retain the complete setup. See the collection guide for dependencies and editing instructions.

## Quick start

1. Restart Rack after installing the update.
2. Open `examples/Rhythm16-808-Drum-Machine.vcv`. It contains SEQUENCER 808-16 and Rack's built-in Audio 2, already connected.
3. Choose your audio device in Audio 2 if needed. Press START / STOP.
4. Select BD, SD or another instrument key, then click the colored steps to program that lane. Each drum has LEVEL, TONE, TUNING and DECAY knobs. MASTER controls MIX AUDIO.

To add it to another patch, search **SEQUENCER 808-16** under **Video Feedback**. Connect **MIX L / R** to your audio output module. Use L alone for mono. The factory A/B patterns are ready to play; C–I start empty.

## Patterns A–I and song presets

The nine buttons **A B C D E F G H I** at the top select the pattern to edit and queue for playback. Each bank stores all twelve lanes (eleven drums plus accent), with sixteen steps per lane. During playback, a change takes effect at the next loop boundary. The active bank has a light strip; the orange bank is selected for editing. The original PATTERN selector also offers all nine banks.

Each pattern independently remembers **tempo, swing, length, all eleven levels/tone/tuning/decay controls, master level, accent boost, alternate voice switches, hat choke, and its own sixteen sample assignments**. Clicking a letter saves the outgoing controls and recalls that letter’s settings. Knobs always edit the orange-selected letter; the playing bank uses its own settings, even when you edit a different bank. The display shows the playing bank’s tempo and length. Song Mode and PAT CV recall these settings at the playback boundary. External clock still determines timing when connected.

Right-click any **A–I** letter and choose a destination from:

- **Copy Pattern** — copy all twelve step lanes; keep destination settings.
- **Copy Settings** — copy all the controls and sample/library assignments; keep destination steps.
- **Copy Pattern+Settings** — copy both.

Copies replace the destination contents selected by that command and support Rack **Undo/Redo**. Copying to the currently edited bank updates the knobs. Pattern length belongs to Settings. Sample assignments belong to Settings too. Copies initially share the same recordings; assigning a different sample or selecting a new library afterward changes only that destination pattern.

Older patches and song presets retain their original controls by initializing every bank with the former shared settings and sample kit. Older A/B patches keep A/B notes, and C–I start empty. Save again to retain future per-pattern changes.

### Reusable pattern presets

Right-click any **A–I** letter:

- **Save Pattern Preset…** saves that letter to a portable **`.r16pattern`** file, including all twelve step lanes, all 55 settings (tempo, swing, length and every sound control), and its sixteen sample slots with original audio files.
- **Load Pattern Preset…** replaces that letter’s steps, settings and samples. The other eight banks, edit-bank selection and song arrangement remain unchanged. Loading into the selected bank updates its knobs. Rack **Undo/Redo** restores/reapplies the whole loaded pattern, including its samples.

Files default to Rack’s `VideoFeedbackRhythm/patterns/` folder; you can save and load elsewhere. A preset can be loaded into any letter in another song or shared with another computer running v2.10.0 or later. Source libraries are not required. Saving the destination song or Rack patch embeds the imported samples again. Shared song presets (`.r16song`) and single-pattern presets (`.r16pattern`) use separate commands and file formats.

Loading takes effect on the next audio frame, so loading into the playing bank changes its sounds immediately. Invalid or incomplete files are rejected before replacing the destination. Saves use a temporary file and atomic replacement. Audio limits are 128 MiB per source file, 512 MiB of files per preset, and 256 MiB of decoded audio per kit; the module’s total 512 MiB decoded limit still applies. Extracted audio lives under `VideoFeedbackRhythm/pattern-samples/` and is retained for loaded patterns and Undo/Redo.

### Song Mode: arrange patterns in any order

Choose **SONG → Edit arrangement…**. The editor starts with two rows, A × 1 and B × 1, with Song Mode off. An arrangement can contain **up to 64 rows**, and each row can play any bank A–I **1–64 times**. For example: `A × 4 → C × 2 → B × 1 → I × 4 → A × 2`.

- **ADD ROW** appends the bank currently selected for editing, with one repeat.
- Click the pattern name or repeat value to choose from a menu; adjacent arrows and −/+ change the value one at a time.
- **UP / DOWN** reorder rows, **COPY** inserts a duplicate immediately below, and **REMOVE** deletes a row. Scroll or use page arrows for more rows. Arrangement edits support Rack Undo/Redo.
- Turn **SONG MODE ON**, then **START / STOP**. Song Mode is also a checkbox in the SONG menu. **END: LOOP SONG / STOP** chooses whether to repeat the whole arrangement or finish after the final row.
- The highlighted row and status show the current pattern and repeat. The main display shows `S01.02` for row 1, repeat 2, or `DONE` after completion. **CLOSE** returns to the drum controls without stopping playback.

Every repeat plays one complete pattern cycle at that pattern’s saved LENGTH setting. The arrangement advances at loop boundaries using either each pattern’s saved tempo/swing or external clock. The final pattern finishes its full duration before Stop-at-end takes effect; existing audio tails can ring out. Empty arrangements stop without playing a pattern.

Start always begins at row 1. **RESET SONG** or the existing RESET button/input returns to row 1 and pattern step 1; while stopped it arms the next start. With an external clock, a reset followed by a clock edge starts step 1. A high RUN input retains transport priority; at the end of a non-looping song it must go low then high, or receive RESET, before starting again. An explicit arrangement edit also rearms it.

**Song Mode takes playback priority over PAT CV and the manual bank request.** The A–I buttons still select the bank you edit, and PAT CV resumes control when Song Mode is off. Edits or mode changes made while playing take effect at the next pattern boundary and restart the revised arrangement from row 1. Stopped edits apply immediately. `Arrangement changes queued` indicates pending edits.

**SONG → Save song as…** stores the row order, every repeat count, Song Mode, and the Loop/Stop choice together with all patterns, BPM, knobs and samples. Saving the Rack patch stores the arrangement too. Loading restores transport stopped at the beginning. Older patches and presets without an arrangement load in Pattern Mode.

### Patch a pattern selection

Connect a CV source to **PAT CV**, beside the PATTERN selector. It selects playback using the first channel, rounded to the nearest whole volt:

| Voltage | Pattern |
| --- | --- |
| 0 V | A |
| 1 V | B |
| 2 V | C |
| 3 V | D |
| 4 V | E |
| 5 V | F |
| 6 V | G |
| 7 V | H |
| 8 V | I |

Half-volt boundaries round upward (0.5 V selects B); negative voltages clamp to A and voltages above 8 V clamp to I. This is an absolute selection input: a trigger does not advance to the next bank. Use a stepped CV sequencer, constant voltage, or another CV source. A connected cable at 0 V selects A.

When Song Mode is off, CV overrides the playback request while connected. During playback the latest CV is sampled at step 1 of each loop; a brief pulse between boundaries is not latched. While stopped, selection follows CV immediately. With external clocking, send the selection CV before or together with the clock edge that starts the next loop. Disconnecting returns to the button-selected bank at the next loop, or immediately while stopped.

The **A–I buttons remain your edit-bank selection**, so a changing CV will not move the steps you are editing. A blue dot marks the CV-selected bank, the white strip marks the bank playing, and orange marks the edit bank. The display shows `CV:I` when I is selected or `CV>I` when I is queued. Presets retain the manual bank selection; live input voltage and cables belong to the Rack patch. Non-finite input falls back to the manual selection.

Click **SONG → Save song as…** to create a **`.r16song`** file. It contains:

- Independent BPM, swing and pattern length for every A–I bank, plus the selected bank and edit lane.
- Every bank’s persistent knobs/switches: all levels, master, tone, tuning, decay, accent, alternate voices and hat choke.
- All nine banks, including every drum and accent step.
- The complete arrangement, row repeat counts, Song Mode and Loop/Stop-at-end setting.
- The exact original audio files for all nine pattern kits, including alternate pads and sounds mixed from different libraries. Shared kits are embedded once.

**SONG → Load song…** restores the file into this module. Songs saved in Rack's `VideoFeedbackRhythm/songs/` folder also appear directly in the menu. The folder can be opened from that menu; files may be saved elsewhere and loaded with the file picker. Keep the `.r16song` extension. The single file can be moved or shared with another computer running this plugin. Audio is copied unchanged into the preset and is not rendered with knob settings. The file stores settings and patterns, not a mixed audio recording.

Loading restores transport stopped and resets the playhead. A connected high RUN gate can start it again, and an external clock still overrides internal BPM. Momentary START/STOP, RESET, CLEAR and step-button presses are not recalled as held buttons. Audio-device settings, cables and other Rack modules remain part of the Rack patch, outside a song preset.

A preset is decoded and validated before replacing the song. Files are written through a temporary file, so a failed save keeps the previous preset. Loaded audio is kept under `VideoFeedbackRhythm/song-samples/`; saving the Rack patch embeds it again. Original source libraries are not required. Limits are 128 MiB per source file, 512 MiB of audio files per song, 256 MiB of decoded audio per kit, and 512 MiB of decoded audio across distinct pattern kits. New presets use format version 2 and require plugin v2.9.0 or later; version 1 presets remain supported and initialize all patterns with their single kit. Do not manually delete the song-samples folder while unsaved patches depend on it.

## Sample Library

Select an **A–I** letter, then click **LIBRARY A** (or the corresponding letter) at the top of the panel, or right-click the background. Select **TR-808 (factory)** or an imported library. This replaces only that pattern’s kit and preserves its steps and controls. The label and pad names follow the selected edit bank. Song Mode and PAT CV play the kit belonging to the active playback bank. Changing a playing kit stops its old tails; switching to a different kit at a pattern boundary also stops those tails. Editing a different bank’s kit leaves the playing voices alone. Pad labels show the selected sample names; the menu lists full names, sample rates, duration and mono/stereo information.

### Browser: preview and mix samples from different libraries

Click **BROWSE** at the top of the module (or **Browse / preview / assign samples…** in the context menu). The browser opens over the controls without changing your sequence. You can also hover over the module and press **Shift+B** to toggle it; **Escape** closes it.

1. Choose a library on the left, or **All libraries**. Search libraries and samples independently. Sample search also matches the source library name. Use the arrows or scroll over either list to browse more results.
2. Click a sound to audition it. **PREVIEW** retriggers it; **STOP** silences it. **AUTO PREVIEW** can be turned off. The selected sound shows its original sample rate, channels and duration.
3. Choose a destination on the right, then click **ASSIGN TO PATTERN …**. The destination header identifies the selected pattern. Repeat with sounds from any library. Pads 01–11 are the drum voices; 12–16 are the optional alternate voices for pads 03–07. Assigning a main/alternate sound selects that voice for its lane. Accent has no sample.
4. Click **CLOSE** to return to the sequencer. Closing stops audition playback. Save your song preset or Rack patch to embed every pattern’s kit, or export the current pattern’s library to reuse it elsewhere.

Previews play through **MIX L/R**, including while the sequencer is stopped; connect these to an audio output and turn up MASTER. Preview is a separate neutral one-shot voice at 60% gain before MASTER. It ignores pad level/tone/tuning/decay and never enters VOICES or trigger outputs. You can audition over a running pattern. Source files are never processed or rewritten.

Assignment updates only the selected pattern and shows the new sample/source on its destination. Its steps and sound controls remain intact; the matching main/alternate switch is selected automatically. The top selector reads **Mixed kit**. Export uses a unique `Mix-…` library name with the same import naming rules. Selecting a whole library replaces all assignments in the selected pattern only. **REFRESH** rescans imported libraries. Browsing does not load every library into memory; only the selected audition is decoded. The complete mixed kit retains the 256 MiB decoded-audio limit.

### Importing a library

1. Put your samples in one folder, with one file per sample slot.
2. Name each file `[PAD_NUMBER]-[LIBRARY_NAME]-[CUSTOM_SAMPLE_NAME].[format]`. Brackets are placeholders; do not include them.
3. Choose **Sample Library → Import library folder…** and select that folder.
4. The kit becomes available immediately and is copied into Rack’s user folder under `VideoFeedbackRhythm/libraries/`. **Open Sample Library folder** opens that location. Originals are copied unchanged; moving the source folder does not break the imported library.

Examples:

```text
01-Studio-Drums-Deep_Kick.wav
02-Studio-Drums-Dry_Snare.aiff
10-Studio-Drums-Open_Hat.flac
11-Studio-Drums-Closed_Hat.wav
```

The number is a **sample slot**, not a step number. The module has eleven sounding pads plus accent; the sixteen colored keys are sequencer steps. Slots 12–16 are optional alternate samples for pads 03–07.

| Slot | Main pad / factory sound |
| --- | --- |
| 01 | Bass drum |
| 02 | Snare |
| 03 / 12 | Low tom / optional low conga |
| 04 / 13 | Mid tom / optional mid conga |
| 05 / 14 | High tom / optional high conga |
| 06 / 15 | Rim shot / optional claves |
| 07 / 16 | Clap / optional maracas |
| 08 | Cowbell |
| 09 | Cymbal |
| 10 | Open hi-hat |
| 11 | Closed hi-hat |

Custom kits can put any sound on any pad. One or two digit numbers are accepted (1 and 01 both mean pad 1). Missing main pads are silent. Missing optional alternate samples fall back to their main pad. Accent remains a velocity lane and has no sample slot. The optional hat choke always links pads 11 and 10, regardless of their names.

All supported audio files in the folder must use exactly the same library name. Library names may contain hyphens, so `01-TR-808-Bass_Drum.wav` is valid. Parsing uses the first and last hyphens as separators: use spaces or underscores, **not hyphens**, in the custom sample name. Both names accept ASCII letters, numbers, spaces and underscores, up to 48 characters; library names also accept hyphens. Avoid leading/trailing spaces. Extensions are case-insensitive.

Duplicate slot numbers, mixed library names, invalid names and unreadable samples cancel the entire import and leave the current kit unchanged. Hidden files, subfolders and non-audio files are ignored. Existing library names cannot be overwritten; use a new name for a revised kit. TR-808 and factory are reserved for the built-in kit.

### Audio formats and quality

| Format | Supported high-quality options | Suggested use |
| --- | --- | --- |
| WAV (.wav) | 16/24/32-bit integer PCM; 32/64-bit IEEE float | 24-bit for recordings; 32-bit float for DAW exports |
| AIFF (.aif, .aiff) | 16/24/32-bit PCM | Uncompressed interchange, especially 24-bit AIFF |
| FLAC (.flac) | Lossless PCM, including 16/24-bit | Smaller libraries without loss of the encoded PCM |

Mono and stereo are supported at 8–384 kHz, up to 30 seconds per file. Import limits are 128 MiB per source file and 256 MiB of decoded audio per library. WAV/AIFF decoding uses dr_wav and FLAC uses dr_flac; their license notices are in `vendor/`. Lossy MP3/AAC imports are not supported.

Use the recording’s original sample rate; upsampling does not restore missing detail. Files are preserved byte-for-byte, without normalization, trimming or effects baked in. Playback uses Rack’s 32-bit float signal path, so 32-bit integer and 64-bit float source precision is converted to float. Stereo stays stereo through MIX L/R. Tone, tuning and decay remain optional playback controls; neutral settings preserve decoded samples at their native sample rate. Playback at other rates, or with tuning, uses linear interpolation.

### Saving, sharing and exporting

Saving a Rack patch embeds all nine patterns’ imported libraries and mixed kits using Rack’s patch asset storage. Shared kit assets are stored once; prior embedded folders are retained so undo can recover earlier assignments. The patch therefore retains its samples when shared with another computer that has this plugin installed. Library selection also saves with the patch. If neither the managed copy nor embedded audio is available, the panel shows **NO KIT** and produces no sample audio; it never silently substitutes the TR-808. Reimport that library or choose another kit. Trigger sequencing remains available.

**Export current library / naming template…** copies the current original audio files into a new folder using the naming convention. It does not render knob settings into the exported audio. Export the factory TR-808 as a template, rename its library component in every filename, replace the samples, then import your new kit. A ready-to-copy factory export is also provided in the workspace’s `Sample Libraries/TR-808` folder. Factory attribution travels with the export.

## Factory sounds

The kit contains 16 original Michael Fischer / Technopolis recordings from a real Roland TR-808's individual outputs, at 16-bit / 44.1 kHz: kick, snare, low/mid/high tom, rim shot, clap, cowbell, cymbal, open/closed hi-hat, low/mid/high conga, claves and maracas. Eleven drum lanes can play at once; the twelfth lane is accent.

Right-click the module background for the alternate voice switches:

- Low, mid and high tom can each become the corresponding conga.
- Rim shot can become claves.
- Clap can become maracas.

These select different recorded WAV files. Source files remain unchanged. With neutral sound controls, playback at 44.1 kHz passes the decoded PCM through exactly at unity gain; other host rates use interpolation to retain the original pitch and duration. There is no synthesized drum model, compressor, limiter, reverb or saturation. Recording provenance and hashes are in `res/samples/SOURCES.md` and `manifest.json`.

Each drum has a level knob. MASTER affects both MIX audio outputs. The AC knob adds optional volume boost to hits coinciding with accent steps; its default is zero. Optional closed-hat choking is in the context menu and is off by default, preserving full sample tails. Retriggering a lane restarts that sample. Different lanes overlap. Stopping transport allows existing samples to ring out; RESET silences them.

## Per-drum sound controls

All eleven drum lanes have independent controls. Alternate conga, claves and maracas sounds use the settings of their lane. These controls shape recorded samples; they do not recreate the original instrument's analog circuits.

| Control | Range and behavior | Neutral setting |
| --- | --- | --- |
| LEVEL | Drum volume, 0–100% | Factory default 80% |
| TONE | Negative values darken the sound; positive values remove low frequencies for a brighter sound. Blends toward a 1.2 kHz low-pass or high-pass filter. | 0% |
| TUNING | Continuous pitch adjustment, −12 to +12 semitones. Changing playback speed also changes the sample's duration. | 0 semitones |
| DECAY | 0–100%: adds an exponential fade to shorten the tail. 0% reaches −60 dB in about 20 ms; 50% in about 338 ms. 100% plays the full recorded tail. Cannot extend beyond the recorded sample. | 100% |

Sound controls apply to both MIX AUDIO and VOICES. They do not change the trigger outputs. Changes during a hit are smoothed over approximately 5 ms; each new hit starts with the current settings. Returning DECAY to 100% during a hit stops further attenuation without restoring volume already lost. Double-click a knob to return it to its default, or right-click to enter an exact value.

The accent lane retains its BOOST control and has no drum sample to shape.

## Sequencer controls

- **START / STOP:** start from step 1 or stop. Transport restores stopped on patch load (a high RUN input can start it).
- **RESET:** restart internally from step 1; externally, arm step 1 for the next clock edge. A simultaneous reset and clock triggers step 1. Reset alone does not start a stopped sequencer.
- **PATTERN / A–I buttons:** select A through I for editing. Playback changes at the next loop boundary; QUEUED indicates a pending change. Selection while stopped is immediate.
- **TEMPO:** 30–300 BPM. **SWING:** 0–50%, internal clock only. **LENGTH:** 1–16 steps; hidden steps are retained.
- **CLEAR:** erase the selected track in the edit pattern. Rack Randomize affects only that track. Initialize restores factory patterns and controls.
- Bright strips in the step keys show programmed hits. Red lights and the outlined key show playback position.

Patterns, levels, tone, tuning, decay, voice selections, choke and accent settings save with the Rack patch.

## Connections

| Port | Signal |
| --- | --- |
| PAT CV | Input: 0–8 V selects playback banks A–I, nearest whole volt; first channel; changes at the next loop while running. |
| MIX L | Mono mix when R is unconnected; left channel when R is connected. Controlled by MASTER. |
| MIX R | Right channel of the stereo mix, controlled by MASTER. Connect L and R for stereo. |
| VOICES | 11-channel polyphonic audio: pads 01–11; stereo samples are averaged to mono per pad. After per-pad level, before MASTER |
| Top BD…AC jacks | Original independent 10 V / 1 ms trigger outputs; retained for external instruments |
| TRIG POLY | All 12 trigger lanes, BD through AC |
| CLK OUT | 10 V / 1 ms pulse at each step |
| CLK IN | External sixteenth-note clock: one rising edge per step, 4 PPQN. Disables internal tempo/swing; still needs START or RUN high. |
| RESET | Rising-edge reset |
| RUN | Gate at least 1 V runs; low stops. Overrides START / STOP while connected. New high restarts at step 1. |

At unity drum level, a full-scale PCM value maps to 5 V audio. MIX sums voices without clipping or limiting; reduce MASTER when layering many loud sounds. The defaults leave headroom for the factory grooves.

## Upgrade and examples

Existing parameter and port IDs are unchanged, so 2.0–2.2 patches retain their patterns, settings and cables. Older patches select the TR-808 factory library. The appended right output adds stereo without changing the original mono routing. New tone, tuning and decay controls default to neutral. The panel is now 80 HP wide (previously 60 HP); existing patches may need neighboring modules moved to the right. The included drum-machine example already has the required spacing.

- `Rhythm16-808-Drum-Machine.vcv`: self-contained sampled drum machine with Audio 2.
- `Rhythm16-Starter.vcv`: standalone module.
- `Rhythm16-Drum-Demo.vcv`: the older external Befaco/VCV drum demonstration, retained for comparison.

