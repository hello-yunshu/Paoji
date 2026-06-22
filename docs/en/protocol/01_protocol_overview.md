# 01. Paoji Protocol Overview

> 中文版：[../../protocol/01_protocol_overview.md](../../protocol/01_protocol_overview.md)

## 1. Definition

Paoji is an open expression object protocol. It uses a copyable short text Token to represent an expression entry point, then the Resolver locates the corresponding expression document, component pack, and resources, and finally the Renderer displays it as a visual expression.

## 2. Core Objects

```text
YS Token  →  Resolver  →  PJD  →  PJP  →  Renderer  →  SVG / PNG / dynamic expression
```

| Object | Purpose |
|---|---|
| YS Token | Propagation, identification, verification, addressing |
| Visual Hint | Human-readable emoji / Unicode visual hint |
| Payload | Machine-decodable authoritative entry data |
| PJD | Paoji Document, plaintext expression structure |
| PJP | Paoji Pack, component, material, animation, and character resource pack |
| PJR | Paoji Registry, resource discovery, version, trust, and hash index |
| Renderer | Resolve, load, verify, render, and fallback |

## 3. Differences Between Paoji and Emoji

| Emoji | Paoji |
|---|---|
| Fixed character set | Extensible expression object protocol |
| New additions depend on Unicode standard | Official, community, and user extensible |
| Font rendering | Resolver + Renderer rendering |
| Inconsistent platform styles | Can lock pack / version / hash |
| Hard to customize | Users can design components and resource packs |
| No complex parameters | Supports materials, animations, nodes, components, semantics |

## 4. Core Architecture

```text
Paoji
├─ YS Token
│  ├─ InlineCore
│  ├─ PackRef
│  ├─ DocRef
│  ├─ BundleRef
│  └─ Hybrid
│
├─ PJD Document
│  ├─ packs
│  ├─ core
│  ├─ nodes
│  ├─ materials
│  ├─ motion
│  ├─ semantics
│  ├─ requires
│  ├─ fallback
│  └─ ext
│
├─ PJP Pack
│  ├─ manifest
│  ├─ components
│  ├─ palettes
│  ├─ materials
│  ├─ motions
│  ├─ glyphs
│  └─ fallbacks
│
├─ PJR Registry
│  ├─ namespace
│  ├─ version
│  ├─ hash
│  ├─ trust
│  └─ lifecycle
│
└─ Renderer
   ├─ resolve
   ├─ verify
   ├─ sandbox
   ├─ render
   ├─ fallback
   └─ cache
```

## 5. Compatibility Levels

| Level | Capability |
|---|---|
| Level 0 | Only displays Token or Visual Hint |
| Level 1 | Supports Paoji Core basic rendering |
| Level 2 | Supports loading PJP Pack |
| Level 3 | Supports animations, materials, filters, advanced components |
