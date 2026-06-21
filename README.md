# Paoji Design Wiki

Paoji 是一套开放式、可扩展的表情对象协议。它不是“更多 emoji”，而是让任何人都能创造、分享、解析、渲染和降级显示新表情的协议系统。

## 核心一句话

**Paoji = 短码入口 + 表情文档 + 组件包生态 + 注册表 + 渲染器 + 降级机制。**

## 为什么需要 Paoji

传统 emoji 的增长依赖中心化标准，新增慢、表达有限、用户不能真正创造可传播的新表情。Paoji 的目标是让表情从“固定字符”变成“可扩展对象”。

## 文件目录

项目文档按主题分组在 `docs/` 下，通过 GitHub Pages 部署。

```text
Paoji/
├── .github/workflows/deploy.yml   # GitHub Pages 部署工作流
├── docs/                          # GitHub Pages 站点根目录
│   ├── index.html                 # 文档索引页（按主题分组）
│   ├── paoji_landing.html         # 现代化官网原型
│   ├── paoji_wiki.html            # 设计师可读版 Wiki
│   ├── protocol/                  # 协议基础
│   │   ├── 01_protocol_overview.md
│   │   ├── 02_ys_token.md
│   │   ├── 03_pjd_document.md
│   │   └── 04_pjp_pack.md
│   ├── components/                # 组件
│   │   ├── 05_component_ecosystem.md
│   │   ├── 06_designer_guide.md
│   │   ├── 13_component_schema.md
│   │   └── 15_designer_checklist.md
│   ├── schemas/                   # 数据结构与渲染
│   │   ├── 11_payload_schema.md
│   │   └── 12_renderer_resolver.md
│   ├── registry/                  # 注册表与治理
│   │   ├── 07_registry_security.md
│   │   └── 14_governance_registry.md
│   ├── examples/                  # 示例与本地化
│   │   ├── 08_examples.md
│   │   └── 09_i18n_localization.md
│   ├── reference/                 # 参考
│   │   ├── 16_implementation_roadmap.md
│   │   ├── 17_api_reference.md
│   │   └── 18_testing_compatibility.md
│   └── meta/                      # 元信息
│       ├── 10_license_mit.md
│       ├── 19_glossary.md
│       ├── 20_faq.md
│       └── 21_contribution_guide.md
├── locales/                       # i18n 资源
│   ├── en-US.json
│   └── zh-CN.json
├── LICENSE
├── README.md
└── package.json
```

### 在线访问

推送到 GitHub 后，在仓库 **Settings → Pages → Build and deployment → Source** 选择 **GitHub Actions**，推送 main 分支即可自动部署。站点地址形如 `https://<user>.github.io/Paoji/`。

## 当前建议版本

```text
Paoji v0.6
YS Token: ⟦YS1<visualHint?>~<payload>.<crc>⟧
PJD: Paoji Document
PJP: Paoji Pack
PJR: Paoji Registry
```

## 设计原则

1. Token 永远短。
2. 表情能力可以无限扩展。
3. 无限扩展不靠 token，靠 PJD / PJP / Registry。
4. 官方组件和用户组件走同一套格式。
5. 区别只在 trust level，不在技术结构。
6. 所有组件必须有 namespace、version、hash、fallback。
7. 所有高级能力必须声明 requires。
8. 所有旧 token 必须尽量可降级显示。


## 多语言策略

```text
主语言：中文 zh-CN
首批辅助语言：英文 en-US
协议字段：不本地化
UI / 文档 / alt 文本：支持本地化
```

## 授权策略

Paoji 协议、文档、参考实现和网页原型采用宽松 MIT 授权。  
第三方组件包、用户组件包和商业资源包可以声明独立 license。


## 当前文档补全状态

v0.7.0 已补齐从概念、协议、设计、组件、渲染、安全、治理、测试到贡献的基础 Wiki。  
后续若进入开发阶段，建议把这些 Markdown 拆成正式 docs 站点，并配合 JSON Schema、测试用例和参考实现。
