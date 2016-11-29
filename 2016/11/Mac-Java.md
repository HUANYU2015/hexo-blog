---
title: 一个Java程序员眼中的Mac OS（系列七：J2EE 开发环境）
date: 2016-11-28 22:23:10
description: "如果只是单纯以开发 Java 应用为准星，Mac 其实没啥特别的"
categories: [Mac]
tags: [Mac,终端]
---


<!-- more -->

## 本文初衷

- 整理自己脑袋中、收藏中的那些资料，来一次清空，让自己重新开始。
- 帮助 Mac 后来者，减少他/她入门成本
- 如果你不是后台开发者，一般不需要用到这个东西，可以不用学的。如果你非要学，那你可以认为你现在看到的东西和在 Linux 上看到的没啥本质的区别，做好这个准备，对你很重要。

## 先总结

- 其实 Java 相关的开发环境，不管是 Windows、Mac、Linux 其实本质都一样的，都是改路径，改系统变量，如果还有 IntelliJ IDEA 这种 IDE，有些压根就不需要系统变量了。
- Windows 的路径结构是这样的：`D:\360Downloads\HotFix`
- Mac/Linux 的路径结构是这样的：`/usr/local`
- 没用过 Unix 系统的人会很不爽这种路径结构，其实嘛我觉得是 Windows 那种路径结构不好。
- 系统变量的更改位置，Mac/Linux 一般都是习惯在终端改，Windows 一般在 GUI，但是本质 Windows 也是可以在 cmd 改的，只是 Windows 的终端真的是太差劲了。

## JDK

- 和 Windows 没啥区别，都是下一步下一步
- 不管是 Windows、Mac、Linux，如果是开发环境，JAVA_HOME 我都是 JDK8，同时还装有 JDK6、JDK7，在使用 IntelliJ IDEA 的时候，可以同时使用三个版本的 JDK。
- 下载地址 JDK7：<http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html>
- 下载地址 JDK8：<http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html>

## IntelliJ IDEA

- 最优秀的 IDE，没有之一，我所有的生产力设备都是为了支持它而购买的，所以内存一定要够大。
- 下面的 Maven、Tomcat 都是依赖于 IntelliJ IDEA 运行的，所以本质上我只要搞定 IntelliJ IDEA，其他的环境 IntelliJ IDEA 都会帮我解决。
- 官网下载：<http://www.jetbrains.com/idea/>
- 关于安装/配置等相关，请看我写的这个系列：[IntelliJ IDEA 简体中文专题教程](https://github.com/judasn/IntelliJ-IDEA-Tutorial)

## Maven

- 安装方式和 Windows、Linux 没啥本质区别，我是直接把 Windows 的 settings.xml 复制过来，修改下本地仓库的路径，其他没变。
- 本地仓库是直接从 Windows 下拷贝过来的，这个是任何系统下都兼容的。
- 然后再用 IntelliJ IDEA 对 Maven 的配置路径重新做了修改。

## Tomcat

- 因为是开发环境，所以不需要配置 CATALINA_HOME 变量，直接用 IntelliJ IDEA 指向 Tomcat 的解压目录即可，如果不懂，请看我的：[IntelliJ IDEA 简体中文专题教程](https://github.com/judasn/IntelliJ-IDEA-Tutorial)
- 官网下载 Tomcat 7：<http://tomcat.apache.org/download-70.cgi>
- 官网下载 Tomcat 8：<http://tomcat.apache.org/download-80.cgi>

## MySQL

- MySQL 官网有提供 dmg 格式的安装包，下一步下一步安装即可，没必要折腾的编译的安装方式。
- 下载地址 MySQL 5.6：<http://dev.mysql.com/downloads/mysql/5.6.html#downloads>
- 下载地址 MySQL 5.7：<http://dev.mysql.com/downloads/mysql/>

## Git

- 和 Windows 没啥区别，都是下一步下一步
- 官网下载：<http://git-scm.com/download/mac.>


## 结束语

- 感谢 JetBrains 这样的公司存在，让我省去很多麻烦。
