---
layout: post
title: "Quartz Composer & Origami 2.0 介绍及教程（1）"
date: 2015-03-08 22:54:46
author: 大蔚陈
categories: 
- Others
img: origami.png
thumb: origami-small.png
---

## 介绍 Origami

随着互联网尤其是移动互联的急剧发展，设计变得更受重视，于是越来越多的产品经理和设计师开始寻找简单好用的工具。

<!--more-->

2014年可谓是原型工具爆发的一年，各类工具层出不穷。我也尝试用过很多种，从代码级别的 Framerjs，到  Quartz Composer，当然我最喜欢的其实还是 Xcode 和 Keynote。

Origami 是 Quartz Composer 的一个库。Facebook 的设计团队在设计过程中就是用它来进行设计的。前不久 Origami 2.0 的发布，大大降低了学习难度，而且还可以在手机上实时交互，让这个工具开始火热起来了。

Facebook 官方也发布了 Origami 2.0 的样例和教程，本篇主要源自于 Introduction to Origami 的视频教程，所以我自己做了一遍，另外增添了一些内容。

好的，废话不多说，看干货。

### 初步介绍
- 打开 QC
- 创建新 Origami File

![New file](/assets/img/blog/origami/1-new-file.png)


- 左边是编辑区，右侧是 Viewer，可以点击 Resize to third 三分之。

![Resize to Third](/assets/img/blog/origami/2-view.png)


- 在编辑区的右侧有 Viewer Patch（模块）


### 添加资源

先简单介绍一下模块的概念。QC 中模块分为几种：

![image](/assets/img/blog/origami/qc-intro.png)

1. 方角的，四角是尖的称之为 Macro（宏），可以双击进入详细编辑，类似于程序中函数的概念（ 函数是由事件驱动的或者当它被调用时执行的可重复使用的代码块）。你在这个 View （视图）里，还可以包含其他的 View（视图），实在不理解，就把他当做图层组吧。你可以双击进入详细编辑，在工具栏中点击向上箭头哪个按钮（底部写着 Edit Parent）可以返回上一层。

2. 圆角的是普通模块。

3. 蓝色的是输出模块，会在 Viewer 中看到。

4. 紫色模块则代表该模块内部还有其他模块。

添加资源很简单，只需要把对应的图片文件拖到 Editor 区域中即可，会自动创建一个图片模块以及图层模块。

![Add File](/assets/img/blog/origami/add-file.png)

### 图层模块

图层是一个显示类模块，可在屏幕上显示。你可以设置它的 X/Y/Z Position，你可以双击输入数值，也可以长按后左右拖动变更数值。同时还可以选择 Anchor Point（锚点）是左上开始还是居中等。

你也可以点击 Mask Image，或者改变不透明度，缩放等。

按住 command + enter 键，可以查看 Quartz Composer 的各种库，包括了 Origami 库。

![Library](/assets/img/blog/origami/library.png)

选择 Interaction 2号，交互2号。我们可能会奇怪这个「2号」怎么来的，但是你搜索的时候就明白了，QC 本身就有一个 Interaction，就好比在 Mac 系统里，你复制一个同名同类型的文件，为了避免重复，就变成了「交互2号」会自动加上（2）一样。

交互2号的含义是：
 - Down 点击，鼠标按下。
 - Up
- Tap 轻拍，轻触
- Drag 拖拽

如果需要图的过渡变化，就需要用到过渡模块了。

### 过渡模块

取一个0-1之间的数值，并将其转换为由开始值和结束值之间的范围内的一个数值。通过 Progress 输入口数字的变化，输出一个在 Start Value 和 End Value 之间的对应值。

在这我设置的起始值为1，结束值为 0.4，和官网稍稍有些不同。官网默认是看到缩放了的居中的图片，而我设置的是默认在有图有文字的页面，这也方便各位去琢磨对比过渡模块的用途。

### 添加动效

在图片缩放的时候，其实有一个动效，Pop 动效。
现在就让我们来添加这个动效。

有个快捷方式是，你鼠标悬在圆点处，然后按键盘上的 A，就可以出来 Pop Animation 了。

但是问题仍然在，图片缩放后无法保持缩放后的状态，所以我们需要一个开关进行状态切换。


### Switch 开关


一个开关可以记住一个状态。它工作的原理和点灯开关有些类似，一开始是关着的，如果你按一下，他就变成开了，然后你再按一下，就变成关了。举个例子，如果你想轻触一个图片时，它会缩小而且当你松开手指的时候，他会保留这个状态。


Flip 端口对对称式的交互式很有用的，比如说你重复点击一个图片，让它从缩放从小到大。举个例子，在一个编辑窗口，你可能会有一个编辑按钮来打开这个开关（在窗口动效）以及在窗口中的「取消」和「确定」按钮来关闭这个开关。

快捷键：Shift + ⬆️ 

![Add animation](/assets/img/blog/origami/add-animation.png)

### 添加过渡

添加 Chrome 图片（图片名叫 Chrome，并不是指 Chrome 浏览器）

![Add File](/assets/img/blog/origami/add-file-2.png)

为含有评论的 chrome 图片图层添加透明度的过渡，并将过渡模块的 progress 输入口与 Switch 模块的 On/off 连接起来。

OK，大功告成，第一个视频里的 Demo 已经完成了。另外在说一句的是 QC 里的图层顺序。

![Add opacity](/assets/img/blog/origami/add-opacity.png)

### Layer Order 图层顺序

数字越大，优先级越高，越靠前。

### 开始把玩

最后，下载一个 Origami Live，把 iPhone 和 Mac 连接起来。这样，你就可以在尽情的玩耍了。

关于 Origami Live 的体验如何，可以参考我在知乎上的回答：[点此查看](http://www.zhihu.com/question/28359440/answer/40970934)

Facebook 官方视频连接：[http://facebook.github.io/origami/tutorials/](http://facebook.github.io/origami/tutorials/)

部分引用内容参考链接：[次时代交互原型神奇 Origami 档案](http://www.csdn.net/article/2014-06-09/2820131)（感谢这位仁兄，写的非常详细）

