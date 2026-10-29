# SEQUENCER 808-16: installation and first play

Version **2.10.2** targets **VCV Rack 2.6.6**, with separate **macOS Apple Silicon / ARM64** and **Windows x64** binaries. Both complete packages contain the same songs, patterns, examples, factory recordings and documentation. Intel Mac, Windows ARM64 and Linux packages are not provided.

Free to use under the included [proprietary freeware license](LICENSE.txt). Support: [admin@comfycode.ai](mailto:admin@comfycode.ai). The module is distributed independently, outside the VCV Library.

## Choose your package

| Computer | Complete ZIP | Plugin package inside Plugin/ |
| --- | --- | --- |
| Apple Silicon Mac | SEQUENCER-808-16-2.10.2-mac-arm64.zip | VideoFeedbackRhythm-2.10.2-mac-arm64.vcvplugin |
| 64-bit Windows PC | SEQUENCER-808-16-2.10.2-win-x64.zip | VideoFeedbackRhythm-2.10.2-win-x64.vcvplugin |

Download the complete Mac or PC ZIP from [the public release](https://github.com/videofeedback/SEQUENCER-808-16-Downloads/releases/tag/v2.10.2). The automatic Source code archives contain only this download repository’s documentation and assets, not an installable plugin.

Extract the complete ZIP. It contains `Plugin/`, `Content/`, `examples/`, platform installers, both platform guides, the full module reference and the shared content hash manifest.

## Install

1. Install and launch the matching edition of VCV Rack 2 once, then quit Rack.
2. Copy the matching .vcvplugin file directly into the plugin folder below. Keep it intact; Rack extracts it on startup.
3. Copy the contents of `Content/` into the Rack user folder. Merge folders and keep existing personal files.
4. Start Rack and search for **SEQUENCER 808-16**, brand **Video Feedback**.

| Platform | Default Rack user folder | Plugin subfolder |
| --- | --- | --- |
| macOS ARM64 | ~/Library/Application Support/Rack2/ | plugins-mac-arm64/ |
| Windows x64 | %LOCALAPPDATA%\Rack2\ | plugins-win-x64/ |

Optional installers: `INSTALL-MACOS.command` on Mac, or `INSTALL-WINDOWS.cmd` on Windows. Each installs the matching plugin and merges the shared content. Existing content files are preserved; differing files are reported for review. Use a backup before intentionally replacing your own presets. Custom Rack user folders are supported; see [MACOS.md](MACOS.md) or [WINDOWS.md](WINDOWS.md).

Platform binaries cannot be copied between operating systems. Songs, patterns, sample kits and complete patches can. Re-select the audio device on each computer.

## Examples and playback

For a simple first check, open `examples/Rhythm16-808-Drum-Machine.vcv`, choose the Audio 2 output device and press the sequencer's **START / STOP**.

The four complete examples are in `examples/SEQUENCER-808-16/` and in the installed `VideoFeedbackRhythm/examples/SEQUENCER-808-16/` folder:

| Example | Workflow | Tempo |
| --- | --- | --- |
| 01 Sequencer - Basic Groove.vcv | Prepared samples | 110 BPM |
| 02 Sequencer - Song and Fill.vcv | Prepared samples and song arrangement | 118 BPM |
| 03 Modular - Basic Groove.vcv | Original recordings with visible effects | 110 BPM |
| 04 Modular - Song and Fill.vcv | Visible effects and song arrangement | 118 BPM |

All four require **VCV Fundamental, Impromptu Modular, MindMeld** and Rack Core. Examples 03-04 additionally require **Befaco Percall** and **stoermelder PackOne / GLUE**. Install each dependency's matching platform binary separately through the VCV Library or vendor.

Open `examples/SEQUENCER-808-16/START HERE.html` for the offline illustrated guide. Choose your device in **Audio 2**, press **F4** to fit the modules, then **RUN on Clocked**. Complete examples open stopped. The song arrangement loops A x2, B x2, C x2, I x1. Save the whole .vcv patch to keep both sequencers, cables, mixer and effects.

## Find the songs and samples

Use **SONG** and **LIBRARY A-I** on the module. Right-click a pattern letter to load a .r16pattern file. See [CONTENT.md](CONTENT.md) for the shared-core inventory, transfer paths and the personal sample libraries not included in this distribution.

## Troubleshooting

- **Plugin missing:** quit Rack, check the architecture and plugin folder, then restart. A patch autosaved while the plugin was missing can omit its module; reopen the original example after the plugin loads.
- **OS blocks the plugin:** retain the error and obtain an approved build or resolve the applicable policy with the computer administrator. Recopying the DLL does not resolve an Application Control block. Do not disable protections as part of installation.
- **Other modules missing:** install the example dependencies; this plugin does not include their binaries.
- **No sound:** select Audio 2's device and output channels, start the appropriate transport, and check mixer mute/solo and levels.
- **Browser audition silent:** audition uses the sequencer's MIX L/R. In the complete examples, route those to a monitored spare mixer input; normal drum voices use separate outputs.
- **Empty content menus:** install Content/ into the Rack user folder, not inside plugins-*/VideoFeedbackRhythm/. Reopen the menu.
- **Guide images missing:** extract the entire ZIP and keep its folder structure.
- **Migrating a Mac patch:** use the Windows binary, install matching dependencies and re-select the Windows output device. Keep embedded audio or portable presets.

For support, include the plugin version, Rack version, operating system/architecture, exact error and example filename. [Official Rack installation reference](https://vcvrack.com/manual/Installing).
