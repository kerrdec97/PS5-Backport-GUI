# Reporting issues

**All technical bug reports must be submitted through [GitHub Issues](https://github.com/kerrdec97/PS5-Backport-GUI/issues).**

[Report a bug](https://github.com/kerrdec97/PS5-Backport-GUI/issues/new?template=bug_report.yml)

Reports without logs or meaningful diagnostic evidence can't be investigated.

## 1. The app's own logs: Export logs

Click **Export logs** in the top bar. A ZIP named `PS5BackportGUI_logs_<date>_<time>.zip` is saved to your Desktop
and Explorer opens on it.

It contains only this program's logs: the activity log, and for every run its result, the engine's plan, the build
log, engine reports and any error trace, plus your settings file and a short system summary. It contains **no game
files**.

Attach this ZIP to your GitHub issue with your description: game, PPSA, version, exact
firmware, console model, options used and what happened.

If a run failed, the app also offers to save this ZIP when the run finishes.

## 2. Console evidence: Console Logs tab

For crashes, black screens, missing audio and PS5 Pro problems, a **klog** is strongly recommended.

You need a jailbroken console with an ELF loader listening on port 9021 (the default), and the PC and console on the
same network.

1. Open the **Console Logs** tab, enter the console's IP address and click **Connect**. With *Send klog + debug
   payloads on connect* ticked, the tab sends its bundled klog, FTP and debug payloads to the loader and starts
   streaming the klog.
2. Start the game and reproduce the problem.
3. **Crash:** when the console writes a crash dump, the tab downloads it automatically and saves
   `PS5_logs_<ip>_<time>_crash_<…>.zip`. Attach that ZIP.
4. **Freeze or black screen without a crash:** click **Capture hang** while it is stuck, then **Save & Zip logs**.
5. **Other problems:** click **Save & Zip logs** after reproducing it.

Logs are saved to `Desktop\PS5 Logs` (**Open folder** opens it).

If you use another klog tool, close it first: the console accepts one klog connection at a time.

## 3. If you can't capture a klog

Say so in the form and explain why. Then give as much as you can: the error code, a photo or screenshot of the error,
exactly when it happens, and whether other games or another firmware behave differently.

## Privacy

Before attaching anything:

- remove personal information, credentials and tokens;
- remove private IP addresses where they are not needed (log file names contain the console's IP; renaming is fine);
- remove unrelated private data; and
- **never upload game files, game executables or other copyrighted binaries.** The logs ZIPs never contain them.

Incomplete reports receive `needs-information` and a request explaining the missing details. After 14 days without a response, they may be closed and reopened when evidence is available. Alternative meaningful evidence is accepted when klog capture is not possible. Closing a report does not mean it has been fixed.
