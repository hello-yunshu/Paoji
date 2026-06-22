# 04. PJP：Paoji Pack

> English version: [../en/protocol/04_pjp_pack.md](../en/protocol/04_pjp_pack.md)

PJP 是 Paoji 的组件包格式。官方组件、用户组件、创作者组件都使用 PJP。

## 1. 包结构

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

## 3. 组件定义

组件不是图片，而是可参数化对象。

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

## 4. 必须包含的信息

每个 PJP Pack 必须有：

- namespace
- version
- hash
- author
- license
- requires
- fallback
- lifecycle status
- trust level
