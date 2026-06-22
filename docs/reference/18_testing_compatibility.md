# 18. 测试与兼容性

> English version: [../en/reference/18_testing_compatibility.md](../en/reference/18_testing_compatibility.md)

Paoji 需要测试的不只是渲染效果，还包括协议稳定性、安全、降级和跨版本兼容。

## 1. Token 测试

- 合法 token 可解析。
- CRC 错误会拒绝。
- visualHint 被改动后 CRC 失败。
- payload 非 base64url 会拒绝。
- 超长 token 会拒绝或警告。
- YS 大小写敏感。

## 2. Payload 测试

- InlineCore 可展开。
- PackRef 可定位 pack。
- DocRef 可定位 PJD。
- 未知 schema 可以安全失败。
- 未知 block 可以跳过。
- 缺失字段有合理错误。

## 3. PJD 测试

- 缺少可选字段仍可渲染。
- 缺少必需字段给出明确错误。
- requires 不满足时会 fallback。
- 多语言字段按回退链显示。
- nodes 顺序和 layer 正确。

## 4. PJP 测试

- manifest 完整性。
- hash 校验。
- signature 校验。
- 组件 fallback 存在。
- SVG 安全扫描。
- 文件大小限制。
- 外部资源拒绝。

## 5. 渲染测试

建议尺寸：

```text
32px
64px
128px
256px
1024px
```

场景：

```text
浅色背景
深色背景
透明背景
高对比模式
无动画模式
低性能模式
```

## 6. 降级测试

每个复杂表情都必须测试：

```text
完整资源可用
缺少高级能力
缺少自定义 pack
registry 离线
hash 不匹配
只剩 visualHint
只剩 alt 文本
```

## 7. 兼容性矩阵

| 客户端 | Level 0 | Level 1 | Level 2 | Level 3 |
|---|---:|---:|---:|---:|
| 纯文本 | ✅ | ❌ | ❌ | ❌ |
| 基础 Web | ✅ | ✅ | ❌ | ❌ |
| Paoji Web | ✅ | ✅ | ✅ | 部分 |
| 高级 App | ✅ | ✅ | ✅ | ✅ |
