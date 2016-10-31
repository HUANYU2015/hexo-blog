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

- 构建工具是 Java Web 开发者绕不过去的一道坎

### 我要怎么做

- 安装
    - 打开终端，复制该命令：`ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
        - 根据提示，按回车键
        - 根据提示，输入当前用户的密码
        - 终端中提示正在下载和安装 Homebrew，这个时间根据你网速的快慢来决定时间，反正我是很慢，还出现了下载速度 0kb 的状况，然后重新运行了一次就成功。
    
- 配置

紧接着，我们需要做一件事让通过 Homebrew 安装的程序的启动链接 (在 /usr/local/bin中）可以直接运行，无需将完整路径写出。通过以下命令将 /usr/local/bin 添加至 $PATH 环境变量中:

echo 'export PATH="/usr/local/bin:$PATH"' >> ~/.bash_profile

Cmd+T 打开一个新的 terminal 标签页，运行以下命令，确保 brew 运行正常。
$ brew doctor
如果输出：`Your system is ready to brew.`，则表示安装成功。

- 卸载
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/uninstall)"
sudo rm -rf /usr/local/Homebrew


- Homebrew 基本使用

安装一个包，可以简单的运行：
$ brew install <package_name>

更新 Homebrew 在服务器端上的包目录：
$ brew update

查看你的包是否需要更新：
$ brew outdated

更新包：
$ brew upgrade <package_name>

Homebrew 将会把老版本的包缓存下来，以便当你想回滚至旧版本时使用。但这是比较少使用的情况，当你想清理旧版本的包缓存时，可以运行：
$ brew cleanup

查看你安装过的包列表（包括版本号）：
$ brew list --versions

搜尋套件
$ brew search 套件名稱


套件資訊
$ brew info 套件名稱



卸载更方便了
brew uninstall 套件名稱

- 使用国内源
- 默认的源实在速度有够慢的

cd /usr/local/Homebrew && git remote set-url origin https://git.coding.net/homebrew/homebrew.git
cd $home && brew update

如何检验了?


### 资料整理

- 来自 Google 过程中的资料（真心感谢这些作者）：
    - <https://aaaaaashu.gitbooks.io/mac-dev-setup/content/Homebrew/index.html>
    - <http://mac-osx-for-newbie-book.kejyun.com/software/SoftwareManageHomebrew.html>
    - <http://www.cnblogs.com/TankXiao/p/3247113.html>
    - <>
    - <>
    - <>
    - <>


## 过程细节

- 过去 2014 年里，基本上关于 Maven 的知识都是在 Google 上搜索出来的。
- 在 2015 年才看到极客学院上面有成套资料
     
     
## 结束语

- Maven 也许开始要过时了，但是即使 Gradle 的时代要到来了，你会害怕吗？我想你不会的，因为你会学习知识的方法，更而且他们还差不多。
