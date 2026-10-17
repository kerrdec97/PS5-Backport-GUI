# Roadmap

These are development priorities, not delivery promises.

1. **Automatic backport coverage:** improve dependency/import analysis, evidence-based patch selection, fakelib handling, audio checks, build verification and regression detection.
2. **PS5 Pro:** investigate model/firmware differences, especially below firmware 12.00, with better diagnostics and checks for regressions across console models.
3. **General compatibility:** investigate startup crashes, black screens, missing audio, save problems, unresolved dependencies, output validation and reproducibility.
4. **GUI:** improve batch management, progress, errors, selection, backups, SDK guidance and useful logs.
5. **SDK targets:** SDK 4–13 selection is already implemented. Improve validation and compatibility evidence for each target; SDK 5–13 remain experimental. No untested firmware support is promised.
6. **Diagnostics:** improve klog/crash collection and analysis, model and firmware tracking, regression testing and reproducible reports. Automatic hardware testing and core-dump analysis are not included in this release.
7. **Platforms:** release Linux and macOS once the maintainer is happy with Windows testing. Linux has an internal build; macOS packaging remains untested. No public date is confirmed.
