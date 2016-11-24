---
title: Mac 系统下的好用包管理器：Homebrew
date: 2016-10-31 22:23:10
description: "据我所知，Mac 系统下目前大家都是用它做包管理"
categories: [Mac]
tags: [Mac,Homebrew,终端]
---


<!-- more -->

## 本文初衷

- ![Maven](http://img.youmeek.com/2016/maven.png)
- 整理自己脑袋中、收藏中的那些资料，来一次清空，让自己重新开始。
- 帮助 Mac 后来者，减少他/她入门成本


## 先总结

- 有 Homebrew 配置，安装/维护一些开发包/组件会方便很多，提供开发者效率，仅此而已。
- 如果不是开发者，一般人就不用折腾这个，一般来讲是浪费时间

## Homebrew 知识

### Homebrew 是什么

- 术语定义
    - Homebrew 官网：<http://brew.sh/index_zh-cn.html>
    - 维基百科定义：<https://weiji.ga/zh-hans/Homebrew>
    - 我的理解：类似 Ubuntu 的 apt-get，CentOS 的 yum。
- 同类常见技术
    - `Fink`
    - `MacPorts`
- 同类技术比较：
    - [Homebrew 和 Fink、MacPort 相比有什么优势？](http://www.zhihu.com/question/19862108)
- 学习前提/依赖
    - 一点英文
    - 一点 Unix/Linux 系统的思想
    - 一点 shell 概念

### 为什么会出现

- 有些操作，命令行或者说脚本的方式效率是远高于 GUI 界面操作的，这个概念需要用过 Unix/Linux 做过开发的人会懂，特别是搞运维的。如果你不理解，可以找一些运维的视频教程来看看，会有很多事情的处理都是搞脚本的做的。所以在维护一些开发包/组件的时候，懂一些包管理工具的话会帮你提高工作效率，仅此而已。

### 哪些人不喜欢它

- 不需要用到终端的用户


### 为什么学习它

- 方便安装开发包/组件，便于管理这些东西

### 我要怎么做

- 安装
    - 先安装 Xcode command line tools（一般系统默认会有，如果没有再装）：`xcode-select --install `
    - 打开终端，复制该命令：`ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
        - 根据提示，按回车键
        - 根据提示，输入当前用户的密码
        - 终端中提示正在下载和安装 Homebrew，这个时间根据你网速的快慢来决定时间，反正我是很慢，还出现了下载速度 0kb 的状况，然后重新运行了一次就成功。
- 测试
    - 打开终端，复制该命令：`brew doctor`
        - 如果输出：`Your system is ready to brew.`，则表示安装成功。
- 卸载
    - 打开终端，复制该命令：`ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/uninstall)"`
    - 删除目录：`sudo rm -rf /usr/local/Homebrew`
- Homebrew 基本使用
    - 安装指定软件包：`brew install 软件包名称`，安装过程的讲解可以看这篇文章：<https://www.zybuluo.com/phper/note/87055>
    - 卸载指定软件包：`brew uninstall 软件包名称`
    - 更新指定软件包：`brew upgrade 软件包名称`
    - 搜索是否存在对应的软件包：`brew search 软件包名称`
    - 查看对应软件包的信息：`brew info 软件包名称`
    - 更新 Homebrew 在服务器端上的包目录：`brew update`
    - 清理旧版本的包缓存时：`brew cleanup`
    - 查看你安装过的包列表：`brew list`
    - 更新 Homebrew 在服务器端上的包目录：`brew update`
    - 查看那些已安装的程序需要更新：`brew outdated`
- 使用国内源
    - 默认的源实在速度有够慢的
    - USTC 的源：<https://lug.ustc.edu.cn/wiki/mirrors/help/brew.git>
        - 方法：
            - `cd "$(brew --repo)"`
            - `git remote set-url origin git://mirrors.ustc.edu.cn/brew.git`



## 资料整理

- 来自 Google 过程中的资料（真心感谢这些作者）：
    - <https://aaaaaashu.gitbooks.io/mac-dev-setup/content/Homebrew/index.html>
    - <http://mac-osx-for-newbie-book.kejyun.com/software/SoftwareManageHomebrew.html>
    - <http://www.cnblogs.com/TankXiao/p/3247113.html>
    - <http://brew.sh/index_zh-cn.html>
    - <https://www.zybuluo.com/phper/note/87055>
    - <http://www.udpwork.com/item/11775.html>
    - <http://www.zhihu.com/question/22624898>
    - <http://wiki.jikexueyuan.com/project/mac-dev-setup/homebrew.html>
    - <http://blog.devtang.com/2014/02/26/the-introduction-of-homebrew-and-brewcask/>


## 过程细节

     
## 结束语

- 如果你需要它就你就好好学习，如果你的职业现在完全用不到，那就把这篇文章加收藏，有需要再打开，不希望你花时间多做一些没有太大意义的事情。
