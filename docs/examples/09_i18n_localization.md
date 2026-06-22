# 09. 多语言与本地化设计

> English version: [../en/examples/09_i18n_localization.md](../en/examples/09_i18n_localization.md)

Paoji 的协议、设计文档、官网、组件说明、Registry 元数据都支持多语言本地化，各语言版本应保持语义一致。

## 1. 支持语言

```text
支持语言：zh-CN, en-US
后续可选：zh-TW / ja-JP / ko-KR / fr-FR / es-ES
```

原则：

1. 协议字段与标识符不本地化；面向人的内容支持本地化。
2. 协议术语应有清晰定义，并在各支持语言中提供别名。
3. Token、ID、namespace、payload 不做自然语言本地化。
4. 面向用户的 UI、组件名称、alt 文本、帮助文档可以本地化。
5. PJD / PJP / Registry 需要支持多语言字段。

## 2. 不应本地化的内容

这些内容必须保持稳定：

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

例如：

```text
user.hiyunshu.cloudglass.eye.sleepy-crystal
paoji.core.eye.sleepy
svg.gradient
material.glass
```

这些是机器协议，不应该翻译。

## 3. 可以本地化的内容

这些内容可以多语言：

```text
组件显示名
组件描述
表情名称
alt 文本
设计师说明
UI 文案
错误提示
Registry 页面
官网内容
Wiki 内容
```

## 4. PJD 多语言字段

PJD 建议支持：

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

## 5. PJP 多语言字段

组件包 manifest 建议支持：

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

## 6. 翻译键命名

官网和编辑器 UI 可以使用 key-value 翻译：

```text
home.hero.title
home.hero.subtitle
protocol.token.title
designer.anchor.description
error.crc_failed
error.pack_not_found
```

示例：

```json
{
  "home.hero.title": "Emoji, after fixed lists.",
  "home.hero.lead": "Paoji 是一套开放式表情对象协议。",
  "error.crc_failed": "Token 校验失败，可能已被修改或损坏。"
}
```

## 7. 语言回退链

推荐回退顺序：

```text
用户语言
↓
同语族语言
↓
zh-CN
↓
en-US
↓
组件 ID / alt 文本
```

例如用户语言是 `zh-TW`：

```text
zh-TW → zh-CN → en-US → id
```

用户语言是 `fr-FR`：

```text
fr-FR → en-US → zh-CN → id
```

官方文档应保证各语言版本完整同步。

## 8. 设计师注意事项

1. 命名尽量短，方便在小界面显示。
2. alt 文本要描述视觉结果，不要只写组件名。
3. 组件 ID 用英文和连字符，便于机器处理。
4. 展示名可以中文化、可爱化、风格化。
5. 同一个组件的多语言名称不必逐字翻译，但语义要对应。
6. 表情语义标签应保持稳定，翻译只影响显示，不影响协议。

## 9. 推荐目录

```text
locales/
├─ zh-CN.json
├─ en-US.json
└─ zh-TW.json
```

## 10. 最小语言包结构

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
