# Paoji Official Core Pack

> 中文版：[README.md](README.md)

`paoji.core` is the minimum official component set recommended for every full Paoji Renderer. Its elements require no scripts, external fonts, or network assets, allowing an `InlineCore` Token to compose a readable, degradable expression from a small set of component IDs.

![Paoji Core composition examples](preview.svg)

## Initial Inventory

| Type | Count | Components |
|---|---:|---|
| `base` | 3 | round, soft-square, cloud |
| `eye` | 6 | dot, happy, sleepy, pleading, surprised, wink |
| `brow` | 3 | soft, worried, angry |
| `mouth` | 6 | smile, open-smile, pout, flat, surprised, cat |
| `cheek` | 2 | blush, lines |
| `deco` | 4 | heart, tear, sweat, sparkles |
| `palette` | 4 | warm, lilac, mint, mono |

The initial release contains **24 vector components and 4 base palettes**. Every component uses the `0 0 1024 1024` canvas and aligns with the standard anchors in `catalog.json`.

## Composition

Renderers compose components in this order:

```text
base → cheek → eye → brow → mouth → deco
```

Example composition:

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

## Files

- `manifest.json`: PJP metadata, resource lists, and pack fallback.
- `catalog.json`: component IDs, types, names, anchors, and per-component fallbacks.
- `components/*.svg`: transparent component layers with no scripts or external dependencies.
- `palettes/*.json`: base palette tokens.
- `preview.svg`: composed examples for visual inspection only.

## Stability

The current release is `0.1.0 experimental`. IDs follow the intended namespace rules but may still change before Paoji v1. Every change must preserve a fallback path for previous IDs.
