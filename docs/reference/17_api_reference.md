# 17. 参考 API 草案

这不是最终实现，只是开发者理解协议的参考接口。

## 1. Token

```ts
type YSToken = string

function parseToken(token: YSToken): ParsedToken
function verifyToken(token: YSToken): VerifyResult
function createToken(input: TokenInput): YSToken
```

## 2. Resolver

```ts
interface Resolver {
  resolve(token: YSToken): Promise<PJD>
  resolvePayload(payload: Uint8Array): Promise<PJD>
  loadPack(ref: PackRef): Promise<PJP>
  verifyPack(pack: PJP): Promise<boolean>
}
```

## 3. Renderer

```ts
interface Renderer {
  capabilities(): RendererCapabilities
  render(doc: PJD): Promise<RenderResult>
  renderFallback(doc: PJD): Promise<RenderResult>
}
```

## 4. Component Registry

```ts
interface Registry {
  findPack(id: string, version?: string): Promise<PackRecord>
  findComponent(id: string): Promise<ComponentRecord>
  getTrustLevel(id: string): Promise<TrustLevel>
}
```

## 5. PJD 类型简化

```ts
type PJD = {
  format: "PJD"
  version: number
  id?: string
  name?: LocalizedText
  packs: PackRef[]
  core: Record<string, unknown>
  nodes: PJDNode[]
  requires?: string[]
  fallback: FallbackSpec
}
```

## 6. PJD Node

```ts
type PJDNode = {
  id: string
  component: string
  slot?: string
  transform?: {
    x?: number
    y?: number
    scale?: number
    rotation?: number
    opacity?: number
  }
  params?: Record<string, unknown>
  layer?: number
}
```

## 7. LocalizedText

```ts
type LocalizedText = {
  "zh-CN": string
  "en-US"?: string
  [locale: string]: string | undefined
}
```
