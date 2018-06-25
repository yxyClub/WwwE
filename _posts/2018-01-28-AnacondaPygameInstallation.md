---
layout: post
title: Anaconda安装和Pygame安装
date: 2018-01-28
categories: blog
tags: [Anaconda,安装,pygame,实验室]
description: 我用的是Mac系统，直接就安装了，安装好之后，所有的库其实都是在Anaconda系统里的，也就是连同我新安装的Python3.6什么的都在Anaconda的控制之下。以后安装插件包直接从Anaconda下就可以了。但是有的时候不是很顺利。
---

## Anaconda安装比较顺利

我用的是Mac系统，直接就安装了，安装好之后，所有的库其实都是在Anaconda系统里的，也就是连同我新安装的Python3.6什么的都在Anaconda的控制之下。以后安装插件包直接从Anaconda下就可以了。但是有的时候不是很顺利。

## Terminal终端直接调用Python

这里有一个坑，就是非计算机专业的初学者不知道怎么直接在 终端里运行 yourscriptname.py程序。这里我遇到的是，终端里直接敲python yourscriptname.py是无法运行的，你必须要打开那个存放了你的py文件的文件夹才能够运行哦。这里要用到命令：pwd 用来显示你现在所在的文件夹的位置，如果你在根目录文件夹下，你就需要挨个使用cd 「AAA」（这是个文件夹的名字）的打开子文件夹，可以是逐级打开，到了这个文件夹之后，例如运行"python ex1.py"那么就可以运行了。

## Pygame安装遇到了问题

在Anaconda的Navigater里安装pygame的python3.6以上版本的时候报错说是不兼容。我以前的机器里已经安装过python3.4和Python2.7，也装过了Pygame的包，但是在新安装的Anaconda里面，并不能成功安装，在Anaconda的列表里搜索不到，根据网站上的提示如下：
```
itifadeMacBook-Pro:LP3THW yyy$ conda install -c cogsci pygame
Solving environment: failed

UnsatisfiableError: The following specifications were found to be in conflict:
  - pygame
  - xlwings
Use "conda info <package>" to see the dependencies for each package.
```
我到了Pygame的官方网站上搜索告诉我这样做：这样做的结果是，我安装成功了，也运行成功了，但是报了个错误。
```
itifadeMacBook-Pro:LP3THW yyy$ python3 -m pip install pygame --user
The directory '/Users/yyy/Library/Caches/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
The directory '/Users/yyy/Library/Caches/pip' or its parent directory is not owned by the current user and caching wheels has been disabled. check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
Collecting pygame
  Downloading pygame-1.9.3-cp36-cp36m-macosx_10_9_intel.whl (4.8MB)
    100% |████████████████████████████████| 4.8MB 47kB/s
Installing collected packages: pygame
Successfully installed pygame-1.9.3
itifadeMacBook-Pro:LP3THW yyy$ python ex11old.py
python ex11old.py
```
## ChangeLog

- 本文件是2018-01-28 创建，但是pygame的问题依然没有解决。
- 20180625调整了格式。
