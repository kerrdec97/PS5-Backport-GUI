# Changelog

## 18 October 2026

## New: PS5 Pro PSSR 2 test

Experimental work addressing [issue #6](https://github.com/kerrdec97/PS5-Backport-GUI/issues/6). **This has not yet been tested on a PS5 Pro. Tester reports are the first hardware check; this is not a confirmed fix.**

- New **PS5 Pro PSSR 2 test** option builds a Pro-only ZIP named `… Pro PSSR2 test backport files.zip` for games using PSSR.
- The PSSR library uses the console's real Pro, app-info and title queries instead of always-negative stubs. This is intended to let the game select its requested PSSR model (for example `13.00A`) and permit the system PSSR upgrade.
- Corrects the bundled AGC library's always-negative Pro detection so games can select their Pro/PSSR path.
- On Pro firmware 9.x–12.x, restores the game's requested PSSR version when the console drops it.
- Refuses a requested model absent from the packaged files. Games without PSSR receive the normal ZIP with a note.
- New row-menu action **Make a PS5 Pro PSSR 2 test from a backport** accepts an existing backport ZIP or backported game folder without originals. Folder input produces a small ZIP containing only changed files.
- **Pro firmware 9.00+ only.** Base PS5 consoles do not run PSSR and should keep the normal FW 4xx ZIP.

## Bug fixes

- Changes targeting [#2](https://github.com/kerrdec97/PS5-Backport-GUI/issues/2), [#7](https://github.com/kerrdec97/PS5-Backport-GUI/issues/7) and [#8](https://github.com/kerrdec97/PS5-Backport-GUI/issues/8) (MGS4, 007 First Light, Planet of Lana): handles dumps whose `sce_sys/about/right.sprx` fails conversion with `Invalid param magic 0x79A6EB9E` by replacing that file with the standard copy. Other conversion failures now explain that the dump is probably still encrypted. These build changes do not establish gameplay compatibility.
- Ignores invalid SDK/firmware values such as 0.00, 70.00 or 92.00 from repacked `param.json` files and reads the SDK from `eboot.bin`, avoiding false target-SDK refusals.

## Usability

- **Report a problem** pre-fills SDK/fakelib options and the game's title, PPSA and version.
- **Apply to game folders** warns when the PSSR 2 test would write Pro-only files into the folder.
- Tooltips stay on-screen; PSSR help text is shorter.
- Antialiased checkbox ticks and rounded boxes.
- Output fields show the end of long paths and use Windows backslashes.

## Validation and limitations

The maintainer reports passing beta (58) and root (941) test suites, with PSSR 2 builds completing end to end through the EXE. These tests were not rerun during this upload. Offline checks are not console validation. Black screens, crashes, missing audio, save problems and firmware/model differences remain possible. Keep original files and backups.

Issues #3, #4, #5 and #9 still require logs or separate per-game investigation; #9 needs a klog showing the unresolved NID. No issues are being closed by this release.



## Early Testing Beta

First public Windows x64 testing release: batch extracted-game processing, SDK selection, verified output and original-file backup ZIPs, optional journaled apply/restore, console log collection and support-log export.

SDK 5–13, PS5 Pro fixes and console diagnostics remain experimental. A successful offline build is not a console test. Linux and macOS releases follow when the maintainer is happy with Windows testing.
