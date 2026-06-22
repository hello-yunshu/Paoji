# 14. Registry and Ecosystem Governance

> 中文版：[../../registry/14_governance_registry.md](../../registry/14_governance_registry.md)

Paoji must have a governance mechanism to support unlimited expansion. Governance is not centralized control; it is about making components discoverable, verifiable, degradable, and blockable.

## 1. Registry is Not the Only Center

Paoji can have multiple Registries:

```text
official registry
community registry
creator registry
personal registry
enterprise internal registry
offline registry
```

The Registry is responsible for discovery; hash and signature are responsible for verification.

## 2. Registry Records

```json
{
  "id": "user.hiyunshu.cloudglass",
  "type": "pack",
  "version": "1.0.0",
  "hash": "sha256-...",
  "signature": "ed25519-...",
  "publisher": "user.hiyunshu",
  "trust": "personal",
  "status": "stable",
  "mirrors": [
    "https://...",
    "ipfs://..."
  ],
  "license": "MIT"
}
```

## 3. Trust Level

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

Suggested defaults:

```text
official and above: automatic rendering
community: may prompt for confirmation
personal: local or friend source
untrusted: not loaded by default
blocked: refused to load
```

## 4. Lifecycle

```text
draft
experimental
stable
deprecated
archived
blocked
```

Important rules:

```text
deprecated does not mean deleted
archived can still be referenced by old tokens
blocked is only used for security or severe infringement risk
```

## 5. Namespace Reservation

```text
paoji.core.*       official core
paoji.std.*        standard components
paoji.official.*   official extensions
creator.*          verified creators
community.*        community maintained
user.*             regular users
local.*            local private
```

Users cannot register `paoji.core.*` or `paoji.official.*`.

## 6. Conflict Handling

If two packs are visually similar, it is not necessarily a conflict.
If two packs use the same namespace, the later registrant must rename.

## 7. Takedown Policy

When a component pack is taken down:

```text
cached users can still render locally
new users no longer auto-download
Registry marks as archived / blocked
Renderer can use fallback
```
