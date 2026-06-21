# 11. Payload Schema 设计

YS Token 的 payload 是机器入口数据。它不负责承载无限复杂度，而是负责告诉 Resolver：这个表情应该如何展开。

## 1. Payload 基本原则

```text
1. payload 必须短。
2. payload 必须可校验。
3. payload 必须可版本化。
4. payload 必须支持多 schema。
5. payload 不能假设所有表情都可内联。
6. payload 必须能指向 PJD / PJP / Bundle。
```

## 2. 推荐 Schema 类型

| Schema | 名称 | 用途 |
|---:|---|---|
| 0x01 | InlineCore | 只用 Paoji Core / Standard 的轻量自包含表情 |
| 0x02 | PackRef | 引用某个 PJP Pack 里的 glyph / variant |
| 0x03 | DocRef | 引用完整 PJD 文档 |
| 0x04 | BundleRef | 引用离线 `.paoji` Bundle |
| 0x05 | Hybrid | Token 内带基础 fallback，同时引用完整资源 |
| 0x7F | Extension | 预留扩展 schema |

## 3. 为什么不用固定 bit 表长期扩展

固定 bitpack 适合 MVP，但不适合未来：

```text
theme 5 bits     → 只能支持 32 种主题
palette 5 bits   → 只能支持 32 种色板
node type 5 bits → 只能支持 32 种节点
```

Paoji 的目标是无限扩展，所以固定 bitpack 只能用于 `InlineCore`，不能成为唯一 payload 格式。

## 4. TLV / Block 推荐结构

未来正式 payload 推荐采用 block 结构：

```text
Payload
├─ HeaderBlock
├─ EntryBlock
├─ FallbackBlock?
├─ IntegrityBlock?
└─ ExtensionBlock[]
```

每个 block：

```text
blockType varint
blockLength varint
blockData bytes
```

优点：

```text
旧解析器遇到未知 block 可以跳过
新字段可以逐步增加
可以支持 DocRef / PackRef / Hybrid
可以支持压缩和签名
```

## 5. PackRef Payload 明文态

```json
{
  "schema": "PackRef",
  "pack": {
    "id": "user.hiyunshu.cloudglass",
    "version": "1.0.0",
    "hash": "sha256-..."
  },
  "glyph": "cloud-cat",
  "variant": "sleepy-glass",
  "fallback": {
    "inlineCore": "..."
  }
}
```

## 6. DocRef Payload 明文态

```json
{
  "schema": "DocRef",
  "doc": {
    "id": "doc_9f3a",
    "hash": "sha256-...",
    "mirrors": [
      "https://registry.paoji.example/doc/doc_9f3a",
      "ipfs://..."
    ]
  },
  "fallback": {
    "visualHint": "🐱💜🥺😿🫧",
    "alt": "淡紫玻璃猫云，委屈大眼，猫嘴"
  }
}
```

## 7. Hybrid Payload

Hybrid 是最适合公开分享的长期方向：

```text
Token 内置基础 fallback
+
引用完整 PJD / PJP
```

这样即使资源包无法加载，也能显示基础版本。

## 8. Payload 版本策略

payload schema 应独立于 YS Token 主版本。

```text
YS1 = token 外壳版本
payloadSchema = payload 结构版本
PJD version = 文档格式版本
PJP version = 资源包格式版本
```

不要把所有版本绑在一起。
