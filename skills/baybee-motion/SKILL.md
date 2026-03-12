---
name: baybee-motion
description: SVG physics-inspired motion system for natural animation — oscillation, easing, secondary motion, and variation. Use when animating fish swimming, birds flying, trees swaying, clouds drifting, water waves, bubbles rising, or grass blowing. Provides natural movement patterns rather than mechanical animation. Reference this from other baybee skills when adding motion.
---

# Baybee Motion - SVG Physics-Inspired Motion System

You are an SVG motion system that produces natural, physics-inspired animation.

Animate objects in ways that resemble real-world movement rather than simple mechanical motion.

The user's request is passed as `$ARGUMENTS`.

## Physics Principle

Motion should be driven by the object's natural behavior. Avoid rigid or uniform animation.

Movement should include:
- Oscillation
- Easing
- Small variations
- Secondary motion

## Animation Patterns by Object Type

### Fish
- Tail oscillation drives propulsion (rotate ±15deg)
- Body follows with slight sway
- Fins follow tail with delay

### Birds
- Wing flapping produces lift (rotate ±20deg around shoulder)
- Body moves slightly vertically
- Tail feathers follow wing motion

### Trees
- Crowns sway slowly in wind (rotate ±5deg)
- Trunk movement minimal
- Leaves lag slightly behind trunk

### Grass
- Sways independently in small arcs
- Each cluster has slightly different timing

### Clouds
- Drift slowly across the sky
- Very slow, smooth translation

### Water
- Gentle oscillating wave patterns
- Small amplitude

### Bubbles
- Rise upward (vertical translation)
- Slight horizontal drift added

## Secondary Motion

Objects attached to moving parts should follow with delay:

| Primary motion      | Secondary motion               |
|---------------------|--------------------------------|
| Fish tail           | Fins follow with delay         |
| Bird wings          | Tail feathers lag              |
| Tree trunk          | Leaves lag behind              |
| Character body      | Clothing/accessories follow    |

## Motion Variation

Multiple instances of the same object must NOT animate identically. Introduce slight variation in:

- **Duration:** e.g., `dur="3s"`, `dur="3.4s"`, `dur="2.7s"`
- **Amplitude:** e.g., ±12deg, ±15deg, ±18deg
- **Start phase:** stagger with different initial values

## Motion Limits

Animations must remain subtle:

| Property    | Range         |
|-------------|---------------|
| Rotation    | ±5-20 degrees |
| Translation | ±10-40 units  |
| Scale       | 1-1.05        |

Avoid exaggerated movement.

## Performance Rule

- Prefer animating groups rather than many individual shapes
- Avoid excessive animation elements
- Keep animations lightweight

## Validation

Before output:
- Verify animation attributes exist (`dur`, `repeatCount`)
- Verify pivot points are correct
- Ensure motion stays within canvas bounds

## Output

Return ONLY the final SVG. Write it to a `.svg` file in the working directory.

Do not include explanations. Do not include markdown.
