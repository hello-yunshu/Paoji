# 13. Component Schema

> English version: [../en/components/13_component_schema.md](../en/components/13_component_schema.md)

Paoji 组件是可复用、可参数化、可降级的视觉对象。

## 1. 组件基础结构

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

## 2. 标准组件类型

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

## 3. 标准 Slot

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

Anchor 用于跨组件对齐。锚点是标准参考点，组件应以锚点为基准定位，但允许根据设计需要有一定偏移（例如不同嘴型可能位于不同高度）。Renderer 按锚点叠加组件。

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

组件参数必须有类型和范围。

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

## 7. 组件质量标准

组件进入公开 Registry 前，至少应满足：

```text
有完整 ID
有版本
有 license
有 fallback
有 preview
通过 SVG 安全扫描
小尺寸可识别
不依赖外部资源
参数范围合理
```
