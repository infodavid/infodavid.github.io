---
layout: post
title:  "给你的终端装上强大的 oh my zsh"
date:   2014-10-21 11:54:46
author: David
categories: 
- blog
- Framerjs
img: framer-icon.png
thumb: framer-icon-02.png
---

近期工作特别忙，都没来得及更新。补上一篇。

Oh My Zsh 是异常强大的命令补全工具，有了它，输入命令更简单。

# Git 安装（未安装 Git 的用户）

下载 Git, [点击此处进入官网下载](http://git-scm.com/downloads/ "下载")<!--more-->

# 通过 Git 安装强大的命令补全工具 oh-my-zsh

可点击 [此处](https://github.com/robbyrussell/oh-my-zsh "oh-my-zsh") 查看文档，或者通过下面的步骤安装：

1. 克隆仓库：

	```
	git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh	```
1. 也可以选择备份一下你的 `~/.zshrc` 文件：

	```
	cp ~/.zshrc ~/.zshrc.orig
	```
1. 通过复制作者提供的 Zsh 模板，创建一个 Zsh 配置文件：

	```
	cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
	```
1. 设置 Zsh 为默认的 Shell

	```
	chsh -s /bin/zsh
	```
1. 通过新开一个命令行窗口，打开或者重启 Zsh 

搞定！