# 09. Multilingual and Localization Design

> 中文版：[../../examples/09_i18n_localization.md](../../examples/09_i18n_localization.md)

Paoji's documentation and ecosystem support multilingual localization. The protocol, design documents, official website, component descriptions, and Registry metadata should all support multiple languages, with each language version keeping semantic correspondence.

## 1. Supported Languages

```text
Supported languages: zh-CN, en-US
Extensible to: zh-TW / ja-JP / ko-KR / fr-FR / es-ES
```

Principles:

1. Protocol fields and identifiers are not localized; human-facing content supports localization.
2. Protocol terms should have clear definitions, with aliases available in supported languages.
3. Token, ID, namespace, payload are not natural-language localized.
4. User-facing UI, component names, alt text, and help documentation can be localized.
5. PJD / PJP / Registry need to support multilingual fields.

## 2. Content That Should Not Be Localized

The following content must remain stable:

```text
YS Token
namespace
component id
pack id
schema id
payload
hash
signature
version
requires capability
```

For example:

```text
user.hiyunshu.cloudglass.eye.sleepy-crystal
paoji.core.eye.sleepy
svg.gradient
material.glass
```

These are machine protocol identifiers and should not be translated.

## 3. Content That Can Be Localized

The following content can be multilingual:

```text
Component display name
Component description
Expression name
alt text
Designer notes
UI copy
Error messages
Registry pages
Official website content
Wiki content
```

## 4. PJD Multilingual Fields

PJD is recommended to support:

```json
{
  "name": {
    "zh-CN": "困困玻璃猫云",
    "en-US": "Sleepy Glass Cloud Cat"
  },
  "description": {
    "zh-CN": "粉色玻璃猫云，困困眼，猫嘴，带泡泡装饰",
    "en-US": "A rose glass cloud-cat with sleepy eyes, cat mouth, and bubble decorations."
  },
  "alt": {
    "zh-CN": "粉色玻璃猫云，困困眼，猫嘴，带泡泡装饰",
    "en-US": "Rose glass cloud-cat with sleepy eyes and bubbles."
  }
}
```

## 5. PJP Multilingual Fields

The component pack manifest is recommended to support:

```json
{
  "name": {
    "zh-CN": "云朵玻璃组件包",
    "en-US": "Cloud Glass Pack"
  },
  "summary": {
    "zh-CN": "一组柔软、通透、带云朵感的 Paoji 组件。",
    "en-US": "A soft translucent cloud-themed Paoji component pack."
  },
  "components": [
    {
      "id": "user.hiyunshu.cloudglass.eye.sleepy-crystal",
      "name": {
        "zh-CN": "水晶困困眼",
        "en-US": "Sleepy Crystal Eyes"
      },
      "description": {
        "zh-CN": "适合柔软、半透明、委屈或困困风格的眼睛组件。",
        "en-US": "Eye component for soft, translucent, sleepy or pleading expressions."
      }
    }
  ]
}
```

## 6. Translation Key Naming

The official website and editor UI can use key-value translation:

```text
home.hero.title
home.hero.subtitle
protocol.token.title
designer.anchor.description
error.crc_failed
error.pack_not_found
```

Example:

```json
{
  "home.hero.title": "Emoji, after fixed lists.",
  "home.hero.lead": "Paoji 是一套开放式表情对象协议。",
  "error.crc_failed": "Token 校验失败，可能已被修改或损坏。"
}
```

## 7. Language Fallback Chain

Recommended fallback order:

```text
User language
↓
Same language family
↓
zh-CN
↓
en-US
↓
Component ID / alt text
```

For example, if the user language is `zh-TW`:

```text
zh-TW → zh-CN → en-US → id
```

If the user language is `fr-FR`:

```text
fr-FR → en-US → zh-CN → id
```

Official documentation should ensure all language versions are complete and in sync.

## 8. Notes for Designers

1. Keep names short so they display well in small interfaces.
2. alt text should describe the visual result, not just the component name.
3. Component IDs should use English and hyphens for easy machine processing.
4. Display names can be localized, cute, or stylized.
5. Multilingual names for the same component do not need to be word-for-word translations, but the semantics should correspond.
6. Expression semantic tags should remain stable; translation only affects display, not the protocol.

## 9. Recommended Directory

```text
locales/
├─ zh-CN.json
├─ en-US.json
└─ zh-TW.json
```

## 10. Minimal Language Pack Structure

```json
{
  "meta.language": "简体中文",
  "meta.source": "zh-CN",
  "home.hero.title": "固定列表之后的 Emoji。",
  "home.hero.lead": "Paoji 是一套开放式、可扩展的表情对象协议。",
  "protocol.short": "短码入口",
  "protocol.document": "表情文档",
  "protocol.pack": "组件包",
  "fallback.title": "永远降级可见"
}
```
