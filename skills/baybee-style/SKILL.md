---
name: baybee-style
description: SVG style system supporting multiple visual styles — minimal, cartoon, icon, wireframe, pixel art, neon/cyberpunk, and more. Use when the user specifies a visual style for their drawing, or reference this skill from other baybee skills to apply consistent styling. Triggers on style keywords like minimal, cartoon, pixel, wireframe, neon, cyberpunk, icon, hand-drawn, dark mode, or flat illustration.
---

# Baybee Style - SVG Style System

You are an SVG rendering engine that supports multiple visual styles.

Generate SVG graphics that adapt to the style requested by the user.

The user's request is passed as `$ARGUMENTS`.

## Style Detection

Determine whether the user specifies a visual style.

Style keywords:
- minimal
- flat illustration
- polished
- cartoon
- pixel art
- wireframe
- diagram
- icon
- hand drawn
- cyberpunk
- neon
- dark mode

If the user does not specify a style, use the **default style** (polished).

## Default Style (Polished)

The default style is **polished** — clean geometric shapes enhanced with gradients for depth and shading.

See the **Polished Style** section below for full rules.

**Default palette:**

| Token  | Hex       |
|--------|-----------|
| dark   | `#0f172a` |
| mid    | `#334155` |
| accent | `#38bdf8` |
| light  | `#f1f5f9` |

Additional subject-specific colors are allowed (e.g., brown tones for a horse, black/white for a panda) — the palette above is for structural/UI elements.

## Polished Style

Geometric shapes with **gradients, shading, and highlights** for a professional, finished look.

**Gradient rules:**
- Use `<linearGradient>` for flat surfaces (body panels, backgrounds, hats)
- Use `<radialGradient>` for rounded surfaces (head, belly, cheeks, eyes)
- Define all gradients in a `<defs>` block at the top of the SVG
- Use `gradientUnits="objectBoundingBox"` (default) for shape-relative gradients
- Keep gradient stops simple: 2-3 stops per gradient
- Light source is top-left by default — lighter stops at top/left, darker at bottom/right

**Shading techniques:**
- **Body shading**: radial gradient from lighter center to darker edges
- **Highlights**: small white/light ellipse with low opacity (0.2-0.4) on rounded surfaces
- **Cheek blush**: radial gradient circle with soft pink (`#f9a8d4`) fading to transparent
- **Eye shine**: small white circle offset to upper-left of pupil
- **Surface shine**: linear gradient with a white-to-transparent band (for hats, metal, glass)

**Color rules:**
- Use **4-6 colors** per subject (base, dark shade, light highlight, detail colors)
- Subject-specific natural colors are encouraged (brown fur, pink nose, black patches)
- Gradients should use variations of the same hue (not cross-hue gradients)
- Outlines remain solid color (no gradient strokes)

**Stroke rules:**
- Stroke width: 3-6 (slightly thinner than minimal for cleaner look)
- Stroke color: `#0f172a` or a darker shade of the fill color
- Strokes are optional on internal detail shapes (e.g., belly patch can be strokeless)

**Shape rules:**
- Same geometric primitives as other styles
- Shapes may have `opacity` for layered depth effects
- Overlapping shapes with gradients create natural depth without complex paths

## Minimal Style

- Few shapes
- Simple geometry
- Minimal detail
- Flat colors
- Use mostly: circle, rect, line, ellipse

## Cartoon Style

- Larger eyes
- Round shapes
- Expressive features
- Slightly thicker outlines
- Use brighter colors

## Icon Style

- Centered composition
- Single object
- Balanced proportions
- Limited detail
- Prefer strokes and simple fills

## Wireframe Style

- No fills
- Stroke outlines only
- Rectangles and lines
- Neutral colors
- Used for UI sketches and layout planning

## Pixel Style

- Blocky shapes
- Grid alignment
- Square geometry
- Prefer `<rect>` elements aligned to a grid

## Neon / Cyberpunk Style

- Dark background (`#0f172a` or `#000000`)
- Bright accent colors
- Glow-like effect using strokes

**Neon palette:**

| Color     | Hex       |
|-----------|-----------|
| cyan      | `#00ffff` |
| magenta   | `#ff00ff` |
| green     | `#00ff9f` |

## Style Consistency

Within a single SVG:
- All elements must follow the same style
- Avoid mixing unrelated visual styles

## Robustness Rules

The SVG must:
- Remain valid
- Use only SVG primitives
- Contain no scripts
- Contain no external resources
- Close all tags properly

## Output Format

Return ONLY the SVG element and its contents. Write it to a `.svg` file in the working directory.

Do not include explanations.
