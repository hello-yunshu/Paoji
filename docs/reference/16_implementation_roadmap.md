# 16. 实现路线图

> English version: [../en/reference/16_implementation_roadmap.md](../en/reference/16_implementation_roadmap.md)

## Phase 0：概念验证

目标：证明 Token → PJD → SVG 可行。

- YS Token 解析
- CRC 校验
- Visual Hint
- InlineCore payload
- 简单 SVG 渲染器
- PNG / SVG 导出

## Phase 1：官方核心组件

目标：建立最小可用官方 Core。

- paoji.core pack
- base / eye / mouth / deco / palette / style
- PJD 基础格式
- PJP manifest
- Core fallback

## Phase 2：组件编辑器

目标：让设计师能制作组件。

- SVG 上传
- 安全清洗
- 组件类型选择
- 锚点编辑
- 参数定义
- fallback 选择
- preview 生成
- PJP 导出

## Phase 3：PackRef 与 Registry

目标：支持复杂自定义组件。

- PackRef payload
- pack 加载与 hash 验证
- 本地 Registry
- 远程 Registry 原型
- 缓存机制
- trust level

## Phase 4：社区与发布

目标：建立组件生态雏形。

- 用户账号
- Pack 发布
- 版本管理
- license 声明
- 搜索和标签
- 审核 / 举报
- blocked list

## Phase 5：高级能力

目标：扩展到更复杂的表情对象。

- 动画
- 材质
- 多状态角色
- 表情系列生成
- 输入法 / 浏览器插件
- SDK
- 离线 `.paoji` bundle

## Phase 6：协议稳定

目标：冻结 Paoji v1。

- 规范文档
- 测试套件
- 兼容性矩阵
- 参考实现
- 安全规范
- 官方 Core v1 长期维护
