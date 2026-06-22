# 10. License：松散 MIT

> English version: [../en/meta/10_license_mit.md](../en/meta/10_license_mit.md)

Paoji 当前建议采用偏宽松的 MIT 授权。

## 1. 授权范围

MIT 授权适用于本设计包中的：

```text
协议说明
设计文档
参考代码
官网原型
Wiki 页面
示例 Token
示例 JSON
```

## 2. 不自动包含的内容

MIT 授权不自动覆盖：

```text
第三方商标
外部字体
第三方图标
用户上传的自定义组件包
创作者声明了其他协议的 PJP Pack
平台私有资源
```

也就是说，Paoji 协议本身是宽松开放的，但具体组件包可以声明自己的 license。

## 3. 推荐规则

```text
Paoji 协议：MIT
官方基础组件：MIT 或 CC0
官方主题包：MIT / CC-BY / CC-BY-NC 可选
用户组件包：用户自定，但必须在 manifest 里声明
商业组件包：可以闭源，但必须声明使用限制
```

## 4. PJP Pack license 字段

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

## 5. 重要原则

协议开放，不等于所有组件资产都开放。  
Paoji 需要把“协议授权”和“组件包授权”分开处理。
