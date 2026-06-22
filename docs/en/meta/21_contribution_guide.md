# 21. Contribution Guide

> 中文版：[../../meta/21_contribution_guide.md](../../meta/21_contribution_guide.md)

The Paoji ecosystem needs designers, developers, protocol designers, and the community to participate together.

## 1. What You Can Contribute

```text
Protocol proposals
Official Core components
Official Standard components
PJP Packs
Documentation translations
Renderer implementations
Test cases
Security rules
Registry design
Design tools
```

## 2. Minimum Requirements for Contributing Components

- Complete namespace.
- Version number.
- license.
- fallback.
- preview.
- Passes security scan.
- Complete Chinese description provided.
- Complete English description provided.

## 3. Naming Rules

```text
scope.owner.pack.type.name
```

Example:

```text
creator.mochi.plushcat.eye.sleepy-soft
```

## 4. Requirements for Official Inclusion

Official inclusion is stricter:

- Clear semantics.
- Recognizable at small sizes.
- Compatible with Core.
- Does not infringe third-party copyright.
- Has a long-term maintenance plan.
- Has a fallback graph.
- Has test screenshots.

## 5. Documentation Contributions

Documents support multiple languages.  
Each language version should be kept in sync and complete.

## 6. Versioning Principles

- patch: fix, does not change visual semantics.
- minor: new capability, backward compatible.
- major: breaking change, requires a new ID or new version range.

## 7. Deprecation Principles

Components can be deprecated, but should not be deleted.  
Old tokens must remain degradable whenever possible.
