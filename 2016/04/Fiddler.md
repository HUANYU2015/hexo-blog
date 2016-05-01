---
title: 抓包工具 Fiddler 相关知识总结
date: 2016-04-30 10:14:25
description: "最近工作又需要用到性能测试，需要抓包，所以干脆总结下在使用抓包工具的一些积累"
categories: [开发工具,测试]
tags: [开发工具,测试,Fiddler]
---


<!-- more -->


## 本文初衷

- 整理对 Fiddler 工具的知识积累
- 分享给更多需要使用抓包工具的人

## Fiddler 介绍

### 它是什么


- 术语定义
    - 官网定义：<http://www.telerik.com/fiddler>
    - 百度百科定义：<http://baike.baidu.com/item/Fiddler>
    - 维基百科定义：<https://en.wikipedia.org/wiki/Fiddler_%28software%29>
        - 简单地讲就是一个抓包工具，或者是叫做网络嗅探器，把网络传输的数据抓取下来进行分析、Debug
        - 它可以对常用的浏览器：IE、Chrome、Firefox、Safari 等进行抓包，支持 HTTP、HTTPS
        - 支持代理，可以通过它，在同一个局域网中抓取 APP 的网络请求，然后进行分析
        - 一般我们用来做测试
        - 支持插件扩展
	    - 其本质：
	    - ![Fiddler 抓包原理](http://img.youmeek.com/2016/Fiddler-a-1.jpg)
	        - 图片来源：<http://www.jikexueyuan.com/course/1926_2.html>
        - 别人这样说：
        - > Fiddler是位于客户端和服务器端的HTTP代理，也是目前最常用的http抓包工具之一 。它能够记录客户端和服务器之间的所有HTTP请求，可以针对特定的HTTP请求，分析请求数据、设置断点、调试web应用、修改请求的数据，甚至可以修改服务器返回的数据，功能非常强大，是web调试的利器。
	    - > 来源：<http://blog.csdn.net/ohmygirl/article/details/17846199>
- 官网资料：
	- Windows 版本需要 .NetFrameWork 环境
	- 官网下载（Windows-大小 1M）：<https://www.telerik.com/download/fiddler>
	- 官网下载（Linux-大小 1M）：<http://fiddler.wikidot.com/mono>
	- 插件官网：<http://www.telerik.com/fiddler/add-ons>
	- 官网文档：<http://docs.telerik.com/fiddler/configure-fiddler/tasks/configurefiddler>
	- 官网博客：<http://www.telerik.com/blogs/tag/fiddler>
- 它的历史
	- 版本发布历史：<http://www.telerik.com/support/whats-new/fiddler/release-history/fiddler-v2.x>
- 同类技术：
    - Wireshark（强大）、httpwatch（浏览器扩展）、firebug（浏览器扩展）、Chrome 开发者模式
- 学习前提/依赖
    - 略懂 HTTP 相关知识，比如 GET POST PUT 等这类 request method，Content-type 等这种 request header
	- 如果你没有相关知识，可以看下面视频教程：
		- [了解 web 及网络基础](http://www.jikexueyuan.com/course/1418.html)
		- [细说 HTTP 的报文格式和工作流程](http://www.jikexueyuan.com/course/1706.html)
		- [深入学习 URL](http://www.jikexueyuan.com/course/1755.html)

### 哪些人不喜欢它

- 非 Web 端开发人员

### 为什么学习它

- 因为开发中需要测试，需要了解整个 Web 应用的具体细节，了解细节后可以尽可量防止漏洞，可以对细节做性能测试
- 不管是 Web 开发的前端还是后端，都需要，或者是说只要开发中含有 HTTP 请求的都需要抓包工具


## 积累

### 我要怎么做

- 看教程
    - 极客学院教程：<http://search.jikexueyuan.com/course/?q=Fiddler>
    - 2014 年出版过一本书：[Fiddler调试权威指南](http://search.jd.com/Search?keyword=Fiddler调试权威指南&enc=utf-8&cu=true&utm_source=ads.union.jd.com&utm_medium=tuiguang&utm_campaign=t_248690136_&utm_term=ffff09ca5c61406da6c33f0593ae97b0-p_276666007)
	- [【HTTP】Fiddler（一） - Fiddler简介 ](http://blog.csdn.net/ohmygirl/article/details/17846199)
	- [【HTTP】Fiddler（二） - 使用Fiddler做抓包分析 ](http://blog.csdn.net/ohmygirl/article/details/17849983)
	- [【HTTP】Fiddler（三）- Fiddler命令行和HTTP断点调试 ](http://blog.csdn.net/ohmygirl/article/details/17855031)
	- [使用前端开发利器Fiddler调试手机程序](http://unclechen.github.io/2015/04/30/使用前端开发利器Fiddl)
	- [Web工作方式](http://wiki.jikexueyuan.com/project/go-web-programming/03.1.html)
	- [神器——Chrome开发者工具(一)](https://segmentfault.com/a/1190000000683599)
	- [Fiddler In Action - Part 1](http://www.mehdi-khalili.com/fiddler-in-action/part-1/)
	- [Fiddler In Action - Part 2](http://www.mehdi-khalili.com/fiddler-in-action/part-2/)
	- [Fiddler实用教程](http://www.kuqin.com/shuoit/20160113/350023.html)
	- [Fiddler实战 ](http://mp.weixin.qq.com/s?__biz=MzAxNzA0MTE0Nw==&mid=401100349&idx=1&sn=58ba7af67c30da1b00901bef053af536&3rd=MzA3MDU4NTYzMw==&scene=6#rd)
	- [使用Fiddler自定义百度云分享提取码](http://www.jianshu.com/p/cb33b8132b42)
	- [猫哥网络编程系列：HTTP PEM 万能调试法](http://www.jianshu.com/p/ab962c00ec32)
	- [App测试->抓取手机网络请求](http://www.jianshu.com/p/1626832d8f5d)
	- [抓包与安全](http://www.jianshu.com/p/5beb461d603d)
	- [Web开发利器-Fiddler简介](http://mccxj.github.io/blog/20130531_introduce-to-fiddler.html)
	- [Fiddler 扩展使用](http://www.jianshu.com/p/a248df383c9d)


### 细节积累

- Fiddler 的界面介绍，如下图（[图片来源](http://www.jikexueyuan.com/course/1926_2.html)）
	- ![Fiddler 的界面介绍](http://img.youmeek.com/2016/Fiddler-b-1.jpg)
- Fiddler 工具栏介绍，如下图
	- ![Fiddler 的界面介绍](http://img.youmeek.com/2016/Fiddler-b-2.jpg)
- Fiddler 自定义显示列信息，如下图
	- ![Fiddler 的界面介绍](http://img.youmeek.com/2016/Fiddler-b-3.gif)
- Fiddler 选中会话后的常用右键菜单，如下图
	- ![Fiddler 的界面介绍](http://img.youmeek.com/2016/Fiddler-c-1.jpg)
	- ![Fiddler 的界面介绍](http://img.youmeek.com/2016/Fiddler-c-2.jpg)
	- ![Fiddler 的界面介绍](http://img.youmeek.com/2016/Fiddler-c-3.jpg)
- 按 Ctrl + A 全选所有会话，右边可以查看所有请求的一个总的情况
	- ![Fiddler 的界面介绍](http://img.youmeek.com/2016/Fiddler-f-1.jpg)
- 修改某个请求数据，进行模拟
	- ![Fiddler 的界面介绍](http://img.youmeek.com/2016/Fiddler-f-2.jpg)
- 开启 HTTPS 捕获，默认是没有开启的
	- ![Fiddler 的界面介绍](http://img.youmeek.com/2016/Fiddler-d-1.gif)
- 使用 AutoResponder，这是前端开发必备技能
	- AutoResponder 作用：可用于截拦某一请求，并重定向到本地资源，或者使用 Fiddler 内置响应。
	- 使用场景：比如线上服务器的某个 JavaScript / Images 有问题，正常修改此 Bug 的流程应该是这样的：本地修改后提交到服务器预览修改后效果，但是作为前端开发者其实很多时候是不具备使用服务器的权限的。这时候 AutoResponder 就起作用了，在页面加载的时候，我们让服务器不加载服务器的那个 JavaScript 请求，而是使用本地的那个 JavaScript 文件。
		- 但是使用该场景需要有一个特别注意的：在使用规则之后，重新刷新网页的时候最好是先清除下浏览器缓存，省得有意外，浪费你时间。
	- 下图演示的是我把博客的头像换成一张橘黄色的图片
		- ![Fiddler 的界面介绍](http://img.youmeek.com/2016/Fiddler-e-1.gif)
- Fiddler 的命令行工具中常用命令：
	- 官网对这些命令的整理：<http://docs.telerik.com/fiddler/knowledgebase/quickexec>
	- `?cc=`，用来匹配请求地址中含有 ?cc 的请求
	- `> 5000 或 < 5000`，找响应大小大于 5000 字节，或小于 5000 字节的请求
	- 关于 Debug 命令：
		- 开启中断请求命令
			- `bpafter beautiful`，中断 URL 包含 beautiful 字符的全部会话
			- `bpu beautiful`，中断 URL 包含 beautiful 字符的全部会话
			- `bps 404`，中断 HTTP 响应状态为 404 的全部会话
			- `bpm GET 或者 bpv GET`，中断 GET 请求方式的全部会话
		- 取消中断请求命令
			- 使用同样的开启命令，但是不带参数即可取消，比如我们使用了 `bpu code.youmeek.com` 中断，我们要取消这个中断，则使用：`bpu` 即可



## 结束语

- 更多的细节还需要你自己继续去摸索



