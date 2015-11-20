---
layout: post
title: "设计师们，四步快速搭建属于你自己的网站"
date: 2015-03-24 03:21:46
author: 大蔚陈
categories: 
- Daily News
img: jekyll.png
thumb: jekyll-icon.png
---


## 不懂技术，你也可以搭建自己的网站。

更新了一下这篇文章的内容，希望能让更多的人，尤其是不懂技术的人能够搭建自己的网站。

不需要去买服务器，不用懂太多技术，无需备案，就像广告里说的不打针不吃药不运动20天就能减30斤一样。现在，来填我埋下的坑了。其实也是和大家一起打气：

**很多事情并没有想象的那么难，只要我们勇敢迈出第一步**

## 写在前面

如果你对编程有一些了解，那么你一定听过 **GitHub**，它有着超高人气，包括 Google, Facebook, Twitter 等世界顶级互联网公司的许多项目都托管在上面，号称程序员中的 **Facebook**。

当然，如果你不懂技术，不了解也没关系，下面就跟着我的步骤，开始搭建专属你的网站！<!--more-->

## 步骤一：安装 Git

Git 是一款免费、开源的分布式版本控制系统。GitHub 是一个代码托管网站，可以托管多个 Git 库，。GitHub Pages 是免费的静态站点，而我们快速搭建网站，

1. 下载并安装最新版本的 Git

	下载 Git, [点击此处进入官网下载](http://git-scm.com/downloads/ "下载")
	
	![image](/assets/img/blog/install-git.png)

1. 在你的电脑中，打开 **终端** 程序
1. 告诉 Git 你的名字，这样你的提交会正确的标签化。输入在`$`后的内容

	```
	$ git config --global user.name "姓名"
	```
	
1. 告诉 Git 邮箱地址将会让你和你的 Git 提交结合起来。你设定的邮箱必须和你用来注册 GitHub 的邮箱是同一个。

	```
	git config --global user.email "你的邮箱地址"
	```
	
## 步骤二：创建主页

- GitHub 注册和本地 Jekyll 环境配置，在 GitHub 上创建一个以`username.github.io`新的仓库。`username`就是你的用户名（或团队名）。

![image](/assets/img/blog/createProject.png)


注：如果在仓库的第一部分没有准确的匹配你的用户名，就无法正常运作，所以，请确保输入正确。

## 步骤三：克隆项目，更新并推送

1. Git 命令获取远程文件

	```
	git clone https://github.com/username/username.github.io
	```

1. 进入到本地项目文件夹，创建一个` index.html` 文件，写个 Hello World。

	```
	cd username.github.io
	echo "Hello World" > index.html
	```
	
	扫盲一下，`cd`命令指的是`change directory`，更换目录，简单的说，就是进入到`username.github.io`这个文件夹了。`echo "Hello World" > index.html`，就意味着你生成了一个 **index.html** 文件，同时输入了一段文字 “Hello World”在这个文件里。
	
1. 推送至 GitHub，追踪，提交，并推送你的变化。

		git add --all
		git commit -m "Initial commit"
		git push

	
## 步骤四：大功告成！

现在，等个几分钟，登录你的主页(`username.github.io`）上去看看吧！


## 超快速进阶方法

如果你嫌刚刚的太简单，就现在就开始搭好一个 Blog，发篇技术/设计文章过过瘾，别急，大蔚陈老师让你三分钟搭建一个崭新的 Blog，还带归档功能哦。而且，还能让你瞬时用上 Bootstrap 前端框架。

让我们回到 **步骤二**，你已经在 GitHub 上建立了一个以`username.github.io`命名的新仓库了，那么，输入以下代码，把一个 Jekyllbootstrap 的主题克隆下来：

	git clone https://github.com/plusjade/jekyll-bootstrap.git USERNAME.github.io
	
再进入到你的文件目录，敲下以下代码：

	cd USERNAME.github.io
	git remote set-url origin git@github.com:USERNAME/USERNAME.github.io.git
	
推送至 Master 分支：

	git push origin master
	
好的，你的 Blog 已经生成了，赶紧喝杯白开水庆祝一下！

## 最最便利方法

其实，除了上面的招，还有一个更便利的办法。去 [一个免费开源的 Jekyll 主题网站](http://jekyllthemes.org/)，获取一个主题，里面都是开源免费的主题，告别盗版，让你从此做一个体面的人。

在里面随意下载一个主题，然后解压一下，放到你的`username.github.io`文件夹里面，然后再输入几行代码（复制就行）：

	git add --all
	git commit -m 'apply a theme'
	git push origin master
	
OK，到这就差不多 OK 了。

目前你还没有安装 Jekyll，之后我会写文章（可能时间会比较长）将会详细介绍如何安装，如何用 Jekyll 发博客，Jekyll 的目录结构代表什么，Jekyll 用的是 Liquid 模板语言，啥意思啊？

现在嘛，你已经成功一半了，至少搭的能看，而且那些主题中大多有文档告诉你怎么使用。

## 最后再唠叨几句

你要问大蔚陈老师，是不是我这么做就完全没问题了？

回答是：No!!!

在实际过程中，你可能会遇到一些麻烦，比如说 Git 命令是怎么回事，英文不好看不太懂怎么办？

知易行难，你只有不断去试，才知道最终的解决方案。就在 GitHub 上搭建一个网站来说，只需要简单四步，但是如果遇到问题的话，还是需要自己查文档。最后奉上一些个链接供各位参考：

> [利用Jekyll在GitHub Pages上部署博客](http://blog.csdn.net/zhangao0086/article/details/37922607)



> [阮一峰--搭建一个免费的，无限流量的 Blog -- Jekyll 和 GitHub Pages 入门](http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html)


我的网站就是这么搭起来的，过程当中也遇到一些问题，但是通过看各类资料，基本都解决了。如果在做的过程中，遇到任何问题，欢迎邮件与我沟通。

Email: [idavid.info@gmail.com](idavid.info@gmail.com)


