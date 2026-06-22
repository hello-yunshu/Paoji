# 01. Paoji 协议总览

> English version: [../en/protocol/01_protocol_overview.md](../en/protocol/01_protocol_overview.md)

## 1. 定义

Paoji 是一套开放式表情对象协议。它通过一段可复制的短文本 Token 表达一个表情入口，再由解析器找到对应的表情文档、组件包和资源，最终由渲染器显示成可视化表情。

## 2. 核心对象

```text
YS Token  →  Resolver  →  PJD  →  PJP  →  Renderer  →  SVG / PNG / 动态表情
```

| 对象 | 作用 |
|---|---|
| YS Token | 用于传播、识别、校验、寻址 |
| Visual Hint | 给人看的 emoji / Unicode 视觉提示 |
| Payload | 机器可解码的权威入口数据 |
| PJD | Paoji Document，表情明文结构 |
| PJP | Paoji Pack，组件、材质、动画、角色资源包 |
| PJR | Paoji Registry，资源发现、版本、信任和 hash 索引 |
| Renderer | 解析、加载、验证、渲染和降级 |

## 3. Paoji 与 emoji 的区别

| Emoji | Paoji |
|---|---|
| 固定字符表 | 可扩展表情对象协议 |
| 新增依赖 Unicode 标准 | 官方、社群、用户都可扩展 |
| 字体渲染 | Resolver + Renderer 渲染 |
| 平台样式不统一 | 可锁定 pack / version / hash |
| 难以自定义 | 用户可设计组件与资源包 |
| 无复杂参数 | 支持材质、动画、节点、组件、语义 |

## 4. 核心架构

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

## 5. 兼容级别

| Level | 能力 |
|---|---|
| Level 0 | 只显示 Token 或 Visual Hint |
| Level 1 | 支持 Paoji Core 基础渲染 |
| Level 2 | 支持加载 PJP Pack |
| Level 3 | 支持动画、材质、滤镜、高级组件 |
