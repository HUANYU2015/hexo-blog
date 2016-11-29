---
title: 一个Java程序员眼中的Mac OS（系列六：终端方案iTerm2 + Zsh）
date: 2016-11-28 22:23:10
description: "很多人说 iTerm2 是 Mac 下最好的终端，试试也无妨"
categories: [Mac]
tags: [Mac,终端]
---


<!-- more -->

## 本文初衷

- 整理自己脑袋中、收藏中的那些资料，来一次清空，让自己重新开始。
- 帮助 Mac 后来者，减少他/她入门成本
- 如果你不是后台开发者，一般不需要用到这个东西，可以不用学的。如果你非要学，那你可以认为你现在看到的东西和在 Linux 上看到的没啥本质的区别，做好这个准备，对你很重要。

## 先总结

- 比 Mac 默认的 Terminal 终端好用，配合 Zsh 确实更加得体
- **牢记：** 装了 zsh 之后，修改终端配置就变成了：`vim ~/.zshrc`，而不是：`vim ~/.bash_profile`，所以以后看到别人的文章中需要：`vim ~/.bash_profile`，那你自己要变通思想过来。
	- 同时更新修改后的配置文件也从：`source ~/.bash_profile`，变成了：`source ~/.zshrc`，当然还有其他取取巧方式，这里不谈。

## iTerm2 知识

### iTerm2 是什么

- 术语定义
    - iTerm2 官网：<http://iterm2.com/>
    - WIKI：<https://en.wikipedia.org/wiki/ITerm2>
    - iTerm2 作者意思：Mac 的默认终端 Terminal 太难用了，我们开发一个新的终端来代替它吧。
- 同类常见技术
    - `Terminal`
- 学习前提/依赖
    - 一点英文
    - 一点 Unix/Linux 系统的思想
    - 一点 shell 概念

### 为什么会出现

- 有些操作，命令行或者说脚本的方式效率是远高于 GUI 界面操作的，这个概念需要用过 Unix/Linux 做过开发的人会懂，特别是搞运维的。如果你不理解，可以找一些运维的视频教程来看看，会有很多事情的处理都是搞脚本的做的。所以终端、shell 对于开发人员一直是存在的，没有消失过，以后也会一直存在，只要它的效率一直高于 GUI 就没有理由消失。

### 哪些人不喜欢 iTerm2

- 设计师？
- 前端开发者？可能真正的好前端开发者也是会很好地用终端的，因为 node.js 的 npm 就有很多命令。
- 不喜欢学习的，因为这里面涉及到很多 Unix/Linux 系统的知识点，很枯燥，而且很多快捷键需要背，需要花很多精力。


### 为什么学习 iTerm2

- 作为后端开发者必须学会的一个技能，不管是为了简化安装一些软件或是处理一些事情，还有工作中的后端程序的软件部署，都会跟 shell 打交道。

### 安装 iTerm2

- 在安装之前先说下前提，你的 Mac 必须装有：Homebrew，等下 zsh 要用到。
	- 如果你不知道这是做什么，可以查看我写的另外一篇文章：[一个Java程序员眼中的Mac OS（系列五：包管理工具）](http://code.youmeek.com/2016/11/27/2016/11/Mac-Homebrew/)
- 下载 iTerm 2
    - 当前时间（2016-10-31）最新版为：3.0.10
    - 下载地址，官网：<https://iterm2.com/>
- 安装 iTerm 2
    - 官网下载下来是一个 zip 压缩包，解压出来有一个 `.app` 文件，双击运行即可安装。其他安装方式暂不考虑。
- 更改配色方案
    - 目前大家喜欢设置的配色方案为 solarized，我记得 iTerm2 默认是有带的，如果没有则访问：<https://github.com/altercation/solarized>
        - 在项目中找到 solarized/iterm2-colors-solarized 目录，下面有两个文件：Solarized Dark.itermcolors 和 Solarized Light.itermcolors，双击这两个文件就可以把配置文件导入到 iTerm 里了。
    - 更改后的配色最终效果如下图：已经截图了。同时还要再切换到 Text 标签，把 `Draw bold text in bold font` 的勾去掉。
    - ![YouMeek 公众号](http://img.youmeek.com/2016/Homebrew.jpg)
- 如果中文乱码
	- 确保Preferences->Profiles->Terminal->Terminal Emulation中的字符编码为UTF-8。
	- 修改：`vim ~/.zshrc`，把这一行改为 UTF-8：
``` bash
# You may need to manually set your language environment
export LANG=en_US.UTF-8
```


### iTerm2 软件特色

- 智能选中
    - 在 iTerm2 中，双击选中，三击选中整行，四击智能选中（智能规则可配置），可以识别网址，引号引起的字符串，邮箱地址等。（很多时候双击的选中就已经很智能了）
	- 在 iTerm2 中，选中即复制。即任何选中状态的字符串都被放到了系统剪切板中。
- iTerm2 常用快捷键
    选中终端中的内容即复制，鼠标中键粘贴
    输入的命令开头字符 + Command + ; 根据历史记录自动补全
    Command + enter 进入与返回全屏模式
    Command + 鼠标单击：可以打开文件，文件夹和链接
    Command + n：新建窗口（对吗?）
    command + p/n: 上一条/下一条命令，相当于方向键上和下。（对吗?）
    Command + t：新建标签页
    Command + w：关闭当前页
    Command + 方向键：切换标签页
    Command + d：竖直分屏
    Command + r：清屏
    Command + /：显示光标位置
    Command + 数字 ： 各 tab 标签切换
    Command + f ： 查找 ，所查找的内容会被自动复制 ,输入查找的部分字符，找到匹配的值按tab，即可复制
    Command + d ： 横着分屏 
    Command + r ： 换到新一屏
    Command + enter：切换全屏
    Command + 方向键左 / Command + 方向键右 : 到一行命令最左边/最右边 
    Command + option + e,全屏展示所有的 tab，可以搜索。
    Command + Option + e：查找所有来定位某个标签页
    Command + Option + b：历史回放
    Command + Option + 数字：切换窗口
    Command + shift + h：iterm2将自动列出剪切板的历史记录
    Command + shift + d ： 水平分屏
    Command + Shift + d：上下分屏
    Command + Shift + h：自动补全剪贴板历史
    Command + shift + h ： 会列出剪切板历史
    Command + f：查找，然后用 tab 和 ⇧ + tab 可以向右和向左补全，补全之后的内容会被自动复制， 还可以用 ⌥ + enter 将查找结果输入终端
    Control + u ：清空当前行，无论光标在什么位置
    Control + u：清空当前行
    Control + a：移动到行首
    Control + e：移动到行尾
    Control + f：向前移动
    Control + b：向后移动
    Control + p：上一条命令
    Control + n：下一条命令
    Control + r：搜索历史命令
    Control + y：召回最近用命令删除的文字
    Control + h：删除光标之前的字符
    Control + d：删除光标所指的字符
    Control + w：删除光标之前的单词
    Control + k：删除从光标到行尾的内容
    Control + t：交换光标和之前的字符
- Hotkey Window (快速调出窗口)
	- 这个非常好用，默认是没有设置，需要自己设置下。
	- 实际使用时我们经常会遇到这种场景： 有时候只是执行几行命令，然后就不再使用它。可是我们还是必须要打开Terminal，然后使用后关闭它。在这种情况下借住iTerm的Hotkey Window 功能我们将会得到前所未有的体验。
	- Hotkey Window支持一键调出iTerm 它将以半透明的形式 覆盖在屏幕上方，配置如下：
	- http://hujiandong.com/2016/09/11/iterm2/

### 安装 Zsh + oh-my-Zsh

- Zsh 官网：<https://www.zsh.org/>
- oh-my-Zsh 官网：<http://ohmyz.sh/>
- 先说下：Zsh 和 oh-my-Zsh 的关系
	- Zsh 是 Shell 中的一种，什么 Shell 你可以再搜索下，简单粗暴讲你可以认为就是系统命令操作的一个界面，而且这个 Unix 世界还有其他几个这样的东西，这东西本身也是软件。
	- 由于 Zsh 配置门槛有点高，或者说需要专门花时间去了解 Zsh 才能配置好一个好用的 Zsh，也因为这样，用户也就相对少了。
	- 直到有一天 oh-my-Zsh 的作者诞生，他想统一一个配置框架出来，让大家直接使用他的这个公认最好的 Zsh 配置。所以，oh-my-Zsh 就诞生了，它只是会了让你减少 Zsh 的配置，然后又可以好好享受 Zsh 这个 Shell。
- Mac 和一般 Linux 默认的 shell 是 bash，一般人都觉得不好用，作为一般人，也都喜欢 Zsh，所以这里就用 Zsh。
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
- 此外按下 tab 键显示出所有待选项后，再按一次 tab 键，即进入选择模式，进入选择模式后，按 tab 切向下一个选项，按 shift+tab 键切向上一个选项，ctrl+f/b/n/p 可以向前后左右切换。
- 快捷键
- kill + 空格键 + Tab键，列出运行的进程，要啥哪个进程不需要再知道 PID 了，当然了 zsh，提供了让你知道 PID 的方法：
	- kill emacs
    - 按下 tab，变成：kill 5643
- ls **/*，分层级地列出当前目录下所有文件及目录，并递归目录
- ls *.png查找当前目录下所有 png 文件，ls **/*.png递归查找
- zsh 的目录跳转更为智能，你无需输入cd，直接输入路径即可。..表示后退一级目录，../../表示后退两级，依次类推。（...的作用和../../相同）
- 在命令窗口中输入：d，将列出当前 session 访问过的所有目录，再按提示的数字即可进入相应目录。
- 给 man 命令增加结果高亮显示：
	- 编辑配置文件：`vim ~/.zshrc`
``` bash
# man page highlight
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


## 结束语

- 如果你需要它就你就好好学习，如果你的职业现在完全用不到，那就把这篇文章加收藏，有需要再打开，不希望你花时间多做一些没有太大意义的事情。
