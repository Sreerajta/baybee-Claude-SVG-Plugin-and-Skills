# Baybee

SVG drawing and animation plugin for Claude Code. Create, edit, and animate SVG illustrations using natural language.

## What it does

Baybee turns natural language prompts into SVG illustrations. It draws characters, animals, scenes, diagrams, and animations — all rendered as clean, valid SVG files.

Animals and organic subjects are drawn in a geometric/logo art style using simple shapes (circles, rectangles, polygons, ellipses). The default visual style is polished, using gradients and shading for depth.

## Installation

```
claude install gh:Sreerajta/baybee
```

## Usage

Once installed, Baybee activates when you ask Claude Code to draw, illustrate, or create SVG graphics.

**Examples:**

```
draw a panda sitting
draw a beach scene with a shack
draw a flowchart for user login
draw a neon cat icon
add a tree to the scene
make the panda bigger
animate the fish swimming
```

Output is written as `.svg` files in your working directory.

## Skills

Baybee is composed of 15 skills that handle different aspects of SVG rendering:

| Skill | Purpose |
|-------|---------|
| `baybee` | Core illustration engine — character construction, geometric style, anatomy |
| `baybee-plan` | Request router — analyzes prompts and activates the right rendering modules |
| `baybee-scene` | Scene composition — layered environments with background, subjects, foreground |
| `baybee-edit` | Scene editing — add, remove, modify elements in existing SVGs |
| `baybee-select` | Object selection — target elements by natural language ("the cow", "all trees") |
| `baybee-spatial` | Spatial reasoning — interprets "next to", "above", "behind", etc. |
| `baybee-procedural` | Procedural generation — forests, starfields, groups of repeated elements |
| `baybee-rig` | Character rigging — grouped body parts for independent animation |
| `baybee-motion` | Physics-inspired motion — oscillation, easing, secondary animation |
| `baybee-style` | Visual styles — polished (default), minimal, cartoon, neon, pixel, wireframe |
| `baybee-layout` | Spatial arrangement — grids, alignment, spacing, margins |
| `baybee-complexity` | Detail control — minimal, simple, normal, detailed, highly detailed |
| `baybee-diagram` | Diagram rendering — flowcharts, architecture diagrams, wireframes |
| `baybee-debug` | Debug overlays — layout grids, bounding boxes, zone visualization |
| `baybee-validate` | SVG validation — structural checks, repair, and correction |

## Canvas

All illustrations render on a 1000x1000 SVG canvas:

```xml
<svg viewBox="0 0 1000 1000" xmlns="http://www.w3.org/2000/svg">
```

## Style

The default style uses:

- Geometric shapes for characters and animals
- Gradients (`<linearGradient>`, `<radialGradient>`) for shading and depth
- SVG animation primitives (`<animate>`, `<animateTransform>`) for motion
- Semantic group IDs for all major elements (`<g id="panda-1">`)

Other styles available: minimal, cartoon, neon/cyberpunk, pixel, wireframe, icon, dark mode.

## Version

0.3.0

## Author

sreerajta

## License

MIT
