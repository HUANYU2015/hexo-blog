---
title: Maven-入门知识-系统整理
date: 2016-03-09 19:56:08
description: "如果你是学习 Java 或是说 JVM 语言相关的内容的话，在实际使用中有一个东西你是绕不过去的，构建工具。等你到企业还有一个东西你也绕不过去，持续集成。"
categories: [Java]
tags: [Maven,Java,CI]
---------------------


<!-- more -->

## 本文初衷

- 整理自己脑袋中、收藏中的那些资料，来一次清空，让自己重新开始。
- 整理这篇的起点是本人已经会使用 Maven，并且已经使用了一年多，所以我个人觉得这篇文章对完全不懂 Maven 来讲是有压力的，但是对于刚刚入门 Maven 的人是有帮助的。
- 以此篇为引，希望可以得到你的建议，我只想成长，真心感谢!（鞠躬）


## Maven 知识


## 先总结

- 如果你是学习 Java 或是说 JVM 语言相关的内容的话，在实际使用中有一个东西你是绕不过去的，构建工具。等你到企业还有一个东西你也绕不过去，持续集成。
- 在说持续集成前，先简单地解释两个概念：集群、分布式
    - 应用集群：同样的一套程序/代码，放在一批服务器上，每台服务器上的代码一样。
    - 应用分布式：不同的组件代码，放在一批服务器上，不同的服务器放不同模块的代码。
- 在大公司，现在的项目基本都是分布式的，而要做到分布式那就得尽可能地分层、分割、分布。也因为这样，一个项目一般都是由不同模块组合成的。公司里在不同的地区或是部门做不同的模块，尽量减少部门与部门、地区与地区模块的耦合度，也就是降低必要的联系，让他们尽可能的能独立开发、测试。
    - 这样的拆分，对一个项目的好处是：
        - 分布式架构：具有高性能、高可用、可伸缩、可扩展等优点
        - 公司成本会降低，类似阿里的去 IOE
        - 效率会提高
        - 容错能力更强
        - 灵活性更高
    - 举一个两者简单的对比例子
        - 应用分布式
            - 一个采用分布式架构的电商，在做抢购的特殊时候，压力特别的大的部分应该是：购物车、订单、库存、日志等这些跟购物有关的模块，那既然这几个模块压力大，那我们就在抢购前多部署几套跟购物业务相关的模块到服务器上，此时要求这类服务器性能只要能承载对应的模块即可。其他比如：资讯、客服等无压力模块就原样部署即可，无需变动。
        - 应用集群
            - 一个采用应用集群架构的电商，在做抢购的特殊时候，为了抗住压力，必须把整个应用一套一套地部署到新服务器上，此时就要求服务器性能要好，能承载整个应用。
        - 对比总结：降低成本
        - 扩展内容
            - 在未来容器虚拟化（以 Docker 为主）的情况下，模块化的组件更容易部署到这些容器上面，也就很容易发生这样的事情：一台服务器部署非常多模块，成本就会降得更低。
- 我们已经知道了分布式效益更好，我们也知道分布式的系统都是需要拆分的，对项目进行拆分，把一个大项目拆分成很多小模块项目，然后大家彼此依赖或通信。此时问题来了：如何高效地依赖。
- 高效地依赖解决办法是：自动化的构建 + 持续集成。
    - 在目前 Java 界，最常用的构建工具就是：Maven
    - 在多模块的项目中，还是以一个电商项目为例，购物车模块肯定是会依赖 core 模块、Parent 模块等，而这些模块的开发者在不同城市或是不同部门。在协同开发中，不可能每次他们一有更新就得专门安排一个人来交付依赖，这种方式效率是非常低的。
    - 今天整理这个 Maven 材料其实是为了后面整理持续集成做的准备的，大家必须有这个基础才能说后面的持续集成，后续的持续集成会涉及到：TeamCity、Jenkins、Hudson

### Maven 是什么

- 术语定义
    - Maven 官网：<http://maven.apache.org/>
    - Maven 官网对自己的定义：<http://maven.apache.org/what-is-maven.html>
    - 百度百科定义：<http://baike.baidu.com/view/336103.htm>
    - 维基百科定义：<https://zh.wikipedia.org/wiki/Apache_Maven>
        - 在 Wiki 上还需要注意如下，这些有助于你站在更加宏观的角度看待它，但是可能需要积累：
            - `参见`
            - `补充阅读`
            - `参考资料`
            - `外部链接`
- 它的历史
    - Google 搜索：`Maven History`
        - 搜索结果：
            - 历史介绍：<http://maven.apache.org/background/history-of-maven.html>
            - 创始人：**jason van zyl**
            - 创始人现在在：<http://takari.io/>
    - Google 搜索：`Maven 区别`、`Maven difference`
        - 搜索结果：
            - 人们在关注：
            - gradle maven区别
            - ant maven区别
            - ivy maven区别
            - maven maven2区别
                - 通过这个搜索结果我们知道，现阶段我们要的是 Maven 3：
                - <http://www.infoq.com/cn/news/2011/07/xxb-maven-10-time-to-update>
                - <http://tech.it168.com/a2010/1108/1123/000001123274_all.shtml>
                - <http://www.infoq.com/cn/news/2011/07/xxb-maven-10-time-to-update>
- 同类常见技术（按技术出现时间正序）
    - `Ant`
    - `Gradle`
- 同类技术比较：
    - Google 搜索：`Ant Maven Gradle`
        - 搜索结果：
            - 三者对比：<http://blog.csdn.net/napolunyishi/article/details/39345995>
- 学习前提/依赖
    - 要有 Java 基础相关（如果你完全没学过 Java，建议跳过，不适合你）
    - 最好有 Java Web 相关知识
    - 不需要会 Ant 或是 Maven 早期版本的内容

### 为什么会出现

- Google 搜索：（这些一般都是一些故事，你自己来判断，别人的坎坷是你成长的基石）
    - 关键字：`为什么用 maven`
    - 关键字：`why use maven`
    - 关键字：`What does Maven do`
    - 关键字：`Why do we need Maven`
    - 关键字：`Why should we use Maven`

### 哪些人不喜欢它

- Google 搜索：（这些一般都是一些故事，你自己来判断，别人的坎坷是你成长的基石）
    - 关键字：`不用 maven`
    - 关键字：`Why I Don't Use Maven`


### 为什么学习它

- 构建工具 是 Java Web 开发者绕不过去的一道坎

### 我要怎么做（按优先级从高到低排序）

- 看教程
    - 官网快速入门文档
        - 在官网中查看带有下面几个关键字的链接：
            - `Getting Started`
            - `Quick Start`
            - `Getting Started Guides`
            - `usage page`
            - `Tutorials`
            - `Guides`
            - `Development Guides`
            - `Documentation`
            - `Docs`
            - `Screencasts`
            - Maven 主页上得到字眼有：
                - `documentation index`，地址：<http://maven.apache.org/guides/index.html>
                - 在子页面我们得到：
                    - `Getting Started in 5 Minutes`，地址：<http://maven.apache.org/guides/getting-started/maven-in-five-minutes.html>
                    - `Getting Started in 30 Minutes`，地址：<http://maven.apache.org/guides/getting-started/index.html>
    - 在极客学院搜索对应的教学视频（我是年 VIP）
        - 极客学院对 Maven 的讲解比较到位，从初级到中级都涵盖（需要 VIP 权限）：
        - Maven 概述及安装，包含下面内容：
            - `Maven 概述及安装`
            - `在 Mac 电脑上安装及配置 Maven`
            - `在 Windows 电脑上安装及配置 Maven`
            - `在 Linux 电脑上安装及配置 Maven`
            - 地址：<http://www.jikexueyuan.com/course/571.html>
        - Maven 核心概念讲解，包含下面内容：
            - `POM概述`
            - `插件与目标`
            - `项目的生命周期阶段`
            - 地址：<http://www.jikexueyuan.com/course/866.html>
        - 在工具中使用 Maven，包含下面内容：
            - `使用命令行工具构建一个 Maven 项目`
            - `使用 Eclipse 构建一个 Maven 项目`
            - `使用 IntelliJIDEA 构建一个 Maven 项目`
            - 地址：<http://www.jikexueyuan.com/course/580_1.html?ss=1>
        - 使用 Maven 构建 Web 项目，包含下面内容：
            - `创建一个Web项目`
            - `使用 Tomcat 插件运行 Web 项目`
            - `使用 Jetty 插件运行 Web 项目`
            - `添加 J2EE 依赖`
            - `创建 JSP 和 Servlet`
            - `在 Eclipse 中使用 Maven 构建 Web 项目`
            - 地址：<http://www.jikexueyuan.com/course/908.html>
            - 地址：<http://www.jikexueyuan.com/course/951.html>
         - 使用 Maven 构建多模块项目（本篇作者：感觉是不是要开始来到分布式的世界了？！）
            - `多模块项目介绍`
            - `创建 helloweb 项目的骨架结构`
            - `将 helloweb 项目导入 Eclipse`（本篇作者：后续我会讲解一篇基于 IntelliJ IDEA 的 Maven 多模块，科科，我的 IntelliJ IDEA 可不是盖的。）
            - `使用 dependencyManagement 管理依赖`
            - `使用 pluginManagement 管理插件`
            - `定义项目属性及配置信息`
            - `完善 helloweb-entity 模块`
            - `完善 helloweb-core 模块`
            - `完善 helloweb-web 模块`
            - `使用 log4j 打印日志`
            - `使用 junit 进行单元测试`
            - `使用 guava 美化代码`
            - 地址：<http://www.jikexueyuan.com/course/957.html>
            - 地址：<http://www.jikexueyuan.com/course/964.html>
            - 地址：<http://www.jikexueyuan.com/course/977.html>
            - 地址：<http://www.jikexueyuan.com/course/989.html>
    - 极客学院上整理得很好的文字教程：<http://wiki.jikexueyuan.com/project/maven/>
    - 国外著名的教程网：<http://www.tutorialspoint.com/maven/index.htm>
    - Google 搜索：`Maven 视频 教程 百度云网盘`    
    - Google 搜索：`Maven 视频 教程`
    - 简书-搜索相关内容：<http://www.jianshu.com/>
    - 知乎-搜索相关内容：<http://www.zhihu.com/>
    - Quora-搜索相关内容：<https://www.quora.com/>
    - 微博-搜索相关内容：<http://weibo.com>
    - 公众号-搜索相关内容：<http://weixin.sogou.com/>
    - 开发者头条-搜索相关内容：<http://toutiao.io/>
    - 京东-图书：<http://book.jd.com/>
    - YouTube-搜索相关内容：<http://youtube.com/>
    - 参考的资料：
        - <http://my.oschina.net/MyHeaven1987/blog/99781>
        - <http://my.oschina.net/MyHeaven1987/blog/100704?fromerr=SWanTA4V>
        - <>
        - <>
        - <>
        - <>
        - <http://www.cnblogs.com/haippy/archive/2012/07/04/2576453.html>
        - <>
        - <>
        - <>
        - <>
        - <>
        - <>
- 自己写 Demo
    - Maven 下载地址：<http://maven.apache.org/download.cgi>
    - 最新版本为：**Apache Maven 3.3.9**
    - JDK 要求：Maven 3.3 要求 JDK 1.7 或是更新 
    - 操作系统没要求：`No minimum requirement. Start up scripts are included as shell scripts and Windows batch files`
        - 但是，按系统常见压缩格式，我个人建议：
        - Windows 下载的文件：**apache-maven-版本号-bin.zip**
        - 类 Unix 下载的文件：**apache-maven-版本号-bin.tar.gz**
- 参考别人 Demo
    - 通过上面的学习，我们知道，我们要学习别人的 Maven 配置，只要能看懂他们的 POM 文件配置即可，所以现在你需要做的是找一些开源项目，读懂他们的 POM
    - Gtihub 搜索 Demo：<https://github.com/search/advanced>
    - Git@OSC 搜索 Demo：<http://git.oschina.net/>
- 项目场景模拟、提高
    - 我现在所有的 Java 相关的项目都是 Maven 构建的
    - 自己做持续集成的话，有 Nexus 做私有仓库
    - 平时开发连接的是：**开源中国 Maven 库**：
        - 使用技巧：
        - <http://maven.oschina.net/help.html>
        - <http://my.oschina.net/huangyong/blog/180189>
    - POM 依赖 jar 常去的查找地：
        - 官网：<http://search.maven.org/>
        - 开源中国：<http://maven.oschina.net/home.html>
        - Nexus 库：<https://repository.sonatype.org/>
        - MVNRepository：<http://mvnrepository.com/>
- 遇到问题
    - 找官网 FAQ：<https://maven.apache.org/general.html>
    - Google
    - Stack Overflow：<http://stackoverflow.com/>


### 归纳整理并分享

- 整理
    - 为知笔记里面内容
    - 浏览器书签
    - 简书中收藏：<http://www.jianshu.com/bookmarks>
    - 简书中喜欢：<http://www.jianshu.com/favourites>
    - 开发者头条中收藏：<http://toutiao.io/favorites>
    - 微博中收藏：<http://weibo.com/fav>
    - RSS 订阅：<http://www.inoreader.com/>
        - 无法订阅的博客使用 Feed43 生成 RSS：<http://feed43.com/>
- 分享
    - 写博客
    - 分享到开发者头条
    - 分享到简书
    - 分享到微信公众号
    - 系统整理 Demo 在 Github 上


## 过程细节

- Google 搜索必备：
    - `Maven site:www.youmeek.com`，表示搜索结果局限于在：www.youmeek.com 这个站点
    - `Maven link:www.youmeek.com`，返回所有链接到 www.youmeek.com 的网页
    - `related:www.qq.com`，查找类似 www.youmeek.com 的网站
    - `cache:www.youmeek.com`，查找 www.youmeek.com 的历史快照
     
     
## 结束语

- 我猜测你可能需要 VPN 或是 Shadowsocks