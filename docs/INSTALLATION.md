# Installation and first use

## Requirements

- **Windows 10 or 11, 64-bit.** Linux and macOS are coming once the maintainer is happy with Windows testing; no date is confirmed.
- About **1 GB free disk space** for the program's engine and working files, plus space for your backports.
- No Python, .NET or other runtime: everything is inside the program.
- For the **Console Logs** tab only: a jailbroken PS5 with an ELF loader on port 9021, on the same network as the PC.

## Install

1. Get `PS5-Backport-Windows-x64.zip` and `SHA256SUMS.txt` from the [GitHub release](https://github.com/kerrdec97/PS5-Backport-GUI/releases/tag/early-testing-beta).
2. Optional but recommended: check the download. In PowerShell:
   ```powershell
   Get-FileHash .\PS5-Backport-Windows-x64.zip -Algorithm SHA256
   ```
   The hash must match the line in `SHA256SUMS.txt`.
3. Extract the ZIP to a folder of your choice (for example `C:\Tools\PS5 Backport`).
4. Run `PS5BackportGUI.exe`.

The program is not code-signed, so Windows SmartScreen may show *Windows protected your PC*. Click **More info → Run
anyway** if the checksum matched. Some antivirus programs flag self-contained Python applications; check the checksum
rather than disabling your antivirus.

## First start

The first start of each version unpacks the backport engine (about 160 MB) into `%LOCALAPPDATA%\D97B\<version>`. The
status bar shows *Preparing engine…* and then *Ready*. Later starts are fast.

## Using it

1. **Add folders**: choose a folder that contains extracted games, or a single game folder. Subfolders are searched
   (6 levels by default; see Settings). A game folder is one with `eboot.bin` at its root. You can also drag folders
   onto the window. Scanning only reads files.
2. **Save to**: choose two *separate* folders:
   - **Backport ZIPs**: each game's `FW 4xx <PPSA> <Title> (<version>) backport files.zip` is saved here;
   - **Originals backup ZIPs**: each game's `<PPSA> <Title> (<version>) original files.zip` (the untouched originals of
     only the files the backport replaces) is saved here.

   Each folder also gets a `_backport_details` subfolder with the run's loose files, reports and manifests.
3. **Options**:
   - **Target SDK**: SDK 4 (default) loads on FW 4.00 and later. Choose SDK 5 or higher only for consoles on that
     firmware or newer (an SDK *N* build only loads on FW *N*.00+). SDK 5–13 are experimental.
   - **Apply to game folders** (off by default): also copies the backport into the game folder after a verified backup.
     Only use this on a copy of the game.
   - **PS5 Pro fix** (experimental): for black screens or GPU hangs on a PS5 Pro.
4. Tick the games and click **Start Backport**. Each game shows its own status; the Activity panel shows progress.
5. Copy the files from the backport ZIP over the game on the console, keeping their folder structure.

The fakelib providers a backport needs are added automatically; there is nothing to configure.

## Where things are stored

| What | Location |
|---|---|
| Settings and the list of applied backports | `%APPDATA%\Deckerr97BackportGuiBeta\` |
| Logs (`app_<date>.log`, and `runs\<run>\` per game) | `%LOCALAPPDATA%\Deckerr97BackportGuiBeta\logs\` |
| Backport engine | `%LOCALAPPDATA%\D97B\<version>\` |
| Console Logs captures | `Desktop\PS5 Logs\` |

**Export logs** collects the program's logs into one ZIP. **Settings → Open logs folder** opens the logs folder.

## Updating

Download the new release and replace the old `PS5BackportGUI.exe`. Your settings stay. The new version unpacks its own
engine on first start and removes old engine folders.

## Uninstalling

Delete the program folder, `%APPDATA%\Deckerr97BackportGuiBeta`, `%LOCALAPPDATA%\Deckerr97BackportGuiBeta` and
`%LOCALAPPDATA%\D97B`. Your backport and originals ZIPs are not touched.
