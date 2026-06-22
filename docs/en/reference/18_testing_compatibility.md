# 18. Testing and Compatibility

> 中文版：[../../reference/18_testing_compatibility.md](../../reference/18_testing_compatibility.md)

Paoji needs to test not only rendering results, but also protocol stability, security, fallback, and cross-version compatibility.

## 1. Token Tests

- Valid token can be parsed.
- CRC error will be rejected.
- visualHint modification causes CRC to fail.
- payload that is not base64url will be rejected.
- Overly long token will be rejected or warned.
- YS is case-sensitive.

## 2. Payload Tests

- InlineCore can be expanded.
- PackRef can locate pack.
- DocRef can locate PJD.
- Unknown schema can fail safely.
- Unknown block can be skipped.
- Missing fields produce reasonable errors.

## 3. PJD Tests

- Missing optional fields still render.
- Missing required fields give clear errors.
- requires not satisfied triggers fallback.
- Multilingual fields display according to fallback chain.
- nodes order and layer are correct.

## 4. PJP Tests

- manifest integrity.
- hash verification.
- signature verification.
- Component fallback exists.
- SVG security scan.
- File size limit.
- External resources rejected.

## 5. Rendering Tests

Recommended sizes:

```text
32px
64px
128px
256px
1024px
```

Scenarios:

```text
Light background
Dark background
Transparent background
High contrast mode
No animation mode
Low performance mode
```

## 6. Fallback Tests

Every complex expression must be tested:

```text
Full resources available
Missing advanced capabilities
Missing custom pack
registry offline
hash mismatch
Only visualHint left
Only alt text left
```

## 7. Compatibility Matrix

| Client | Level 0 | Level 1 | Level 2 | Level 3 |
|---|---:|---:|---:|---:|
| Plain text | ✅ | ❌ | ❌ | ❌ |
| Basic Web | ✅ | ✅ | ❌ | ❌ |
| Paoji Web | ✅ | ✅ | ✅ | Partial |
| Advanced App | ✅ | ✅ | ✅ | ✅ |
