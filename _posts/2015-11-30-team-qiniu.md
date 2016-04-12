---
layout: post
title: 如何协作使用七牛云空间？
date: 2015-11-30
categories: blog
tags: [七牛,图床]
description: 继续折腾，七牛云。

---

![](http://assets.qiniu.com/qiniu-409x220.png)

题图：七牛云存储

## 背景

[如何使用七牛云做为图床？ - 读立写生](http://cnfeat.com/blog/2015/11/30/cli-qiniu/)

[如何为七牛云生成索引目录？ - 读立写生](http://cnfeat.com/blog/2015/12/02/index-qiniu/)

如上，已经搞掂

- 命令行上传图片>>>方便自己上传图片
- 生成索引目录>>>方便自己/别人查看

那么，问题又来了，如果我要和别人共享一个 七牛云 空间，应如何操作？

## 分析

考虑到共享空间必须能分辨出每人的上传的文件，所以，共享空间就

- 不能共用一个目录 
- 有独立的子目录

譬如，我建立了一个七牛空间「omcomc」(实际无此空间)

那么，总体的 七牛空间 的共享目录应该是这样的：

````

http://omcomc.qiniudn.com/
    +- share/ #共享的目录
    +- team/  #团队人员目录
    |   +- cnfeat1/ #团队人员之一
    |   +- cnfeat2/ #团队人员之二
    |   +- cnfeat3/ #团队人员之三
    |   +- cnfeat4/ #团队人员之四
    +- ...

````

而实际上，七牛云 是 `单向数据同步服务`的，所以，协助者的目录就简单了


````

http://omcomc.qiniudn.com/
    +- share/ #共享文件的目录
    +- team/  #团队人员目录
    |   +- cnfeat1/ #团队人员之一
    +- ...

````


## 操作

明白原理，操作就简单了。

举个例子，我就将本地协作的目录按如下安排了

````

Users/cnfeat/Documents/qrsync/
    +- share/ 
	+- team/  
    |   +- cnfeat/ 
    +- ...

````

## 短化命令行

继续用 [atext](http://www.jianshu.com/p/a15a6cb0f08d) 个性短化：

- `;cm`>>`cd /Users/cnfeat/Documents/qrsync/omc/team`
- `;pf`>>`python gen4idx.py ./ footer-7niu.html NULL`
- `;qo`>>`qrsync /Users/cnfeat/7niu/omcomc.json`
	+ 为共享空间设定专用的 `conf.json`文件
	+ 以此类推，不同的空间设定不同的`conf.json`文件
	+ 你就可以往不同的空间上传文件了
- `;po`>>`![](http://omcomc.qiniudn.com/team/cnfeat/)`

收工！

## 迭代

- 2015-12-07 17:01:15 共享目录十分容易覆盖
- 2015-11-30 23:51:33


## 参考链接

- [我们是如何使用7牛云储存的 ](http://blog.zhgdg.org/2013-08/usage7niu/)
- [PyCon2014China 志愿者协同手册 PyChina.org](http://pychina.org/imho/cooperate-guider.html)
- [cn.pycon.org/2014 官方网站内部维护仓库](https://gitcafe.com/lins05/MkDoc4PyCon/blob/master/README.md)



----

### **【六经皆我注脚】**

````

修行之道：
关注大师的言行，
跟随大师的举动，
和大师一并修行，
领会大师的意境，
成为真正的大师。

````

——[如何成为一名黑客 ](http://translations.readthedocs.org/en/latest/hacker_howto.html)



----

- 陈素封
- 公众号：cnfeat
- Blog：cnfeat.com














