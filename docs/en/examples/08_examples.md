# 08. Examples

> 中文版：[../../examples/08_examples.md](../../examples/08_examples.md)

## 1. Lightweight Inline Expression

Token:

```text
⟦YS1🌥️💗😴🙂🫧~AQABAAAAABBpUiIp4Y5uBA._cw⟧
```

Features:

- Uses official base components
- payload is self-contained
- Does not depend on external pack
- Suitable for simple expressions

## 2. Complex Custom Expression

Token:

```text
⟦YS1🐱💜🥺😿🫧🌙🪽💧~AgEBAf8A.gGs⟧
```

Features:

- Uses PackRef
- token only stores packId / glyphId / variantId
- Full component provided by PJP Pack
- Has fallback

## 3. Complex PJD Fragment

```json
{
  "format": "PJD",
  "version": 1,
  "name": "玻璃猫云 · 委屈泡泡版",
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
    "palette": "lilac-glass",
    "emotion": "pleading",
    "expression": "cat-pout",
    "style": "glass"
  },
  "requires": [
    "svg.path",
    "svg.gradient",
    "filter.blur",
    "material.glass"
  ],
  "fallback": {
    "visualHint": "🐱💜🥺😿🫧",
    "alt": "淡紫玻璃猫云，委屈大眼，猫嘴，带泡泡和翅膀"
  }
}
```
