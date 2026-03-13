# Baybee

SVG drawing and animation plugin for [Claude Code](https://docs.anthropic.com/en/docs/claude-code). Turn natural language into illustrated SVG graphics — characters, scenes, diagrams, and animations.

## Examples

> "draw a panda"

<img src="examples/panda.svg" width="400">

> "draw a beach scene with a shack"

<img src="examples/beach-scene.svg" width="500">

> "draw a neon cat icon"

<img src="examples/neon-cat.svg" width="400">

> "animate fish swimming in an ocean"

<img src="examples/ocean-scene.svg" width="500">

> "draw a flowchart for user login"

<img src="examples/login-flowchart.svg" width="500">

## Install

```
claude install gh:Sreerajta/baybee
```

## Usage

Just ask Claude Code to draw something. Baybee activates automatically for drawing, illustration, and SVG requests.

```
draw a panda sitting in a bamboo forest
draw a beach scene with palm trees and a shack
draw a flowchart for user authentication
draw a neon cat icon
animate a bird flying
```

You can also edit existing illustrations incrementally:

```
add a tree to the scene
make the panda bigger
change the sky to sunset colors
animate the fish swimming
```

Output is written as `.svg` files in your working directory.

## What it can do

- **Characters & Animals** — Penguins, pandas, cats, dogs, horses, fish, birds, and more. Built from geometric shapes with polished gradient shading.
- **Scenes & Environments** — Beaches, forests, farms, oceans, rooms, cities. Multi-layered compositions with backgrounds, subjects, and foreground details.
- **Diagrams** — Flowcharts, architecture diagrams, system designs, wireframes. Clean node-and-edge layouts.
- **Animation** — Breathing, swimming, flying, wagging, swaying, drifting. Physics-inspired motion using native SVG `<animate>` and `<animateTransform>`.
- **Incremental Editing** — Add, remove, move, resize, or restyle elements in an existing SVG without regenerating the whole scene.
- **Multiple Styles** — Polished (default), minimal, cartoon, neon/cyberpunk, pixel art, wireframe, icon, dark mode.
- **Procedural Generation** — Forests, starfields, skylines, swarms. Repeating elements with natural variation.

## How it works

Baybee is composed of 15 skills that handle different aspects of SVG rendering:

| Skill | What it does |
|-------|-------------|
| `baybee` | Core illustration engine — geometric character construction, anatomy, shading |
| `baybee-plan` | Request router — analyzes prompts and orchestrates the right rendering modules |
| `baybee-scene` | Scene composition — layered environments with depth and spatial structure |
| `baybee-edit` | Incremental editing — add, remove, or modify elements in existing SVGs |
| `baybee-select` | Object targeting — select elements by natural language ("the cow", "all trees") |
| `baybee-spatial` | Spatial reasoning — interprets "next to", "above", "behind", etc. |
| `baybee-procedural` | Procedural generation — forests, starfields, groups of repeated elements |
| `baybee-rig` | Character rigging — grouped body parts for independent animation |
| `baybee-motion` | Physics-inspired motion — oscillation, easing, secondary animation |
| `baybee-style` | Visual styles — polished, minimal, cartoon, neon, pixel, wireframe |
| `baybee-layout` | Spatial arrangement — grids, alignment, spacing, margins |
| `baybee-complexity` | Detail control — minimal, simple, normal, detailed, highly detailed |
| `baybee-diagram` | Diagram rendering — flowcharts, architecture diagrams, wireframes |
| `baybee-debug` | Debug overlays — layout grids, bounding boxes, zone visualization |
| `baybee-validate` | SVG validation — structural checks, repair, and correction |

## Style

The default polished style uses:

- Geometric shapes (circles, ellipses, rectangles, polygons) for all subjects
- `<radialGradient>` for rounded surfaces, `<linearGradient>` for flat surfaces
- Eye shine highlights, cheek blush, and surface shading for depth
- SVG animation primitives (`<animate>`, `<animateTransform>`) for motion
- Semantic group IDs (`<g id="panda-1">`) for editability

All output renders on a 1000x1000 SVG canvas:

```xml
<svg viewBox="0 0 1000 1000" xmlns="http://www.w3.org/2000/svg">
```

## License

MIT
