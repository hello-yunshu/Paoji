# 12. Resolver and Renderer

> 中文版：[../../schemas/12_renderer_resolver.md](../../schemas/12_renderer_resolver.md)

The Paoji display flow is completed jointly by the Resolver and the Renderer.

## 1. What is a Resolver

The Resolver is responsible for expanding a YS Token into a renderable object.

```text
YS Token
↓
parse boundary / family / version
↓
verify CRC
↓
decode payload
↓
locate PJD / PJP
↓
verify hash / signature
↓
obtain PJD
```

The Resolver is not responsible for drawing; it is responsible for "finding the correct object".

## 2. What is a Renderer

The Renderer is responsible for rendering a PJD into a visual result.

```text
PJD
↓
load components
↓
process slot / anchor
↓
apply transform / params
↓
apply material / motion
↓
generate SVG / Canvas / PNG / animation
```

## 3. Recommended Rendering Pipeline

```text
parseToken()
→ verifyToken()
→ resolvePayload()
→ loadPacks()
→ verifyPacks()
→ expandPJD()
→ checkCapabilities()
→ render()
→ fallbackIfNeeded()
```

## 4. Error Handling

| Error | Response |
|---|---|
| CRC failure | Refuse to render, prompt that the token is corrupted |
| Pack not found | Try Registry, then fallback |
| Hash mismatch | Refuse to load the resource |
| Capability not supported | Degrade rendering |
| Component missing | Use component fallback |
| All failed | Show Visual Hint / alt |

## 5. Renderer Capability Declaration

Clients should declare their own capabilities:

```json
{
  "renderer": "paoji-web",
  "version": "0.7.0",
  "supports": [
    "paoji.core@1",
    "svg.path",
    "svg.gradient",
    "svg.mask",
    "filter.basic",
    "motion.basic"
  ],
  "limits": {
    "maxTokenLength": 512,
    "maxNodes": 256,
    "maxPackSizeBytes": 2097152
  }
}
```

## 6. Rendering Security Restrictions

The Renderer must process user components in a sandbox:

```text
no script
no event handlers
no external network requests
no foreignObject
limit filter
limit node count
limit path length
limit animation duration
limit resource pack size
```

## 7. Degraded Rendering

Degradation is not a failure; it is part of the protocol.

```text
full advanced rendering
↓
basic SVG rendering
↓
Core component substitution
↓
Visual Hint
↓
alt text
```
