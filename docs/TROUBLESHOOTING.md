# Troubleshooting

There are no universal fixes for console-side problems. This page explains what each problem usually means and what
evidence to collect. When in doubt, report it with the logs described in [Reporting issues](REPORTING_ISSUES.md). **Report technical problems through [GitHub Issues](https://github.com/kerrdec97/PS5-Backport-GUI/issues).**

## The program

### It doesn't start, or shows "The bundled backport engine could not be prepared"
- Make sure the drive with `%LOCALAPPDATA%` has at least 1 GB free.
- Antivirus software can block the engine from unpacking. Check its quarantine.
- Close the program, delete `%LOCALAPPDATA%\D97B`, and start it again (it unpacks a fresh copy).
- Still failing? Report it with the newest `app_<date>.log` from `%LOCALAPPDATA%\Deckerr97BackportGuiBeta\logs`.

### A game isn't listed
- A game folder must have `eboot.bin` directly inside it. Point *Add folders* at the extracted game, not at a ZIP or
  disc image (those aren't supported).
- Only 6 folder levels below each scan location are searched by default (*Settings → Subfolder depth*).
- The backport and originals folders are never scanned.

### "Already backported" / "This game folder already contains backport files"
The folder already has the backport fakelibs in it. Originals can't be captured from a patched folder. Use an
unmodified copy of the game, or *Settings → Restore originals from a backup* if this program applied it.

### The run can't start: destination errors
The backport and originals folders must both be set, must be two different folders, must not be inside each other or
inside a game folder, and must have enough free space. The message names the folder at fault.

### A game fails during the backport
The row shows **Failed** with the reason. Common ones:
- **"Target SDK N is higher than this game's own SDK"**: choose a lower Target SDK.
- **"The SDK N build was refused"**: for example, executables in a format the signer can't rewrite. Build with SDK 4.
- **"No safe backport was produced"** or **"No backport is needed"**: the engine found nothing it can fix with a
  confirmed fix, or something it must not touch. This is reported, not guessed. Please report it with the logs.

After a failed run the program offers to save a logs ZIP. Attach it to your report.

### "Partial"
The backport was built, but the ZIP or *Apply to game folders* step didn't finish. Details are in the row's
*Show details*. An interrupted apply is rolled back automatically, and offered for rollback at the next start if the
program was closed during it.

### The output ZIP is missing or invalid
Every ZIP is re-read and checked against its recorded hashes before the run reports success. If a ZIP still won't
open, check free space and antivirus, then report it with the logs.

## On the console

A finished backport has passed offline checks only. **It is not proof that the game works.**

### Black screen or GPU hang
- On **FW 5.00 or later**, try **Target SDK 5** (or higher, up to the game's own SDK). This has fixed some black
  screens, not all.
- On a **PS5 Pro**, try the **PS5 Pro fix** option.
- Report it with a klog. Use **Capture hang** in the Console Logs tab while the screen is black.

### Crash on startup or during gameplay
Report it with the crash ZIP that the Console Logs tab saves automatically when the console writes a crash dump. Note
exactly when it crashes.

### No audio or broken audio
Every build is checked for a known audio failure on all firmware bands, but other audio problems exist. Report it with
a klog, and include your audio output setup (TV, AV receiver or headphones; stereo, 5.1 or 7.1).

### Save data problems
Report it with a klog captured while saving or loading, and describe the exact action.

### Works on one firmware or model but not another
This is expected in some cases. Report it with the exact firmware and model for both the working and the failing
console.

### The game doesn't appear or won't load
Check that the backport files were copied with their folder structure (`eboot.bin` at the game root, `fakelib\`,
`sce_module\`). An SDK *N* build only loads on firmware *N*.00 and later.

### No klog
- The console needs an ELF loader on the port shown (9021 by default) and must be on the same network.
- Only one klog connection is accepted at a time: close other klog tools.
- If *Connect* stays on *Connecting…*, check the IP and the loader. If you still can't get a klog, say so in your report
  and give the other evidence.
