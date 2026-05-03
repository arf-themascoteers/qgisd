# QGIS Source Learning Project

## Goal
Learn QGIS internals by building it from source and making real code changes.
Building is a means. Understanding the source is the end.

## Approach
- Arif runs all commands himself — agent guides, not executes.
- Each phase teaches something new about QGIS architecture.
- Finish with a visible code change confirmed in a live build.

## Environment
- OS: Ubuntu 24.04 LTS (required for Qt6 support)
- QGIS target: 4.x (main branch)
- Build system: CMake + ninja
- Qt: 6.6+ (Qt5 not supported in QGIS 4)
- C++ standard: C++20
- Python: 3.11+, PyQt6

## Source
- Repo: https://github.com/qgis/QGIS
- Build doc: https://github.com/qgis/QGIS/blob/master/INSTALL.md

---

## TODO

### Phase 1 — Environment Setup
- [x] Verify Ubuntu version is 24.04+ (24.04.4 LTS confirmed)
- [x] Install all build dependencies via apt
- [x] Verify tool versions (cmake 3.28.3, python 3.12.3, Qt 6.4.2)

### Phase 2 — Get the Source
- [ ] Clone QGIS repo from GitHub
- [ ] Explore top-level repo structure (understand what lives where)

### Phase 3 — Configure the Build
- [ ] Create a build directory
- [ ] Run CMake with correct flags
- [ ] Read and understand CMake output (what features are enabled/disabled)

### Phase 4 — Compile
- [ ] Run the build (ninja or make)
- [ ] Understand what is being compiled (libs, app, plugins, Python bindings)
- [ ] Fix any build errors if they arise

### Phase 5 — Run the Built QGIS
- [ ] Launch the compiled QGIS binary
- [ ] Confirm it runs correctly

### Phase 6 — Source Orientation
- [ ] Understand the major source directories (src/app, src/core, src/gui, etc.)
- [ ] Trace how the main window is constructed
- [ ] Locate a simple UI element in the source (e.g. a toolbar button or splash color)

### Phase 7 — Make a Visible Change
- [ ] Identify a safe, visible target (e.g. splash screen color, toolbar background, about dialog text)
- [ ] Edit the relevant source file
- [ ] Rebuild (incremental — only changed files recompile)
- [ ] Launch and confirm the change is visible

---

## Notes
- QGIS 4.x is Qt6 only — all UI code uses Qt6/PyQt6, not Qt5/PyQt5.
- Known gotcha: install `pyqt6-dev-tools` explicitly or QGIS fails at startup.
- Incremental rebuilds after a small change are fast (seconds to minutes, not hours).
