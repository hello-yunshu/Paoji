# 03. PJD: Paoji Document

> 中文版：[../../protocol/03_pjd_document.md](../../protocol/03_pjd_document.md)

PJD is the plaintext state of a Paoji expression. The Token is the short entry; PJD is the complete structure.

## 1. Minimal Structure

```json
{
  "format": "PJD",
  "version": 1,
  "name": "困困玻璃猫云",
  "packs": [],
  "core": {},
  "nodes": [],
  "requires": [],
  "fallback": {}
}
```

## 2. Complete Structure Recommendation

```json
{
  "format": "PJD",
  "version": 1,
  "id": "user.hiyunshu.cloudglass.glyph.sleepy-cat",
  "name": "困困玻璃猫云",
  "author": {
    "name": "云舒",
    "handle": "@hi.yunshu"
  },
  "packs": [
    {
      "id": "paoji.core",
      "version": "1.0.0"
    },
    {
      "id": "user.hiyunshu.cloudglass",
      "version": "1.0.0",
      "hash": "sha256-..."
    }
  ],
  "core": {
    "theme": "cat-cloud",
    "palette": "rose-glass",
    "emotion": "sleepy",
    "expression": "cat-pout",
    "style": "glass"
  },
  "nodes": [
    {
      "id": "base",
      "component": "user.hiyunshu.cloudglass.base.cloud-cat",
      "slot": "base",
      "transform": {
        "x": 512,
        "y": 520,
        "scale": 1,
        "rotation": 0
      }
    },
    {
      "id": "eyes",
      "component": "user.hiyunshu.cloudglass.eye.sleepy-crystal",
      "slot": "eyes",
      "params": {
        "sparkle": 0.7,
        "opacity": 0.95
      }
    }
  ],
  "requires": [
    "paoji.core@1",
    "svg.path",
    "svg.gradient",
    "material.glass"
  ],
  "fallback": {
    "visualHint": "🐱💗😴😿🫧",
    "core": {
      "base": "paoji.core.base.cat",
      "eye": "paoji.core.eye.sleepy",
      "mouth": "paoji.core.mouth.cat",
      "palette": "paoji.core.palette.rose",
      "style": "paoji.core.style.glass"
    },
    "alt": "粉色玻璃猫云，困困眼，猫嘴，带泡泡装饰"
  }
}
```

## 3. Design Principles

- PJD must be readable, editable, and versionable.
- PJD can be long; it does not need to be extremely short.
- PJD must use full namespace when referencing components.
- PJD must declare `requires`.
- PJD must provide a fallback.
- PJD should not contain unsafe scripts or arbitrary external links.
