---
title: 一个Java程序员眼中的Mac OS（系列六：终端方案iTerm2+Zsh）
date: 2016-10-31 22:23:10
description: "很多人说它是 Mac 下最好的终端，试试也无妨。"
categories: [Mac]
tags: [Mac,终端]
---


<!-- more -->

## 本文初衷

- 整理自己脑袋中、收藏中的那些资料，来一次清空，让自己重新开始。
- 帮助 Mac 后来者，减少他/她入门成本
- 如果你不是后台开发者，一般不需要用到这个东西，可以不用学的。如果你非要学，那你可以认为你现在看到的东西和在 Linux 上看到的没啥本质的区别，做好这个准备，对你很重要。

## 先总结

- 比 Mac 默认的 Terminal 终端好用，配合 Zsh 更加便捷
- **牢记：** 装了 zsh 之后，修改终端配置就变成了：`vim ~/.zshrc`，而不是：`vim ~/.bash_profile`，所以以后看到别人的文章中需要：`vim ~/.bash_profile`，那你自己要变通思想过来。
	- 同时更新修改后的配置文件也从：`source ~/.bash_profile`，变成了：`source ~/.zshrc`

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

### 哪些人不喜欢它

- 设计师？
- 前端开发者？可能真正的好前端开发者也是会很好地用终端的，因为 node.js 的 npm 就有很多命令。node.js 到底要算前端还是后端、全栈端？╮（╯＿╰）╭
- 不喜欢学习的，因为这里面涉及到很多 Unix/Linux 系统的知识点，很枯燥，而且很多快捷键需要背，需要花很多精力。


### 为什么学习它

- 作为后端开发者必须学会的一个技能，不管是为了简化安装一些软件或是处理一些事情，还有工作中的后端程序的软件部署，都会跟 shell 打交道。

### 我要怎么做

- 在安装之前先说下前提，你的 Mac 必须装有：Homebrew，如果你不知道这是做什么，可以查看我写的另外一篇文章：
- 下载
    - 当前时间（2016-10-31）最新版为：3.0.10
    - 官网：<https://iterm2.com/>
- 安装 iTerm 2
    - 官网下载下来是一个 zip 压缩包，解压出来有一个 `.app` 文件，双击运行即可安装。
    - 其他安装方式不说
        
    - 设置配色方案为 solarized，我记得 iTerm2 默认是有带的，如果没有则访问：https://github.com/altercation/solarized
    如果你使用的是 Terminal 的话，在 solarized/osx-terminal.app-colors-solarized 下双击 Solarized Dark ansi.terminal 和 Solarized Light ansi.terminal 就会自动导入两种配色方案 Dark 和 Light 到 Terminal.app 里。
    如果你使用的是 iTerm2 的话，到 solarized/iterm2-colors-solarized 下双击 Solarized Dark.itermcolors 和 Solarized Light.itermcolors 两个文件就可以把配置文件导入到 iTerm 里。
    最终效果如下图：已经截图了。然后再切换到 Text 标签，把 Draw bold text in bold font 的勾去掉。
    
- 安装 Zsh + oh-my-Zsh
    - 默认的 shell 是 bash，一般人都觉得不好用，一般人也都喜欢 Zsh，所以这里就用 Zsh。
    - 为了简化安装、配置 Zsh，我们这里选择 oh-my-Zsh 这个插件。
	- 不区分大小写智能提示。我是不喜欢大小写区分的那种人，所以用了 zsh
    - 在终端，先安装 git（已经安装的跳过该步骤），输入命令：`brew install git`
    - 在终端，安装 wget 工具，输入命令：`brew install wget`
    - 在终端，安装 Zsh：`brew install Zsh`
    - 在终端，安装 oh-my-Zsh：`sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-Zsh/master/tools/install.sh -O -)"`
        - 下载完后，会提示你输入当前登录系统的用户密码，输入完成之后就会从 bash 切换到 Zsh，如果你没有输入密码直接跳过了，可以运行该命令进行手动切换：`chsh -s /bin/Zsh 你当前系统用户名`
        - 切换完成之后，关掉终端，重新打开
        - 修改 oh-my-Zsh 的主题，具体可以看我过去整理的这篇文章：https://github.com/judasn/Linux-Tutorial/blob/master/Zsh.md
    
- iTerm2 软件特色
	- 智能选中
	    - 在 iTerm2 中，双击选中，三击选中整行，四击智能选中（智能规则可配置），可以识别网址，引号引起的字符串，邮箱地址等。（很多时候双击的选中就已经很智能了）
	- 在 iTerm2 中，选中即复制。即任何选中状态的字符串都被放到了系统剪切板中。
	- 与 tmux 兼容性好。等下会介绍 tmux。
	- iTerm2 常用快捷键
	
    ⌘ + ;：自动补全历史记录
    ⌘ + shift + h：iterm2将自动列出剪切板的历史记录
    command+enter进入与返回全屏模式
    command+option+e,全屏展示所有的 tab，可以搜索。
    ⌘ + Click：可以打开文件，文件夹和链接
    ⌘ + n：新建窗口
    ⌘ + t：新建标签页
    ⌘ + w：关闭当前页
    ⌘ + 数字 & ⌘ + 方向键：切换标签页
    ⌥⌘ + 数字：切换窗口
    ⌘ + enter：切换全屏
    ⌘ + d：左右分屏
    ⇧⌘ + d：上下分屏
    ⇧⌘ + h：自动补全剪贴板历史
    ⌥⌘ + e：查找所有来定位某个标签页
    ⌘ + r & ⌃ + l：清屏
    ⌘ + /：显示光标位置
    ⌥⌘ + b：历史回放
    ⌘ + f：查找，然后用 tab 和 ⇧ + tab 可以向右和向左补全，补全之后的内容会被自动复制， 还可以用 ⌥ + enter 将查找结果输入终端
    选中即复制，鼠标中键粘贴

	很多快捷键都是通用的，和 Emace 等都是一样的

    ⌃ + u：清空当前行
    ⌃ + a：移动到行首
    ⌃ + e：移动到行尾
    ⌃ + f：向前移动
    ⌃ + b：向后移动
    ⌃ + p：上一条命令
    ⌃ + n：下一条命令
    ⌃ + r：搜索历史命令
    ⌃ + y：召回最近用命令删除的文字
    ⌃ + h：删除光标之前的字符
    ⌃ + d：删除光标所指的字符
    ⌃ + w：删除光标之前的单词
    ⌃ + k：删除从光标到行尾的内容
    ⌃ + t：交换光标和之前的字符
	    - ⌘ + 数字 ： 各 tab 标签切换
	    - ⌘ + f ： 查找 ，所查找的内容会被自动复制 ,输入查找的部分字符，找到匹配的值按tab，即可复制
	    - ⌘ + d ： 横着分屏 
	    - ⌘ + shift + d ： 竖着分屏
	    - ⌘ + r ： 换到新一屏
	    - ctrl + u ：清空当前行，无论光标在什么位置
	    - 输入的命令开头字符 + ⌘ + ; ：自动补全
	    - ⌘ + shift + h ： 会列出剪切板历史
	    - ⌘← / ⌘→ : 到一行命令最左边/最右边 
	    - ⌘ + enter : 全屏
	    
	    
这个非常好用，默认是没有设置，需要自己设置下。
Hotkey Window (快速调出窗口)
实际使用时我们经常会遇到这种场景： 有时候只是执行几行命令，然后就不再使用它。可是我们还是必须要打开Terminal，然后使用后关闭它。在这种情况下借住iTerm的Hotkey Window 功能我们将会得到前所未有的体验。
Hotkey Window支持一键调出iTerm 它将以半透明的形式 覆盖在屏幕上方，配置如下：
http://hujiandong.com/2016/09/11/iterm2/

//======================================================
- zsh 软件特色
	- 不区分大小写智能提示。我是不喜欢大小写区分的那种人，所以用了 zsh 之后，经常按 Tab 进行提示。
	- 此外按下 tab 键显示出所有待选项后，再按一次 tab 键，即进入选择模式，进入选择模式后，按 tab 切向下一个选项，按 shift+tab 键切向上一个选项，ctrl+f/b/n/p 可以向前后左右切换。
	- 快捷键
		- kill + 空格键 + Tab键，列出运行的进程，要啥哪个进程不需要再知道 PID 了，当然了 zsh，提供了让你知道 PID 的方法：
			- kill emacs
	        - 按下 tab，变成：
	        - kill 5643
		- ls **/*，分层级地列出当前目录下所有文件及目录，并递归目录
		- ls *.png查找当前目录下所有 png 文件，ls **/*.png递归查找
zsh 的目录跳转更为智能，你无需输入cd，直接输入路径即可。..表示后退一级目录，../../表示后退两级，依次类推。（...的作用和../../相同）
输入d，将列出当前 session 访问过的所有目录，再按提示的数字即可进入相应目录。


给 man 命令增加结果高亮显示：
编辑配置文件：`vim ~/.zshrc`

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

//======================================================
- tmux 是什么？
Terminal Multiplexer，简单的说：它是一个多终端进程管理器，方便地在一个终端窗口下进行分屏。
那么问题来了：Mac自带的Iterm2很好用啊。既支持多标签，也支持窗体内部Panel的分割，为什么还要用tmux？其实，多标签和分割窗体只是tmux的部分功能。用tmux的主要原因是它提供了一个窗体组随时存储和恢复的功能。

主要两个功能
split窗口。可以在一个terminal下打开多个终端，也可以对当前屏幕进行各种split，即可以 同时打开多个显示范围更小的终端。
在使用SSH的环境下，避免网络不稳定，导致工作现场的丢失。想象以下场景， 你在执行一条命令的过程中，由于网络不稳定，SSH连接断开了。这个时候，你就不知道之前 的那条命令是否执行成功。如果此时你打开了很多文件，进入了较深层次的目录，由于网络 不稳定，SSH连接断开。重新连接以后，你又不得不重新打开那些文件，进入那个深层次的 目录。如果使用了tmux，重新连接以后，就可以直接回到原来的工作环境，不但提高了工作 效率，还降低了风险，增加了安全性。



安装：`brew install tmux`
配置：`vim ~/.tmux.conf`
- 基础概念：tmux -> session -> window -> pane

    Tmux可以管理多组会话
    一个会话（Session）可以包含多个窗口，一个窗口（Window）可以包含多个窗格（Pane）

插件包管理工具：
https://github.com/tmux-plugins/tpm

安装窗口保持插件：
http://zhaozhiming.github.io/blog/2015/11/22/save-and-restore-your-tmux/

也有人帮帮你做好了一个配置文件，用它的就可以啦：http://cenalulu.github.io/linux/tmux/

关于powerline，你可以先看下这篇文章：
http://cenalulu.github.io/linux/mac-powerline/
如果乱码，安装这个补丁：https://gist.github.com/qrush/1595572/raw/417a3fa36e35ca91d6d23ac961071094c26e5fad/Menlo-Powerline.otf


tmux的手册非常详尽，请输入man tmux后阅读。 

使用Tmux 的最好方式是使用会话的方式，这样你就可以以你想要的方式，将任务和应用组织到不同的会话中。如果你想改变一个会话，会话里面的任何工作都无须停止或者杀掉。让我们来看看这是怎么工作的。
让我们开始一个叫做”session”的会话，并且运行top命令

tmux new -s new session
top

Prefix-Command前置操作：所有下面介绍的快捷键，都必须以前置操作开始。tmux默认的前置操作是CTRL+b。例如，我们想要新建一个窗体，就需要先在键盘上摁下CTRL+b，松开后再摁下n键。

下面所有的prefix均代表CTRL+b

快捷键看这篇文章不错：
http://blog.kissdata.com/2014/07/29/tmux.html


- 快捷键：
	- Ctrl+b // 激活控制台；此时以下按键生效
	- 系统操作
		- $ 重命名当前的会话
		- ? // 列出所有快捷键；按q返回
		- d // 脱离当前会话；这样可以暂时返回Shell界面，输入tmux attach能够重新进入之前的会话
		- D // 选择要脱离的会话；在同时开启了多个会话时使用
		- Ctrl+z // 挂起当前会话
		- r // 强制重绘未脱离的会话
		- s // 选择并切换会话；在同时开启了多个会话时使用
		- : // 进入命令行模式；此时可以输入支持的命令，例如kill-server可以关闭服务器
		- [ // 进入复制模式；此时的操作与vi/emacs相同，按q/Esc退出
		- ~ // 列出提示信息缓存；其中包含了之前tmux返回的各种提示信息
		- L // 切换回上一次的会话
	- 窗口操作
		- c           创建新窗口
		- n           选择下一个窗口
		- p           选择前一个窗口
		- l           最近一次活跃窗口之间进行切换
		- 0~9         选择几号窗口
		- ,           重命名窗口
		- .           更改窗口的编号，但只能更改成未使用的编号，所以要交换窗口的话，得更改多次进行交换
		- &           关闭窗口
		- w           以菜单方式显示及选择窗口
		- f           在所有窗口中查找内容
	- 面板操作
		- ” // 将当前面板平分为上下两块
		- % // 将当前面板平分为左右两块
		- x // 关闭当前面板
		- ! // 将当前面板置于新窗口；即新建一个窗口，其中仅包含当前面板
		- Ctrl+方向键 // 以1个单元格为单位移动边缘以调整当前面板大小
		- Alt+方向键 // 以5个单元格为单位移动边缘以调整当前面板大小
		- Space // 在预置的面板布局中循环切换；依次包括even-horizontal、even-vertical、main-horizontal、main-vertical、tiled
		- q // 显示面板编号
		- o // 在当前窗口中选择下一面板
		- 方向键 // 移动光标以选择面板
		- { // 向前置换当前面板
		- } // 向后置换当前面板
		- Alt+o // 逆时针旋转当前窗口的面板
		- Ctrl+o // 顺时针旋转当前窗口的面板

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
    - <>
    - <>
    - <>


     
## 结束语

- 如果你需要它就你就好好学习，如果你的职业现在完全用不到，那就把这篇文章加收藏，有需要再打开，不希望你花时间多做一些没有太大意义的事情。
