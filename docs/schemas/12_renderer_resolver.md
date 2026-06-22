# 12. Resolver 与 Renderer

> English version: [../en/schemas/12_renderer_resolver.md](../en/schemas/12_renderer_resolver.md)

Paoji 的显示流程由 Resolver 和 Renderer 共同完成。

## 1. Resolver 是什么

Resolver 负责把 YS Token 展开成可渲染对象。

```text
YS Token
↓
解析边界 / family / version
↓
校验 CRC
↓
解码 payload
↓
定位 PJD / PJP
↓
验证 hash / signature
↓
得到 PJD
```

Resolver 不负责画图，它负责“找到正确的对象”。

## 2. Renderer 是什么

Renderer 负责把 PJD 渲染成视觉结果。

```text
PJD
↓
加载组件
↓
处理 slot / anchor
↓
应用 transform / params
↓
应用 material / motion
↓
生成 SVG / Canvas / PNG / 动态图
```

## 3. 推荐渲染管线

```text
parseToken()
→ verifyToken()
→ resolvePayload()
→ loadPacks()
→ verifyPacks()
→ expandPJD()
→ checkCapabilities()
→ render()
→ fallbackIfNeeded()
```

## 4. 错误处理

| 错误 | 应对 |
|---|---|
| CRC 失败 | 拒绝渲染，提示 token 损坏 |
| Pack 不存在 | 尝试 Registry，再 fallback |
| Hash 不匹配 | 拒绝加载该资源 |
| Capability 不支持 | 降级渲染 |
| 组件缺失 | 使用组件 fallback |
| 全部失败 | 显示 Visual Hint / alt |

## 5. Renderer 能力声明

客户端应声明自己的能力：

```json
{
  "renderer": "paoji-web",
  "version": "0.7.0",
  "supports": [
    "paoji.core@1",
    "svg.path",
    "svg.gradient",
    "svg.mask",
    "filter.basic",
    "motion.basic"
  ],
  "limits": {
    "maxTokenLength": 512,
    "maxNodes": 256,
    "maxPackSizeBytes": 2097152
  }
}
```

## 6. 渲染安全限制

Renderer 必须在沙箱中处理用户组件：

```text
禁止 script
禁止事件处理器
禁止外部网络请求
禁止 foreignObject
限制 filter
限制节点数
限制路径长度
限制动画时长
限制资源包大小
```

## 7. 降级渲染

降级不是失败，而是协议的一部分。

```text
完整高级渲染
↓
基础 SVG 渲染
↓
Core 组件替换
↓
Visual Hint
↓
alt 文本
```
