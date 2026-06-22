# 10. License: Loose MIT

> 中文版：[../../meta/10_license_mit.md](../../meta/10_license_mit.md)

Paoji currently recommends the permissive MIT license.

## 1. Scope of License

The MIT license applies to the following in this design pack:

```text
Protocol specifications
Design documents
Reference code
Website prototype
Wiki pages
Example tokens
Example JSON
```

## 2. What Is Not Automatically Included

The MIT license does not automatically cover:

```text
Third-party trademarks
External fonts
Third-party icons
User-uploaded custom component packs
PJP Packs whose creators have declared other licenses
Platform-private assets
```

That is, the Paoji protocol itself is loosely open, but individual component packs may declare their own license.

## 3. Recommended Rules

```text
Paoji protocol: MIT
Official core components: MIT or CC0
Official theme packs: MIT / CC-BY / CC-BY-NC (optional)
User component packs: user-defined, but must be declared in manifest
Commercial component packs: may be closed-source, but usage restrictions must be declared
```

## 4. PJP Pack license Field

```json
{
  "license": "MIT",
  "licenseUrl": "https://opensource.org/license/mit",
  "rights": {
    "commercialUse": true,
    "derivatives": true,
    "redistribution": true
  }
}
```

## 5. Key Principles

An open protocol does not mean all component assets are open.  
Paoji treats "protocol license" and "component pack license" separately.
