# 14. Registry 与生态治理

> English version: [../en/registry/14_governance_registry.md](../en/registry/14_governance_registry.md)

Paoji 要支持无限扩展，必须有治理机制。治理不是中心化控制，而是让组件可发现、可验证、可降级、可屏蔽。

## 1. Registry 不是唯一中心

Paoji 可以有多个 Registry：

```text
official registry
community registry
creator registry
personal registry
enterprise internal registry
offline registry
```

Registry 负责发现，hash 和 signature 负责验证。

## 2. Registry 记录

```json
{
  "id": "user.hiyunshu.cloudglass",
  "type": "pack",
  "version": "1.0.0",
  "hash": "sha256-...",
  "signature": "ed25519-...",
  "publisher": "user.hiyunshu",
  "trust": "personal",
  "status": "stable",
  "mirrors": [
    "https://...",
    "ipfs://..."
  ],
  "license": "MIT"
}
```

## 3. Trust Level

```text
core
standard
official
verified
community
personal
untrusted
blocked
```

默认建议：

```text
official 及以上：自动渲染
community：可提示确认
personal：本地或好友来源
untrusted：默认不加载
blocked：拒绝加载
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

重要规则：

```text
deprecated 不等于删除
archived 仍可被旧 token 引用
blocked 只用于安全或严重侵权风险
```

## 5. 命名空间保留

```text
paoji.core.*       官方核心
paoji.std.*        标准组件
paoji.official.*   官方扩展
creator.*          认证创作者
community.*        社区维护
user.*             普通用户
local.*            本地私有
```

用户不能注册 `paoji.core.*` 或 `paoji.official.*`。

## 6. 冲突处理

如果两个包视觉上类似，不一定冲突。  
如果两个包使用相同 namespace，则后注册者必须更名。

## 7. 下架策略

组件包被下架时：

```text
已缓存用户仍可本地渲染
新用户不再自动下载
Registry 标记为 archived / blocked
Renderer 可使用 fallback
```
