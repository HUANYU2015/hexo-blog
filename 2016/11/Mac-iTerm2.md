---
title: Mac 系统下的终端方案：iTerm2+Zsh+oh my Zsh+tmux 使用说明
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
- 如果你不是后台开发者，一般不需要用到这个东西，可以不用学的。如果你要学，那你可以认为你在接触 Unix 系统的一些思想，做好这个准备，对你很重要。

## 先总结

- 比默认的 Terminal 终端好用，配合 Zsh 确实很便捷
- 如果不是开发者，一般人就不用折腾这个，一般来讲是浪费时间

## iTerm2 知识

### iTerm2 是什么

- 术语定义
    - iTerm2 官网：<http://iterm2.com/>
    - WIKI：<https://en.wikipedia.org/wiki/ITerm2>
    - 我的理解：Mac 的默认终端 Terminal 太难用了，我们开发一个新的终端来代替它吧。
- 同类常见技术
    - `Terminal`
- 学习前提/依赖
    - 一点英文
    - 一点 Unix/Linux 系统的思想
    - 一点 shell 概念

### 为什么会出现

- 有些操作，命令行或者说脚本的方式效率是远高于 GUI 界面操作的，这个概念需要用过 Unix/Linux 做过开发的人会懂，特别是搞运维的。如果你不理解，可以找一些运维的视频教程来看看，会有很多事情的处理都是搞脚本的做的。所以终端、shell 对于开发人员一直是存在的，没有消失过，以后也会一直存在，只要它的效率一直高于 GUI 就没有理由消失。

### 哪些人不喜欢它

- 设计师？
- 前端开发者？可能真正的好前端开发者也是会很好地用终端的，因为 node.js 的 npm 就有很多命令。node.js 到底要算前端还是后端？╮（╯＿╰）╭
- 不喜欢学习的，因为这里面涉及到很多 Unix/Linux 系统的知识点，很枯燥，而且很多快捷键需要背，需要花很多精力。


### 为什么学习它

- 作为后端开发者必须学会的一个技能，不管是为了简化安装一些软件或是处理一些事情，还有工作中的后端程序的软件部署，都会跟终端/shell 打交道。

### 我要怎么做

- 在安装之前先说下前提，你的 Mac 必须装有：Homebrew，如果你不知道这是做什么，可以查看我写的另外一篇文章：
- 下载
    - 当前时间（2016-10-31）最新版为：3.0.10
    - 官网：<https://iterm2.com/>
- 安装 iTerm 2
    - 官网下载下来是一个 zip 压缩包，解压出来有一个 `.app` 文件，双击运行即可安装。
    - 其他安装方式不说
- 安装 Zsh
    - 默认的 shell 是 bash，一般人都觉得不好用，一般人也都喜欢 Zsh，所以这里就用 Zsh。
    - 为了简化安装、配置 Zsh，我们这里选择 oh-my-Zsh 这个插件。
    - 在终端，先安装 wget 工具：`brew install wget`
    - 如果你没安装 git，先安装 git：`brew install git`
    - 在终端，安装 Zsh：`brew install Zsh`
    - 在终端，安装 oh-my-Zsh：`sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-Zsh/master/tools/install.sh -O -)"`
        - 下载完后，会提示你输入当前用户密码，输入就会从 bash 切换到 Zsh，如果你没有输入密码直接跳过了，可以运行：`chsh -s /bin/Zsh 你当前系统用户名`
        - 切换完成之后，关掉终端，重新打开
    
- 软件特色
- 智能选中
    - 在 iTerm2 中，双击选中，三击选中整行，四击智能选中（智能规则可配置），可以识别网址，引号引起的字符串，邮箱地址等。（很多时候双击的选中就已经很智能了）
在 iTerm2 中，选中即复制。即任何选中状态的字符串都被放到了系统剪切板中。


### Proxychains4

- Mac 下的 Homebrew 默认源在境外，有时候速度非常慢，国内源有时候也不好用，所以就想着直接穿越了，反正我那边有一个 vps 服务器。
- 安装：`brew install proxychains-ng`
- 修改配置文件：`vim /usr/local/etc/proxychains.conf`
    - 在配置文件中找到：`[ProxyList]`，在其下面一行新增一条：`socks5  127.0.0.1 1080 # my vps`
- 测试：`proxychains4 curl google.com`，如果显示的命令行信息中，前缀都带有：`[proxychains]`，则表示成功了。以后只要在命令前面加个：proxychains4，即可。
- 修改终端配置，让命令更加简洁：
    - 如果你是 zsh 终端，配置修改：`vim ~/.zshrc`，添加一行：`alias pc='proxychains4'`
    - 如果你是 bash 终端，配置修改：`vim ~/.bash_profile`，添加一行：`alias pc='proxychains4'`
    - 修改之后，以后要用 proxychains4 执行命令的话，那就可以这样写：`pc curl google.com`
    
    
## Zsh 知识

### Zsh 是什么

- 术语定义
    - iTerm2 官网：<http://iterm2.com/>
    - WIKI：<https://en.wikipedia.org/wiki/ITerm2>
    - 我的理解：Mac 的默认终端 Terminal 太难用了，我们开发一个新的终端来代替它吧。
- 同类常见技术
    - `Terminal`
- 学习前提/依赖
    - 一点英文
    - 一点 Unix/Linux 系统的思想
    - 一点 shell 概念


### 为什么学习它

- 作为后端开发者必须学会的一个技能，不管是为了简化安装一些软件或是处理一些事情，还有工作中的后端程序的软件部署，都会跟终端/shell 打交道。

### 我要怎么做

- 在安装之前先说下前提，你的 Mac 必须装有：Homebrew，如果你不知道这是做什么，可以查看我写的另外一篇文章：
- 下载
    - 当前时间（2016-10-31）最新版为：3.0.10
    - 官网：<https://iterm2.com/>
- 安装 iTerm 2
    - 官网下载下来是一个 zip 压缩包，解压出来有一个 `.app` 文件，双击运行即可安装。
    - 其他安装方式不说
- 安装 Zsh
    - 默认的 shell 是 bash，一般人都觉得不好用，一般人也都喜欢 Zsh，所以这里就用 Zsh。
    - 为了简化安装、配置 Zsh，我们这里选择 oh-my-Zsh 这个插件。
    - 在终端，先安装 wget 工具：`brew install wget`
    - 如果你没安装 git，先安装 git：`brew install git`
    - 在终端，安装 Zsh：`brew install Zsh`
    - 在终端，安装 oh-my-Zsh：`sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-Zsh/master/tools/install.sh -O -)"`
        - 下载完后，会提示你输入当前用户密码，输入就会从 bash 切换到 Zsh，如果你没有输入密码直接跳过了，可以运行：`chsh -s /bin/Zsh 你当前系统用户名`
        - 切换完成之后，关掉终端，重新打开






## 资料整理

- 来自 Google 过程中的资料（真心感谢这些作者）：
    - <http://wiki.jikexueyuan.com/project/mac-dev-setup/iterm.html>
    - <http://wulfric.me/2015/08/iterm2/>
    - <http://yanghui.name/blog/2015/07/19/make-all-command-through-proxy/>
    - <>
    - <>
    - <>
    - <>
    - <>
    - <>
    - <>


     
## 结束语

- 如果你需要它就你就好好学习，如果你的职业现在完全用不到，那就把这篇文章加收藏，有需要再打开，不希望你花时间多做一些没有太大意义的事情。
