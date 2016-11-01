---
title: Mac-iTerm2 使用说明
date: 2016-10-31 22:23:10
description: "很多人说它是 Mac 下最好的终端，试试也无妨。"
categories: [Mac]
tags: [Mac,终端]
---


<!-- more -->

## 本文初衷

- ![Maven](http://img.youmeek.com/2016/maven.png)
- 整理自己脑袋中、收藏中的那些资料，来一次清空，让自己重新开始。
- 帮助 Mac 后来者，减少他/她入门成本


## 先总结

- 比默认的终端好用，配合 zsh 确实很便捷
- 如果不是开发者，一般人就不用折腾这个，一般来讲是浪费时间

## iTerm2 知识

### iTerm2 是什么

- 术语定义
    - iTerm2 官网：<http://maven.apache.org/>
    - Maven 官网对自己的定义：<http://maven.apache.org/what-is-maven.html>
    - 百度百科定义：<http://baike.baidu.com/view/336103.htm>
    - 维基百科定义：<https://zh.wikipedia.org/wiki/Apache_Maven>
- 它的历史
    - Google 搜索：`Maven History`
        - 搜索结果：
            - 历史介绍：<http://maven.apache.org/background/history-of-maven.html>
            - 创始人：**jason van zyl**
            - 创始人现在：<http://takari.io/>
    - Google 搜索：`Maven 区别`、`Maven difference`
        - 搜索结果：
            - 人们在关注：
            - gradle maven区别
            - ant maven区别
            - ivy maven区别
            - maven maven2区别
                - 通过这个搜索结果我们知道，现阶段我们要的是 Maven 3：
                - [Maven实战（十）——Maven 3，是时候升级了](http://www.infoq.com/cn/news/2011/07/xxb-maven-10-time-to-update)
                - [六年等一回 Maven 3的10大新特性详解](http://tech.it168.com/a2010/1108/1123/000001123274_all.shtml)
- 同类常见技术（按技术出现时间正序）
    - `terminal`
    - `tmux`
- 同类技术比较：
    - Google 搜索：`Ant Maven Gradle`
        - 搜索结果：
            - [Java构建工具：Ant vs Maven vs Gradle](http://blog.csdn.net/napolunyishi/article/details/39345995)
            - [Maven和Gradle对比](http://www.cnblogs.com/huang0925/p/5209563.html)
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

- Mac 下的 Homebrew 默认源在境外，有时候速度非常慢，国内源有时候也不好用，所以就想着直接穿越了，反正我那边有一个 vps 服务器。

### 我要怎么做

- 安装：`brew install proxychains-ng`
- 修改配置文件：`vim /usr/local/etc/proxychains.conf`
    - 在配置文件中找到：`[ProxyList]`，在其下面一行新增一条：`socks5  127.0.0.1 1080 # my vps`
- 测试：`proxychains4 curl google.com`，如果显示的命令行信息中，前缀都带有：`[proxychains]`，则表示成功了。以后只要在命令前面加个：proxychains4，即可。
- 修改终端配置，让命令更加简洁：
    - 如果你是 zsh 终端，配置修改：`vim ~/.zshrc`，添加一行：`alias pc='proxychains4'`
    - 如果你是 bash 终端，配置修改：`vim ~/.bash_profile`，添加一行：`alias pc='proxychains4'`
    - 修改之后，以后要用 proxychains4 执行命令的话，那就可以这样写：`pc curl google.com`


### 资料整理

- 来自 Google 过程中的资料（真心感谢这些作者）：
    - <http://yanghui.name/blog/2015/07/19/make-all-command-through-proxy/>
    - <>
    - <>
    - <>


## 过程细节

- 过去 2014 年里，基本上关于 Maven 的知识都是在 Google 上搜索出来的。
- 在 2015 年才看到极客学院上面有成套资料
     
     
## 结束语

- Maven 也许开始要过时了，但是即使 Gradle 的时代要到来了，你会害怕吗？我想你不会的，因为你会学习知识的方法，更而且他们还差不多。
