---
title: 搭建 Hexo 博客--增强篇
date: 2016-02-29 23:43:30
description: "本文将讲解 Hexo 博客的常用插件、站点 SEO 等内容！"
categories: Hexo
tags: Hexo
---


<!-- more -->


## 主题优化 

### 主题配置介绍 

我这里只讲自己在使用的 yelle 主题，你可以参考下，可能还有一些改动我后续会自己在慢慢改，但是大体基本也就这样了。

从中我们也可以看出，对于主题来讲，大部分可以配置的地方其实都是在这里的，所以对于主题的使用者来讲，懂这里很重要。

- 基本上主题的配置文件都是有内容改，但是下面这几点我觉得特别重要：
- `duoshuo`，如果你是打算采用多说评论系统的话，你需要设置这里，但是我个人对多说没好印象
- `youyan`，有言也是国内实用比较多的评论系统之一，个人感觉相对比较稳定
- `open_in_new`，我个人觉得这个东西就应该是 true，不是用新标签的都是坏人
- `baidu_tongji`，我个人使用的是百度统计，具体百度统计的使用可以查看百度统计官网：<http://tongji.baidu.com>


### 我的 yelle 主题配置 

``` bash
# >>> Basic Setup | 基础设置 <<<

# Header | 主菜单
## About Page: `hexo new page about`
## Tags Cloud Page: `hexo new page tags`
menu:
  主页: /
  关于我: /about/
  标签云: /tags/
  所有文章: /archives/
  IntelliJ IDEA: /tags/IntelliJ IDEA

# Link to your avatar | 填写头像地址
avatar: /img/avatar.png

# Small icon of Your site | 站点小图标地址
favicon: /favicon.png

# If your site' url is 'http://yoursite.com/blog', set root_url as '/blog/'
# 网站若存放在子目录，请按上面格式填写
# https://hexo.io/docs/configuration.html#URL
root_url: 

# Social info. Bar | 社交信息展示
## Keep "mailto:" in Email | 设置 Email 时保留 "mailto:"
## Encrypt email 加密邮件地址 http://ctrlq.org/encode/
## RSS requires a plugin to take effect | 使用 RSS 需先安装对应插件
## https://github.com/hexojs/hexo-generator-feed

subnav:
  Email: "mailto:judas.n@qq.com"
  #新浪微博: "sina weibo"
  GitHub: "https://github.com/judasn/IntelliJ-IDEA-Tutorial"
  RSS: "/atom.xml"
  #V2EX: "#"
  #知乎: "zhihu"
  #豆瓣: "douban"
  #简书: "jianshu"
  #SegmentFault: ""
  #网易云音乐: "netease"
  #虾米音乐: "xiami"
  #Facebook: "#"
  #Google: "#"
  #Twitter: "#"
  #LinkedIn: "#"
  #QQ: "#"
  #微信: "Wechat"
  #PayPal: "#"
  #StackOverflow: "#"
  #Instagram: "#"
  #Flickr: "#"
  #reddit: ""
  #Medium: ""
  #TiddlyWiki: ""
  #Tumblr: ""
  #_500px: ""

# >>> Conments 评论系统 <<<
# Chose ONE as your comment system and keep others disable.
# 选一个作为网站评论系统，其他保持禁用。

disqus: 
  #on: true
  shortname: 
  # https://help.disqus.com/customer/en/portal/articles/466208-what-s-a-shortname-
  # It is unnecessary to enable disqus here if 
  # you have set "disqus_shortname" in your site's "_config.yml" 

duoshuo: 
  #on: true
  domain: 
  # 是否开启多说评论，http://duoshuo.com/create-site/
  # 使用上面网址登陆你的多说，然后创建站点，在 domain 中填入你设定的域名前半部分
  # http://<要填的部分>.duoshuo.com (domain只填上<>里的内容，不要填整个网址)

youyan:
  on: true
  id: 1738968
  # 是否开启友言评论，http://www.uyan.cc/index.php
  # id 中填写你的友言用户数字ID，注册后进入后台管理即可查看
  # 友言服务在 Web 环境下运行，普通本地环境无法查看，请部署后在线上测试。


# >>> Style Customisation 样式自定义 <<<

# Background | 背景
## "5": show images form bg-1.jpg to bg-5.jpg in `/yelee/source/background/`
## "5": 显示`/yelee/source/background/`文件夹中 bg-1.jpg 到 bg-5.jpg 这5张图片
## "0": white-gray background | 淳朴灰白背景
background_image: 0

highlight_style:
  on: true
  inline_code: 3  # Value: 0 - 9 可选，3还不错
  code_block: 2  # Value: 0 - 4 
  # Set inline_code to style highlight text
  # Chose a highlight theme for code block
  # 通过 inline_code 切换内置文本高亮样式
  # 通过 code_block 切换内置代码高亮配色主题

blockquote_style:
  on: true
  blockquote: 3  # Value: 0 - 7 可选
  # 自定义文章「引用部分」的样式

# 左边栏宽度 px
left_col_width: 330

# Copyright info. of post | 文末版权信息
copyright: true

# Table of contents | 文章目录
toc: true

# 目录中标题不换行
# Keep TOC title on the same line | 
toc_nowrap: true

# 自定义"阅读全文"链接按钮的显示文字
# Customize the text on excerpt link
excerpt_link: more

# 是否显示边栏中的搜索框（仅样式，未添加搜索功能）
# Search Box in left column
search_box: false

# 是否开启主页及加载头像时的动画效果
# Animation in Homepage and Loading avatar
animate: true

# Load jQuery UI to style tooltips
# 工具提示框样式美化
jquery_ui: false

# >>> Small features | 小功能设置 <<<

# 是否开启边栏多标签切换
# Birdhouse button in left column
tagcloud: true

# Blogroll, Link exchange | 友情链接
friends:
  YouMeek: http://www.YouMeek.com
  YouMeek导航: http://i.YouMeek.com
  GitHub: https://github.com/
  IntelliJ IDEA: http://www.jetbrains.com/idea/
#friends: false

#是否开启“关于我”。
aboutme: 此地只专注于技术
#aboutme: true

# 是否在新窗口打开链接
# Open ALL link in a new tab
open_in_new: true

# Customize feed link 自定义订阅地址
rss: /atom.xml


# >>> Vendors | 第三方工具 & 服务 <<<

# images viewer | 图片浏览器
## http://www.fancyapps.com/fancybox/
fancybox: true

# Display Math(LaTeX, MathML...) | 数学公式支持
## https://www.mathjax.org/
mathjax: false

# Socail Share | 是否开启分享
share: true

# 百度、谷歌站长验证。填写 HTML 标签 content
# Site Verification for Google and Baidu. HTML label content.
baidu_site: 
google_site: 

# Fill in Google Analytics tracking ID, #e.g. UA-XXXXX-X
google_analytics: 

# 百度统计 http://sitecenter.baidu.com/sc-web/
# 查看代码，填入 //hm.baidu.com/hm.js? 之后的内容
baidu_tongji: b68dade9d355a0b3d875d0ffbbe1f212

# 不蒜子网站计数设置
# http://ibruce.info/2015/04/04/busuanzi/
visit_counter:
  on: true
  site_visit: 本站到访数
  page_visit: 本页阅读量

# GitHub Repo Widget
# https://github.com/hustcc/GitHub-Repo-Widget.js
github_widget: false
```

## 常用页面添加

### 404、关于我、标签页

- 还是以上一篇文章我们讲解的项目根目录上：E:\git_work_space\hexo，在该目录启动 Git Bash：
- 新增一个 404 页面：`hexo new page 404`
- 新增一个 about 页面：`hexo new page about`
- 新增一个 tag 标签云页面：`hexo new page tags`
- 新增一个 robot.txt 文件，把该文件放在：E:\git_work_space\hexo\source 目录下，如果你没有该文件可以到我的项目上找：<https://github.com/judasn/judasn.github.io>
- robot 文件内容：

```
User-Agent: *
Allow: /
Disallow: /background
Disallow: /css
Disallow: /fancybox
Disallow: /font-awesome
Disallow: /img
Disallow: /js
Sitemap: http://code.youmeek.com/sitemap.xml
Sitemap: http://code.youmeek.com/baidusitemap.xml
``` 


## 插件推荐

### 插件的基本使用命令

- 安装插件：`npm install 插件名 --save`
- 卸载插件：`npm uninstall 插件名`
- 更新插件和博客框架（需要在 E:\git_work_space\hexo 目录下）：`npm update`
    - 它实质上是通过项目根目录下 package.json 文件更新各大组件

### 必备插件

- 支持RSS：`npm install hexo-generator-feed --save`
- 生成站点地图：`npm install hexo-generator-sitemap --save`
- 生成百度站点地图：`npm install hexo-generator-baidu-sitemap --save`
- HTML 压缩：`npm install hexo-html-minifier --save`
- JavaScript 压缩：`npm install hexo-uglify --save`
- CSS 压缩插件：`npm install hexo-clean-css --save`
- SEO优化：`npm install hexo-generator-seo-friendly-sitemap`

## 结束语

- 真心希望这是 Hexo 最后一篇，因为我们只是要安心写东西而已，不需要太多折腾。
