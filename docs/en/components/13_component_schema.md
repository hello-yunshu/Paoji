# 13. Component Schema

> 中文版：[../../components/13_component_schema.md](../../components/13_component_schema.md)

Paoji components are reusable, parameterizable, and degradable visual objects.

## 1. Component Basic Structure

```json
{
  "format": "PaojiComponent",
  "id": "user.hiyunshu.cloudglass.eye.sleepy-crystal",
  "type": "eye",
  "version": "1.0.0",
  "status": "stable",
  "viewBox": "0 0 1024 1024",
  "resources": {},
  "anchors": {},
  "params": {},
  "requires": [],
  "fallback": {},
  "license": "MIT"
}
```

## 2. Standard Component Types

```text
base
eye
brow
mouth
cheek
deco
effect
background
foreground
material
motion
layout
template
```

## 3. Standard Slots

```text
base
leftEye
rightEye
eyes
brows
mouth
leftCheek
rightCheek
deco
background
foreground
effect
```

## 4. Anchor

Anchors are used for cross-component alignment. An anchor is a standard reference point; components should be positioned based on the anchor but may have slight offsets by design (for example, different mouth shapes may sit at different heights). Renderers compose components using anchors as the baseline.

```json
{
  "anchors": {
    "leftEye": { "x": 400, "y": 455 },
    "rightEye": { "x": 624, "y": 455 },
    "mouth": { "x": 512, "y": 615 }
  }
}
```

## 5. Params

Component parameters must have types and ranges.

```json
{
  "params": {
    "sparkle": {
      "type": "number",
      "default": 0.4,
      "min": 0,
      "max": 1
    },
    "color": {
      "type": "color",
      "default": "ink.soft"
    },
    "mirror": {
      "type": "boolean",
      "default": true
    }
  }
}
```

## 6. Component Fallback

```json
{
  "fallback": {
    "component": "paoji.core.eye.sleepy",
    "strategy": "same-slot"
  }
}
```

## 7. Component Quality Standards

Before entering the public Registry, components should at least meet:

```text
Has complete ID
Has version
Has license
Has fallback
Has preview
Passes SVG security scan
Recognizable at small sizes
Does not depend on external resources
Reasonable parameter ranges
```
