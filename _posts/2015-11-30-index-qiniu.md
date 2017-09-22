---
layout: post
title: 如何为七牛云生成索引目录？
date: 2015-11-30
categories: blog
tags: [七牛,图床]
description: 继续折腾，七牛云。

---

![](http://assets.qiniu.com/qiniu-409x220.png)

题图：七牛云存储


## 背景

前一篇的 [如何使用七牛云做为图床？ - 读立写生](http://cnfeat.com/blog/2015/11/24/qiniu/)

想必都已经能用 命令行 上传图片了。

>其实，如果你能上传图片，理论上也能上传其他格式文件了，例如：keynote、ppt、excel等。

可文件一多，找起来就比较麻烦，这时你可能想在 七牛空间 建立子目录了，例如
 
- 将 图片 放在 image 文件夹
- 将 pdf 放在 pdf 文件夹
- 将 录音 放在 tapes 文件夹
- ……

可是，七牛云 空间是没有目录概念的，或者说，它只有一个根目录。

如果你在 [七牛云网页空间](https://portal.qiniu.com/)上传过图片，你就能深切地体会到了，所有的文件都放在一个目录，如果没有极好的命名习惯，那将是一场灾难。

各位感受一下：

![](http://cnfeat.qiniudn.com/image/qiniu-portal.jpg)

如上就是我还没为七牛建立目录的样子。

那么，如何管理好 七牛云 空间？为其建立目录索引呢？


## 七牛云 特性须知



### 单向数据同步服务

在动手折腾目录之前，你必须知道 七牛云 的特性：

-  一般的云盘是 `双向数据同步空间服务`，如何解释呢？举个例子
	+ 百度云、微云、360网盘、dropbox 等就是使用`双向数据同步空间服务`
		+ 你在本地增加一个 cnfeat.txt 文件
		+ 同步之后，云盘多了一个 cnfeat.txt 文件
		+ 你在本地删除一个 cnfeat.txt 文件
		+ 同步之后，云盘少了一个 cnfeat.txt 文件
-  七牛云 不同于以上的 云盘，它是 `单向数据同步服务`
	+  何为 `单向数据同步服务`？ 简单地来说，你可以想像 七牛云空间 就像是你私人邮箱，你将本地文件发送到你的邮箱，七牛云有了副本，就算本地的文件删除了，七牛云上的文件依然存在，除非你去邮箱删除。
		* 你在本地增加一个 cnfeat.txt 文件
		* 同步之后，七牛云多了一个 cnfeat.txt 文件
		* 你在本地删除一个 cnfeat.txt 文件
		* 同步之后，七牛云的 cnfeat.txt 文件依然还在！

那么，如何删除 七牛云 的数据？

暂时发现的方法

- （1）登录网页版，搜索文件删除；
- （2）利用[Demo 集锦- 七牛云存储](http://developer.qiniu.com/demo/index.html)的 [qiniu upload files](https://chrome.google.com/webstore/detail/qiniu-upload-files/emmfkgdgapbjphdolealbojmcmnphdcc) 插件 删除


### 目录理解

- 既然前面说了 七牛云 是没有目录的，那如何理解 七牛云 的目录？
	+  比如：`http://cnfeat.qiniudn.com/image/cnfeat-img.jpg`
	+  你会以为`cnfeat-img.jpg`是存在`image`文件夹下，而实际上，七牛云是没有 `image` 文件夹的
	+  所以 `image/cnfeat-img.jpg` 它就一个完整的文件名
	+  看下图：

![](http://cnfeat.qiniudn.com/image/Cap-cnfeat-img.jpg)

但这并不意味着你需要为每个文件起个类似 `image/cnfeat-img.jpg` 的文件名，你只需要在 七牛云 建立目录即可。

## 如何为 七牛云 建立目录?

### 准备工具

- footer-7niu.html
- gen4idx.py

链接: http://pan.baidu.com/s/1i49VE9R 密码: w4gx

### 说明

以上的工具是 大妈 自行制作的索引页面生成脚本。

````

python gen4idx.py /path/2/gen /path/2/foot.html[模板] excludePath
                     |               |                   +- 排除的目录
                     |               +- 就是footer-7niu.html
                     +- 扫描的起始目录

````

如果文件目录不复杂，直接用以下的命令即可

`python gen4idx.py ./ footer-7niu.html NULL`

每次运行，都会在本地生成一个 `index.html` 的文件索引文件，上传至 七牛云 中，就可以在指定的地址中直观地查看文件。


### 配置

将以上的 `footer-7niu.html`
和 `gen4idx.py` 文件 放入你的需同步的本地目录中

+ 例如我的本地目录是 `/Users/cnfeat/Documents/qrsync/blog`

放置后的目录如下：


````

/Users/cnfeat/Documents/qrsync/blog/
    +- footer-7niu.html
    +- gen4idx.py
    +- image
	|   +- cnfeat-img.jpg
	|   +- ...
    +- pdf
    |   +- WOOP-Toolkit-for-Educators-中文.pdf
    |   +- ...
    +- ...

````

![](http://cnfeat.qiniudn.com/image/7niu-local-set.jpg)


多出了的 `index.html`如何生成呢？

### 建立目录索引


- 用 终端 进入本地同步目录
	+ 打开 终端 输入 `cd /Users/cnfeat/Documents/qrsync/blog`
- 运行脚本，生成 `index.html` 
	+ 终端 输入 `python gen4idx.py ./ footer-7niu.html NULL`
- 运行 七牛同步命令行 将 `index.html` 上传至 七牛云
	+ 终端 输入 `qrsync /Users/cnfeat/7niu/cnfeat.json`
	+ [如何使用七牛云做为图床？ - 读立写生](http://cnfeat.com/blog/2015/11/24/qiniu/)
- 验证
	+ 打开 `http://cnfeat.qiniudn.com/` 发现页面如下，证明`index.html`生成并渲染成功


![](http://cnfeat.qiniudn.com/image/7niu-index.jpg)


### 补充说明

- 因为 七牛云 是 `单向数据同步服务`
- 所以，索引目录几乎只能是个人本地实时的目录
	+ 注定了 主干目录 只能由少数人生成，其他人在 支干目录 协作
- 如果你在 本地空间 将 已同步的 文件删除
- 随后再生成的目录将 不再索引出 该文件
- 你可以用 七牛云网页版 通过 关键词 查找出来

![](http://cnfeat.qiniudn.com/image/index-image-list.jpg)

或尝试用[Demo 集锦- 七牛云存储](http://developer.qiniu.com/demo/index.html)的 [qiniu upload files](https://chrome.google.com/webstore/detail/qiniu-upload-files/emmfkgdgapbjphdolealbojmcmnphdcc) 插件 来查找你的文件。


## 短化 命令行

以上的 命令行 不外乎四条，继续用 [atext](http://www.jianshu.com/p/a15a6cb0f08d) 短化：

- `;cg`>>`cd /Users/cnfeat/Documents/qrsync/blog`
- `;pf`>>`python gen4idx.py ./ footer-7niu.html NULL`
- `;qr`>>`qrsync /Users/cnfeat/7niu/cnfeat.json`
- `;pi`>>`![](http://cnfeat.qiniudn.com/image/)`

搞掂！


## 迭代 


- 2015-11-29 21:00:53


## 参考链接

- [我们是如何使用7牛云储存的 ](http://blog.zhgdg.org/2013-08/usage7niu/)
- [PyCon2014China 志愿者协同手册 PyChina.org](http://pychina.org/imho/cooperate-guider.html)
- [cn.pycon.org/2014 官方网站内部维护仓库](https://gitcafe.com/lins05/MkDoc4PyCon/blob/master/README.md)



----

### **【六经皆我注脚】**

《阿甘正传》，当Jenny问Forrest「你为什么对我这么好」

Forrest 回答：「You are my girl.」

你觉得以上这句话如何翻译好？



----

- 陈素封
- 公众号：cnfeat
- Blog：cnfeat.com

（题图：七牛云存储）


