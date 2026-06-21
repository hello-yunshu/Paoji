# 02. YS Token 规范

## 1. 基本格式

```text
⟦YS1<visualHint?>~<payload>.<crc>⟧
```

示例：

```text
⟦YS1🐱💜🥺😿🫧🌙🪽💧~AgEBAf8A.gGs⟧
```

## 2. 字段说明

| 字段 | 说明 |
|---|---|
| `⟦` | 开始边界 |
| `YS` | 协议族，大小写敏感 |
| `1` | 主版本号 |
| `visualHint` | 可选视觉提示区 |
| `~` | payload 起始 |
| `payload` | base64url 编码的机器入口数据 |
| `.` | checksum 起始 |
| `crc` | CRC16-CCITT 的 base64url 3 字符 |
| `⟧` | 结束边界 |

## 3. Visual Hint 规则

Visual Hint 不是权威数据，只做人类提示和降级显示。

推荐结构：

```text
[主题][色调][情绪][表情][风格][自由提示...]
```

示例：

```text
🐱💜🥺😿🫧🌙🪽💧
```

解释：

```text
🐱 = 主题：猫
💜 = 色调：紫
🥺 = 情绪：委屈
😿 = 表情：哭哭 / 猫脸
🫧 = 风格：玻璃 / 泡泡
🌙🪽💧 = 自由氛围提示
```

建议：

- 标准提示位：0 或 5 个 grapheme cluster。
- 自由扩展位：0–27 个。
- 总长度建议 ≤ 16，硬上限 32。
- 解析时必须按 grapheme cluster，而不是普通字符串长度。
- checksum 覆盖 visualHint，避免被随意篡改。

## 4. Payload Schema

Payload 可以指向不同类型的数据：

| Schema | 用途 |
|---|---|
| InlineCore | 纯官方基础组件，可自包含 |
| PackRef | 引用某个 PJP Pack 里的 glyph / variant |
| DocRef | 引用完整 PJD 文档 |
| BundleRef | 引用离线 bundle |
| Hybrid | 内置 fallback，同时引用完整文档或资源包 |

## 5. 解码流程

```text
1. 粗识别 ⟦YS1...⟧
2. 检查边界和协议族
3. 切出 visualHint / payload / crc
4. 校验 CRC
5. base64url 解码 payload
6. 根据 schema 解析为入口对象
7. 解析 PJD 或 PJP 引用
8. 验证 hash / version / signature
9. 渲染
10. 失败则 fallback
```

## 6. 正则粗识别

```regex
⟦YS[0-9A-Z].+?~[A-Za-z0-9_-]+\.[A-Za-z0-9_-]{3}⟧
```

注意：正则只负责粗识别，不能代替完整校验。
