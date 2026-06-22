# 05. Component Ecosystem

> 中文版：[../../components/05_component_ecosystem.md](../../components/05_component_ecosystem.md)

The Paoji component ecosystem must support both large-scale official growth and uncontrollable user growth.

## 1. Official Component Tiers

```text
Paoji Core
Paoji Standard
Paoji Official Packs
Paoji Experimental
```

| Tier | Description |
|---|---|
| Core | Minimal core; all renderers must support it |
| Standard | Stable extensions; recommended for most clients |
| Official Packs | Official theme packs; downloaded on demand |
| Experimental | Official experimental capabilities; must have fallback |

## 2. Unofficial Component Tiers

```text
creator.*
community.*
user.*
local.*
untrusted.*
```

| Tier | Description |
|---|---|
| creator | Verified creators |
| community | Community-maintained |
| user | General users |
| local | Local private |
| untrusted | Unverified or low-trust |

## 3. Namespace Rules

Format:

```text
<scope>.<owner>.<pack>.<type>.<name>
```

Examples:

```text
paoji.core.eye.sleepy
paoji.std.deco.bubble
paoji.official.cloud.deco.soft-bubble
user.hiyunshu.cloudglass.eye.sleepy-crystal
creator.mochi.plushcat.mouth.pout
```

Bare IDs are prohibited:

```text
sleepy
bubble
cat
rose
```

## 4. Lifecycle

```text
draft
experimental
stable
deprecated
archived
blocked
```

Components can be deprecated, but cannot be deleted in a way that breaks old tokens.

## 5. Fallback Graph

Every complex component must declare a fallback chain:

```json
{
  "fallback": [
    "paoji.official.cloud.deco.bubble-simple",
    "paoji.std.deco.bubble",
    "paoji.core.deco.circle",
    "visualHint",
    "alt"
  ]
}
```

## 6. Core Principles

- Official and user components use the same technical format.
- The only difference is trust level.
- All components must be namable, verifiable, and degradable.
- Old components cannot change semantics.
