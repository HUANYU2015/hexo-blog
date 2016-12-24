---
title: VPS + Shadowsocks 可以是什么，做什么，如果使用（详细图文）
date: 2016-08-19 20:10:16
description: "对于开发者而言，穿越这件事可能要做一辈子"
categories: [开发工具]
tags: [开发工具,VPS,Shadowsocks,Vultr]
---


<!-- more -->


## 本文初衷

- 帮助我弟弟，理解 VPS，理解服务器部署相关，最重要的是理解穿越这件事
- 帮助更多的开发者或是求知者，勇于求知，丰富自己的精神世界
- 以这篇文章作为回报，感谢鐡的指导
- 写、修改这篇文章大概花了差不多 5 个小时，如果连同过去的一些素材积累，差不多 7 个小时，希望能帮助你。



## VPS 介绍

### 它是什么

- 术语定义
    - 维基百科定义：<https://en.wikipedia.org/wiki/Virtual_private_server>
    - 百度百科定义：<http://baike.baidu.com/item/VPS>
        - 简单地讲就是：服务器中的隔板房
        - 本质：利用虚拟化技术，把一台实体服务器利用软件分割成多台虚拟化的服务器。
        - 你可以简单粗暴地理解为：阿里云、腾讯云提供的那些服务器服务，本质都没啥区别，就是提供资源。
- 同类技术：
    - 你可以用中文搜索：`云主机 虚拟主机 VPS` 
    - 你可以用英文搜索：`Dedicated hosting VPS Virtual cloud Shared hosting` 
    - 今天有看到这样一个标题顺便拿来做说明：linuxVPS基本命令，这个标题是不合理的。Linux 命令和 VPS 没啥关系，以后不要再犯这种错误了。
- 学习前提/依赖
    - 英文单词好点
    - 会点 Linux 命令，关于 Linux 知识我有整理过：<https://github.com/judasn/Linux-Tutorial>
    - 懂一点代理相关的思维，不懂也没关系
    - 知道外面世界和内部世界的差别，不知道也没关系


### 哪些人不喜欢它

- 懒人


### 为什么学习它

- 需要：Google
- 搭建博客
- 搭建个人私有云
- 放爬虫程序
- 做离线下载（注意经常别下盗版，外国要求这个很严），你看到很多人把 Youtube 视频转到国内优酷啥的，基本就是利用它的
- 服务器能做啥，它就能做啥，所以靠你想象力，也希望你能帮我想一下还有啥可以玩的，我这边 768M 内存感觉用不完


## VPS 使用过程

### 选择一个 VPS 提供商

- 目前在国内，使用的主流外国 VPS 厂商有这些：
    - [Linode](http://www.linode.com/)，算是业界 Top，就是贵
    - [Vultr](http://www.vultr.com/?ref=6959017)，我现在用的，也是下文演示的 VPS
        - [我的 Vultr 夏季特别推荐码](http://www.vultr.com/?ref=6959018-3B)
        - [来自我朋友：鐡的 Vultr 夏季特别推荐码](http://www.vultr.com/?ref=6958038-3B)
        - 使用这个注册我可以得到 30 美金，你可以得到 20 美金，这些钱提取不出来的，只能在里面消费。
    - [DigitalOcean（跟 Vultr 模式差不多）](https://www.digitalocean.com/)
    - [BandwagonHost（俗称：搬瓦工）](https://bandwagonhost.com/)
    - [HostUs](https://hostus.us/)
    - [Amazon AWS](https://aws.amazon.com)
    - [VPS](https://www.vps.net/)


### Vultr 注册账号

- [Vultr](http://www.vultr.com/?ref=6959017)
	- [我的 Vultr 夏季特别推荐码](http://www.vultr.com/?ref=6959018-3B)
	- [来自我朋友：鐡的 Vultr 夏季特别推荐码](http://www.vultr.com/?ref=6958038-3B)
    - 点击链接上面，注册的按钮就在官网页面右上角，你自己去注册吧
- 注册要点说明：
- > vultr 是禁止用户重复注册账号的，即如果你的支付信息有2个账号在使用，那么你的账户会被后台关闭的。简单的说就是一个账户的支付信息比如paypal 账号是对应唯一的一个的，如果你再次使用这个paypal支付另外一个新注册的账号的话，那么账户就会被关闭。所以，重复的注册账号是不可取的，试用到期效果好续费即可。
- > 来源：<https://www.bandwagong.com/vultrvps/>
- Vultr 的一些特性介绍：
    - Vultr 官网优点介绍集合：<https://www.vultr.com/features/>
    - 各个节点的下载速度测试：<https://www.vultr.com/faq/#downloadspeedtests>
    - 各个节点当前的状态情况：<https://www.vultr.com/status/>


### Vultr 收费模式

- 按每小时计算，比如官网套餐中： 5 美元一个月的机器配置，本质就是把 5 美元平摊到每个月里每个小时需要花多少金额。
- 也因为这个按时模式，所以你可以在 Vultr 上随便创建世界上不同地区节点的服务器，自己不喜欢的，速度不好的，都可以随便销毁。每次开通一个服务器，最低消费是 0.01 美金，所以本质上开通是需要成本的。
    - 推荐你刚刚开始的时候可以自己多创建几个服务器，然后对比测试下，看看你当前的网络下，使用哪个地区节点速度更好。国内三大运营商走的路线是不同的，所有还是有差异的。


### Vultr 账号充值

- 既然是服务器肯定是要钱的啦，不然别人没法活。
- 建议用 Paypal 支付，别用信用卡，不然后面取消绑定信用卡是个麻烦事，充值方法操作具体看下图。
    - 如果你没 Paypal 账号，那就注册一个，这个是不需要穿越的：<https://www.paypal.com>
    - 在 Paypal 上绑定一个全币卡信用卡，我不知道银联的国内单币卡可不可以，我猜想是不可以的。建议开发者平时还要准备一个全币卡，方便生活
    - Paypal 的购买流程跟常规银联的支付流程差不多，这里不多说
    - ![Vultr 支付](http://img.youmeek.com/2016/VPS-Vultr-pay.jpg)


### Vultr 上创建空白系统 或 一键搭建某些应用

- Vultr 提供其他一些支持，比如提供专用的主机，存储类云（用的是机械硬盘，容量大）。支持单独开通 IPV6，开通自动备份，防 DDOS 攻击等等，当然了这些肯定是收费的。这些都跟新手没关系，如果你会了自己去勾选，这里不讲。
- 访问创建系统页面：<https://my.vultr.com/deploy/>
- 创建空白系统：
    - 第一步选择服务器所在地区，效果如下图：
        - 目前，国内建议选洛杉矶（Los Angeles, California），其他我都试过了，包括日本，响应都不是最优的，包括鐡在上海的方案，基本也是倾向于洛杉矶的。
        - 亚特兰大（Atlanta, Georgia）目前没有了，但是我测试了它公开的服务下载速度，发现是最快的，所以如果后面有亚特兰大的也建议开一个服务器，对比下，如果不错就换过来。
        - 平时你还可以关注下：西雅图（Seattle, Washington），硅谷（Silicon Valley, California）
        - ![Vultr 创建服务器1](http://img.youmeek.com/2016/VPS-Vultr-server-location.jpg)
    - 第二步选择服务器系统，效果如下图：
        - 如果你会 Linux，你喜欢选 CentOS 或是 Ubuntu、Debian 我都是无所谓的，本质没啥区别，但是如果你不会，那就乖乖地跟着箭头来。
        - ![Vultr 创建服务器2](http://img.youmeek.com/2016/VPS-Vultr-server-type.jpg)
    - 第三步选择服务器硬件情况，效果如下图：
        - 如果你土豪，你选啥我都觉得没事，但是如果你跟我一样，主要是为了 Shadowsocks，那就选择图片上的红圈内容，最便宜，而最合适。
        - 默认 Vultr 是选择第二个，10 美金一个月的套餐，所以你要注意点。
        - ![Vultr 创建服务器3](http://img.youmeek.com/2016/VPS-Vultr-server-size.jpg)
    - 第四步开始自动部署系统，效果如下图：
        - 页面下面剩下的选项跟你没关系，懂的人自己去考虑。新手只要点击：Deploy Now。
        - ![Vultr 创建服务器4](http://img.youmeek.com/2016/VPS-Vultr-deploy.jpg)
- 创建 Vultr 帮我们直接安装好的某个应用系统：
    - 第一步同创建空白系统，这里不重复
    - 第二步选择服务器应用，效果如下图：
        - 如果你懂这些应用各代表什么意思，那就选。我用过 OpenVPN
        - 效果是，部署完后在服务器详情页面下面会给我们一个 OpenVPN 服务地址、账号、密码，访问地址可以下载到一个专用的本地客户端，下载下来安装完成后，打开这个软件，输入账号密码即可连接。
        - ![Vultr 创建服务器2](http://img.youmeek.com/2016/VPS-Vultr-server-application.jpg)
    - 第三步同创建空白系统，这里不重复
    - 第四步同创建空白系统，这里不重复


### 在 Vultr 上销毁一个系统

- 访问我们的服务器列表页面：<https://my.vultr.com/>
    - ![Vultr 服务器操作区](http://img.youmeek.com/2016/VPS-Vultr-operate.jpg)
    - 主要操作按钮如下：
        - `Server Details`，查看该服务器相关详情，比如 SSH 的账号密码等
        - `Server Stop`，停止当前服务器，让服务器无法提供服务，费用可是照扣
        - `Server Restart`，重启服务器
        - `Server Destroy`，点击这个按钮即可销毁服务器，并且里面的数据全部跟着销毁，费用不会再扣


### 本地 SSH 连接到 VPS 系统

- 从这里开始就需要会一点 Linux 知识
- 点击上一步教学中提到的：`Server Details`，查看你自己的服务器 SSH 账号、密码，效果如下图：
    - 把红框中的，IP 地址，用户名，密码，都记录下来，等下要用。端口是默认的 22。
    - ![Vultr 服务器详细](http://img.youmeek.com/2016/VPS-Vultr-detail.jpg)
- 下载 Xshell 进行 SSH 连接
    - 这篇文章有使用 Xshell 说明：[@Xshell+Xftp–在win下最喜欢的SSH终端仿真器/终端模拟器(介绍+下载)](http://www.youmeek.com/ssh-terminal-emulator-recommend-xshell-and-xftp/)
    - 把上面记下的：IP 地址，用户名，密码在 Xshell 里进行配置


### 测试 VPS 性能

- 下面内容建立在你已经 SSH 连上服务器的基础上
- 测试 VPS 纯硬件性能
    - 使用 UnixBench 测试机子性能：
        - `cd /opt`
        - `wget --no-check-certificate https://github.com/teddysun/across/raw/master/unixbench.sh`
        - `chmod +x unixbench.sh`
        - `./unixbench.sh`，剩下就等结果，其他不用管了，执行的时间我这边大概是 30 min，所以还是有点长的。
        - 我最后的结果是：`System Benchmarks Index Score==1286.7`，简单粗暴地讲，如果是 1 个 CPU 的机子，如果你的结果值低于 500，那就是比较垃圾的 VPS 了，优秀的应该在 1000 左右，八九百算是普通（别人说的）。
        - 2016-12-11，我也购买了：DigitalOcean 旧金山每月 5 美金的机子，测试得到的分数：`973.8`。
- 测试我们当前位置到 VPS 所在地址之间的网络请求响应能力
    - 线上 TraceRoute 工具：
        - <http://tool.chinaz.com/Tracert/>
        - <http://www.webkaka.com/tracert.aspx>
        - <http://www.17ce.com/>
    - 本地客户端工具：WinMTR
        - 下载地址：<http://winmtr.net/download-winmtr/>
        - 扫描结果类似这样（实际地址我改动了）：

``` bash
|------------------------------------------------------------------------------------------|
|                                      WinMTR statistics                                   |
|                       Host              -   %  | Sent | Recv | Best | Avrg | Wrst | Last |
|------------------------------------------------|------|------|------|------|------|------|
|                            61.144.0.226 -    2 |   86 |   85 |    1 |    9 |  105 |   11 |
|                            183.56.31.85 -    0 |   90 |   90 |    1 |    9 |   74 |    5 |
|                              61.144.3.6 -    2 |   86 |   85 |    3 |    8 |   20 |    5 |
|                           202.97.33.194 -   17 |   54 |   45 |    0 |    7 |   24 |   10 |
|                            202.97.60.42 -   19 |   49 |   40 |    0 |    6 |   19 |    5 |
|                           202.97.58.134 -    4 |   78 |   75 |  175 |  180 |  193 |  179 |
|                            202.97.50.26 -    2 |   86 |   85 |  166 |  174 |  203 |  166 |
|                           218.30.54.182 -    6 |   74 |   70 |  263 |  267 |  278 |  267 |
|                          50.248.117.226 -    2 |   86 |   85 |  160 |  168 |  179 |  169 |
|                   las-b4-link.telia.net -   12 |   62 |   55 |  272 |  277 |  382 |  277 |
|                   25.132.70.2.vultr.com -    0 |   90 |   90 |  173 |  179 |  201 |  181 |
```

### 在 CentOS 上搭建 Shadowsocks 服务器端

- 重要声明：即使你有 Shadowsocks，你也不一定能用。如果你的公司环境是有很强的内网拦截，或是各种屏蔽，你依旧还是可能使用不了的。如果是一般家用，基本不会出现问题。
- Shadowsocks 中文名称：影梭？也有称作：小飞机，本质是：Socks 5 代理，也是一个代理工具。
- 这里安装 Shadowsocks 使用的是网络上的一键脚本，更多资料可以看：
    - shadowsocks-libev 一键安装脚本（CentOS）：<https://teddysun.com/357.html>
    - Shadowsocks-Python 版一键安装脚本（CentOS，Debian，Ubuntu）：<https://teddysun.com/342.html>  
    - Shadowsocks-go 一键安装脚本（CentOS，Debian，Ubuntu）：<https://teddysun.com/392.html>  
    - ShadowsocksR 一键安装脚本（CentOS，Debian，Ubuntu）：<https://shadowsocks.be/9.html>
- 我推荐使用：shadowsocks-libev 一键安装脚本
    - 部署方法（新手请保证是 root 权限）：
        - `cd /opt ; wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-libev.sh`
        - `chmod +x shadowsocks-libev.sh`
        - `./shadowsocks-libev.sh 2>&1 | tee shadowsocks-libev.log`
    - 接下来会有几个交互提示，需要你按要求完成，比如输入你要设置的端口、账号、密码等，具体看提示。脚本安装完成后，会将 shadowsocks-libev 自动加入开机自启动。
    - 安装完成后效果是这样的：

``` bash
Congratulations, shadowsocks-libev install completed!
Your Server IP:你自己的服务器IP
Your Server Port:你自己设置的服务器端口
Your Password:你自己设置的密码
Your Local IP:127.0.0.1
Your Local Port:1080
Your Encryption Method:aes-256-cfb

Welcome to visit:https://teddysun.com/357.html
Enjoy it!
```

- 卸载 Shadowsocks：
    - `cd /opt ; ./shadowsocks-libev.sh uninstall`
- 其他命令：
    - 启动：`/etc/init.d/shadowsocks start`
    - 停止：`/etc/init.d/shadowsocks stop`
    - 重启：`/etc/init.d/shadowsocks restart`
    - 查看状态：`/etc/init.d/shadowsocks status`


### Shadowsocks 客户端的介绍

- 因为是开源的，所有有很多，这里也感谢 Shadowsocks 的开源者：[clowwindy](https://github.com/clowwindy)
- Windows 客户端：<https://github.com/shadowsocks/shadowsocks-windows/releases>
    - 百度云（密码：rlh1）：<http://pan.baidu.com/s/1jHXGG1w>
    - 360 云盘（密码：30d3）：<https://yunpan.cn/cMZLSPzTeUWJp>
- Linux 客户端：<https://github.com/shadowsocks/shadowsocks-gui>
- OS X 客户端：<https://github.com/shadowsocks/shadowsocks-iOS/wiki/Shadowsocks-for-OSX-Help>
- iOS 客户端（在 App Store 中搜索下面名字）：
	- 这类软件都很友好，配置都是很简单的，跟 PC 客户端类型，填上 SS 的相应信息即可。
	- Shadowrocket，收费，我正在用的
	- Surge，收费
	- Wingy，免费
	- Potatso，收费
	- A.BIG.T，收费
- Android 客户端：<https://github.com/shadowsocks/shadowsocks-android/releases>
- 别人整理的客户端列表：<https://shadowsocks.com/client.html>
- 以 Windows 的 Shadowsocks 客户端为例进行说明：
    - Windows 的 Shadowsocks 是一个绿色版软件
    - 重要思维提醒：
        - （**重点**）Shadowsocks 是一个代理工具，一启动该软件，即使你没有勾选：`启用系统代理`，也是同样可以用的，只是你需要利用浏览器扩展进行代理设置，本文下一个锚点会讲这个知识点
    - 如果你想简单方便，不利用浏览器的扩展进行高级设置的话，那你也可以直接使用 Shadowsocks 自带功能，勾选：`启用系统代理`，然后在 `系统代理模式` 这个选项上选择对应模式
        - 对于系统代理模式有两个选项模式：
        - `PAC 模式`，我称作：自动模式。它有一个 PAC 文件，里面有一些网址的匹配规则，这些网址是历代国人整理出来的，帮你辨别一些有用网站需要使用它就自动代理。这里有一个衍生知识：[GFWList](https://github.com/gfwlist/gfwlist)
            - 也因为有这样的一个 PAC 文件，所以你也可以自己添加规则，如果你会的话。当然了，如果你经常做这种事，那我建议你使用下面要讲的，配合浏览器扩展使用。
            - 最新的 GFWList 地址：<https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt>
        - `全局模式`，系统中所有支持 Socks 5 的软件都可以利用它代理，所以这里的要点是要用它代理必须是支持 Socks 5
            - 也因为 Shadowsocks 这个特点，所以如果你要真正的全局代理，建议还是用 VPN 工具，比如 OpenVPN
    - （**重点**）整体效果看下图 Gif：[Gif 图片太大，点击单独打开](http://img.youmeek.com/2016/VPS-Shadowsocks-settings.gif)


### 浏览器扩展的使用

- Firefox 扩展 FoxyProxy Standard：<https://addons.mozilla.org/zh-CN/firefox/addon/foxyproxy-standard/>
    - （**重点**）配置方法如下图 Gif 演示：[Gif 图片太大，点击单独打开](http://img.youmeek.com/2016/VPS-FoxyProxy-Standard-settings.gif)
    - 配置要点整理：
        - 新建代理服务器
        - 填写 Shadowsocks 默认的本地代理信息：主机或 IP 地址：127.0.0.1，端口：1080
        - 选择 Socks 代理、Socks V5
        - 工作模式选择：使用基于其预定模板的代理服务器
        - 模式订阅增加 GFWList 地址：<https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt>
        - 快速添加功能的开启，这个是为了方便我们添加一些不在 GFWList 的站点进行代理的便捷操作。
- Chrome 扩展 Proxy SwitchyOmega：<https://chrome.google.com/webstore/detail/proxy-switchyomega/padekgcemlokbadohgkifijomclgjgif?hl=zh-CN> 
    - （**重点**）配置方法如下图 Gif 演示：[Gif 图片太大，点击单独打开](http://img.youmeek.com/2016/VPS-Proxy-SwitchyOmega-settings.gif)
    - 配置要点整理：
        - 编辑 proxy 设置，填写 Shadowsocks 默认的本地代理信息：主机或 IP 地址：127.0.0.1，端口：1080，选择 Socks 代理、Socks V5
        - 编辑 auto switch 设置
        - 模式订阅增加 GFWList 地址：<https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt>
        - 规则列表规则选择：proxy
        - 浏览器工作模式选择：auto switch
        - 其他人文章参考：<http://www.ihacksoft.com/chrome-switchyomega.html>

## Shadowsocks 的同类

- SpechtLite：<https://github.com/zhuhaow/SpechtLite/releases>
- ShadowsocksX：<https://github.com/RobertYan/ShadowsocksX/releases>
- ShadowsocksX-R：<https://github.com/yichengchen/ShadowsocksX-R/releases>


## 资料整理

- 来自 Google 过程中的资料（真心感谢这些作者）：
    - <http://www.laozuo.org/tag/vultr-vps>
    - <https://www.bandwagong.com/vultrvps/>


## 结束语

- 不管你是不是开发者，不管你身在何处。请，多求知、求真。以上。