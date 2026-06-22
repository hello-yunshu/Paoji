# 08. 示例

> English version: [../en/examples/08_examples.md](../en/examples/08_examples.md)

## 1. 轻量内联表情

Token：

```text
⟦YS1🌥️💗😴🙂🫧~AQABAAAAABBpUiIp4Y5uBA._cw⟧
```

特点：

- 使用官方基础组件
- payload 自包含
- 不依赖外部 pack
- 适合简单表情

## 2. 复杂自定义表情

Token：

```text
⟦YS1🐱💜🥺😿🫧🌙🪽💧~AgEBAf8A.gGs⟧
```

特点：

- 使用 PackRef
- token 只存 packId / glyphId / variantId
- 完整组件由 PJP Pack 提供
- 有 fallback

## 3. 复杂 PJD 片段

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
