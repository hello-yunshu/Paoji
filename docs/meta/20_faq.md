# 20. FAQ

> English version: [../en/meta/20_faq.md](../en/meta/20_faq.md)

## Paoji 是 emoji 吗？

不是传统 Unicode emoji。Paoji 是开放式表情对象协议。

## Paoji 能替代 emoji 吗？

目标是替代表情表达机制，而不是替代 Unicode 字符编码本身。Paoji 更像“表情对象协议 + 资源生态 + 渲染器”。

## 为什么还需要 Visual Hint？

因为没有渲染器时，用户至少能看到大概语义。Visual Hint 是降级的一部分。

## Visual Hint 是权威数据吗？

不是。权威数据来自 payload 展开的 PJD / PJP。

## 用户可以自定义组件吗？

可以。用户通过 PJP Pack 添加自定义组件，但必须声明 namespace、version、hash、fallback 和 license。

## 官方组件也会无限增长怎么办？

官方组件也必须包化、版本化、注册化。Core 只保持最小稳定集，其他官方组件通过 official packs 增长。

## 如果别人没有我的组件包怎么办？

Renderer 会按 fallback 链降级显示：自定义组件 → 官方组件 → Visual Hint → alt 文本。

## 协议为什么用 MIT？

MIT 足够宽松，方便扩散、实现、二次开发和商业使用。但具体组件包可以使用自己的 license。

## Paoji 会不会有安全风险？

有，所以用户组件必须沙箱化，SVG 必须清洗，禁止脚本、事件、外部请求和不受控资源。

## Paoji 的第一版应该做什么？

先做：

```text
YS Token
PJD 基础格式
PJP manifest
官方 Core 组件
Web Renderer
Designer Wiki
SVG / PNG 导出
```
