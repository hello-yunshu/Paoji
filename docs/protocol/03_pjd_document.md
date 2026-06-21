# 03. PJD：Paoji Document

PJD 是 Paoji 表情的明文状态。Token 是短入口，PJD 是完整结构。

## 1. 最小结构

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

## 2. 完整结构建议

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

## 3. 设计原则

- PJD 必须可读、可编辑、可版本化。
- PJD 可以很长，不追求极短。
- PJD 引用组件时必须使用完整命名空间。
- PJD 必须声明 `requires`。
- PJD 必须提供 fallback。
- PJD 不应该包含不安全脚本或任意外链。
