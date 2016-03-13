---
title: 持续集成工具推荐--TeamCity
date: 2016-03-13 20:50:51
description: "做 Java 开发绕不过去的一个问题：是否引入持续集成？"
categories: [TeamCity,Java]
tags: [TeamCity,Maven,Java,持续集成]
---


<!-- more -->


- ![TeamCity](http://img.youmeek.com/2016/TeamCity.jpg)


## 本文初衷

- 让大家了解持续集成（CI），以及入门了解 JetBrains 家的 TeamCity 的一些简单实用。
- TeamCity 的一些复杂使用我暂时也不会，一样也是要看文档的，所以不管怎样你都要养成看官网文档的习惯。
- TeamCity 和 Jenkins、Hudson 其实是非常一样的，基本流程都是差不多的，所以如果你会其他的几个 CI 工具的话，学习起来很快。
- Docker 已经开始在引入到 CI、CD（持续交付）过程中，可以大大简化整体的过程，也许这是未来的一个方向，有兴趣的可以了解更多。


## 它是什么

- 官网定义（就一句话）：`Powerful Continuous Integration out of the box`
- 官网首页：<https://www.jetbrains.com/teamcity/>
- 官网特性总结：<https://www.jetbrains.com/teamcity/features/>
- 百度百科：<http://baike.baidu.com/view/3703414.htm>
- 官网文档：<https://confluence.jetbrains.com/display/TCD9/TeamCity+Documentation>
- 支持的平台、环境如下图（看不懂也没关系，只要知道它最友好的是 Java 开发即可）：
- ![TeamCity](http://img.youmeek.com/2016/TeamCity-Supported-Platforms-and-Environments.png)
- 对上图的具体讲解可以看（**很重要**）：<https://confluence.jetbrains.com/display/TCD9/Supported+Platforms+and+Environments>

## 为什么会出现

- TeamCity 的出现需要了解这个概念：持续集成（Continuous Integration）
- 百科定义：<http://baike.baidu.com/view/5253255.htm>
- 网络文章：<http://www.ruanyifeng.com/blog/2015/09/continuous-integration.html>


## 哪些人喜欢它

- [持续集成学习笔记－入门篇（1）持续集成基本概念](http://blog.csdn.net/leijiantian/article/details/7916483)
- [7 reasons why you should be using Continuous Integration](https://about.gitlab.com/2015/02/03/7-reasons-why-you-should-be-using-ci/)
- [What is CI and why use it?](https://blog.rainforestqa.com/2014-07-17-what-is-CI-and-why-use-it/)


## 哪些人不喜欢它

- Google 不到结果，应该是没人不喜欢，只是有些人用不惯


## 为什么学习它

- 更好地保证项目质量


## 同类工具

- Jenkins：<http://jenkins-ci.org/>
- Travis CI：<http://travis-ci.org/>
- Bamboo：<http://www.atlassian.com/software/bamboo>
- Hudson：<http://hudson-ci.org/>
- QuickBuild：<http://www.pmease.com/>
- 其他：<http://www.oschina.net/project/tag/344/ci?lang=0&os=0&sort=view&p=1>
- 好的网络文章介绍：
    - [持续集成工具的选择](http://cristal.iteye.com/blog/482658)


## TeamCity 入门

- 先来看一段官网的介绍视频
- 这个视频其实已经很清楚地说明了一个整理流程是怎样的，我今天只是做一个更加清晰的细节讲解而已
- 你需要穿越：<https://www.youtube.com/watch?v=J-iYMMG6jmc#action=share>


### TeamCity 安装部署（Linux 环境）

- 在我讲之前，如果你英文还可以，就到官网这里看下：
- [Installation Quick Start](https://confluence.jetbrains.com/display/TCD9/Installation+Quick+Start#InstallationQuickStart-onLinuxandOSX)
- 安装环境要求：
    - JDK 1.7 以上，如果你要使用的是 2016 最新的 TeamCity 9.1 的话，JDK 官网推荐的 1.8
- 安装包下载：<https://www.jetbrains.com/teamcity/download/#section=linux-version>
- 开始安装（eg：TeamCity-9.1.6.tar.gz）：
    - 解压压缩包（解压速度有点慢）：`tar zxf TeamCity-9.1.6.tar.gz`
    - 解压完的目录结构讲解：<https://confluence.jetbrains.com/display/TCD9/TeamCity+Home+Directory>
    - 下载的 tar.gz 的本质是已经里面捆绑了一个 Tomcat，所以如果你会 Tomcat 的话，有些东西你可以自己改的。
    - 按我个人习惯，把解压缩的目录放在 usr 目录下：`mv TeamCity/ /usr/program/`
    - 进入解压目录：`cd /usr/program/TeamCity/`
    - 启动程序：`bin/runAll.sh start`
    - 停止程序：`bin/runAll.sh stop`
    - 启动需要点时间，最好能给它一两分钟吧
    




### 首次进入

- 假设我们已经启动了 TeamCity
- 访问（TeamCity 默认端口是：8111）：<http://192.168.1.113:8111/>
- 如果访问不了，请先关闭防火墙：`service iptables stop`
- 你也可以选择把端口加入白名单中：
    - `sudo iptables -I INPUT -p tcp -m tcp --dport 8111 -j ACCEPT`
    - `sudo /etc/rc.d/init.d/iptables save`
    - `sudo service iptables restart`
- 如果你要改变端口，找到下面这个 8111 位置：`vim /usr/program/TeamCity/conf/server.xml`

``` bash
<Connector port="8111" ...
```

- 在假设你已经可以访问的情况，我们开始进入 TeamCity 的设置向导：
- ![TeamCity 向导](http://img.youmeek.com/2016/TeamCity-guide-a-1.jpg)
    - 如上图英文所示，TeamCity 的一些软件安装的配置、服务的配置默认都会放在：`/root/.BuildServer`
    - 如果你要了解更多 TeamCity Data Directory 目录，你可以看：<https://confluence.jetbrains.com/display/TCD9/TeamCity+Data+Directory>
- ![TeamCity 向导](http://img.youmeek.com/2016/TeamCity-guide-a-2.jpg)
    - 如上图英文所示，TeamCity 的一些构建历史、用户信息、构建结果等这类数据是需要放在关系型数据库上的，而默认它给我们内置了一个。
    - 如果你要了解更多 TeamCity External Database，你可以看：<https://confluence.jetbrains.com/display/TCD9/Setting+up+an+External+Database>
    - 首次使用，官网是建议使用默认的：`Internal(HSQLDB)`，这样我们无需在一开始使用的就考虑数据库迁移或安装的问题，我们只要好好感受 TeamCity 给我们的，等我们决定要使用了，后续再更换数据也是可以的。但是内置的有一个注意点：'TeamCity with the native MSSQL external database driver is not compatible with Oracle Java 6 Update 29, due to a bug in Java itself. You can use earlier or later versions of Oracle Java.'
    - 假设我们就选 `Internal(HSQLDB)` ，则在创建初始化数据库的过程稍微需要点时间，我这边是几分钟。
- ![TeamCity 向导](http://img.youmeek.com/2016/TeamCity-guide-a-3.jpg)
    - 如上图所示，接受下协议
- ![TeamCity 向导](http://img.youmeek.com/2016/TeamCity-guide-b-1.jpg)
    - 如上图所示，我们要创建一个顶级管理员账号，我个人习惯测试的账号是：`admin`，`123456`
- ![TeamCity 向导](http://img.youmeek.com/2016/TeamCity-guide-b-2.jpg)
    - 如上图所示，安装完首次进来地址：<http://192.168.1.113:8111/profile.html?tab=userGeneralSettings>
    - 我们可以完善一些管理员信息和基础配置信息，这些配置不配置都无所谓了，只是完善了可以更加好用而已
    - 如果你有 SMTP 的邮箱，你可以来这里开启邮件通知功能：<http://192.168.1.113:8111/admin/admin.html?item=email>
    - 如果你要开启通知功能那肯定下一步就是考虑通知内容的模板要如何设定：<https://confluence.jetbrains.com/display/TCD9//Customizing+Notifications>
    - 模板存放路径在：`/root/.BuildServer/config/_notifications`，用的是 FreeMarker 的语法


### 创建需要构建的项目






项目管理地址：
http://192.168.1.113:8111/admin/admin.html?item=projects  

一个这样的项目，分下面几个模块：
- Youshop-Parent，输出pom
    - Youshop-manage，输出pom
        - Youshop-pojo，输出jar


现在让我们来创建项目：
http://192.168.1.113:8111/overview.html

正常我们这里一般选择的都是：Create project from URL
因为我们一般都是要配合版本控制系统使用的，公司内部一般也都是用版本控制的的。

我这里使用远程的项目来做测试，你也可以使用服务器本机的或是公司局域网的，TeamCity 也支持 SVN，
所以现在主流的 Git、SVN，TeamCity 都是可以很好的支持的。

如上图，即使是远程的，只要你服务器能连上外网，TeamCity 一样可以支持的。

TeamCity 自动识别到我这个项目中有 POM 文件，所以认定我可以使用 Maven 进行构建。

我们这里勾选上 Maven 选项，然后下一步 TeamCity 就自动帮我们生成一个针对 Maven 的构建步骤，如果你对此不满意或是有内容想修改可以点击箭头上的 Edit。
建议你还是要 Edit 一下的，因为有些信息还是需要改下的。
TeamCity 会自动识别你的 JAVA_HOME 和 M2_HOME
只要这些都有了，构建项目的时候它会自动去读这些系统变量的，当然你也可以选择高级设置，自己在指定的下拉框来选择对应的版本。
这里这里比较悲催的是：Maven 在 TeamCity 9.1 中最高支持的是：3.2.5，而我使用的是 3.3.9，所以我需要重新下载 3.2.5：<http://archive.apache.org/dist/maven/maven-3/3.2.5/binaries/>

https://confluence.jetbrains.com/display/TCD9/Configure+and+Run+Your+First+Build  
现在我们要创建一个项目：
项目支持 Git 、SVN等
链接有要求：https://confluence.jetbrains.com/display/TCD9/Guess+Settings+from+Repository+URL#GuessSettingsfromRepositoryURL-VCSURLFormat

创建好之后，配置好build方式，
开始第一次build：<https://confluence.jetbrains.com/display/TCD9/Configure+and+Run+Your+First+Build> 
对 Build 的一些要求可以看文章上面官网的对环境要求的链接。


TeamCity 默认对 Maven 项目的 Goals是：clean test，这两个单词其实是 Maven 的相关命令，如果你对 Maven 的命令不熟悉可以看我这篇文章：

如果你已经懂了 Maven 的命令之后，我们这里就好办了，我们希望 TeamCity 帮我们做什么，你可以就写在这里，让它来帮我们做，一般我们都喜欢：clean install

Maven 相关的配置解释
https://confluence.jetbrains.com/display/TCD9/Maven

Gradle 相关的配置解释
https://confluence.jetbrains.com/display/TCD9/Gradle




















### 配置自动构建触发行为



构建事件的触发机制讲解：
https://confluence.jetbrains.com/display/TCD9/Configuring+Build+Triggers


TeamCity 采用的 Cron 语法是 Quartz，具体你可以看：
- [Quartz CronTrigger Tutorial](http://www.quartz-scheduler.org/documentation/quartz-1.x/tutorials/crontrigger#CronTriggersTutorial-Specialcharacters)


TeamCity 的插件列表：
https://confluence.jetbrains.com/display/TW/TeamCity+Plugins










集成到IntelliJ IDEA
https://confluence.jetbrains.com/display/TCD9/IntelliJ+Platform+Plugin


使用外部数据库：
使用外部数据库：https://confluence.jetbrains.com/display/TCD9/Setting+up+an+External+Database
迁移到外部数据库：https://confluence.jetbrains.com/display/TCD9/Migrating+to+an+External+Database 

数据备份：
https://confluence.jetbrains.com/display/TCD9/TeamCity+Data+Backup

代码检查功能：
https://confluence.jetbrains.com/display/TCD9/Code+Quality+Tools
https://confluence.jetbrains.com/display/TCD9/Code+Quality+Tools#CodeQualityTools-IntelliJIDEA-poweredCodeAnalysisTools  
https://confluence.jetbrains.com/pages/viewpage.action?pageId=74847276
