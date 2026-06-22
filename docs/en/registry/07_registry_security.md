# 07. Registry, Security and Trust

> 中文版：[../../registry/07_registry_security.md](../../registry/07_registry_security.md)

## 1. Role of PJR Registry

The PJR Registry is responsible for:

- Registering components
- Resolving namespace
- Viewing version
- Downloading PJP Pack
- Verifying hash
- Viewing trust level
- Viewing lifecycle status
- Viewing fallback
- Viewing license

The Registry should not be the only center. Paoji can have multiple registries such as official, community, personal, and enterprise intranet.

## 2. Resource Verification

Each pack must have:

```json
{
  "id": "user.hiyunshu.cloudglass",
  "version": "1.0.0",
  "hash": "sha256-...",
  "signature": "ed25519-...",
  "publisher": "user.hiyunshu"
}
```

## 3. Trust Levels

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

Suggested default policy:

- Automatically render `official` and above.
- `community` may prompt user for confirmation.
- `untrusted` is not loaded automatically by default.
- `blocked` is refused to load.

## 4. Safe SVG Subset

Allowed:

- path
- rect / circle / ellipse / polygon
- g
- defs
- linearGradient / radialGradient
- clipPath / mask whitelist
- limited filter
- transform
- opacity

Prohibited:

- script
- foreignObject
- iframe
- onload / onclick and other events
- external network requests
- external image loading by default
- remote fonts
- oversized base64
- infinite filters
- overly long animations

## 5. Fallback Chain

```text
full PJP rendering
↓
basic PJD rendering
↓
Paoji Core fallback
↓
Visual Hint
↓
alt text
```

If Paoji wants to replace emoji, it must ensure that there is always a visible fallback in any environment.
