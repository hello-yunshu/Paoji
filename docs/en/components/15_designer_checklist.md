# 15. Designer Checklist

> 中文版：[../../components/15_designer_checklist.md](../../components/15_designer_checklist.md)

For designers to self-check before submitting Paoji components or component packs.

## 1. Component Basics

- [ ] Uses 1024×1024 viewBox.
- [ ] Component type is clear.
- [ ] Namespace is complete.
- [ ] Has version number.
- [ ] Has display name and description.
- [ ] Has Chinese description text.
- [ ] Has English description text.
- [ ] Has license.

## 2. Composability

- [ ] Has reasonable anchors.
- [ ] Can compose with official Core components.
- [ ] Parameters do not depend on a fixed background.
- [ ] Still recognizable at small sizes.
- [ ] Does not conflict with other standard slots.

## 3. Parameters

- [ ] Parameters have types.
- [ ] Parameters have default values.
- [ ] Numeric parameters have min / max.
- [ ] Color parameters can inherit palette.
- [ ] Not too many parameters.

## 4. Fallback

- [ ] Has same-type official fallback.
- [ ] Has Visual Hint.
- [ ] Has alt text.
- [ ] Can still degrade gracefully when pack is missing.

## 5. Security

- [ ] Does not contain script.
- [ ] Does not contain event handlers.
- [ ] Does not depend on external images.
- [ ] Does not depend on remote fonts.
- [ ] SVG passes security scan.
- [ ] Reasonable file size.

## 6. Visual Quality

- [ ] Recognizable at 32px.
- [ ] Has detail at 64px.
- [ ] Looks good at 256px.
- [ ] Not rough at 1024px.
- [ ] Works with transparent background.
- [ ] Readable on both dark and light backgrounds.

## 7. Publishing

- [ ] manifest is complete.
- [ ] preview.png is generated.
- [ ] hash is generated.
- [ ] signature is optional but recommended.
- [ ] Registry metadata is complete.
