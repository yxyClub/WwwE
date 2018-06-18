---
layout: post
title: Pyinstaller打包Python脚本递归错误等问题的解决方案
date: 2018-06-14
categories: blog
tags: [Pyinstaller,递归错误,MaximumRecursionEepthExceeded]
description: Pyinstaller打包成独立软件的时候“递归深度报错”，报错 “RecursionError: maximum recursion depth exceeded”解决方案。
---

## 概述

我用 python 编写了一个小程序，用于解决以“解一元三次方程”为核心的问题。具体是在已经知道了一元三次方程的各个阶的系数值以及 y 值，求 x 值。写成的代码可以在 python 环境中运行，但是无法在没有安装 Python 解释器的电脑上运行。因此，我需要将py 文件打包成可执行文件（exe），以供没有安装 python 解释器的同事们来用。但是在生成 exe 的过程中遇到了若干问题，通过检索和综合别人的解决方案，最终解决了这些问题。

## 程序编制和运行环境

我有两台电脑三套系统， MACpro-64位（另装了 win7的32位虚拟系统）和 ThinkPad 的Win7-64位，分别装上了 Anaconda 集成开发环境。

## 报错内容以及解决方法

###  递归深度报错

> 使用 Pyinstaller打包成独立软件的时候“递归深度报错”，报错“RecursionError: maximum recursion depth exceeded”

### 解决思路：

首先，看到递归深度错误，我首先想到的是代码中可能存在 Python 系统能解决但是生成 exe 无法解决的问题，所以才出现递归错误。我上网搜索关键词“Python + maximum recursion depth exceeded”，stackoverflow.com上点赞较多的人所说的解决方案是增加递归深度设定（python 默认的递归深度是1000？），[具体的方法](https://stackoverflow.com/questions/8177073/python-maximum-recursion-depth-exceeded)是:

    import sys
    sys.setrecursionlimit(10000) # 10000 is an example, try with different values

然而，没什么用。我甚至将这个递归深度增加到10亿次，到达了程序的设计边界，依然不行。

难道是代码本身错误？但是 python 自己却认呢？Why 啊？
抱着谨慎的态度，我以此检查数据类型，

>
    for i in range (0,8):
        d = solveset(TA0 + TA1*x + TA2*(x**2) +TA3*(x**3) - 1/(273.15+T[i]), x) # 核心计算公式。使用T[i]从T这个数组中按照索引取出数据。
        d1,d2,d3 = d # 将数组d进行切片。
        d1=float(d1)# 新增加20180612,将sympy 内嵌的float类型装换位通用的 float 类型。
        N = 2.718281825**d1 #转换出N值
        print (round(N))# "N值为："

### 终极解决方案

降级 Python3.6.4→Python3.5.5）+Pyinstaller3.3.1。
使用 Mac-Win7-32内装的Anaconda集成系统的Environments中，另建立一个环境PY35, 其中出了安装了 Python3.5.5之外，还单独安装了 sympy（安装具体包的方法请到 Anaconda官方网站上查看，使用官方命令进行安装）。通过降级的 Python，在Terminal中打开程序所在的文件夹，使用Pyinstaller yourscriptname.py的方法，进行打包程序，在 dish 文件夹下面有一个单独的文件夹叫yourscriptname，里面有一大堆文件，其中有一个文件是.exe文件，其他文件都是支持性的文件，双击 exe 文件就可以在window7下运行了。我这样打包出来的程序没有问题，但是网上另外推荐里一种打包成一个文件而不是一个文件包的方法，还是使用'Pyinstaller -F yourscriptname.py'的方法制作成了一个 单独exe 文件，如果希望让图标 ICO 好看的话，就在这个 py 文件下，存放一个myico.ico文件，在打包的时候输入'Pyinstaller -F -i myico.ico yourscriptname.py',然后就生成了独立的带有漂亮的图标的一个独立程序了。但是我发现这样的程序在安装了 python的程序里运行没有问题，但是在没有安装 python 的电脑里会报错“无法定位程序输入点 GetFinalPathNameByHandleW 于动态链接库 KERNEL32.dll上”。

#### 参考来源：
1.[关于python 降级解决递归错误的方法](https://stackoverflow.com/questions/49468674/pyinstaller-development-version-recursion-depth-reached)

### 无法定位程序输入点报错

接上面话题，生成了独立的 exe 程序之后，在其他电脑上运行，报错“无法定位程序输入点 GetFinalPathNameByHandleW 于动态链接库 KERNEL32.dll上”。也就是说，我生成的这个独立的 exe 文件可能并没有打包完全，里面缺少 dll 控件。如果仅仅是为了用的话，dish 文件夹下由pyinstaller系统生成了‘单独的文件夹yourscriptname中 exe’可以直接用了。如果非要生成一个独立的 exe 文件的话，我想这个是库中的文件包打包不全造成了，记得网上有一个说法是继续加一个参数-p（path）……

{  }由于时间有限，暂时不深究，此处刨坑，等来日再解决。

## LOG

20180614 下午念起
20180615 上午用了一小时左右敲了出来。
