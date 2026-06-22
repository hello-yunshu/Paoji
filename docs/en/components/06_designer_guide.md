# 06. Paoji Designer Guide

> 中文版：[../../components/06_designer_guide.md](../../components/06_designer_guide.md)

This document is for designers, focusing on how to design Paoji components and expressions rather than underlying code.

## 1. Three Objects Designers Need to Understand

| Name | You can think of it as |
|---|---|
| PJD | A design source file for an expression |
| PJP | A reusable component library |
| YS Token | A short code that users copy and share |

## 2. Component Types

Common component types:

```text
base       face shape / body base
eye        eye
brow       eyebrow
mouth      mouth
cheek      blush
deco       decoration
effect     effect
material   material
motion     animation
background background
foreground foreground
```

## 3. Standard Canvas

Recommended for all components:

```text
viewBox = 0 0 1024 1024
```

This makes cross-component alignment easier.

## 4. Anchor Design

Base components must provide anchors:

```json
{
  "anchors": {
    "leftEye": { "x": 400, "y": 455 },
    "rightEye": { "x": 624, "y": 455 },
    "mouth": { "x": 512, "y": 615 },
    "leftCheek": { "x": 350, "y": 560 },
    "rightCheek": { "x": 676, "y": 560 }
  }
}
```

The purpose of anchors: after changing the face shape, eyes, mouth, and decorations can still automatically find their correct positions.

## 5. Component Design Requirements

A good component should:

- Have a clear purpose.
- Be reusable.
- Have parameters, but not too many.
- Have an official fallback.
- Not depend on external images.
- Not use scripts.
- Adapt to the 1024×1024 canvas.
- Remain recognizable at small sizes.
- Have clear semantic tags.

## 6. Visual Style Guidelines

The official Paoji base style should maintain:

- Simplicity
- High recognizability
- Softness
- Scalability
- Composability
- Clarity at small sizes
- Not relying on complex shadows to work

User packs can have their own style, but must provide fallback.

## 7. Design Workflow

```text
1. Choose component type
2. Draw on the 1024 canvas
3. Set anchors
4. Set parameters
5. Choose fallback
6. Fill in semantic tags
7. Generate preview
8. Package as PJP
9. Generate test Token
10. Check degraded display
```

## 8. Components Not Recommended to Design

- Components only visible at very large sizes
- Components without fallback
- Components depending on external fonts or images
- Components with overly complex visual styles that cannot degrade
- Components with confusing same-name semantics
