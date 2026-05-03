# QGIS 4.x From-Source Build — Agent Context

## Project Goal
Arif wants hands-on experience building QGIS 4+ from source on Ubuntu, and eventually modifying its code. This is a learning project. Building is a means. Understanding the source is the end.

## Approach
- Arif runs all commands himself — agent guides, not executes (unless Arif explicitly asks)
- Always explain WHY a command is needed when asking Arif to run it
- Each phase teaches something new about QGIS architecture
- Finish with a visible code change confirmed in a live build

---

## Current Status
- Phase 1 (Environment Setup): COMPLETE
- Phase 2 (Get the Source): COMPLETE — cloned to ~/QGIS
- Phase 3 (Configure the Build): COMPLETE — cmake works

## NEXT STEP
**Phase 4 — Compile.** Run from ~/QGIS/build:

```bash
cd ~/QGIS/build && ninja
```

This will take 30–90 minutes. After it finishes, run:

```bash
~/QGIS/build/output/bin/qgis
```

---

## Environment
- OS: Ubuntu 24.04.4 LTS
- QGIS version: 4.1.0 Master (40100)
- Build dir: ~/QGIS/build
- Install prefix: ~/qgis-install
- Build type: Debug (good for learning/dev)
- Build tool: Ninja

## Working CMake Command
```bash
cd ~/QGIS/build && cmake -G Ninja -DCMAKE_BUILD_TYPE=Debug -DCMAKE_INSTALL_PREFIX=$HOME/qgis-install -DWITH_PDAL=FALSE ..
```

---

## Verified apt Dependencies (official INSTALL.md + extras found during build)

Run as ONE line:
```
sudo apt-get install -y bison build-essential ca-certificates ccache cmake cmake-curses-gui dh-python expect flex flip gdal-bin git graphviz grass-dev libcups2-dev libdraco-dev libexiv2-dev libexpat1-dev libfcgi-dev libgdal-dev libgeographiclib-dev libgeos-dev libgsl-dev libmeshoptimizer-dev libpq-dev libproj-dev libprotobuf-dev libqca-qt6-dev libqca-qt6-plugins libqscintilla2-qt6-dev libsfcgal-dev libspatialite-dev libspatialindex-dev libsqlite3-dev libsqlite3-mod-spatialite libyaml-tiny-perl libzip-dev libzstd-dev lighttpd locales ninja-build nlohmann-json3-dev ocl-icd-opencl-dev opencl-headers pandoc pkgconf poppler-utils protobuf-compiler pyqt6-dev pyqt6-dev-tools pyqt6.qsci-dev python3-all-dev python3-autopep8 python3-dev python3-gdal python3-matplotlib python3-mock python3-nose2 python3-owslib python3-packaging python3-psycopg2 python3-pyqt6 python3-pyqt6.qsci python3-pyqt6.qtmultimedia python3-pyqt6.qtpositioning python3-pyqt6.qtserialport python3-pyqt6.qtsvg python3-pyqt6.sip python3-pyqtbuild python3-termcolor python3-yaml qt6-3d-assimpsceneimport-plugin qt6-3d-defaultgeometryloader-plugin qt6-3d-dev qt6-3d-gltfsceneio-plugin qt6-3d-scene2d-plugin qt6-5compat-dev qt6-base-dev qt6-base-private-dev qt6-multimedia-dev qt6-positioning-dev qt6-serialport-dev qt6-svg-dev qt6-tools-dev qt6-tools-dev-tools qt6-webengine-dev qtkeychain-qt6-dev sip-tools spawn-fcgi xauth xfonts-100dpi xfonts-75dpi xfonts-base xfonts-scalable xvfb qtcreator
```

---

## Key Source Directories
- `src/core/` — core logic, no UI (layers, features, geometry, CRS)
- `src/gui/` — reusable Qt widgets (map canvas, dialogs)
- `src/app/` — the desktop application, main() lives here
- `src/plugins/` — built-in plugins
- `src/server/` — QGIS Server
- `src/analysis/` — raster/vector analysis
- `src/3d/` — 3D view
- `python/` — Python bindings
- `resources/` — icons, styles, UI assets

## Key Facts
- QGIS 4.x is Qt6 only (no Qt5)
- C++20, PyQt6, CMake >= 3.22
- Qt version installed: 6.4.2 (minimum is 6.4; 6.6 preferred but 6.4 works)
- PDAL not available in Ubuntu 24.04 repos — disabled with -DWITH_PDAL=FALSE
- Known gotcha: install pyqt6-dev-tools explicitly or startup fails

## Official References
- Repo: https://github.com/qgis/QGIS
- Build doc: https://github.com/qgis/QGIS/blob/master/INSTALL.md

---

## About Arif (for new agent)
- Analyst Programmer / GIS Developer, Wimmera CMA, Horsham, Victoria, Australia
- PhD in ML (hyperspectral remote sensing, band selection, dimensionality reduction)
- Strong: Python, GIS, remote sensing, ArcGIS Pro, QGIS, Earth Engine
- Background: Java, PHP, Groovy, Grails, Selenium/Java
- Tools: ArcGIS Pro 3.6.0, QGIS 3.44, Cursor IDE, Qt Creator, Ubuntu servers, Windows desktops

## Response Rules (MUST follow)
- Every response starts with R1, R2, R3... (sequential per session)
- Absolutely brief — longer than needed is not tolerated
- Numbered lists only (no bullets)
- No code comments of any kind
- Suggest only ONE option; ask before offering alternatives
- No extra theory/background unless asked
- Always explain WHY when asking Arif to run a command
- Readability over cleverness in all code
- No one-liners; unroll into explicit named steps
- All scripts need `if __name__ == "__main__":` guard
