# 3D T-Tetromino Cube Solver

A browser-based web app for solving and visualizing a 3D packing puzzle made from identical **T-tetromino** pieces.

The app runs entirely on the client side with **JavaScript** and **Three.js**. No backend is required.

## Demo

This project is designed to work well on **GitHub Pages** because it is a static site with a single entry file:

- `index.html`

## Features

- Solve a 3D T-tetromino packing puzzle directly in the browser
- Visualize the solution in 3D with free camera movement
- Support two target modes:
  - `SOLID_CUBE`
  - `SURFACE_CUBE`
- Layer slicing UI for inspecting the puzzle by `z` level
- Per-piece coloring and hover highlight
- Backtracking solver with heuristic cell selection
- No server, database, or build step required

## Piece Definition

Each puzzle piece is a flat **T-tetromino** made of exactly 4 voxels:

```text
[
  [0,0,0],
  [1,0,0],
  [2,0,0],
  [1,1,0]
]
```

The solver generates unique orientations across the `XY`, `XZ`, and `YZ` planes.

## Supported Sizes

For the current UI, the app exposes:

- `N = 4`
- `N = 6`

These are the practical sizes for the current browser-based solver and visualization workflow.

## Run Locally

You can run the app in either of these ways:

### Option 1: Open directly

Open `index.html` in your browser.

### Option 2: Use a local static server

```bash
python -m http.server
```

Then open:

```text
http://localhost:8000/
```

## Usage

1. Choose `N`
2. Choose the target mode
3. Click `Solve Fast`
4. Use the bottom `Layer Z` scrubber to inspect slices
5. Hover a piece to highlight it and show its `Piece #id`

## Solver Notes

The solver uses:

- precomputed target cells
- precomputed placements
- `cell -> placements` mapping
- backtracking
- a heuristic that chooses the most constrained empty cell first

This makes the app responsive enough for `N = 4` and usable for `N = 6`, but larger search spaces become expensive very quickly.

## Performance Limits

This is still a combinatorial search problem.

Practical notes:

- `N = 4` is fast
- `N = 6` is significantly heavier
- larger sizes would require stronger pruning and/or a different solver strategy

## Tech Stack

- HTML
- CSS
- JavaScript
- Three.js

## License

Use this project however you like, or add your preferred license before publishing.
