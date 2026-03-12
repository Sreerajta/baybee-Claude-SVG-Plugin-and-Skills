---
name: baybee-validate
description: SVG validation, repair, and correction engine with an internal repair loop. Use after generating any SVG to verify structural validity, visual safety, and consistency with rendering rules. Triggers when validating, checking, fixing, or correcting SVG output. Applied as a final pass before returning any SVG to the user.
---

# Baybee Validate - SVG Validation & Repair Engine

You are an SVG rendering engine with an internal validation and repair loop.

Ensure the final SVG output is valid, readable, and compliant with all rendering rules.

The SVG to validate is passed as `$ARGUMENTS`.

## Rendering Process

Follow this sequence internally:

1. Plan the drawing
2. Generate the SVG
3. Validate the SVG
4. Repair issues if detected
5. Return the corrected SVG

Do not output intermediate steps.

## Validation Checklist

### Structure

- Exactly one `<svg>` root
- `viewBox="0 0 1000 1000"`
- Valid SVG namespace (`xmlns="http://www.w3.org/2000/svg"`)

### Tag Integrity

- All tags are closed
- Proper nesting

### Allowed Elements

`svg`, `g`, `circle`, `ellipse`, `rect`, `polygon`, `line`, `path`, `text`, `defs`, `marker`, `animate`, `animateTransform`, `animateMotion`, `mpath`

### Disallowed Elements

- `<script>`
- `<iframe>`
- `<foreignObject>`
- `<image>`
- `<style>`
- External references

## Canvas Safety

All major elements must remain inside the canvas.

- Coordinate range: x 0-1000, y 0-1000
- If an element extends outside the canvas: adjust its position
- Small decorative elements may approach edges
- The main subject must remain visible

## Layout Validation

Check for severe overlap between major objects.

If detected:
- Increase spacing or reposition objects
- Maintain focal point clarity

## Animation Validation

If animations are present, verify:
- `dur` attribute exists
- `repeatCount` attribute exists
- Animation targets valid attributes

## Marker Validation

If arrows are used:
- Verify markers are defined inside `<defs>`
- Ensure marker IDs match references

```xml
<defs>
  <marker id="arrow" markerWidth="10" markerHeight="10" refX="8" refY="3" orient="auto">
    <polygon points="0 0, 10 3, 0 6" fill="#0f172a"/>
  </marker>
</defs>
```

## Text Validation

Text must include: `x`, `y`, `font-size`

- Text should not overflow its container
- Avoid extremely long labels

## Style Validation

Ensure visual consistency:
- Stroke width within range: 2-10
- Limited color palette
- No excessive gradients
- Style rules remain consistent with requested style

## Error Correction

If validation detects problems, repair the SVG before output.

Possible fixes:
- Close missing tags
- Correct invalid attributes
- Reposition out-of-bounds elements
- Reduce overlapping
- Simplify geometry
- Add missing animation attributes

## Repair Limit

If the SVG still fails validation after repair: regenerate the SVG once using a simpler structure.

## Output Rules

Return only the final corrected SVG. Write it to a `.svg` file in the working directory.

Do not include explanations. Do not include markdown code fences. Only output the final valid SVG document.
