
## 部署前准备 

- 该主题需要 Hexo 3 以上版本，所以如果你本地版本比较旧，可以先卸载 Hexo：`npm uninstall -g hexo-cli`
- 然后重新安装最新版的 Hexo：`npm install -g hexo-cli`
- 本篇采用 Git-bash 作为命令终端工具
- Hexo 的基础知识可以看下面两篇文章
	- <http://life.youmeek.com/2016/02/28/2016/02/Hexo/>
	- <http://life.youmeek.com/2016/02/29/2016/02/Hexo-Intensify/>

### 创建新项目

- 打开 Git Bash：
    - 进入该目录：`cd d:/code_space/hexo_code`
    - 创建项目目录：`mkdir wukongcloud`
    - 进入项目目录：`cd wukongcloud`
    - 然后执行：`hexo init`，这个时间也会比较长，也有可能要等几分钟，有显示 WARN 也不用管
    - 现在我们启动 hexo 本地服务，看下默认的博客是怎样的，命令：`hexo server`
    - 现在用浏览器访问：<http://localhost:4000/>
    - 如果要停止 hexo 服务：在 Git Bash 下按 `Ctrl + C` 即可


### 选用 MiHo 主题

- MiHo 主页：<https://github.com/WongMinHo/hexo-theme-miho>
- MiHo 官网文档说明：<https://blog.minhow.com/2017/08/01/blog/installation-configuration/>
- 进入项目目录：`cd d:/code_space/hexo_code/wukongcloud`
- 安装主题依赖：`npm install hexo-generator-json-content --save`
- 下载主题：`git clone https://github.com/WongMinHo/hexo-theme-miho.git themes/miho`
- 下载好主题文件之后，我们现在要修改 `d:/code_space/hexo_code/wukongcloud` 目录下的项目配置文件：**\_config.yml**，把对应的主题目录名改下：`theme: miho`
- 更改主题目录名后，我们还要重新生成主题静态内容：
    - 继续在 Git Bash 中输入命令：
        - 重新生成静态博客的所有内容：`hexo generate`
        - 重启 hexo 本地服务：`hexo server`
        - 重新访问：<http://localhost:4000/>
- 申请一些辅助账号
	- CNZZ 统计：<http://passport.umeng.com/user/products>
	- 畅言评论系统：<http://changyan.kuaizhan.com/>
- 最后，主题的配置可以看主题官网文档
