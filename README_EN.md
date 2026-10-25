# BeadForge · Fuse Bead Pattern Generator

[![License: GPL-3.0](https://img.shields.io/badge/License-GPL--3.0-blue.svg)](LICENSE)
[![No dependencies](https://img.shields.io/badge/dependencies-0-brightgreen.svg)]()
[![Offline ready](https://img.shields.io/badge/offline-ready-success.svg)]()

**A single-file, zero-dependency, offline-ready fuse bead (perler bead) pattern generator.** Drop in any picture and get a pixel pattern mapped to standard brand color charts — with bag codes, row/column rulers and a shopping list. Buy beads by code and start placing.

<p align="center"><img src="docs/cover.png" alt="BeadForge" width="720" /></p>

---

## ✨ Features

- **7 standard brand charts**: MARD (291), COCO (291), Artkal (418), Manman (278), Panpan (285), Mixiaowo (286), Perler (57, the western standard)
- **Perceptual color matching** — redmean weighted distance, much closer to human vision than plain RGB Euclidean
- **Floyd–Steinberg dithering** — smoother photos and gradients, can be turned off
- **Brightness compensation** — finished bead art always looks darker than the screen; try +10 ~ +30 for photos
- **Max color limit** — 6 / 12 / 24 / 36 and up; when exceeded, the least-used color is merged into its nearest neighbor so you buy fewer bags
- **Board size presets** — small board 29 / 2×2 board 58 / 3×3 board 87 beads wide
- **Exports**
  - PNG with codes — bag code printed in every cell, Excel-style row/column rulers (every 10th line bold), color legend at the bottom. Print it or keep it on your phone
  - PNG, pattern only
  - CSV color list — UTF-8 BOM, opens cleanly in Excel
- **Bilingual UI** (中文 / English, top-right switch)
- **Transparency aware** — transparent areas are left empty instead of filled

## 🚀 Quick start

**Option 1 (recommended)**: download `index.html` and open it in your browser. That's it.

**Option 2**: clone and open — nothing to install:

```bash
git clone https://github.com/bushimashen/beadforge.git
```

**Option 3**: host it anywhere — drop `index.html` onto GitHub Pages / Gitee Pages / any static host / Nginx, or run `python -m http.server` locally.

> Works in Chrome / Edge / Firefox / Safari, on desktop and mobile.

## 📖 How to use

1. **Import** — click the upload area, drag & drop an image, or paste a screenshot with `Ctrl+V`
2. **Pick a brand chart** — defaults to MARD (the most common chart in China; brands compatible with MARD codes map 1:1). Choose the brand whose beads you actually buy
3. **Set the width** — slider from 10 to 150 beads; use the 29 / 58 / 87 presets for standard boards
4. **Brightness** — bead art renders darker than your screen; photos usually want +10 ~ +30
5. **Dithering** — off for pixel art / flat colors, on for photos and gradients
6. **Max colors** — lower it to buy fewer bags; 24 is a good default
7. **Preview** — click a swatch in the color list to highlight where that color is used
8. **Export**
   - "Download PNG (codes + rulers + legend)" — recommended, one image has everything
   - "Download color list CSV" — for buying the right number of bags
9. "Change image" starts over

### What does the export look like?

A white, print-friendly sheet: each cell is one bead (round with a highlight), bag code printed inside; Excel-style rulers around all four sides (column/row numbers, every 10th in bold blue); color legend (swatch + code + hex + count) at the bottom.

## 🔒 Privacy

Everything runs **locally in your browser**: no upload, no network requests, no analytics. It works offline. Feel free to process private photos.

## 🧱 Technical notes

- **Single file** — one `index.html` contains all HTML/CSS/JS and the color chart data (~57 KB). No build step, no dependencies, no framework
- **Pipeline** — high-quality downscale → brightness compensation → (optional) Floyd–Steinberg error diffusion → redmean nearest-color match → usage-based color merging
- **Zero external resources** — no CDN, no web fonts, no images; fully offline
- A tiny debug API `window.BeadForge` is exposed (`BRANDS / load(image) / generate() / exportPng() / exportCsv() / drawExport()`) for hacking and automated testing

## 📄 License & data sources

Code is released under **GPL-3.0** (see [LICENSE](LICENSE)).

Brand color charts come from community-maintained references (brands don't publish official HEX values; values below are community-verified):

| Chart | Source |
|---|---|
| MARD (291) / COCO (291) | community chart from [Pindo](https://github.com/LunarXuan/Pindo) (GPL-3.0) |
| Artkal / Manman / Panpan / Mixiaowo | cross-reference data from [pindou-color-data](https://github.com/HansBug/pindou-color-data) |
| Perler (57) | the widely-used community reference table |

Brand names and bag codes belong to their respective owners; used here for identification only.
