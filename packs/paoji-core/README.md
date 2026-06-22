# Paoji 官方核心表情库 / Official Core Pack

> English version: [README.en.md](README.en.md)

`paoji.core` 是每个完整 Paoji Renderer 都应优先支持的最小官方组件库。它提供不依赖脚本、外部字体或网络资源的基础表情元素，让 `InlineCore` Token 可以只靠少量组件 ID 组合出清晰、可降级的表情。

`paoji.core` is the minimum official component set recommended for every full Paoji renderer. Its elements require no scripts, external fonts, or network assets, allowing an `InlineCore` token to compose a readable, degradable expression from a small set of component IDs.

![Paoji Core 组合示例](preview.svg)

## 首版内容 / Initial Inventory

| 类型 / Type | 数量 | 组件 / Components |
|---|---:|---|
| `base` | 3 | round, soft-square, cloud |
| `eye` | 6 | dot, happy, sleepy, pleading, surprised, wink |
| `brow` | 3 | soft, worried, angry |
| `mouth` | 6 | smile, open-smile, pout, flat, surprised, cat |
| `cheek` | 2 | blush, lines |
| `deco` | 4 | heart, tear, sweat, sparkles |
| `palette` | 4 | warm, lilac, mint, mono |

共计 **24 个矢量组件 + 4 套基础色板**。所有组件均使用 `0 0 1024 1024` 画布，并与 `catalog.json` 中的标准锚点对齐。

The initial release contains **24 vector components and 4 base palettes**. Every component uses the `0 0 1024 1024` canvas and aligns with the standard anchors in `catalog.json`.

## 组合方式 / Composition

Renderer 按以下顺序叠加组件：

```text
base → cheek → eye → brow → mouth → deco
```

Renderers compose components in this order:

```text
base → cheek → eye → brow → mouth → deco
```

示例组合：

```json
{
  "pack": "paoji.core@0.1.0",
  "components": {
    "base": "paoji.core.base.round",
    "eye": "paoji.core.eye.pleading",
    "brow": "paoji.core.brow.worried",
    "mouth": "paoji.core.mouth.pout",
    "cheek": "paoji.core.cheek.blush",
    "deco": "paoji.core.deco.tear"
  },
  "palette": "paoji.core.palette.lilac"
}
```

## 文件 / Files

- `manifest.json`：PJP 包元数据、资源列表与 pack fallback。
- `catalog.json`：组件 ID、类型、名称、锚点与逐组件 fallback。
- `components/*.svg`：透明、无脚本、无外部依赖的组件图层。
- `palettes/*.json`：基础色板 token。
- `preview.svg`：若干组合结果，仅用于视觉预览。

- `manifest.json`: PJP metadata, resource lists, and pack fallback.
- `catalog.json`: component IDs, types, names, anchors, and per-component fallbacks.
- `components/*.svg`: transparent component layers with no scripts or external dependencies.
- `palettes/*.json`: base palette tokens.
- `preview.svg`: composed examples for visual inspection only.

## 稳定性 / Stability

当前版本为 `0.1.0 experimental`。组件 ID 已按正式命名空间设计，但在 Paoji v1 之前仍可能调整。所有变更必须保持旧 ID 的 fallback 路径。

The current release is `0.1.0 experimental`. IDs follow the intended namespace rules but may still change before Paoji v1. Every change must preserve a fallback path for previous IDs.
