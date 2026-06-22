# 02. YS Token Specification

> 中文版：[../../protocol/02_ys_token.md](../../protocol/02_ys_token.md)

## 1. Basic Format

```text
⟦YS1<visualHint?>~<payload>.<crc>⟧
```

Example:

```text
⟦YS1🐱💜🥺😿🫧🌙🪽💧~AgEBAf8A.gGs⟧
```

## 2. Field Description

| Field | Description |
|---|---|
| `⟦` | Start boundary |
| `YS` | Protocol family, case-sensitive |
| `1` | Major version number |
| `visualHint` | Optional visual hint section |
| `~` | Payload start |
| `payload` | base64url-encoded machine entry data |
| `.` | Checksum start |
| `crc` | base64url 3-character CRC16-CCITT |
| `⟧` | End boundary |

## 3. Visual Hint Rules

Visual Hint is not authoritative data; it only serves as a human hint and fallback display.

Recommended structure:

```text
[theme][tone][emotion][expression][style][free-form hints...]
```

Example:

```text
🐱💜🥺😿🫧🌙🪽💧
```

Explanation:

```text
🐱 = theme: cat
💜 = tone: purple
🥺 = emotion: pitiful
😿 = expression: crying / cat face
🫧 = style: glass / bubble
🌙🪽💧 = free-form mood hint
```

Recommendations:

- Standard hint slots: 0 or 5 grapheme clusters.
- Free extension slots: 0–27.
- Recommended total length ≤ 16, hard limit 32.
- Must be parsed by grapheme cluster, not by plain string length.
- The checksum covers the visualHint to prevent arbitrary tampering.

## 4. Payload Schema

Payload can point to different types of data:

| Schema | Purpose |
|---|---|
| InlineCore | Pure official core components, can be self-contained |
| PackRef | References a glyph / variant in a PJP Pack |
| DocRef | References a complete PJD document |
| BundleRef | References an offline bundle |
| Hybrid | Built-in fallback, also references a complete document or resource pack |

## 5. Decoding Flow

```text
1. Coarse recognition of ⟦YS1...⟧
2. Check boundaries and protocol family
3. Split out visualHint / payload / crc
4. Verify CRC
5. base64url decode payload
6. Parse as entry object according to schema
7. Resolve PJD or PJP reference
8. Verify hash / version / signature
9. Render
10. Fallback on failure
```

## 6. Regex Coarse Recognition

```regex
⟦YS[0-9A-Z].+?~[A-Za-z0-9_-]+\.[A-Za-z0-9_-]{3}⟧
```

Note: Regex only handles coarse recognition and cannot replace full verification.
