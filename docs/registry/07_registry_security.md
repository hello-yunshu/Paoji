# 07. Registry、安全与信任

> English version: [../en/registry/07_registry_security.md](../en/registry/07_registry_security.md)

## 1. PJR Registry 作用

PJR Registry 负责：

- 注册组件
- 解析 namespace
- 查看版本
- 下载 PJP Pack
- 校验 hash
- 查看 trust level
- 查看 lifecycle status
- 查看 fallback
- 查看 license

Registry 不应该是唯一中心。Paoji 可以有官方、社区、个人、企业内网等多种 registry。

## 2. 资源验证

每个 pack 必须有：

```json
{
  "id": "user.hiyunshu.cloudglass",
  "version": "1.0.0",
  "hash": "sha256-...",
  "signature": "ed25519-...",
  "publisher": "user.hiyunshu"
}
```

## 3. 信任等级

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

默认策略建议：

- 自动渲染 `official` 及以上。
- `community` 可提示用户确认。
- `untrusted` 默认不自动加载。
- `blocked` 拒绝加载。

## 4. 安全 SVG 子集

允许：

- path
- rect / circle / ellipse / polygon
- g
- defs
- linearGradient / radialGradient
- clipPath / mask 白名单
- 有限 filter
- transform
- opacity

禁止：

- script
- foreignObject
- iframe
- onload / onclick 等事件
- 外部网络请求
- 外部图片默认加载
- 远程字体
- 超大 base64
- 无限滤镜
- 超长动画

## 5. 降级链

```text
完整 PJP 渲染
↓
基础 PJD 渲染
↓
Paoji Core fallback
↓
Visual Hint
↓
alt 文本
```

Paoji 想替代 emoji，就必须保证任何环境都有可见退路。
