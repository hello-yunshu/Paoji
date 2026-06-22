# 04. PJP: Paoji Pack

> 中文版：[../../protocol/04_pjp_pack.md](../../protocol/04_pjp_pack.md)

PJP is the component pack format of Paoji. Official components, user components, and creator components all use PJP.

## 1. Pack Structure

```text
cloudglass.pjp/
├─ manifest.json
├─ components/
│  ├─ base.cloud-cat.svg
│  ├─ eye.sleepy-crystal.svg
│  ├─ mouth.soft-cat.svg
│  └─ deco.pearl-bubble.svg
├─ palettes/
│  └─ rose-glass.json
├─ materials/
│  └─ soft-glass.json
├─ motions/
│  └─ breathe.json
├─ glyphs/
│  └─ cloudy-cat.json
├─ fallback/
│  └─ cloudy-cat-core.json
└─ preview.png
```

## 2. manifest.json

```json
{
  "format": "PJP",
  "id": "user.hiyunshu.cloudglass",
  "name": "Cloud Glass Pack",
  "version": "1.0.0",
  "author": {
    "name": "云舒",
    "handle": "@hi.yunshu"
  },
  "trust": "personal",
  "requires": [
    "paoji.core>=1.0.0",
    "svg.path",
    "svg.gradient",
    "material.glass"
  ],
  "components": [
    "components/base.cloud-cat.svg",
    "components/eye.sleepy-crystal.svg",
    "components/deco.pearl-bubble.svg"
  ],
  "fallback": {
    "coreOnly": "fallback/cloudy-cat-core.json"
  },
  "license": "CC-BY-NC-4.0",
  "hash": "sha256-..."
}
```

## 3. Component Definition

Components are not images; they are parameterizable objects.

```json
{
  "format": "PaojiComponent",
  "id": "user.hiyunshu.cloudglass.eye.sleepy-crystal",
  "type": "eye",
  "version": "1.0.0",
  "viewBox": "0 0 1024 1024",
  "anchors": {
    "leftEye": { "x": 400, "y": 455 },
    "rightEye": { "x": 624, "y": 455 }
  },
  "params": {
    "color": {
      "type": "color",
      "default": "ink.soft"
    },
    "sparkle": {
      "type": "number",
      "default": 0.4,
      "min": 0,
      "max": 1
    }
  },
  "requires": [
    "svg.path",
    "svg.gradient"
  ],
  "fallback": {
    "component": "paoji.core.eye.sleepy"
  }
}
```

## 4. Required Information

Every PJP Pack must have:

- namespace
- version
- hash
- author
- license
- requires
- fallback
- lifecycle status
- trust level
