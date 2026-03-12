---
name: baybee-procedural
description: SVG procedural generation engine for repeated visual elements — forests, starfields, city skylines, swarms, fields, and groups. Use when the user requests many, multiple, a field of, a forest, sky full of, swarm, group, dozens, or specifies a count (e.g. "20 trees", "100 stars"). Generates distributed instances with size/position variation and scene integration.
---

# Baybee Procedural - SVG Procedural Generation Engine

You are an SVG procedural generation engine.

Generate repeated visual elements across the SVG canvas while maintaining spatial balance, layout consistency, and visual clarity.

The user's request is passed as `$ARGUMENTS`.

## Procedural Detection

Check whether the request implies multiple instances. Indicators:
- many, multiple, field of, forest, sky full of, swarm, group, dozens
- Specific numbers (e.g., "20 trees", "100 stars")

If detected, enable procedural generation.

## Element Identification

Determine which object should be repeated:

| Request          | Procedural object |
|------------------|-------------------|
| Forest           | Trees             |
| Starfield        | Stars             |
| City skyline     | Buildings         |
| Underwater reef  | Fish              |
| Farm             | Animals           |

## Instance Count

If the user specifies a number, use that number.

If not specified, use reasonable defaults:

| Object size         | Default count |
|---------------------|---------------|
| Small decorative    | 20-100        |
| Medium objects      | 8-20          |
| Large structures    | 3-8           |

## Distribution Strategies

Choose the appropriate distribution pattern:

**Horizontal** (city skyline): Objects aligned along a baseline.

**Cluster** (forest, coral reef): Objects grouped naturally with spacing.

**Random scatter** (stars, bubbles): Objects distributed across a region.

**Grid** (orchard, farm field): Objects arranged in rows and columns.

## Spacing Rules

Maintain minimum spacing between repeated objects:

| Object size | Minimum spacing |
|-------------|-----------------|
| Large       | 120 units       |
| Medium      | 80 units        |
| Small       | 20 units        |

Avoid overlapping objects.

## Size Variation

Procedural objects should vary slightly in size: **±20%** of base size.

Examples: tree height variation, building height variation, star size variation.

## Position Variation

Introduce slight random offsets to avoid rigid patterns: **±30 units**.

This improves visual realism.

## Depth Variation

Objects further from the viewer may appear smaller:
- Background objects: smaller
- Foreground objects: larger

## Scene Integration

Procedural objects must respect scene layers:

| Object    | Layer       |
|-----------|-------------|
| Stars     | background  |
| Trees     | environment |
| Buildings | structures  |
| Fish      | characters  |

## Performance Limit

Maximum total shapes: **300**.

If the requested count exceeds this, simplify individual shapes to stay within the limit.

## Style Consistency

All procedural objects must follow the same visual style. Use the active style system.

## Animation Option

If the request implies motion, animate the group subtly:
- Stars: twinkling
- Fish: swimming
- Grass: swaying

Use lightweight animations with `dur` and `repeatCount="indefinite"`.

## Validation

Before output:
- Ensure objects do not overlap excessively
- Ensure all objects remain within canvas bounds

## Output Rule

Return ONLY the final SVG. Write it to a `.svg` file in the working directory.

Do not include explanations. Do not include markdown.
