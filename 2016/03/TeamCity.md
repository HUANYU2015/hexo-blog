---
title: 我的学习、归纳方法（以学习 Maven 为例）
date: 2016-03-07 20:50:25
description: "以我的个人角度来看待学习这件长久的事，希望对你有帮助，也希望你能提一下你的意见"
categories: [学习方法,Java]
tags: [学习方法,Maven,Java]
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
- 官网特性总结：<https://www.jetbrains.com/teamcity/features/>
- 百度百科：<http://baike.baidu.com/view/3703414.htm>
- 官网文档：<https://confluence.jetbrains.com/display/TCD9/TeamCity+Documentation>
- 支持的平台、环境如下图（看不懂也没关系，只要知道它最友好的是 Java 开发即可）：
- ![TeamCity](http://img.youmeek.com/2016/TeamCity-Supported-Platforms-and-Environments.png)



- 官网的介绍视频
- 这个视频其实已经很清楚地说明了一个整理流程是怎样的，我今天只是做一个更加清晰的细节讲解而已
需要穿越：<https://www.youtube.com/watch?v=J-iYMMG6jmc#action=share>


## 为什么会出现

- TeamCity 的出现需要了解这个概念：持续集成（Continuous Integration）
- 百科定义：<http://baike.baidu.com/view/5253255.htm>
- 网络文章：<http://www.ruanyifeng.com/blog/2015/09/continuous-integration.html>


## 哪些人喜欢它

- [持续集成学习笔记－入门篇（1）持续集成基本概念](http://blog.csdn.net/leijiantian/article/details/7916483)
- [7 reasons why you should be using Continuous Integration](https://about.gitlab.com/2015/02/03/7-reasons-why-you-should-be-using-ci/)
- [What is CI and why use it?](https://blog.rainforestqa.com/2014-07-17-what-is-CI-and-why-use-it/)


## 哪些人不喜欢它

- Google 搜索不到结果


## 为什么学习它

- 更好地包括团队项目质量


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


### TeamCity 部署（Linux 环境）


### 首次进入


### 创建需要构建的项目

### 创建需要构建的项目


构建事件的触发机制讲解：
https://confluence.jetbrains.com/display/TCD9/Configuring+Build+Triggers



TeamCity 的插件列表：
https://confluence.jetbrains.com/display/TW/TeamCity+Plugins


对系统环境的要求：
https://confluence.jetbrains.com/display/TCD9/Supported+Platforms+and+Environments
https://confluence.jetbrains.com/display/TCD9/Supported+Platforms+and+Environments

这里有一张TeamCity的体系统图，可以一眼看出一个情况出来
https://confluence.jetbrains.com/display/TCD9/TeamCity+Documentation

maven相关的配置
https://confluence.jetbrains.com/display/TCD9/Maven



https://confluence.jetbrains.com/display/TCD9/Installation+Quick+Start#InstallationQuickStart-onLinuxandOSX  
TeamCity安装和启用
Make sure you have JRE or JDK installed. Oracle Java 1.7 JDK, and since TeamCity 9.1 JDK 1.8, is recommended. 
tar zxf TeamCity<version number>.tar.gz

mv TeamCity/ /usr/program/

cd /usr/program/TeamCity/

启动：bin/runAll.sh start

<TeamCity home>/bin

启动：runAll.sh start
停止：runAll.sh stop
启动需要点时间，最好能给它一两分钟吧，然后在：
访问：http://192.168.1.113:8111/

项目管理地址：
http://192.168.1.113:8111/admin/admin.html?item=projects  

一个这样的项目，分下面几个模块：
- Youshop-Parent，输出pom
    - Youshop-manage，输出pom
        - Youshop-pojo，输出jar



如果访问不了，请先：service iptables stop
应该是防火墙的问题，如果确实是，可以把端口加入白名单中：



如果要改变端口：<TeamCity Home>/conf/server.xml，改这段：
<Connector port="8111" ...

如果你下载的是war包的方式，推荐的容器是： Apache Tomcat 7
但是，官网推荐下载.tar.gz，里面捆绑了一个Tomcat

解压完一个目录结构讲解：
https://confluence.jetbrains.com/display/TCD9/TeamCity+Home+Directory
简单地讲就是TeamCity的一些软件安装的配置，服务的配置都会放在这里。我这里用默认给我生成：`/root/.BuildServer`，它应该是知道我是 root 用户登录的。



TeamCity Data Directory的目录讲解可以看：
https://confluence.jetbrains.com/display/TCD9/TeamCity+Data+Directory

External Database 的讲解可以看这里：
https://confluence.jetbrains.com/display/TCD9/Setting+up+an+External+Database
简单地讲就是：TeamCity 的一些构建历史、用户信息、构建结果等这类数据是需要放在关系型数据库上的，


首次使用需要选择一个DB软件来存储以后他带来的数据。
首次的话建议用：Internal，也就是默认的，这样我们无需在一开始使用的就需要考虑数据库迁移或安装的问题，我们只要好好感受 TeamCity 给我们的，等我们决定要使用了，后续再更换数据也是可以的。
但是内置的有一个注意点：
TeamCity with the native MSSQL external database driver is not compatible with Oracle Java 6 Update 29, due to a bug in Java itself. You can use earlier or later versions of Oracle Java.
创建初始化数据库的过程稍微需要点时间，几分钟。

安装完首次进来地址：
http://192.168.1.113:8111/profile.html?tab=userGeneralSettings
进行完善个人资料，当然你不完善也行

如果你有SMTP的邮箱，你可以来这里开启邮件通知功能：
http://192.168.1.113:8111/admin/admin.html?item=email

如果你要开启通知功能那肯定下一步就是考虑通知内容的模板要如何设定：
https://confluence.jetbrains.com/display/TCD9//Customizing+Notifications

模板存放路径在： <TeamCity data directory>/config/_notifications/，用的是 FreeMarker 的语法

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
开始第一次build：https://confluence.jetbrains.com/display/TCD9/Configure+and+Run+Your+First+Build 
支持的Build：
Ant 1.6-1.9 (TeamCity comes bundled with Ant 1.8.4, since TeamCity 9.1 - with Ant 1.9.6.)
Maven versions 2.0.x, 2.x, 3.x (known at the moment of the TeamCity release). Java 1.5 and higher is supported. TeamCity comes bundled with Maven 2.2.1, 3.0.5, 3.1, 3.2.3 and since TeamCity 9.0.4 Maven 3.3.1.
IntelliJ IDEA Project runner (requires Java 1.6+)
Gradle (requires Gradle 0.9-rc-1 or higher)
Java Inspections and Java Duplicates based on IntelliJ IDEA (requires Java 1.6+)

TeamCity 默认对 Maven 项目的 Goals是：clean test，这两个单词其实是 Maven 的相关命令，如果你对 Maven 的命令不熟悉可以看我这篇文章：

如果你已经懂了 Maven 的命令之后，我们这里就好办了，我们希望 TeamCity 帮我们做什么，你可以就写在这里，让它来帮我们做，一般我们都喜欢：clean install

如果你的对你的 pom 设置：<packaging>war</packaging>，那 install 出来的 war 包会在：
/usr/program/TeamCity/buildAgent/work/1a60958e5e8b4664/target/youshop.war
/root/.m2/repository/com/youmeek/youshop/youshop/0.0.1-SNAPSHOT/youshop-0.0.1-SNAPSHOT.war


支持的测试框架：
JUnit 3.8.1+, 4.x
NUnit 2.2.10, 2.4.x, 2.5.x, 2.6.x (dedicated build runner); since TeamCity 9.1 NUnit 3.0.x is supported.
TestNG 5.3+
MSTest 8.x, 9.x, 10.x, 11.x, 12.x.; since TeamCity 9.1 MSTest 2015 (14.0) is also supported. The dedicated build runner; requires appropriate Microsoft Visual Studio edition installed on the build agent. Since TeamCity 9.1 the MSTest runner is merged into the Visual Studio Tests runner.
Visual Studio Tests runner, available since TeamCity 9.1, integrates MSTest runner and VSTest console runner formerly provided as an external plugin;  requires the appropriate Microsoft Visual Studio edition installed on the build agent.
MSpec (requires MSpec installed on the build agent)

版本控制要求：
Subversion (server versions 1.4-1.7 and higher as long as the protocol is backward compatible). Check Subversion 1.8 compatibility with different TeamCity versions.
Perforce (requires a Perforce client installed on the TeamCity server). Check compatibility issues.
Git (requires a Git client installed on the TeamCity server).
Mercurial (requires the Mercurial "hg" client v1.5.2+ installed on the server)
Team Foundation Server 2005, 2008, 2010, 2012, 2013. Since TeamCity 9.1, TFS 2015 is supported as well. Requires Team Explorer installed on the TeamCity server (which should run under Windows).
CVS
IBM Rational ClearCase, Base and UCM modes (requires the ClearCase client installed and configured on the TeamCity server)
SourceGear Vault 6 and 7 (requires the Vault command line client libraries installed on the TeamCity server)
Microsoft Visual SourceSafe 6 and 2005 (requires a SourceSafe client installed on the TeamCity server, available only on Windows platforms)
Borland StarTeam 6 and up (the StarTeam client application must be installed on the TeamCity server)

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
