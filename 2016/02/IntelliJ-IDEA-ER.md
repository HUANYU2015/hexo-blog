---
title: 为什么不尝试下 IntelliJ IDEA？我想劝说你
date: 2016-03-11 17:53:17
description: "以我的个人角度来看待学习这件长久的事，希望对你有帮助，也希望你能提一下你的意见"
categories: [学习方法,Java]
tags: [学习方法,Maven,Java]
---


<!-- more -->


![IntelliJ IDEA](http://img.youmeek.com/2016/IntelliJ-IDEA-ER.jpg)


## 本文对象

- Eclipse、MyEclipse、NetBeans、Vim、Sublime Text 重度患者


## 本文目标

- 本篇不讲 IntelliJ IDEA 技巧类的具体东西，关于技巧这类东西我已经系统整理过了，你可以去这里看：<https://github.com/judasn/IntelliJ-IDEA-Tutorial>
- 写这篇文章主要目的是想给你留下一个印象，关于一个沉浸式的 IDE。
- 学习过程的核心思想：**IntelliJ IDEA 跟 Eclipse 或是其他 IDE 完全不一样，所以放下过去的思维。**
- 懂 Maven 和 Gradle 学习它会更快，因为它本身就是模块化的。


## 过去有感

- 在我记忆中，**所有的大学 Java IDE 只有一个：Eclipse**，所以我也是这样过来的。
- 我知道做 Java 开发的你们 Eclipse 用得很习惯，可能要怪大学老师。也知道 MyEclipse 能解决做 Java 开发的常见问题。所以我理解你们还在坚持它们的原因，就像几年前刚到一家公司的时候，我暗地里认为我的 MyEclipse 会是如何如何地好，了解的插件是如何如何多。你们那个 IntelliJ IDEA 界面丑、默认字体丑、占用内存又高，我是排斥的。
- 可是为了融入圈子我只能自己去适应周边的人，我开始逼着自己去了解 IntelliJ IDEA。后来，我专门为它配置了一台 i7、SSD、16G 的机子来伺候它。


## IntelliJ IDEA 特色

- 下面我说几个它特殊的地方，跟 Eclipse / Myeclipse 有重叠或是类似的我这里你就不说了，这些细节在你学习的过程中你自己会发现、对比。
- 我是这样形容 IntelliJ IDEA 的：沉浸式 IDE。
- 鲜明特色：
    - **特点一**：
        - 下面一些语言的支持需要额外装官网提供的插件，具体可以到插件库里找
        - **支持的语言/平台**：
            - `Java、JavaScript、TypeScript 、CoffeeScript、Node.js、AngularJS、React、JRuby、ActionScript、SASS、LESS、HTML、CSS`
            - `Bash、Markdown、Kotlin、PHP、Python、Ruby、Scala、Clojure、Groovy、Android、PhoneGap、Cordova、Ionic`
        - **支持的框架**：
            - `Spring、Spring Boot、Spring MVC、Hibernate、Struts、Mybatis、Flex、JSF、Play`
            - `Web Services、Grails、GWT、Vaadin、Guice、FreeMarker、Velocity、Thymeleaf`
        - **支持的构建工具**：`Maven、Gradle、SBT、Grunt、Bower`
        - **支持的应用容器**：`Tomcat、TomEE、WebLogin、JBoss、Jetty、WebSphere`
        - **支持的版本工具**：`Git、SVN、CVS、Mercurial、Perforce, ClearCase、TFS`
        - **额外支持**：
            - `自带反编译、可以在反编译的类中 Debug、如果是开源框架会自动帮你下载源码`
            - `终端、数据库 GUI（Oracle、SQL Server、PostgreSQL、MySQL），REST Client`
    - **特点二**：
        - 它有美妙的快捷键，以及任何地方都支持自定义快捷键，是一个完全可以离开鼠标的 IDE，撒谎的人是小狗。
    - **特点三**：
        - 无限制、无条件地搜索。IntelliJ IDEA 是有索引的概念，也因为有索引的原因，我们对整个项目进行全文检索是非常非常非常快的，但是也是这个索引，所以当它首次启动某个项目的时候都需要先扫描一下这个项目的所有文件来创建成它的索引，所以，IntelliJ IDEA 首次启动某个项目花的时间会比较多、而且卡。但是我认为这是值得的，后面有无数次的开发我们可以加倍返还。
    - **特点四**：
        - 高效的导航。IntelliJ IDEA 除了各种搜索无敌，还有各种导航。
        - 你任何时候都可以快速到某个类的父类、子类、接口、测试类、引用地，可以快速到某个变量、方法、文件、包。
- 沉浸式的原因是：IntelliJ IDEA 一站解决基本上市场上常见的开发所需。
- 也许你第一眼看到上面的关键字会认为我在说梦话，而我也搞不懂 JetBrains 那些人

     
## 结束语

- IntelliJ IDEA 功能多，耗内存，后端开发内存最好 8 G 以上，前端开发 4 G 以上。
- Android 的开发人员是比较有权力说 Eclipse 和 IntelliJ IDEA 的差异的，希望 IntelliJ IDEA 家的产品没有托你后退。
