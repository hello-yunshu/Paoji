# 20. FAQ

> 中文版：[../../meta/20_faq.md](../../meta/20_faq.md)

## Is Paoji an emoji?

No, it is not a traditional Unicode emoji. Paoji is an Open Expression Object Protocol.

## Can Paoji replace emoji?

The goal is to replace the expression mechanism, not the Unicode character encoding itself. Paoji is more like "expression object protocol + resource ecosystem + renderer".

## Why is Visual Hint still needed?

Because when there is no renderer, users can at least see the approximate semantics. Visual Hint is part of fallback.

## Is Visual Hint authoritative data?

No. Authoritative data comes from the PJD / PJP expanded from the payload.

## Can users customize components?

Yes. Users add custom components through PJP Packs, but must declare namespace, version, hash, fallback, and license.

## What if the official components keep growing indefinitely?

Official components must also be packed, versioned, and registered. Core only maintains a minimal stable set; other official components grow through official packs.

## What if others don't have my component pack?

The Renderer will degrade along the fallback chain: custom component → official component → Visual Hint → alt text.

## Why does the protocol use MIT?

MIT is permissive enough to facilitate diffusion, implementation, secondary development, and commercial use. But specific component packs can use their own license.

## Does Paoji have security risks?

Yes, so user components must be sandboxed, SVG must be sanitized, and scripts, events, external requests, and uncontrolled resources are prohibited.

## What should the first version of Paoji do?

Start with:

```text
YS Token
PJD basic format
PJP manifest
Official Core components
Web Renderer
Designer Wiki
SVG / PNG export
```
