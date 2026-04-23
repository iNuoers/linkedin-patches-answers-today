<p align="center">
  <img src="https://patchesanswers.today/logo.svg" alt="Patches Answers Today" width="80" height="80" />
</p>

<h1 align="center">LinkedIn Patches — Puzzle Archive</h1>

<p align="center">
  <strong>Open-source grid data for every LinkedIn Patches puzzle since Day 1.</strong>
</p>

<p align="center">
  <a href="https://patchesanswers.today">🌐 Website</a> ·
  <a href="https://patchesanswers.today/patches-answer/today">📖 Today's Answer</a> ·
  <a href="https://patchesanswers.today/patches-play/today">🎮 Play Online</a> ·
  <a href="https://patchesanswers.today/archive">🗂️ Archive</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/puzzles-37-blue?style=flat-square" alt="Puzzles" />
  <img src="https://img.shields.io/badge/updated-daily-brightgreen?style=flat-square" alt="Updated Daily" />
  <img src="https://img.shields.io/badge/data-JSON-orange?style=flat-square" alt="JSON" />
  <img src="https://img.shields.io/badge/license-MIT-yellow?style=flat-square" alt="License" />
</p>

---

## What is Patches?

[Patches](https://www.linkedin.com/games/patches/) is a daily logic puzzle by LinkedIn. Players fill a grid by assigning cells to colored regions based on shape clues and region sizes. Think of it as a visual partition puzzle — part Sudoku logic, part jigsaw spatial reasoning.

This repository archives the **grid structure** of every puzzle in a clean, machine-readable JSON format. It does **not** contain solutions.

## Quick Start

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/linkedin-patches-archive.git

# Browse puzzles
ls puzzles/

# Load today's puzzle (example)
cat puzzles/2026-04-23.json | jq '.grid.regions | length'
# → 8 regions
```

## Data Schema

### Puzzle File — `puzzles/YYYY-MM-DD.json`

```jsonc
{
  "puzzle_number": 37,          // Sequential number since launch
  "date": "2026-04-23",         // ISO date
  "date_slug": "april-23-2026", // Human-readable slug
  "grid": {
    "rows": 6,                  // Grid height
    "cols": 6,                  // Grid width
    "regions": [
      {
        "id": 0,                // Region identifier
        "color": "#EF6C00",     // Display color (hex)
        "clueNumber": 4,        // Target cell count
        "clueShape": "SQUARE",  // Shape hint
        "cells": [
          {
            "row": 0,
            "col": 0,
            "borders": ["top", "left"]  // Visible borders
          }
        ]
      }
    ]
  }
}
```

### Index — `puzzles/index.json`

```json
[
  { "date": "2026-03-18", "puzzleNumber": 1 },
  { "date": "2026-03-19", "puzzleNumber": 2 },
  ...
]
```

### Field Reference

| Field | Type | Description |
|:------|:-----|:------------|
| `puzzle_number` | `number` | Sequential puzzle number (1-indexed) |
| `date` | `string` | Puzzle date in `YYYY-MM-DD` format |
| `date_slug` | `string` | Readable date like `april-23-2026` |
| `grid.rows` | `number` | Grid row count (typically 5–8) |
| `grid.cols` | `number` | Grid column count (typically 5–8) |
| `regions[].id` | `number` | Unique region identifier |
| `regions[].color` | `string` | Hex color code for display |
| `regions[].clueNumber` | `number` | How many cells belong to this region |
| `regions[].clueShape` | `string` | Shape hint: `SQUARE`, `VERTICAL_RECT`, `HORIZONTAL_RECT`, `L_SHAPE`, `T_SHAPE`, `UNKNOWN` |
| `regions[].cells` | `array` | Cell positions and visible border edges |

## Statistics

| Metric | Value |
|:-------|:------|
| Total puzzles | 37 |
| Date range | March 18, 2026 — April 23, 2026 |
| Grid sizes | 5×5, 6×6 |
| Avg. regions per puzzle | ~7 |
| Update frequency | Daily |

## Use Cases

- 📊 **Puzzle analytics** — Analyze difficulty trends, region distributions, and grid size patterns
- 🤖 **Solver development** — Build and benchmark automated Patches solvers
- 🎨 **Visualization** — Render puzzle grids programmatically
- 📚 **Research** — Study combinatorial partition puzzles and constraint satisfaction
- 🛠️ **Tool building** — Create practice generators, hint systems, or alternative UIs

## Related

| Resource | Link |
|:---------|:-----|
| 🌐 Daily answers & analysis | [patchesanswers.today](https://patchesanswers.today) |
| 📖 Today's answer | [patchesanswers.today/patches-answer/today](https://patchesanswers.today/patches-answer/today) |
| 🎮 Interactive play | [patchesanswers.today/patches-play/today](https://patchesanswers.today/patches-play/today) |
| 💡 Today's hints | [patchesanswers.today/patches-hints-today](https://patchesanswers.today/patches-hints-today) |
| 🗂️ Full archive | [patchesanswers.today/archive](https://patchesanswers.today/archive) |
| 🎯 Official game | [linkedin.com/games/patches](https://www.linkedin.com/games/patches/) |

## Contributing

Found a missing puzzle or a data error? Feel free to open an issue or submit a PR.

## License

MIT © [Patches Answers Today](https://patchesanswers.today)

LinkedIn Patches is a trademark of LinkedIn Corporation. This project is not affiliated with or endorsed by LinkedIn.
