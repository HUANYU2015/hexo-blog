---
title: 一个Java程序员眼中的Mac OS（系列七：Java 开发环境）
date: 2016-11-30 23:21:40
description: "如果只是单纯以开发 Java 应用为准星，Mac 其实没啥特别的"
categories: [Mac]
tags: [Mac,Java]
---


<!-- more -->

![Java 开发环境](http://img.youmeek.com/2016/Mac-Java.gif)


## 本文初衷

- 整理自己脑袋中、收藏中的那些资料，来一次清空，让自己重新开始。
- 帮助 Mac 后来者，减少他/她入门成本
- 如果你不是 Java 开发者，本章对你没啥太大意义。

## 先总结

- 本篇文章没有细到一步一步截图的地步，需要有 Windows 下 Java 开发经验，以及 Linux 部署 Java 环境为基础。
- 其实 Java 相关的开发环境，不管是 Windows、Mac、Linux 其实本质都一样的，都是改路径，改系统变量，如果你还用 IntelliJ IDEA 这种 IDE，有些压根就不需要系统变量了。
- 各系统的路径差异说明：
	- Windows 的路径结构是这样的：`D:\360Downloads\HotFix`
	- Mac/Linux 的路径结构是这样的：`/usr/local`
	- 没用过 Unix 系统的人会很不爽这种路径结构，其实嘛我觉得是 Windows 那种路径结构不好。
- 系统变量的更改位置，Mac/Linux 一般都是习惯在终端改，Windows 一般在 GUI，但是本质 Windows 也是可以在 cmd 改的，只是 Windows 的终端真的是太差劲了。

## JDK

- 官网下载 JDK7：<http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html>
- 官网下载 JDK8：<http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html>
- Java 开发环境理论上一般都是这个优先安装的。
- 安装过程和 Windows 没啥区别，都是下一步下一步，只是比 Windows 简单，连安装路径都不需要改而已，所以这里不截图了。
- 我这边不管是 Windows、Mac、Linux，只要开发环境，JAVA_HOME 我都是 JDK8，同时还装有 JDK6、JDK7，在使用 IntelliJ IDEA 的时候，我可以同时使用三个版本的 JDK。
- JDK 的环境变量是要添加的，我这边可以贴一下。
- 在本系列前面的章节中我已经说明了，我这边是 Zsh 环境，所以我需要编辑这个配置文件：`vim ~/.zshrc`
- 如果你是 bash，你需要编辑的是这个：`vim ~/.bash_profile`
- 修改后之后刷新配置文件我是：`source ~/.zshrc`

``` bash
# JDK 1.8
JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_112.jdk/Contents/Home
JRE_HOME=$JAVA_HOME/jre
PATH=$PATH:$JAVA_HOME/bin
CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export JAVA_HOME
export JRE_HOME
export PATH
export CLASSPATH
```

## IntelliJ IDEA

- 官网下载：<http://www.jetbrains.com/idea/>
- 最优秀的 IDE，没有之一，我所有的生产力硬件设备都是为了支持它而购买的，所以内存一定要够大。
- 下面的 Maven、Tomcat 都是依赖于 IntelliJ IDEA 运行的，所以本质上我只要搞定 IntelliJ IDEA，其他的 Java 开发环境 IntelliJ IDEA 都会帮我们解决。
- 关于 IntelliJ IDEA Mac 下安装/配置等相关，请看我写的这个系列，里面有详细说明：[IntelliJ IDEA 简体中文专题教程](https://github.com/judasn/IntelliJ-IDEA-Tutorial)
- 在 IntelliJ IDEA 有几个特别的地方我单独拿出来讲讲吧：
	- 如果启动 Tomcat 的时候报：`Permission denied`，你则可以：打开终端，进入 Tomcat\bin 目录，然后执行：`chmod 777 *.sh`
	- 如果启动 Tomcat 之后，控制台乱码了，并且你确认你在 IntelliJ IDEA 的 Preferences 中设置的控制台字体是支持中文的，那你可以尝试下在 Tomcat VM 参数上加上：`-Dfile.encoding=UTF-8`
	- Git 的路径配置：`Preferences -- Version Control -- Git -- Path to Git executable` 的值是：`/usr/local/git/bin/git`
	- 如果你已经看过前面的：[一个Java程序员眼中的Mac OS（系列六：终端方案iTerm2 + Zsh）](http://code.youmeek.com/2016/11/29/2016/11/Mac-iTerm2/)，假设你也已经安装了 zsh
		- 那你的 IntelliJ IDEA 终端路径可以改成 zsh 的，配置方法在 `Preferences -- Tools -- Terminal -- Shell path` 的值改为是：`/bin/zsh`
- IntelliJ IDEA 在 Mac 下的配置文件保存路径
	- 下面内容中：`XXXXXX`，表示 IntelliJ IDEA 的版本号，IntelliJ IDEA 的配置目录是跟版本号有关系的。
	- `/Users/你的用户名/Library/Application Support/IntelliJIdeaXXXXXX`，用于保存安装的插件
	- `/Users/你的用户名/Library/Caches/IntelliJIdeaXXXXXX`，用于保存缓存、日志、以及本地的版本控制信息（local history 这个功能）
	- `/Users/你的用户名/Library/Preferences/IntelliJIdeaXXXXXX`，用于保存你的个人配置、授权文件，等价于 Windows 下的 `config` 目录

## Maven

- 官网下载：<http://maven.apache.org/download.cgi>
- Maven 是绿色版的，任何系统都适用。
- 安装方式和 Windows、Linux 没啥本质区别，都是把 zip 文件夹解压，然后新增几个系统变量，修改 Maven 配置文件参数。
- 如果你不懂 Maven 相关知识可以查看我过去写的这篇文章：[构建工具-Maven-相关知识-整理专题](http://code.youmeek.com/2016/03/09/2016/03/Maven/)
- 我是把 Maven 解压后，直接把 Windows 的 settings.xml 复制过来，修改下该文件本地仓库的路径，其他没啥可以改的了。
- 然后本地仓库的那些依赖包是直接从 Windows 下拷贝过来的，这个是任何系统下都兼容的，不需要额外处理。
- 最后再用 IntelliJ IDEA 对 Maven 的配置路径重新做了修改。
- 以上这些点都需要你对 Maven 和 IntelliJ IDEA 有了解，对于这两个东西我也在本文章都贴了相关的文章链接，我这里不多说了，学习总是需要花时间的。
- Maven 的环境变量是要添加的，我这边可以贴一下：

``` bash
MAVEN_HOME=/Users/youmeek/my_software/work_software/maven3.3.9
PATH=$PATH:$MAVEN_HOME/bin
export MAVEN_HOME
export PATH
```

## Tomcat

- 官网下载 Tomcat 7：<http://tomcat.apache.org/download-70.cgi>
- 官网下载 Tomcat 8：<http://tomcat.apache.org/download-80.cgi>
- Tomcat 在 Windows 下虽然有安装版本，但是一般开发环境我们都不会下载安装版本的，所以假设你也是下载 zip 的压缩版本，这个版本任何系统都是通用的。
- 因为是开发环境，所以不需要配置 CATALINA_HOME 变量，直接用 IntelliJ IDEA 指向 Tomcat 的解压目录即可，如果不懂，还是看我本文上面贴的 IntelliJ IDEA 系列教程地址。

## MySQL

- 官网下载 MySQL 5.6：<http://dev.mysql.com/downloads/mysql/5.6.html#downloads>
- 官网下载 MySQL 5.7：<http://dev.mysql.com/downloads/mysql/>
- MySQL 官网提供的 Mac 系统的安装包，是下一步下一步安装类型的，没啥难度，大家自己试一下。
- 有几个点需要注意的是：
	- 如何重置 root 密码：
		- 打开：`系统偏好设置 -- 底部的 MySQL -- 点击：Stop MySQL Server`，根据提示输入你的 Mac 用户密码。
		- 打开终端，输入命令：`sudo /usr/local/mysql/bin/mysqld_safe --skip-grant-tables`，根据提示输入你的 Mac 用户密码，然后这个终端就这样放着，别动
		- 再打开一个新的终端，输入命令：`sudo /usr/local/mysql/bin/mysql -u root`，根据提示输入你的 Mac 用户密码，密码如果无误的话，此时就进入：`mysql >` 这种状态下。
		- 在：`mysql >` 这种状态下输入命令：`UPDATE user SET authentication_string=PASSWORD('123456') WHERE User='root';FLUSH PRIVILEGES;`，我把密码重置为：`123456` 了。
	- MySQL 配置文件设置
		- Mac 下的 MySQL 默认是没有 my.ini 或是 my.cnf 文件的，需要我们自己复制一个出来。
		- 通过终端进入这个目录：`cd /usr/local/mysql/support-files/`，从该目录下随便找一个 `.cnf` 的文件，复制命名为：`my.cnf`，然后按照 MySQL 的配置规则配置这个文件。
		- 然后把这个 `my.cnf` 的文件复制到 `/etc` 目录下
		- 重启 MySQL 服务即可

## Git

- 官网下载：<http://git-scm.com/download/mac>
- 安装过程和 Windows 没啥区别，都是下一步下一步。
- IntelliJ IDEA 对 Git 的支持很好，也不需要额外配置什么，IntelliJ IDEA 的 Git 操作都很便捷强烈使用 IntelliJ IDEA 作为 Git 的 GUI 操作工具。

## 结束语

- 感谢 JetBrains 这样的公司存在，让我省去很多麻烦。
- ![YouMeek 公众号](http://img.youmeek.com/YouMeek-WX.jpg)