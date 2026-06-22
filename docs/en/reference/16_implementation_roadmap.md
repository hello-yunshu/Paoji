# 16. Implementation Roadmap

> 中文版：[../../reference/16_implementation_roadmap.md](../../reference/16_implementation_roadmap.md)

## Phase 0: Proof of Concept

Goal: Prove that Token → PJD → SVG is feasible.

- YS Token parsing
- CRC verification
- Visual Hint
- InlineCore payload
- Simple SVG Renderer
- PNG / SVG export

## Phase 1: Official Core Components

Goal: Build a minimal usable official Core.

- paoji.core pack
- base / eye / mouth / deco / palette / style
- PJD base format
- PJP manifest
- Core fallback

## Phase 2: Component Editor

Goal: Let designers create components.

- SVG upload
- Safe sanitization
- Component type selection
- Anchor editing
- Parameter definition
- fallback selection
- preview generation
- PJP export

## Phase 3: PackRef and Registry

Goal: Support complex custom components.

- PackRef payload
- pack loading and hash verification
- Local Registry
- Remote Registry prototype
- Caching mechanism
- trust level

## Phase 4: Community and Publishing

Goal: Establish the foundation of a component ecosystem.

- User accounts
- Pack publishing
- version management
- license declaration
- Search and tags
- Review / report
- blocked list

## Phase 5: Advanced Capabilities

Goal: Extend to more complex expression objects.

- Animation
- Materials
- Multi-state characters
- Expression series generation
- Input method / browser plugin
- SDK
- Offline `.paoji` bundle

## Phase 6: Protocol Stabilization

Goal: Freeze Paoji v1.

- Specification documents
- Test suite
- Compatibility matrix
- Reference implementation
- Security specification
- Official Core v1 long-term maintenance
