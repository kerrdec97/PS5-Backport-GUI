# Testing guide

1. Keep original game files and use a separate working copy. Process only files you own or are authorised to use.
2. Record game/PPSA/version, exact firmware, console model, loading method, storage, app build identifier and selected SDK/Pro options.
3. Select different backport and originals output folders. Leave apply disabled for the first run.
4. Keep manifests and the app's Export logs ZIP. A verified build passes offline checks only.
5. Deploy the intended output and test launch, audio, saves and gameplay. Record what was actually tested; leave other firmware/model combinations untested.
6. For a failure, capture klog/crash/hang evidence using Console Logs where possible. Redact private information and submit a [bug report](https://github.com/kerrdec97/PS5-Backport-GUI/issues/new?template=bug_report.yml). Never attach game binaries.
