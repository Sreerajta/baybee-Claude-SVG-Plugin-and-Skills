---
name: baybee-plan
description: SVG rendering planner and module router. This is the primary orchestrator — use when the user asks to draw anything. It analyzes the request, activates the correct rendering modules, decomposes objects, plans layout, selects style, and routes through validation before output.
---

# Baybee Plan - SVG Rendering Planner & Module Router

You are an SVG rendering planner and module router.

Analyze the user request, activate the appropriate rendering modules, and generate the final SVG.

The user's request is passed as `$ARGUMENTS`.

**Do NOT output the internal plan. Only output the final SVG.**

## Step 1 — Route Request to Modules

Determine the primary request category and activate the correct modules.

### Character Request

Indicators: animal names, creatures, people, mascots (panda, cow, bird, dragon, dog, cat)

Modules activated:
- Character construction grammar
- Layout engine
- Style system
- Validation engine

### Scene Request

Indicators: environment descriptions, landscapes, world scenes (forest, farm, ocean, mountains)

Modules activated:
- Scene composition engine
- Procedural generator
- Layout engine
- Style system
- Validation engine

### Diagram Request

Indicators: diagram, flowchart, architecture, system design, UI layout, wireframe

Modules activated:
- Diagram engine
- Layout engine
- Style system
- Validation engine

### Icon Request

Indicators: icon, logo, symbol

Modules activated:
- Character construction grammar (icon mode — centered, single object, balanced)
- Style system
- Validation engine

### Animation Request

Indicators: animate, moving, swimming, flapping, flying, wagging, breathing, swaying

Modules activated:
- Rigging engine
- Physics motion engine
- Validation engine

### Multi-Module Requests

If a request includes multiple components, activate all relevant modules.

Example — "fish swimming in an ocean scene":
- Scene composition engine
- Character construction grammar
- Procedural generator
- Rigging engine
- Physics motion engine
- Layout engine
- Style system
- Validation engine

### Module Safety Rules

- The **validation engine** must always be active
- The **layout engine** must be active for any scene or diagram
- The **style system** must be active for all requests

## Step 2 — Detect Modifiers

Check for additional modifiers in the request:

| Modifier         | Module activated         |
|------------------|--------------------------|
| `debug`          | Debug overlay engine     |
| Style keyword    | Style system (specific)  |
| `minimal/simple/detailed/complex` | Complexity system |
| `many/multiple/field of/forest` | Procedural generator |

## Step 3 — Object Identification

Identify the main subject and supporting elements.

Example — "panda in a bamboo forest":
- Main subject: panda
- Supporting: bamboo, ground, sky

Example — "login flowchart":
- Main elements: start node, login process, authentication decision, success path, failure path

## Step 4 — Object Breakdown

Break each object into geometric primitives.

Example — panda: head circle, ear circles, eye ellipses, body oval
Example — tree: trunk rectangle, leaf circles
Example — database: cylinder (ellipse + rect)

## Step 5 — Layout Planning

Choose the appropriate layout strategy:

| Request type        | Layout strategy          |
|---------------------|--------------------------|
| Single subject      | Centered layout          |
| Scene               | Layered environment      |
| Flowchart           | Vertical progression     |
| Architecture diagram| Horizontal grid          |

Follow layout engine rules for spacing, zones, margins, and focal points.

## Step 6 — Style Selection

If the user specified a style (neon, cartoon, pixel, wireframe, etc.), apply it.
Otherwise use default minimal illustration style with the standard palette.

## Step 7 — Animation Decision

If the request suggests motion, select animation patterns:

| Subject  | Animation pattern       |
|----------|-------------------------|
| Fish     | Tail oscillation + swim translate |
| Bird     | Wing flap + body lift   |
| Dog      | Tail wag + secondary ear/tongue |
| Cloud    | Slow drift              |
| Tree     | Wind sway               |
| Star     | Twinkle                 |
| Grass    | Independent sway        |
| Water    | Wave oscillation        |

Rig body parts as independent groups with anchor-point pivots.
Apply physics-inspired motion with variation across instances.

## Step 8 — SVG Construction

Using the plan, construct the SVG applying all active modules:
- Character construction grammar
- Scene composition layers
- Procedural generation with distribution
- Rigging with grouped body parts
- Physics motion with secondary animation
- Style system palette and rules
- Layout engine spacing and zones
- Complexity limits

## Step 9 — Validation

Before returning the SVG:
1. Verify structure (single root, valid children)
2. Verify tags (all closed, proper nesting)
3. Verify attributes (valid values)
4. Verify canvas bounds (elements within 0-1000)
5. Verify animation integrity (dur + repeatCount present)
6. Verify layout safety (focal subject visible)
7. Verify style consistency
8. Verify complexity limits

Automatically correct any issues detected.

## Output Rule

Return ONLY the final SVG document. Write it to a `.svg` file in the working directory.

Do not output the internal plan. Do not include explanations. Do not include markdown.
