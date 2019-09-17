---
title: "如何在netlify上快速部署hugo博客"
date: 2019-09-17T01:36:30+08:00
draft: false
---
#### 第一步 MAC安装hugo

> Homebrew，是macOS上的安装工具，你可以在[这里](https://brew.sh/)安装。

*打开终端并执行*
` brew install hugo`

*检查是否安装成功*
`hugo version`

```
如果你使用的是windows系统请点下面链接查看安装方法
```
[windows 安装方法](https://gohugo.io/getting-started/installing)
#### 第二步 快速开始 创建站点
*在终端输入如下代码*
`hugo new site quickstart`
![屏幕快照 2019-09-17 下午5.24.44](https://lulinlu.oss-cn-beijing.aliyuncs.com/2019/09/17/ping-mu-kuai-zhao-20190917-xia-wu52444.png)
#### 第三步 为站点添加主题
```
# cd quickstart
git init
git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
echo 'theme = "ananke"' >> config.toml
```
>当然你也可以同时添加多个主题。

#### 第四步 生成文章

`hugo new posts/my-first-post.md`
生成后将自动填充以下内容
```
---
title:"My First Post" //文章的标题
data: 2019-03-26T08:47:11+01:00 //发布时间
draft: ture //为false将不会在网站上显示这篇文章
---
```
#### 第五步 运行Hugo服务

 运行Hugo服务生成静态站点。测试安装是否有问题。-D参数将显示所有draft不为flase的文章
```
▶ hugo server -D

                   | EN
+------------------+----+
  Pages            | 10
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  3
  Processed images |  0
  Aliases          |  1
  Sitemaps         |  1
  Cleaned          |  0

Total in 11 ms
Watching for changes in /Users/bep/quickstart/{content,data,layouts,static,themes}
Watching for config changes in /Users/bep/quickstart/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```
现在可以访问[http://localhost:1313](http://localhost:1313)查看站点。

#### 第六步 自定义config.toml内容
config.toml位于站点根目录

```
baseURL = "https://example.org/" //默认域名
languageCode = "en-us"  //站点使用语言
title = "My New Hugo Site"  //站点标题
theme = "ananke" //站点所使用的主题
```

#### 第七步 将代码部署到GitHub 上

>你需要有一个ﬁgithub的账号，点[这里](http://github.com）注册

登陆GitHub 后在这里生成新的repo
![屏幕快照 2019-09-17 下午6.52.12](https://lulinlu.oss-cn-beijing.aliyuncs.com/2019/09/17/ping-mu-kuai-zhao-20190917-xia-wu65212.png)
---
![屏幕快照 2019-09-17 下午6.54.24](https://lulinlu.oss-cn-beijing.aliyuncs.com/2019/09/17/ping-mu-kuai-zhao-20190917-xia-wu65424.png)
---
![屏幕快照 2019-09-17 下午6.55.35](https://lulinlu.oss-cn-beijing.aliyuncs.com/2019/09/17/ping-mu-kuai-zhao-20190917-xia-wu65535.png)
记住你的仓库地址
![屏幕快照 2019-09-17 下午6.57.03](https://lulinlu.oss-cn-beijing.aliyuncs.com/2019/09/17/ping-mu-kuai-zhao-20190917-xia-wu65703.png)

打开终端进入到quickstart目录
输入以下命令
```
git init
git add .
git commit -m "first commit"
//这里输入你的repo地址
git remote add origin https://github.com/LuLinLu/quickstart.git 
git push -u origin master
```
查看一下你仓库的源码是否同步了。

####第九步 链接到netlify
打开 [https://www.netlify.com/](https://www.netlify.com/)网站。

![屏幕快照 2019-09-17 下午7.06.58](https://lulinlu.oss-cn-beijing.aliyuncs.com/2019/09/17/ping-mu-kuai-zhao-20190917-xia-wu70658.png)
注册好账号

登陆后，点这里创建新的站点
![屏幕快照 2019-09-17 下午7.09.50](https://lulinlu.oss-cn-beijing.aliyuncs.com/2019/09/17/ping-mu-kuai-zhao-20190917-xia-wu70950.png)

链接到您的gitbub仓库，全部设置是都是自动获取的，这里就不截图了。

####第十步 生成静态页面
链接成功后要在这里生成一下静态页面，不然打不开网站。![屏幕快照 2019-09-17 下午7.13.10](https://lulinlu.oss-cn-beijing.aliyuncs.com/2019/09/17/ping-mu-kuai-zhao-20190917-xia-wu71310.png)

好了～hugo博客就架设完毕了～