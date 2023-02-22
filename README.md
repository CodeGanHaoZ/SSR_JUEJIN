# 一、项目介绍

做个简单的自我介绍吧。

### 核心信息概括

基于Nuxt框架，使用Strapi作为CMS的仿掘金站点。

### 项目服务地址（本地）

> 仿掘金站点地址：http://localhost:3000/
>
> CMS操作地址：http://localhost:1337/admin

### Github  地址

https://github.com/CodeGanHaoZ/SSR_JUEJIN

> 仿掘金站点：branch-ghw 、CMS：branch-thy

# 二、项目分工

众人拾柴火焰高

| **团队成员**        | **主要贡献**                                                 |
| ------------------- | ------------------------------------------------------------ |
| @甘皓玮             | 仓库初始化、开发基于NuxtJs的前端页面（首页和详情页）         |
| @田贺元             | 开发CMS数据库，使用Strapi配置数据，编写接口文档、E2E 端到端测试。 |
| @陆冰玲-13281769436 | 汇报文档编写。                                               |
| 李滨                | **无法取得联系**                                             |

# 三、项目实现

合抱之木，生于毫末；九层之台，起于累土；千里之行，始于足下。

### 3.1 技术选型与相关开发文档

#### 3.1.1 需求说明

- 需求背景：随着广大技术人员有技术交流需求日益增多，需要一个平台作为他们交流分享的载体。
- 相关人员：

产品：甘皓玮、田贺元、陆冰玲

前端：甘皓玮

后端：田贺元

测试：田贺元

CMS测试时间：2023.02.19

联调时间：2023.02.21

展示时间：2023.02.22

#### 3.1.2技术选型

-  前端技术选型

仿掘金站点是典型的C端项目，为了实现更好的SEO（搜索引擎优化）和首屏渲染体验，使用SSR开发模式。

本项目主要采用`Vue3 + Nuxt3 + TypeScript +Vite`。`Nuxt3` 是基于 `Vite`、`Vue3` 和 `Nitro` 的 `Nuxt` 框架的重构，具有一流的 `TypeScript` 支持，其基于强大的模块化架构，默认优化应用程序。在团队成员对于Vue框架熟悉的基础上，可以更快上手NuxtJs。

-  后端技术选型

我们需要为 “运营” 同学提供一个 CMS 的平台来帮助它们进行配置。页面中所有的内容预期都是可配的，包括标签，文章，广告等，不能直接代码写死文案。配置需有 GUI 页面，符合非技术人员习惯。

综上，本项目决定使用`Strapi`。`Strapi`是一款灵活的、开放源码的CMS，适合搭配`Nuxt3`搭建一般的内容展示网站。它能够提供对数据库的管理服务，并且它支持多种类型的数据库，并在此基础上封装，抹平了各种数据库在使用上的差异，方便非技术人员使用。使用`Strapi`，我们完全可以不用过多费心在后端接口开发上，只需注重数据库结构设计以及前端开发即可，并且运营人员可以很快的上手。

### 3.2 架构设计

#### 3.2.1 概要设计

- 按层级

![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=N2EyNzZiN2E2ZjAwNjIyZTZkMTI0N2VhNDM0M2JhODVfd2pYNmg2MEZHS2F2Z1hxN3dqSUh0MUtHeXVkSGpoVE9fVG9rZW46Ym94Y25BSk9ycWhBZkJaejN2bTdKQmw0cUxjXzE2NzcwMzA3ODM6MTY3NzAzNDM4M19WNA)

- 按照系统模块和处理流程

![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=ZmQ2MjBkMTQzYjkwNTAwYjAxNzY0NDk0NmFhZjgyOGRfelNEUFk1Wkh5aW90M2JvUGJhT1hEYlFlMTBPSHhZUHhfVG9rZW46Ym94Y25oanpkaVM3ZnY3M2VjNFFqUEVzZmdkXzE2NzcwMzA3ODM6MTY3NzAzNDM4M19WNA)

#### 3.2.2 详细设计

- 开发约定
  - CMS：内容管理系统。
  - Strapi：一种灵活的、开放源码的CMS。
  - 接口文档使用Showdoc书写
  - 代码协作使用github
- 功能实现
  - 接口设计

- [接口文档](https://www.showdoc.com.cn/2184396549651010/9799650440505280) （密码：200295）

- - 系统间交互流程

- ![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=ZDFlOTg2MzZhMDRjZDU3NTA1MzM2OWQyMmI3NDYyYWNfT29XbUZDcjRYc3FmQm1rQ3FwZzZZSFUxVlA4ejNqaUVfVG9rZW46Ym94Y25jUWhCWHpFT2hrU3BFWEQ2RVBvQnplXzE2NzcwMzA3ODM6MTY3NzAzNDM4M19WNA)

- - 存储设计

-  存储结构（数据源）：SQLite

- ![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=YTFiYWMxZjQ2OTAzYzEwZjc5YzJiZmJhMDEwZjFiNmZfM1hLd2pZdUlVQ1N6Ym9hMXJBWlZIN0JsUEdzaDFaTTlfVG9rZW46Ym94Y242Q2I5cWNYMkRVbTdvUGVDUjNEVXBkXzE2NzcwMzA3ODM6MTY3NzAzNDM4M19WNA)

- ![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=MTIxNDBlMDg3Yzk0MmJiY2I3YjQzNDFmYmNhNjAzZjdfVVFWZTlnSENkUGtiT214WTlSbFZZNWFLSUthOVd2MHVfVG9rZW46Ym94Y25XcGRIdEU0clBpN1BxczE3WnM4dTVkXzE2NzcwMzA3ODM6MTY3NzAzNDM4M19WNA)

- 可靠性设计
  - 流量预估
  -  假设：3~5年用户数达到1000万注册用户

  -  每日UV（网站独立访客）：200万（二八原则）； 每日每天点击浏览：30次； PV（页面浏览量）：200万 * 30=6000万； 集中访问量：24小时 * 0.2=4.8小时，有6000万 * 0.8=4800万（二八原则，20%时间会有80%的访问量）； 每分并发量：4.8小时*60=288分钟，每分钟访问4800万/288≈16.7万； 每秒并发量：16.7万/60≈2780； 假设：高峰期为平常值的三倍，则每秒的并发数可以达到8340次。 1毫秒=1.3次访问；

  - 容量预估
  -  按一台web服务器（以tomcat服务器举例），支持每秒300个并发计算。平常大约需要10台服务器，高峰期需要30台服务器；系统CPU一般维持在70%左右的水平，高峰期达到90%的水平，是不浪费资源，并比较稳定的。内存，IO类似。

  -  以上预估仅供参考，因为服务器配置，业务逻辑复杂度等都有影响。在此CPU，硬盘，网络等不再进行评估。

### 3.3 项目代码介绍

#### 3.3.1 CMS内容配置模块

运营人员可通过CMS进行配置。包括导航栏、标签栏、文章信息、作者信息、作者榜、广告位等内容。

（数据表[青训营前端结业项目答辩汇报文档](https://lqu7yom0qg.feishu.cn/docx/A3DZdNjaSoLDtwxOGYdca82tnkg#KyeWdkoIio6EY2xSEO0chrXHn3g) ）

![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=OTc2ODNkNjFhZDkzMTk5MzI0YmZmMjdlMDczOWY4ODlfT2cyUnFxQ3pwNTV2ZHhBUndqb1FmWXM3OEdvOUNNaUlfVG9rZW46Ym94Y25kS0owNUFhTlVoUEZ4bmZ2Y3JKV2VoXzE2NzcwMzA3ODM6MTY3NzAzNDM4M19WNA)

![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=NDBlNmM5MDg3ZDQxNzc2YjliYjUyNDc0MDk0MDAzMzBfcWNwSE5BdlVKNndaWmxhUFhka1pKVDVsb1A3UWRzY3lfVG9rZW46Ym94Y25SeWFuMEtDZEp4ellua0tjbWJGNFVoXzE2NzcwMzA3ODM6MTY3NzAzNDM4M19WNA)

# 四、测试结果

墨菲定理：凡事只要有可能出错，那就一定会出错。

> 建议从功能测试和性能测试两部分分析，其中功能测试补充测试用例，性能测试补充性能分析报告、可优化点等内容。

### 4.1功能测试

### 4.2性能测试

# 五、Demo 演示视频

# 六、项目总结与反思

温故而知新，可以为师矣。

#### 6.1 目前仍存在的问题

Strapi作为后台仍有些许局限性。当后期数据表过多，数据关系更加复杂时，Strapi便显得力不从心。

#### 6.2 已识别出的优化项

#### 6.3 架构演进的可能性

本项目仅基于`Nuxt`使用了`SSR`方式渲染项目，虽然提高了访问速度与 SEO ，但由于项目体量小，许多问题仍未显现，仍存在优化的可能性。针对本项目，可以使用混合渲染的模式，需要首屏优化和SEO的页面采用SSR开发模式；基本内容不变的采用SSG开发模式；其他页面可以采用前后端分离的CSR开发模式，减轻服务器压力。

除此之外，随着用户的增多，访问量将成指数增长，使用Severless云原生替代分布式计算服务器是更好的选择。

#### 6.4 项目过程中的反思与总结

# 七、其他补充资料

（密码：200295）

https://www.showdoc.com.cn/2184396549651010/9799650440505280

https://www.nuxtjs.cn/

https://getstrapi.cn/developer-docs/latest/getting-started/introduction.html

https://strapi.io/

https://blog.csdn.net/weixin_41519463/article/details/125396145

[【前端】青训营大项目 - 基于 SSR 开发仿掘金站点](https://bytedance.feishu.cn/docx/SyuZdfdtNoX8wcxAzhfc1mkUnFg) 

# 八、感谢

一个不懂得感恩的民族，是没有希望的民族。
