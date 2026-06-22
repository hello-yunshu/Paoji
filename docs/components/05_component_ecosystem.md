# 05. 组件生态设计

> English version: [../en/components/05_component_ecosystem.md](../en/components/05_component_ecosystem.md)

Paoji 的组件生态必须同时支持官方大量增长和用户不可控增长。

## 1. 官方组件分层

```text
Paoji Core
Paoji Standard
Paoji Official Packs
Paoji Experimental
```

| 层级 | 说明 |
|---|---|
| Core | 最小核心，所有渲染器必须支持 |
| Standard | 稳定扩展，大多数客户端建议支持 |
| Official Packs | 官方主题包，按需下载 |
| Experimental | 官方实验能力，必须有 fallback |

## 2. 非官方组件分层

```text
creator.*
community.*
user.*
local.*
untrusted.*
```

| 层级 | 说明 |
|---|---|
| creator | 认证创作者 |
| community | 社区维护 |
| user | 普通用户 |
| local | 本地私有 |
| untrusted | 未验证或低信任 |

## 3. 命名空间规则

格式：

```text
<scope>.<owner>.<pack>.<type>.<name>
```

示例：

```text
paoji.core.eye.sleepy
paoji.std.deco.bubble
paoji.official.cloud.deco.soft-bubble
user.hiyunshu.cloudglass.eye.sleepy-crystal
creator.mochi.plushcat.mouth.pout
```

禁止裸 ID：

```text
sleepy
bubble
cat
rose
```

## 4. 生命周期

```text
draft
experimental
stable
deprecated
archived
blocked
```

组件可以废弃，但不能删除导致旧 token 崩坏。

## 5. Fallback Graph

每个复杂组件必须声明 fallback 链：

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

## 6. 核心原则

- 官方和用户组件使用同一技术格式。
- 区别只在 trust level。
- 所有组件必须可命名、可验证、可降级。
- 旧组件不能改变语义。
