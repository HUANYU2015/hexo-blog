---
title: 一个Java程序员眼中的Mac OS（系列六：终端方案iTerm2 + Zsh）
date: 2016-11-29 22:23:10
description: "大家都说 iTerm2 是 Mac 下最好的终端，试试也无妨"
categories: [Mac]
tags: [Mac,终端]
---


<!-- more -->

## 本文初衷

- 整理自己脑袋中、收藏中的那些资料，来一次清空，让自己重新开始。
- 帮助 Mac 后来者，减少他/她入门成本
- 如果你不是后台开发者，一般不需要用到这个东西，可以不用学的。如果你非要学，那你可以认为你现在看到的东西和在 Linux 上看到的没啥本质的区别，做好这个准备，对你很重要。

## 先总结

- iTerm2 比 Mac 默认的 Terminal 终端好用，配合 Zsh 确实更加得体
- **牢记：** 装了 zsh 之后，修改终端配置就变成了：`vim ~/.zshrc`，而不是：`vim ~/.bash_profile`，所以以后看到别人的文章中需要：`vim ~/.bash_profile`，那你自己要变通思想过来。
- 同时更新修改后的配置文件也从：`source ~/.bash_profile`，变成了：`source ~/.zshrc`，当然还有其他取取巧方式，这里不谈。

## iTerm2 知识

### iTerm2 是什么

- 术语定义
    - iTerm2 官网：<http://iterm2.com/>
    - wiki 介绍：<https://en.wikipedia.org/wiki/ITerm2>
    - iTerm2 作者意思：Mac 的默认终端 Terminal 太难用了，我们开发一个新的终端来代替它吧。
- 同类常见技术
    - `Terminal`
- 学习前提/依赖
    - 一点英文
    - 一点 Unix/Linux 系统的思想
    - 一点 Shell 概念

### 为什么会出现

- 有些操作，命令行或者说脚本的方式效率是远高于 GUI 界面操作的，这个概念需要用过 Unix/Linux 做过开发的人会懂，特别是搞运维的。如果你不理解，可以找一些运维的视频教程来看看，会有很多事情的处理都是搞脚本的做的。

### 哪些人不喜欢 iTerm2

- 设计师？
- 前端开发者？可能真正的好前端开发者也是会经常用终端的，因为 node.js 的 npm 就有很多命令。
- 不喜欢学习的，因为这里面涉及到很多 Unix/Linux 系统的知识点，很枯燥，而且很多快捷键需要背，需要花很多精力。


### 为什么学习 iTerm2

- 作为后端开发者必须学会的一个技能，不管是为了简化安装一些软件或是处理一些事情，还有工作中的后端程序的软件部署，都会跟 shell 打交道。

### 安装 iTerm2

- 在安装之前先说下前提，你的 Mac 必须装有：Homebrew，等下 zsh 要用到。
	- 如果你不知道 Homebrew 是做什么，可以查看我写的另外一篇文章：[一个Java程序员眼中的Mac OS（系列五：包管理工具）](http://code.youmeek.com/2016/11/27/2016/11/Mac-Homebrew/)
- 下载 iTerm 2
    - 当前时间（2016-10-31）最新版为：3.0.10
    - 下载地址，官网：<https://iterm2.com/>
- 安装 iTerm 2
    - 官网下载下来是一个 zip 压缩包，解压出来有一个 `.app` 文件，双击运行即可安装，或是拖到应用程序里面。
- 更改配色方案
    - 目前大家喜欢设置的配色方案为 solarized，iTerm2 默认是有带的，如果没有则访问：<https://github.com/altercation/solarized>
        - 在项目中找到 solarized/iterm2-colors-solarized 目录，下面有两个文件：Solarized Dark.itermcolors 和 Solarized Light.itermcolors，双击这两个文件就可以把配置文件导入到 iTerm 里了。
    - 更改后的配色最终效果如下图：已经截图了。同时还要再切换到 Text 标签，把 `Draw bold text in bold font` 的勾去掉。
    - ![YouMeek 公众号](http://img.youmeek.com/2016/Homebrew.jpg)

### iTerm2 软件特色

- 智能选中
    - 在 iTerm2 中，连续双击选中，连续三击选中整行，连续四击智能选中（智能规则可配置），可以识别网址，引号引起的字符串，邮箱地址等。
	- 在 iTerm2 中，选中即复制。即任何选中状态的字符串都被放到了系统剪切板中。
- Hotkey Window (快速调出窗口)
	- 这个非常好用，默认是没有设置，需要自己设置下。
	- 实际使用时我们经常会遇到这种场景：有时候只是执行几行命令，然后就不再使用它。可是我们还是必须要打开终端，使用完成后关闭它。但是用 iTerm2 这个功能只要按快捷键，出来虚化的终端，输入命令，然后再把光标放在其他地方自动就消息了。
- iTerm2 常用快捷键
	- 这篇文章配了很多图，如果你想更加具体地了解可以看这篇文章，我不想截图了：<http://swiftcafe.io/2015/07/25/iterm/>

|快捷键|介绍|
|:---------|:---------|
|输入的命令开头字符 + Command + ;|根据输入的前缀历史记录自动补全|
|Command + ;|根据历史记录自动补全|
|Command + [ 或 command + ]|切换屏幕|
|Command + enter|进入全屏模式，再按一次返回|
|Command + 鼠标单击|可以打开文件，文件夹和链接（iTerm2 是可以对显示的内容进行点击的哦）|
|Command + n|新建新的 Window 窗口|
|Command + t|新建标签页|
|Command + w|关闭当前标签或是窗口|
|Command + d|竖直分屏|
|Command + r|清屏|
|Command + /|按完之后，整个屏幕变成白茫茫的，而光标位置是一个小圆圈清除显示出来|
|Command + 方向键|切换标签页|
|Command + 数字|切换到指定数字标签页|
|Command + f|查找，所查找的内容会被自动复制 ,输入查找的部分字符，找到匹配的值按 tab，即可复制，带有补全功能|
|Command + option + e|全屏并排展示所有已经打开的标签页，带有可以搜索。|
|Command + Option + b|历史回放，i类似视频录像的东西，有记录你最近时间内的操作。有一个类似播放器的进度条可以拖动查看你做了什么。存放内容设置（Preferences -> Genernal -> Instant Replay）。|
|Command + Option + 数字|切换 Window 窗口|
|Command + shift + d |水平分屏|
|Command + shift + h|查看剪贴板历史，在光标位置下方会出现一列你输入过的历史记录|
|Command + Shift + m|可以保存当前位置，之后可以按Command + Shift + j跳回这个位置。|
|Command + shift + alt + w|关闭所有窗口|
|Control + u|清空当前行，无论光标在什么位置|
|Control + a|移动到行首|
|Control + e|移动到行尾|
|Control + f|向前移动，相当于方向键右|
|Control + b|向后移动，相当于方向键左|
|Control + p|上一条命令，相当于方向键上|
|Control + n|下一条命令，相当于方向键下|
|Control + r|搜索历史命令|
|Control + y|召回最近用命令删除的文字|
|Control + h|删除光标之前的字符|
|Control + d|删除光标所在位置的字符|
|Control + w|删除光标之前的单词|
|Control + k|删除从光标到行尾的内容|
|Control + c|结束当前状态，另起一行|
|Control + t|交换光标和之前的字符|

### 安装 Zsh + oh-my-Zsh

- Zsh 官网：<https://www.zsh.org/>
- oh-my-Zsh 官网：<http://ohmyz.sh/>
- 先说下：Zsh 和 oh-my-Zsh 的关系
	- Zsh 是 Shell 中的一种，什么 Shell 你可以再搜索下，简单粗暴讲就是一个：命令解释器，你输入什么命令，它就执行什么，这个东西再 Unix 世界还有其他几个。
	- 由于 Zsh 配置门槛有点高，或者说需要专门花时间去了解 Zsh 才能配置好一个好用的 Zsh，也因为这样，用户也就相对少了。
	- 直到有一天 oh-my-Zsh 的作者诞生，他想要整理出一个配置框架出来，让大家直接使用他的这个公认最好的 Zsh 配置，省去繁琐的配置过程。所以，oh-my-Zsh 就诞生了，它只是会了让你减少 Zsh 的配置，然后又可以好好享受 Zsh 这个 Shell。
- Mac 和一般 Linux 默认的 shell 是 bash，一般人都觉得不好用，我作为一般人，也喜欢 Zsh，所以这里就用 Zsh。
- 为了简化配置 Zsh 过程，我们这里选择 oh-my-Zsh 这个配置库，这是目前大家公认好用的配置。
- 打开终端，先安装 git（已经安装的跳过该步骤），输入命令：`brew install git`
- 打开终端，安装 wget 工具，输入命令：`brew install wget`
- 打开终端，安装 Zsh：`brew install Zsh`
- 打开终端，安装 oh-my-Zsh：`sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-Zsh/master/tools/install.sh -O -)"`
    - 下载完后，会提示你输入当前登录系统的用户密码，输入完成之后就会从 bash 切换到 Zsh，如果你没有输入密码直接跳过了，可以运行该命令进行手动切换：`chsh -s /bin/Zsh 你当前系统用户名`
    - 切换完成之后，关掉终端，重新打开终端即可
- 如果你需要修改 oh-my-Zsh 的主题，和安装 Zsh 插件，具体可以看我过去整理的这篇文章：[Zsh 入门](https://github.com/judasn/Linux-Tutorial/blob/master/Zsh.md)

### Zsh 软件特色

- 不区分大小写智能提示。我是不喜欢大小写区分的那种人，所以用了 zsh 之后，经常按 Tab 进行提示。
- 此外按下 tab 键显示出所有待选项后，再按一次 tab 键，即进入选择模式，进入选择模式后，按 tab 切向下一个选项，按 shift + tab 键切向上一个选项，ctrl+f/b/n/p 可以向前后左右切换。
- kill + 空格键 + Tab键，列出运行的进程，要啥哪个进程不需要再知道 PID 了，当然了 zsh，提供了让你知道 PID 的方法：
	- 比如输入：kill vim，再按下 tab，会变成：kill 5643
- `ls **/*`，分层级地列出当前目录下所有文件及目录，并递归目录
- `ls *.png` 查找当前目录下所有 png 文件
- `ls **/*.png` 递归查找
- zsh 的目录跳转很智能，你无需输入 cd 就可直接输入路径即可。比如：`..` 表示后退一级目录，`../../` 表示后退两级，依次类推。
- 在命令窗口中输入：`d`，将列出当前 session 访问过的所有目录，再按提示的数字即可进入相应目录。
- 给 man 命令增加结果高亮显示：
	- 编辑配置文件：`vim ~/.zshrc`
``` bash
# man context highlight
export LESS_TERMCAP_mb=$'\E[01;31m'       # begin blinking
export LESS_TERMCAP_md=$'\E[01;38;5;74m'  # begin bold
export LESS_TERMCAP_me=$'\E[0m'           # end mode
export LESS_TERMCAP_se=$'\E[0m'           # end standout-mode
export LESS_TERMCAP_so=$'\E[38;5;246m'    # begin standout-mode - info box
export LESS_TERMCAP_ue=$'\E[0m'           # end underline
export LESS_TERMCAP_us=$'\E[04;38;5;146m' # begin underline
```
- 刷新配置文件：`source ~/.zshrc`

### 关于搭配上 tmux

- 这个我觉得不是人人都需要的东西，如果经常用终端，或是运维人员可以考虑学这个东西，我的资料也是网上找的，你们可以自己找一下。


## 资料整理

- 来自 Google 过程中的资料（真心感谢这些作者）：
	- [Mac 终端命令大全](http://www.jianshu.com/p/3291de46f3ff)
    - <http://wiki.jikexueyuan.com/project/mac-dev-setup/iterm.html>
    - <http://wulfric.me/2015/08/iterm2/>
    - <http://yanghui.name/blog/2015/07/19/make-all-command-through-proxy/>
    - <https://segmentfault.com/a/1190000003001555>
    - <http://www.wklken.me/posts/2015/08/06/linux-tmux.html>
    - <http://www.dreamxu.com/mac-terminal/>
    - <http://zhaozhiming.github.io/blog/2015/11/22/save-and-restore-your-tmux/>
    - <http://cenalulu.github.io/linux/tmux/>
    - <http://blog.csdn.net/gatieme/article/details/49301037>
    - <http://blog.jobbole.com/87278/>
    - <http://wulfric.me/2015/08/zsh/>
    - <http://hujiandong.com/2016/09/11/iterm2/>
    - <http://www.jianshu.com/p/68ef9d2e1653>
    - <http://swiftcafe.io/2015/07/25/iterm/>


## 结束语

- 如果你需要它就你就好好学习，如果你的职业现在完全用不到，那就把这篇文章加收藏，有需要再打开，不希望你花时间多做一些没有太大意义的事情。
