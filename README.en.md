<div align="center">
  <img src="docs/assets/brand/paoji-logo.png" width="360" alt="Paoji" />

  <br/>

  **Leave the fixed list behind, embrace infinite expression.**

  <sub>告别固定列表，拥抱无限表达。</sub>

  <br/>

  [![Website](https://img.shields.io/badge/website-hello--yunshu.github.io-D84727?style=flat-square)](https://hello-yunshu.github.io/Paoji/)
  [![Spec](https://img.shields.io/badge/spec-v0.7.0-7655E8?style=flat-square)](https://hello-yunshu.github.io/Paoji/paoji_wiki.html#protocol/01_protocol_overview.md)
  [![License](https://img.shields.io/badge/license-MIT-242128?style=flat-square)](LICENSE)
  [![Docs](https://img.shields.io/badge/docs-English%20%7C%20中文-FF716C?style=flat-square)](README.md)

  <sub>
    <a href="https://hello-yunshu.github.io/Paoji/">Website</a> ·
    <a href="https://hello-yunshu.github.io/Paoji/paoji_wiki.html">Wiki</a> ·
    <a href="https://hello-yunshu.github.io/Paoji/docs.html">Docs Index</a> ·
    <a href="README.md">中文</a>
  </sub>
</div>

<br/>

## What is Paoji

Paoji is an **open, extensible expression object protocol**. It does not try to add another batch of emoji. Instead, it defines a universal way for expressions to be created, composed, shared, resolved, verified, rendered, and gracefully degraded on clients that lack full capability.

> **Paoji = compact token + expression document + component packs + registry + renderer + fallback.**

Traditional emoji rely on a centralized character standard: the release cycle is long, the expressive power is limited, and it is hard for users to create a new expression that can travel across platforms. Paoji promotes expressions from "fixed characters" to "extensible objects" while keeping the advantages of short text — easy to copy, easy to fall back.

---

## How does it work

<div align="center">
  <img src="docs/assets/brand/protocol-flow.svg" width="88%" alt="YS Token to Paoji Renderer protocol flow" />
</div>

```text
YS Token  →  Resolver  →  PJD  →  PJP / PJR  →  Renderer  →  Visual / Fallback
```

1. **YS Token** — a short, copyable, recognizable, verifiable text entry point.
2. **Resolver** — resolves the entry and locates the corresponding PJD, resource pack, and version.
3. **PJD** — describes the structure, semantics, dependencies, and fallback of the expression.
4. **PJP / PJR** — provide component resources, plus version, hash, and trust indices.
5. **Renderer** — verifies and composes resources, outputting SVG, PNG, or animated expressions; when incompatible, it falls back to a Visual Hint or replacement text.

---

## Core Objects

| Object | Full name | Role |
|---|---|---|
| **YS Token** | Short token entry | Propagation, recognition, verification, and addressing |
| **PJD** | Paoji Document | Describes structure, semantics, dependencies, and fallback |
| **PJP** | Paoji Pack | Encapsulates components, materials, animations, glyphs, and theme resources |
| **PJR** | Paoji Registry | Provides resource discovery, version, hash, trust, and lifecycle index |
| **Renderer** | Renderer | Parsing, verification, sandboxing, composition, caching, and fallback display |

---

## Official Core Expression Library

The repository already includes the first experimental [`paoji.core`](packs/paoji-core/README.en.md) component pack — not a finished set of expression stickers, but a set of minimal expression elements that the Renderer can freely compose:

<div align="center">
  <img src="packs/paoji-core/preview.svg" width="72%" alt="Six composition examples of the official Paoji Core Pack" />
</div>

| Type | Count | Contents |
|---|---:|---|
| Base face `base` | 3 | round, soft-square, cloud |
| Eyes `eye` | 6 | dot, happy, sleepy, pleading, surprised, wink |
| Brows `brow` | 3 | soft, worried, angry |
| Mouth `mouth` | 6 | smile, open smile, pout, calm, surprised, cat mouth |
| Face & decoration `cheek / deco` | 6 | blush, shy lines, heart, tear, sweat, sparkle |
| Palette `palette` | 4 | warm sun, lavender, mint, monochrome |

All components are `1024 × 1024` transparent SVG, with no scripts, no external fonts, and no network dependencies. See the [Core Pack guide](packs/paoji-core/README.en.md) or open the [manifest](packs/paoji-core/manifest.json) directly.

---

## Design Principles

- **Short entry, infinite extension** — the token only carries propagation; complex capabilities live in PJD, PJP, and Registry.
- **Isomorphic ecosystem** — official and user components share the same format; differences are reflected in trust level, not technical privilege.
- **Verifiable** — components must declare namespace, version, hash, license, and requires.
- **Degradable** — complex capabilities must have fallback; old tokens should not fail because new versions appear.
- **Progressive compatibility** — from showing only a Visual Hint, to full material, animation, and advanced component rendering.
- **Localization-friendly** — protocol fields stay stable; UI, documentation, semantics, and alt text can be localized.

---

## Current Status

Paoji `v0.7.0` is still primarily a **protocol and ecosystem design specification**. The repository already provides an experimental official Core Pack; the reference Renderer, formal JSON Schema, compatibility test suite, and SDK are still on the implementation roadmap and are not claimed to be production-ready.

| Capability | Status |
|---|---|
| Protocol concepts and core objects | Design documents formed |
| PJD / PJP / Payload structure | Draft formed |
| Component ecosystem, Registry, and security governance | Draft formed |
| API, testing, and compatibility strategy | Draft formed |
| Official Core Pack | `0.1.0 experimental`, 24 components + 4 palettes |
| Reference Renderer, formal Schema, and SDK | Planned |
| Paoji v1 stable specification | Long-term goal |

See the [Implementation Roadmap](https://hello-yunshu.github.io/Paoji/paoji_wiki.html#reference/16_implementation_roadmap.md) for the full plan.

---

## Where to start

| Your role | Recommended reading |
|---|---|
| New to Paoji | [Protocol Overview](https://hello-yunshu.github.io/Paoji/paoji_wiki.html#protocol/01_protocol_overview.md) → [FAQ](https://hello-yunshu.github.io/Paoji/paoji_wiki.html#meta/20_faq.md) |
| Protocol or client developer | [YS Token](https://hello-yunshu.github.io/Paoji/paoji_wiki.html#protocol/02_ys_token.md) → [PJD](https://hello-yunshu.github.io/Paoji/paoji_wiki.html#protocol/03_pjd_document.md) → [Renderer](https://hello-yunshu.github.io/Paoji/paoji_wiki.html#schemas/12_renderer_resolver.md) |
| Component designer | [Component Ecosystem](https://hello-yunshu.github.io/Paoji/paoji_wiki.html#components/05_component_ecosystem.md) → [Designer Guide](https://hello-yunshu.github.io/Paoji/paoji_wiki.html#components/06_designer_guide.md) → [Checklist](https://hello-yunshu.github.io/Paoji/paoji_wiki.html#components/15_designer_checklist.md) |
| Pack / Registry implementer | [PJP](https://hello-yunshu.github.io/Paoji/paoji_wiki.html#protocol/04_pjp_pack.md) → [Registry Security](https://hello-yunshu.github.io/Paoji/paoji_wiki.html#registry/07_registry_security.md) → [Governance](https://hello-yunshu.github.io/Paoji/paoji_wiki.html#registry/14_governance_registry.md) |
| Contributor | [Roadmap](https://hello-yunshu.github.io/Paoji/paoji_wiki.html#reference/16_implementation_roadmap.md) → [Contribution Guide](https://hello-yunshu.github.io/Paoji/paoji_wiki.html#meta/21_contribution_guide.md) |

---

## Repository Structure

```text
Paoji/
├── docs/
│   ├── index.html        # Landing page (GitHub Pages entry)
│   ├── docs.html         # Documentation index
│   ├── paoji_wiki.html   # Wiki document reader
│   ├── assets/           # Core brand and protocol visual assets
│   ├── en/               # English documentation mirror
│   ├── protocol/         # Token, PJD, PJP, and protocol basics
│   ├── components/       # Component ecosystem, schemas, and design guides
│   ├── schemas/          # Payload, Resolver, and Renderer
│   ├── registry/         # Registry, security, and governance
│   ├── examples/         # Examples and localization
│   ├── reference/        # API, roadmap, and compatibility tests
│   └── meta/             # Glossary, FAQ, license, and contribution
├── packs/                # Official PJP component packs (incl. paoji.core)
├── locales/              # zh-CN / en-US localization resources
├── package.json          # Project metadata and release manifest
└── LICENSE               # MIT License
```

---

## Language and Contribution

Paoji's documentation and ecosystem support both Chinese (`zh-CN`) and English (`en-US`), with room for more languages. Protocol fields and identifiers are not localized; human-facing documentation, UI, semantics, and alt text should support localization.

Designers, protocol authors, client developers, security researchers, and translation contributors are all welcome. Please read the [Contribution Guide](https://hello-yunshu.github.io/Paoji/paoji_wiki.html#meta/21_contribution_guide.md) before submitting. The protocol, documentation, and web prototype use the [MIT License](LICENSE); third-party resource packs may declare their own licenses.

<br/>

<div align="center">
  <sub>
    Paoji v0.7.0 · Bilingual (zh-CN / en-US) · MIT License ·
    <a href="https://hello-yunshu.github.io/Paoji/">Website</a> ·
    <a href="README.md">中文 README</a>
  </sub>
</div>
