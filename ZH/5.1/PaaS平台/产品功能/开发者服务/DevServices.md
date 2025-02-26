# 开发者服务

## 服务概述
蓝鲸 PaaS 平台的核心功能就是为开发者提供了通用的、便捷的开发者服务，成为企业内部技术体系的核心发动机，助力企业构建内部私有化的 SaaS 应用市场。

![](../../assets/devall.png)

基于 PaaS 的开发模式，大幅提升企业内部应用构建的效率。

![](../../assets/devmoshi.png)

下面将介绍基于蓝鲸 PaaS 平台的特色开发者服务。

## 开发环境

按照开发者的习惯，为每个开发者自己创建的 SaaS 提供了 3 个环境，最大限度保证自研 SaaS 的可用性。

(1) 本地开发环境：开发者在本地开发、编码的环境

(2) 测试环境：SaaS 未发布之前，部署到 PaaS 平台测试其功能的有效性和完整性

(3) 正式环境：SaaS 部署到正式环境后，其他用户即可在 “工作台” 看到该 SaaS

![](../../assets/devenv.png)

所以，本地环境和测试环境的主要用户为开发者，用于开发者编码和自测；正式环境，即就是将 SaaS 正式发布对外，是所有用户都可以看到并使用的。

说明：虽然用户可以看到系统，但是是否能访问这个系统，取决于应用的设计与开发，可以针对用户进行授权。

## 开发框架

为了提高开发效率，蓝鲸提供了统一的 “开发框架”， 该 “开发框架” 集成统一登录鉴权模块、功能开关模块、WEB 安全防护模块、功能组件模块等通用模块。让用户可以专注于代码逻辑的构建。

当用户将代码在本地运行，或者打开线上的 “开发框架” SaaS ，将会看到下图的界面。

![](../../assets/framework.png)

为了最大程度降低开发难度，基于 “开发框架” 研发了 “开发样例”，即就是做了部分通过的功能。

![](../../assets/frameexample.png)

- 统一登录鉴权模块：统一使用 PaaS 平台的 “用户管理” 和登录逻辑

- WEB 安全防护：主要包括防 csrf 攻击和防 xss 攻击。使用 django 提供的 csrf 模块，开发者无需做其他设置。如需对某些请求去除 csrf 验证，可在对应 view 函数添加 csrf_exempt 装饰器； xss 攻击的中间件，会对所有请求参数将进行特殊字符转义（富文本内容、URL 有特殊处理方式）。

- 功能开关模块：支持开发者在 SaaS 开发迭代中对功能选择性开放、灰度测试等。

## 可扩展的应用变量

对应有些敏感变量，比如外部数据库 IP，账号密码等，直接写到代码中会有暴露风险，而且每次修改，需要拉取代码，修改提测上线后才能使用，蓝鲸开发者中心针对该场景，使用变量设置功能完全可以解决开发者的变量硬编码问题。
![](../../assets/varible.png)

## 免运维托管
该功能是 PaaS 模式最核心的功能，基于 Virtualenv 的应用部署模式，在
SaaS 部署时，平台为会它们创建独立的 Virtualenv，保证每个 SaaS 拥有一套 “隔离” 的 Python 运行环境。SaaS 的服务进程则是以 uWSGI 的 cheaper 模式托管，由于采用了 Busyness 算法，uWSGI 能够根据繁忙度，动态的调配 worker 个数，从而达到合理利用系统资源的目的


## API 网关

API 网关，又称 “企业服务总线”，ESB，API Gateway。它有两个作用：其一，为整个蓝鲸体系服务，蓝鲸的其他平台，如：配置平台、作业平台、数据平台、容器管理平台等，均可以将各平台的特性以 API 的形式对接到组件中，便于 PaaS 平台上的 SaaS 调用，整合各个平台的强大功能，发挥最实用的价值。其二，第三方系统，如微信公众号 / 企业号、邮件系统、OA 系统、AD 系统、财务系统等非蓝鲸体系内的运营系统，同样以 API 的形式将特性对接到组件，丰富和完善整个 PaaS 平台企业服务总线的服务。从而使 PaaS 平台之上的 SaaS 可以调度一些，连接一切。

“API 网关” 仅限于 “管理员” 角色操作，从 “开发者中心”—>“API 网关” 进入使用。

![](../../assets/image010.png)

![](../../assets/image009.png)

“API 网关” 给出了详细的使用文档，分为以下几个部分：

(1) 简介：概述 API 网关，API 网关的两种接入教程：编码方式（采用 Python 语法）和自助接入方式

(2) 系统管理：API 来自于哪个系统，可以看成是 API 的分类

(3) 通道管理：API 访问的路径管理

(4) 自助接入：目前仅支持 http 请求形式的自助接入

(5) 使用指南：详细的 API 网关的使用教程，如接入教程、自定义配置信息调整、CMSI 消息通知如何配置，以及如何为新加入的组件生产 / 更新 “组件文档”

(6) API 文档：查询蓝鲸官方的和自定义接入组件的使用文档

> 注：[蓝鲸组件在线 API 文档](5.1/API文档/BK_LOGIN/README.md)。


## MagicBox


[MagicBox](http://magicbox.bk.tencent.com/)（链接：http://magicbox.bk.tencent.com/ ），又称为前端魔盒。是一个前端资源 PaaS 平台，为蓝鲸应用开发者提供丰富的前端资源，包括常用的 UI 组件、JS 插件及基础模版，开发者可以通过蓝鲸 MagicBox 快速构建页面。它还提供完整的套餐样例供开发者选择，开发者也可以在线拖拽组件组装页面，让前端布局可视化。

![](../../assets/image011.png)

## 开发培训


蓝鲸为开发者提供了详细的线上 [视频教程](https://cloud.tencent.com/developer/edu/major-100008)。

![](../../assets/image013.png)

提供了长期有效的 [早起鸟儿有虫吃](https://bk.tencent.com/s-mart/community/question/440) 学习活动，参与有礼。

## 开发交流

为了提供即时有效的技术沟通，组建了 “运维开发群” QQ：878501914
