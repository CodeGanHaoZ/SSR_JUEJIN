# 一、项目介绍

做个简单的自我介绍吧。

### 核心信息概括

基于Nuxtjs3框架，使用Strapi作为CMS的仿掘金站点。

一个“静态”的掘金~什么意思呢?大家可以理解成是给掘金做一个宣传性的官网，和掘金类似，但是没有登录、评论等用户交互，只有一些静态的功能，并且在它的基础上加上主题化的效果来提高更多用户的交互体验。虽说是”静态，但是仍然存在接口的设计和 BFF 的处理，我们需要为”运营“同学提供一个 CMS 的平台来帮助它们进行配置。

### 项目服务地址（本地）

> 仿掘金站点地址：http://localhost:3000/
>
> CMS操作地址：http://localhost:1337/admin

### Github  地址

https://github.com/CodeGanHaoZ/SSR_JUEJIN

> 仿掘金站点：branch-ghw 、CMS：branch-thy、汇报文档：branch-lbl

# 二、项目分工

众人拾柴火焰高

| **团队成员**        | **主要贡献**                                                 |
| ------------------- | ------------------------------------------------------------ |
| @甘皓玮             | 仓库初始化、开发基于NuxtJs的前端页面（首页和详情页）         |
| @田贺元             | 开发CMS数据库，使用Strapi配置数据，编写接口文档、E2E 端到端测试。 |
| @陆冰玲-13281769436 | 汇报文档编写。                                               |

**GitHub仓库**

![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=MzhjOGY5NzQ5MmVlOGI2OTM5NTg1NGExNWQxZDRlN2FfNzkyMjNmYk1hajBrZnR3TzFXdVkwSGxwVkVCdWxWeTZfVG9rZW46Ym94Y255R2FzZ1JaYmE3TTl4TnA2dUNuNFNkXzE2NzcxMTQ5ODI6MTY3NzExODU4Ml9WNA)

**多次飞书会议讨论**

![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=OTk4OGU3MTkxYzRhY2UyNjAzOGRlYmM2OWY1ZDZlYWVfRzBJOHpuazRPTXZ0aGdWbHMzSWp2WjNKR1FmbmdhdndfVG9rZW46Ym94Y25sb2ROR3ZFWVI0bEFMbGoxcWVZQVhlXzE2NzcxMTQ5ODI6MTY3NzExODU4Ml9WNA)

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

仿掘金站点是典型的**C端项目**，为了实现更好的**`SEO`**（搜索引擎优化）和**首屏渲染体验**，使用**`SSR`**开发模式。

本项目主要采用`Vue3 + Nuxt3 + TypeScript +Vite`。`Nuxt3` 是基于 `Vite`、`Vue3` 和 `Nitro` 的 `Nuxt` 框架的重构，具有一流的 `TypeScript` 支持，其基于强大的模块化架构，默认优化应用程序。在团队成员对于Vue框架熟悉的基础上，可以更快上手NuxtJs。

-  后端技术选型

我们需要为 “运营” 同学提供一个`CMS`的平台来帮助它们进行配置。页面中所有的内容预期都是可配的，包括标签，文章，广告等，不能直接代码写死文案。配置需有 `GUI` 页面，符合非技术人员习惯。

综上，本项目决定使用`Strapi`。`Strapi`是一款灵活的、开放源码的CMS，适合搭配`Nuxt3`搭建一般的内容展示网站。它能够提供对数据库的管理服务，并且它支持多种类型的数据库，并在此基础上封装，抹平了各种数据库在使用上的差异，方便非技术人员使用。使用`Strapi`，我们完全可以不用过多费心在后端接口开发上，只需注重数据库结构设计以及前端开发即可，并且运营人员可以很快的上手。

### 3.2 架构设计

#### 3.2.1 概要设计

- 按层级

![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=ODBlZDJiNDFmZTA0ZjE4MmQ0MGFiNmRmNzgyZGNkNWNfaWhQT3RhQmRUNmFMZVYyWnNmUGFNaFp1SXNoVUR2cGRfVG9rZW46Ym94Y25BSk9ycWhBZkJaejN2bTdKQmw0cUxjXzE2NzcxMTQ5ODI6MTY3NzExODU4Ml9WNA)

- 按照系统模块和处理流程

![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=MzVmZmEzZTFkODJmYTNmMTM1NzQ0MTVjOTgwZGRmNjVfMWtQOUtLcktQbW5NQnRsclVERzA1a2w1NnVUVjR6eHZfVG9rZW46Ym94Y25oanpkaVM3ZnY3M2VjNFFqUEVzZmdkXzE2NzcxMTQ5ODI6MTY3NzExODU4Ml9WNA)

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

- ![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=MDE2MzMxNmU1ZDJkMmVmZTA2MmU5ZWQ1ZGUzODg0ZmNfWTVhU3Nmd2dBd1JRdTlla0FGUW9EeGdNZ0ZwSVJSQk5fVG9rZW46Ym94Y25jUWhCWHpFT2hrU3BFWEQ2RVBvQnplXzE2NzcxMTQ5ODI6MTY3NzExODU4Ml9WNA)

- - 存储设计

-  存储结构（数据源）：SQLite

- ![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=MzQ2YjUzODY2ZTMyMGVjODM4ZTVkMDc0NTQ5ODdmNjJfbjZON1I3R2x0UlpFWEcwV3dGRzIzWHhlNTBvQk1SOHVfVG9rZW46Ym94Y242Q2I5cWNYMkRVbTdvUGVDUjNEVXBkXzE2NzcxMTQ5ODI6MTY3NzExODU4Ml9WNA)

- ![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=OWU5MjBmY2I4YzIxYjI3OWZiOWIxZTIwNDkxNGM3N2NfVmRPVzd4a2dQU2dPaGpHZnlxM0NPZnhYM3J5UUhjNmtfVG9rZW46Ym94Y25XcGRIdEU0clBpN1BxczE3WnM4dTVkXzE2NzcxMTQ5ODI6MTY3NzExODU4Ml9WNA)

- 可靠性设计
  - 流量预估
  -  假设：3~5年用户数达到1000万注册用户

  -  每日UV（网站独立访客）：200万（二八原则）； 每日每天点击浏览：30次； PV（页面浏览量）：200万 * 30=6000万； 集中访问量：24小时 * 0.2=4.8小时，有6000万 * 0.8=4800万（二八原则，20%时间会有80%的访问量）； 每分并发量：4.8小时*60=288分钟，每分钟访问4800万/288≈16.7万； 每秒并发量：16.7万/60≈2780； 假设：高峰期为平常值的三倍，则每秒的并发数可以达到8340次。 1毫秒=1.3次访问；

  - 容量预估
  -  按一台web服务器（以tomcat服务器举例），支持每秒300个并发计算。平常大约需要10台服务器，高峰期需要30台服务器；系统CPU一般维持在70%左右的水平，高峰期达到90%的水平，是不浪费资源，并比较稳定的。内存，IO类似。

  -  以上预估仅供参考，因为服务器配置，业务逻辑复杂度等都有影响。在此CPU，硬盘，网络等不再进行评估。

### 3.3 项目代码介绍

#### 3.3.1 Nuxtjs项目目录结构和strapi项目目录结构

![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=YTc1OGNhZmM5NzkwZjhmY2JkMjBjYTM4MWYwN2FmZWJfV0dnT2lzT0ViT3B1MU1nVVNkdWZySDlVdk5nTXFuMW9fVG9rZW46Ym94Y253MFRQYkdtcERZZXJGOWJmOFdNSzFkXzE2NzcxMTQ5ODI6MTY3NzExODU4Ml9WNA)

![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=YTMyOGMyOGZiZGM0OWU3Mzk3Zjg0NzhkOGJjYzMyOWVfN3lvaTBFWUNQSzZvWnJ2MnJmS216bFF1RnBEWm10ZGVfVG9rZW46Ym94Y25mMVBCMXNzUkkyN2ZQQ3BUcmJaNDBlXzE2NzcxMTQ5ODI6MTY3NzExODU4Ml9WNA)

#### 3.3.2 代码介绍

页面以组件的形式搭建起来，header、nav、main、aside，以此为思路来设计组件和路由。

![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=YmJjZjgyMWUyYjQzN2FlNmUxMWUwZmZiZjM1OGM2MzdfNHNmeGlsN1RnY1FobFJWVWdoUGF4dVZqRkl4RmZieFBfVG9rZW46Ym94Y25WT2lQUVprY3d6cW1YM1k0ak1ZNm9kXzE2NzcxMTQ5ODI6MTY3NzExODU4Ml9WNA)

组件核心部分

![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=OWU0YjMzODY2YjA2NTU4OThkMjljYWIxMzcxMGI0NWFfQ2xYOUEzek42bmp4VDI4Y0xxWXpmZ1JqamQ0djZydGRfVG9rZW46Ym94Y25hVWFBQ2lkOFRSNjB1M1NLdkpJdHdoXzE2NzcxMTQ5ODI6MTY3NzExODU4Ml9WNA)

header代码部分

![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=Y2YyNDJjNThlZDAwMjFmYmJkMDQ5NTFjZTdhYTVkYjRfSGxTQmNndXlhRGp0dWp0ZnpnNEtGYkJRVFl4a1FUZ3BfVG9rZW46Ym94Y25wT0NSSEVXeGVRUm90QVZFRnlKRVJmXzE2NzcxMTQ5ODI6MTY3NzExODU4Ml9WNA)

nav代码部分

![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=OTI1YTM4Y2YyZTZhNmYzOWZkM2FlMTUwMDI2NzM4OWVfbG5yVXBOeGJKajY0YzU1dUtVTkpaYnFUSWhscTZ5M3pfVG9rZW46Ym94Y25qV3p2cVNYTFZqNE1zWFdSaVZpY0VlXzE2NzcxMTQ5ODI6MTY3NzExODU4Ml9WNA)

main文章列表代码部分

![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=ZDMwMmFjMzNkMTEzMTc2NTkyMDA1YzU4MWQ4NmYwZWZfMVk1VzVlN3V6SmpjUzJIdWFldHpjbWY2ckJVdGxzNjJfVG9rZW46Ym94Y25ZRTZ0WDRXZkhVV1dncjFIRk03em9oXzE2NzcxMTQ5ODI6MTY3NzExODU4Ml9WNA)

aside代码部分

![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=YjgwOGFhZmE2MzJlZmM3MjllOWNhMGNhNWY5OWFiNGRfV0QzY1ZyblpMeGlUalA0UWRVeWVUM01JcXNmMWkwQUxfVG9rZW46Ym94Y251TnhkRkxLRGhBemhIRVhBVXpad05nXzE2NzcxMTQ5ODI6MTY3NzExODU4Ml9WNA)

#### 3.3.3 CMS内容配置模块

运营人员可通过CMS进行配置。包括导航栏、标签栏、文章信息、作者信息、作者榜、广告位等内容。

（数据表[青训营前端结业项目答辩汇报文档](https://lqu7yom0qg.feishu.cn/docx/A3DZdNjaSoLDtwxOGYdca82tnkg#KyeWdkoIio6EY2xSEO0chrXHn3g) ）

![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=MWUwMWMyMmYyYjQ2ZDBiNWM5NjM2ZDM2MGU5M2MyYTBfMGNuN1IzNTBOeFgza054cVUzYzNYT0V3czVHY2tEOFFfVG9rZW46Ym94Y25kS0owNUFhTlVoUEZ4bmZ2Y3JKV2VoXzE2NzcxMTQ5ODI6MTY3NzExODU4Ml9WNA)

![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=ZTI0MGQwOTY1NGIzNWI5ZjE0ZjI1YTBlZjIzOTYwZjRfM2FHS2UwMkVlVUtpckJTZWFtV2Y4ajhJbndpdXE1bFlfVG9rZW46Ym94Y25SeWFuMEtDZEp4ellua0tjbWJGNFVoXzE2NzcxMTQ5ODI6MTY3NzExODU4Ml9WNA)

# 四、测试结果

墨菲定理：凡事只要有可能出错，那就一定会出错。

### 4.1功能测试

以header组件为例，采用`Vue Test Utils`+`Jest`进行组件测试。

Jest 是一个“零配置”的前端测试工具，具有诸如模拟和代码覆盖之类的开箱即用特性，比如 Mock 和代码覆盖率等。它主要用于 React 和其他 JavaScript 框架。  

测试主体最小单元，采用了 Given When Then 的经典格式，我们常常称之为测试三部曲，也可以解释为 3A 即：

| **GWT**   | **3A**  | **说明**                                                     |
| --------- | ------- | ------------------------------------------------------------ |
| **Given** | Arrange | 准备测试测试数据，有时可以抽取到 `beforeEach`                |
| **When**  | Act     | 采取行动，一般来说就是调用相应的模块执行对应的函数或方法     |
| **Then**  | Assert  | 断言，这时需要借助的就是 Matchers 的能力，Jest 还可以扩展自己的 Matcher |

**测试原则：**

- 组件分支渲染逻辑必须测
- 事件调用和参数传递一般要测

**测试思路：**

1. 获取快照对比 （确保 UI 组件不会有意外的改变）
2. 组件渲染（包括分支渲染，**这里面会包含部分参数传递和slot**）
3. 事件调用和剩下的参数传递

```JavaScript
import header from '../components/home/header.vue'
import { createLocalVue, shallowMount } from '@vue/test-utils'
import ElementUI from 'element-ui'
const localVue = createLocalVue()

localVue.use(ElementUI)

describe('test heander component', () => {
    const wrapper = shallowMount(header)
    it('test snapshot', () => {
        expect(wrapperWithSnapshot.html()).toMatchSnapshot()
    })

    it('test rendering', () => {
        const parentDOM = wrapper.findComponent(header)
        const navDOM = parentDOM.find('nav')
        const ulDOM = parentDOM.findComponent('ulDOM')
        expect(parentDOM.exists()).toBe(true)
        expect(navDOM.exists()).toBe(true)
        expect(ulDOM.exists()).toBe(true)
    })
})
```

![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=OWQ4OWE1MTQ2Y2YxYmQ4ZDhiNWIxNGZkODgwNDBjMGZfUENSYnZHZzBmdkxsalJjcDh3M0Q0bDNtUUt0S0dWM0VfVG9rZW46Ym94Y25HbHRTY3lXSHdyeXd2MkwwY1BCVWJlXzE2NzcxMTQ5ODI6MTY3NzExODU4Ml9WNA)

### 4.2性能测试

在edge浏览器上面运行，发现接口报错的问题，但是在谷歌浏览器运行没有报错。

![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=MDkwYjRlNzNiYzBlOTlhMDBhNDVlZTFhOTQwYTc0MDZfOW90cGpjYXBDbFJTRk1veExlRjBJb3JhSVlpUzdMdjRfVG9rZW46Ym94Y25KVThxMU51YzMxbndNNjZ1QlZVT2plXzE2NzcxMTQ5ODI6MTY3NzExODU4Ml9WNA)

# 五、Demo 演示视频

暂时无法在飞书文档外展示此内容

# 六、项目总结与反思

温故而知新，可以为师矣。

#### 6.1 目前仍存在的问题

- 文章详情页未完成。
- ipad端没有完美的适配。
- 首页部分细节以及数据调度未完成。
- nuxtjs框架的使用还不是非常熟练，但是经过这几天学习与开发，已经初步了解掌握了nuxtjs的部分功能以及语法。
- Strapi管理员账后有时无法登录，可能和缓存有关。
- 某些接口耦合度过高，文章详情（ArticleInfo）和文章模块（Articles）接口应该分离。
- Strapi作为后台仍有些许局限性。当后期数据表过多，数据关系更加复杂时，Strapi便显得力不从心。

#### 6.2 已识别出的优化项

- 部分代码冗余，代码维护更新起来可迭代性一般，代码耦合度一般。
- Strapi接口返回数据嵌套关系过多，可使用`strapi-plugin-transformer`进行处理，其原理是将嵌套关系提升一级，消去`attributes`层。

#### 6.3 架构演进的可能性

本项目仅基于`Nuxt`使用了`SSR`方式渲染项目，虽然提高了访问速度与 `SEO` ，但由于项目体量小，许多问题仍未显现，仍存在优化的可能性。针对本项目，可以使用混合渲染的模式，需要首屏优化和`SEO`的页面采用`SSR`开发模式；基本内容不变的采用`SSG`开发模式；其他页面可以采用前后端分离的`CSR`开发模式，减轻服务器压力。

除此之外，随着用户的增多，访问量将成指数增长，使用`Severless`云原生替代分布式计算服务器是更好的选择。

#### 6.4 项目过程中的反思与总结

- 在开发前，没有成型、成体系的开发规范；一份好的文档可以在未来替你向别人回答，我们意识到好的文档真的可以提高沟通效率、开发效率和质量。
- 未使用CI/CD自动化部署，每一次输命令效率真的不高。
- 何为前端程序员？仅了解三大件、框架可能是Vue程序员或React程序员，但绝不是前端程序员。前端程序员还要考虑很多：文档、性能、测试...，第五届青训营，对于我们，最大的意义就是——**保持思考**，越来越多的编程成了：**写一写注解，将从四处拷贝来的代码块，拼在一起，改改名字，就成了一个程序**。 
  -  但实际上编程不应该是这样的，并不是说语言有高低之分，越接近底层的程序员越牛逼，只是，一个拼积木的程序员，我怎么能相信他是一个解决能力的程序员呢？

  -  第五届青训营，是思考的过程。你在慢慢前进的时候，会更理解框架的细节，最后得出一个结论：**程序=算法+数据结构+操作系统+计算机网络原理。**

![img](https://lqu7yom0qg.feishu.cn/space/api/box/stream/download/asynccode/?code=NmViYTU2OTYwZDA3NWRjNjNiN2UxYWU2NDIzMmNhN2JfZlM5UVlHREpkdlpTb2xPZzhWV0w5ZmQxVDJRek50ZGpfVG9rZW46Ym94Y250VGlhbW5IdXFkVnlhb28zcFBheU9kXzE2NzcxMTQ5ODI6MTY3NzExODU4Ml9WNA)

# 七、感谢

一个不懂得感恩的民族，是没有希望的民族。

第五届青训营，是一次挑战，也是一个机会。在这里，不仅收获了前沿知识，也结识了来自五湖四海、志同道合的朋友。

😁感谢可以有这样的平台，在这个物欲纵横的年代，可以沉下心来探究，显得难能可贵。

🥰感谢每一位老师和管理员小姐姐的辛勤付出，也许这就是责任与爱。

😉感谢小组的每一位同学，大家一路的相互鼓励和坚持，我们才能走到终点！

# 八、其他资料

（密码：200295）

https://www.showdoc.com.cn/2184396549651010/9799650440505280

https://www.nuxtjs.cn/

https://getstrapi.cn/developer-docs/latest/getting-started/introduction.html

https://strapi.io/

https://blog.csdn.net/weixin_41519463/article/details/125396145

[【前端】青训营大项目 - 基于 SSR 开发仿掘金站点](https://bytedance.feishu.cn/docx/SyuZdfdtNoX8wcxAzhfc1mkUnFg) 
