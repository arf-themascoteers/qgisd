# QGIS 4.x From-Source Build — Agent Context

## Project Goal
Arif wants hands-on experience building QGIS 4+ from source on Ubuntu, and eventually modifying its code. This is a learning project.

## Status
- Research phase complete.
- Arif is about to share his expectations — NOT YET RECEIVED.
- Next step: hear Arif's expectations, then plan the build workflow.

---

## Key Facts: QGIS 4.x on Ubuntu

### Breaking changes vs QGIS 3.x
- Qt6 ONLY (no Qt5)
- C++20 required
- PyQt6 required (no PyQt5)
- CMake >= 3.22.0
- Python >= 3.11

### Minimum versions
- Qt >= 6.6.0
- GDAL/OGR >= 3.2.0
- GEOS >= 3.9
- PROJ >= 8.1.0
- SpatiaLite >= 4.2.0

### Ubuntu recommendation
- Ubuntu 24.04 LTS minimum (22.04 has incomplete Qt6 packaging)

### Core apt dependencies (partial list)
```
bison build-essential cmake cmake-curses-gui flex git ninja-build
libqca-qt6-dev libqscintilla2-qt6-dev pyqt6-dev pyqt6-dev-tools
python3-pyqt6 python3-pyqt6.qsci
libgdal-dev libgeos-dev libproj-dev libspatialite-dev libsqlite3-dev
libpq-dev libsfcgal-dev libdraco-dev libexiv2-dev libzip-dev
python3-all-dev python3-gdal python3-matplotlib python3-owslib
```

### Typical CMake invocation
```bash
mkdir build && cd build
cmake .. \
  -DCMAKE_BUILD_TYPE=Release \
  -DCMAKE_INSTALL_PREFIX=$HOME/apps \
  -DCMAKE_CXX_STANDARD=20 \
  -DWITH_PYTHON=TRUE \
  -DWITH_3D=TRUE
make -j$(nproc)
```

### Known gotchas
1. `pyqt6-dev-tools` missing → startup failure even after successful build. Install explicitly.
2. Some Qt6 builds still have stale PyQt5 import in `/usr/local/share/qgis/python/qgis/core/additions/qgsfeature.py` — fix manually if hit.
3. Ubuntu 22.04 Qt6 packages incomplete — use 24.04.

### Official references
- Repo: https://github.com/qgis/QGIS
- Build doc: https://github.com/qgis/QGIS/blob/master/INSTALL.md
- Qt6 migration blog: https://blog.qgis.org/2025/04/17/qgis-is-moving-to-qt6-and-launching-qgis-4-0/

---

## About Arif (for new agent)
- Analyst Programmer / GIS Developer at Wimmera CMA, Horsham, Victoria, Australia
- PhD in ML (hyperspectral remote sensing, band selection, dimensionality reduction)
- Strong: Python, GIS, remote sensing, ArcGIS Pro, QGIS, Earth Engine
- Background languages: Java, PHP, Groovy, Grails, Selenium/Java
- Weaker in: React, TypeScript
- Tools: ArcGIS Pro 3.6.0, QGIS 3.44, Cursor IDE, Ubuntu servers, Windows desktops

## Response rules (MUST follow)
- Every response starts with R1, R2, R3... label (sequential per session)
- Be absolutely brief — longer than needed is not tolerated
- Numbered lists only (no bullets)
- No code comments of any kind
- Suggest only ONE option (the best); ask before offering alternatives
- No extra theory/background unless asked
- Readability over cleverness in all code
- No one-liners; unroll into explicit named steps
- Minimal function parameters; hard-code constants inside functions
- All scripts need `if __name__ == "__main__":` guard
