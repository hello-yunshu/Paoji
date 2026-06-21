# 21. 贡献指南

Paoji 的生态需要设计师、开发者、协议设计者和社区共同参与。

## 1. 可以贡献什么

```text
协议建议
官方 Core 组件
官方 Standard 组件
PJP Pack
文档翻译
Renderer 实现
测试用例
安全规则
Registry 设计
设计工具
```

## 2. 贡献组件的最低要求

- 有完整 namespace。
- 有版本号。
- 有 license。
- 有 fallback。
- 有 preview。
- 通过安全扫描。
- 有中文主语言说明。
- 推荐有英文说明。

## 3. 命名规则

```text
scope.owner.pack.type.name
```

示例：

```text
creator.mochi.plushcat.eye.sleepy-soft
```

## 4. 提交官方收录的要求

官方收录更严格：

- 语义清晰。
- 小尺寸可识别。
- 与 Core 兼容。
- 不侵犯第三方版权。
- 有长期维护计划。
- 有 fallback graph。
- 有测试截图。

## 5. 文档贡献

文档默认主语言为中文。  
英文文档可以作为辅助语言，但中文说明必须完整。

## 6. 版本原则

- patch：修复，不改变视觉语义。
- minor：新增能力，兼容旧版本。
- major：破坏性变更，需要新 ID 或新版本范围。

## 7. 废弃原则

组件可以 deprecated，但不应删除。  
旧 token 必须尽量可降级显示。
