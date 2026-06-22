# 11. Payload Schema Design

> 中文版：[../../schemas/11_payload_schema.md](../../schemas/11_payload_schema.md)

The payload of a YS Token is the machine-facing entry data. It is not meant to carry unlimited complexity; instead, it tells the Resolver how this expression should be expanded.

## 1. Payload Basic Principles

```text
1. payload must be short.
2. payload must be verifiable.
3. payload must be versionable.
4. payload must support multiple schemas.
5. payload must not assume all expressions can be inlined.
6. payload must be able to point to PJD / PJP / Bundle.
```

## 2. Recommended Schema Types

| Schema | Name | Purpose |
|---:|---|---|
| 0x01 | InlineCore | Lightweight self-contained expressions using only Paoji Core / Standard |
| 0x02 | PackRef | Reference a glyph / variant in a PJP Pack |
| 0x03 | DocRef | Reference a complete PJD document |
| 0x04 | BundleRef | Reference an offline `.paoji` Bundle |
| 0x05 | Hybrid | Token carries a basic fallback while also referencing full resources |
| 0x7F | Extension | Reserved extension schema |

## 3. Why Not to Use Fixed Bit-Packing for Long-Term Expansion

Fixed bitpack is suitable for MVP, but not for the future:

```text
theme 5 bits     → only 32 themes can be supported
palette 5 bits   → only 32 palettes can be supported
node type 5 bits → only 32 node types can be supported
```

Paoji's goal is unlimited expansion, so fixed bitpack can only be used for `InlineCore` and cannot become the only payload format.

## 4. Recommended TLV / Block Structure

The formal payload in the future is recommended to adopt a block structure:

```text
Payload
├─ HeaderBlock
├─ EntryBlock
├─ FallbackBlock?
├─ IntegrityBlock?
└─ ExtensionBlock[]
```

Each block:

```text
blockType varint
blockLength varint
blockData bytes
```

Advantages:

```text
Old parsers can skip unknown blocks
New fields can be added incrementally
Can support DocRef / PackRef / Hybrid
Can support compression and signatures
```

## 5. PackRef Payload Plaintext Form

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

## 6. DocRef Payload Plaintext Form

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
    "alt": "Lilac glass cat cloud, pleading big eyes, cat mouth"
  }
}
```

## 7. Hybrid Payload

Hybrid is the most suitable long-term direction for public sharing:

```text
Token carries basic fallback
+
References complete PJD / PJP
```

This way, even if the resource pack cannot be loaded, a basic version can still be displayed.

## 8. Payload Versioning Strategy

The payload schema should be independent of the YS Token major version.

```text
YS1 = token shell version
payloadSchema = payload structure version
PJD version = document format version
PJP version = resource pack format version
```

Do not tie all versions together.
