---
layout: post
title: Python安装环境的最佳实践探索
date: 2018-12-14
categories: blog
tags: 安装环境,python,最佳实践,Anaconda,大坑
description: 蟒营ch00环境折腾记录。
---





# Python安装环境的最佳实践探索

## 写在前面的话

我的Mac电脑里预装了 py2.7，后来又在网上看到他们指导说 Anaconda 不错，是一个集成了 Python 的安装环境的大包裹，但是经过我的实践，以及在怼圈被大妈怼了，广鹤介绍了俊宇的文档，发现这个 Anaconda 貌似不是他们说的那样好，也是大坑一堆堆，于是萌生了一个想法：一定要把 Python 的安装环境的逻辑搞清楚，并且安装一套合适的 Python 版本控制虚拟环境。

## 现状分析

仔细的研究的一下系统中的 python 环境，发现我系统里可能至少安装了 5个 python：

- /Applications/anaconda3/lib/python3.6（20181225中午删除）

- /Applications/anaconda3/envs/py35/lib/python3.5（20181225中午删除）

- /Applications/anaconda3/envs/py27/lib/python2.7（20181225中午删除）

- /Applications/Python 3.6（20181224中午删除）

- /Applications/Python 2.7（20181226中午删除）

- /anaconda3/pkgs/python-3.7.0-hc167b69_0/bin/python3.7（升级了 Anaconda 之后新的 py37存在这，20181225已经删除）

  新发现我的目录其实在下面这个路径下面还有两个版本的 python-py2.7和 py3.6

  ```
  /Library/Frameworks/Python.framework/Versions/
  ```

  也就是/Applications/Python 2.7这个目录其实也是多余的，不应在这里的。





![root 环境-238包](https://upload-images.jianshu.io/upload_images/3785456-087d78efc02d6a3b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)





![Anaconda 下的 py27和py35包](https://upload-images.jianshu.io/upload_images/3785456-e783bb2320d5ea2a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

从终端中直接运行 python 出来的环境是 py366：

![终端中直接运行 python 出来的环境](https://upload-images.jianshu.io/upload_images/3785456-f062dbbaba5cb00b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

输入exit跳出 python 环境，输入 env命令，显示如下内容

```
xiaoyanMBP:~ yyy$ env
TERM_PROGRAM=Apple_Terminal
SHELL=/bin/bash
TERM=xterm-256color
TMPDIR=/var/folders/qp/wlzlphc57vgcg0d9h9bwkb780000gp/T/
Apple_PubSub_Socket_Render=/private/tmp/com.apple.launchd.j6P3zrH01S/Render
TERM_PROGRAM_VERSION=421.1
TERM_SESSION_ID=48E00D50-F016-42D1-81A9-49C44AA01C94
USER=yyy
SSH_AUTH_SOCK=/private/tmp/com.apple.launchd.fLQX9J2eyt/Listeners
PATH=/Applications/anaconda3/bin:/Library/Frameworks/Python.framework/Versions/2.7/bin:/Library/Frameworks/Python.framework/Versions/3.6/bin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin
PWD=/Users/yyy
LANG=zh_CN.UTF-8
XPC_FLAGS=0x0
XPC_SERVICE_NAME=0
SHLVL=1
HOME=/Users/yyy
LOGNAME=yyy
_=/usr/bin/env

```

上面的路径内容看起来好复杂，貌似看不清楚这到底是 py27还是 py36，如果 py36是那个 py36。

另用命令which python，查到我现在用到的 python 是哪个python

```
xiaoyanMBP:~ yyy$ which python
/Applications/anaconda3/bin/python
```

通过映射py 软连接，发现真实的路径是：/Applications/anaconda3/bin/python3.6

结论是，我在终端里 bash 调用的是anaconda3下的python3.6

另，在 Anaconda 里再次打开 Aconda 自带的root 下终端：

```
Last login: Mon Dec 24 13:26:07 on ttys001
/Users/yyy/.anaconda/navigator/a.tool ; exit;
xiaoyanMBP:~ yyy$ /Users/yyy/.anaconda/navigator/a.tool ; exit;
(base) bash-3.2$ which python
/Applications/anaconda3/bin/python
(base) bash-3.2$ 
```

另，在 Anaconda 里再次打开它带的 py35的终端：

```
Last login: Mon Dec 24 13:48:23 on ttys002
/Users/yyy/.anaconda/navigator/a.tool ; exit;
xiaoyanMBP:~ yyy$ /Users/yyy/.anaconda/navigator/a.tool ; exit;
(py35) bash-3.2$ which python
/Applications/anaconda3/envs/py35/bin/python
(py35) bash-3.2$ 
```

同理，Anaconda 的 py27

```
(py27) bash-3.2$ which python
/Applications/anaconda3/envs/py27/bin/python
(py27) bash-3.2$ 
```

## 试图基于 Anaconda3建立一个环境

在终端 里运行代码 xiaoyanMBP:~ yyy$ pip list

列出了如下代码：

```
Package                            Version          
---------------------------------- -----------------
alabaster                          0.7.10           
altgraph                           0.15             
anaconda-client                    1.6.14           
anaconda-navigator                 1.9.2            
anaconda-project                   0.8.2    
……略……
xlwings                            0.11.4           
xlwt                               1.2.0            
zict                               0.1.3            
The directory '/Users/yyy/Library/Caches/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
You are using pip version 10.0.1, however version 18.1 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.
xiaoyanMBP:~ yyy$ pip install --upgrade pip
The directory '/Users/yyy/Library/Caches/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
The directory '/Users/yyy/Library/Caches/pip' or its parent directory is not owned by the current user and caching wheels has been disabled. check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
Collecting pip
Could not install packages due to an EnvironmentError: [Errno 13] Permission denied: '/Users/yyy/Library/Caches/pip/wheels/63/5e/1d/2a8a6ac468fc01704870fdf67dac2c1b5ede9a201493057102'
Consider using the `--user` option or check the permissions.

You are using pip version 10.0.1, however version 18.1 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.
```

上面的意思是说，你没有 /Users/yyy/Library/Caches/pip/http这个目录或者他的父目录的权限，如果你想要继续的话就要使用sudo -H  这样的形式（但是大妈说了用 sudo 会可能带来莫名其妙的系统级损伤），py提示又说了：你这个路径由于是环境错误还是无法安装，建议你使用‘’‘--user’选项来查查你的权限。。另外还告诉你，你的 pip 版本是10.0.1的，而现在最新的版本是18.1，你使用“pip install --upgrade pip”来升级一下吧。

然而……执行后，又提示如下：

```
(base) bash-3.2$ pip install --upgrade pip
The directory '/Users/yyy/Library/Caches/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
The directory '/Users/yyy/Library/Caches/pip' or its parent directory is not owned by the current user and caching wheels has been disabled. check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
Collecting pip
Could not install packages due to an EnvironmentError: [Errno 13] Permission denied: '/Users/yyy/Library/Caches/pip/wheels/63/5e/1d/2a8a6ac468fc01704870fdf67dac2c1b5ede9a201493057102'
Consider using the `--user` option or check the permissions.

You are using pip version 10.0.1, however version 18.1 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.
```

大概的意思还是告诉你，你对于上面这个目录是没有权限的，你需要使用 sudo 加-H 这个 flag 来进行升级……玩完，又转回来了。

#### 关于 sudo -H 的使用：

大概的意思是，你用直接使用命令的话，你的权限不够，但是你使用sudo -H 这个命令后面再加上你的命令就可以了（至于为什么，我还是不明白……怎么就说我权限不够了呢？）另外[有个作者写了一个方法](http://blog.sina.com.cn/s/blog_a046022d0102w2ux.html)，我没敢试，将来想明白了这里的这些命令的意思再说吧（主要是无法理解sudo chown root/）。

> 他大概的意思是说：使用命令：sudo pip install numpy时，可能遇到：
>
> The directory '/Users/huangqizhi/Library/Caches/pip' ，安装权限不够。解释里说得很清楚，是pip目录的属主不是sudo的root用户。如果必须用sudo pip，更改pip目录属主即可：sudo chown root /Users/huangqizhi/Library/Caches/pip

```
Last login: Mon Dec 24 17:16:52 on ttys003
/Users/yyy/.anaconda/navigator/a.tool ; exit;
xiaoyanMBP:~ yyy$ /Users/yyy/.anaconda/navigator/a.tool ; exit;
(base) bash-3.2$ pip list
Package                            Version          
---------------------------------- -----------------
alabaster                          0.7.10           
altgraph                           0.15             
……
xlwings                            0.11.4           
xlwt                               1.2.0            
zict                               0.1.3            
The directory '/Users/yyy/Library/Caches/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
(base) bash-3.2$ sudo -H pip list
Password:
Package                            Version          
---------------------------------- -----------------
alabaster                          0.7.10  
```

#### 关于 Anaconda 的升级

另外，打开 Anaconda，它就不断的提示你，告诉你 Anaconda 现在可以升级了，强烈的建议你升级到Navigater1.9.6，然后呢，我点了同意，它说他后台会自动升级，然而啥都没有看见，所以我打开 Anaconda 后它依然是原来的版本。一气之下，重新安装 Anaconda 的最新版本，当然是到[Anaconda镜像地址1：](https://mirrors.ustc.edu.cn/anaconda/archive/)下载最新版本。

按照推荐路径安装了最新版本的 Anaconda 之后，竟然又出现了一个 Python，这回是3.7版本（多了个 anaconda3这个环境）的。

![安装了新 Anaconda 之后](https://upload-images.jianshu.io/upload_images/3785456-3ee76353e6f65805.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



竟然出现了个 py37（root），而且这个程序包埋的竟然这么深，为啥在这么深一个目录里，而不是原来的那个目录--anaconda3/lib里了？

![难道root 中的 py37的新路径在这里吗](https://upload-images.jianshu.io/upload_images/3785456-167d8863e57d5f7f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

注意：

这次这个 py 版本是3.7，它的标识是 base（root），它的路径是/anaconda3/bin/python，等等，这个路径竟然不是在原来的 Application 底下，而是和 Application 同一级别的一个文件夹下面了。

![image.png](https://upload-images.jianshu.io/upload_images/3785456-bebeada205cfa673.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

注意，上面这个图上可以看出在新的 base（root）下面直接关联的是 anaconda3程序文件夹，他的真实路径是：

```
/anaconda3/pkgs/python-3.7.0-hc167b69_0/bin/python3.7
```

可能是我安装的时候没有选择我这个当前用户，而是选择了默认的所有用户，所以也就是说所有的账户都可以访问这个 anaconda3。好吧，现在看来即使是不在同一个文件夹下，这个 anaconda3也可以访问所有的py 包。

想要卸载这个新装的 Anaconda 吧，按照[官方的方案](http://docs.continuum.io/anaconda/install/uninstall/)，也是很慢，感觉大坑又在等着我……

![image.png](https://upload-images.jianshu.io/upload_images/3785456-2ce310acbc36407f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 关于 anaconda 的删除

关于[官方的文档](http://docs.continuum.io/anaconda/install/uninstall/),执行之后，并在根目录下的anaconda3这个目录依然没有删除。

![image.png](https://upload-images.jianshu.io/upload_images/3785456-227d7e0275c3d070.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

然而，运行 python 的时候，它还在……

![image.png](https://upload-images.jianshu.io/upload_images/3785456-16fb44551555d120.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 咬牙全部卸载 Anaconda

根据大妈在 Issue 里的怼，说我原来的以来 Anaconda 的思路是完全反的，于是我咬牙一口气卸载了2个 Anaconda，依据的官方的方法见[这里](http://docs.continuum.io/anaconda/install/uninstall/),前面的命令基本看懂了，但是“rm -rf ~/anaconda3”这个命令，我输入进去，没有得到任何反馈，我就找到这个文件夹然后直接右键清除到了回收站里了。最后，让我[再确认路径这一步](http://docs.continuum.io/anaconda/install/uninstall/#removing-anaconda-path-from-bash-profile)，我没看懂，我也不知道该怎么做，跳过了。同样的手法删除了两个 Anaconda。最后我进入终端之后，输入python，然后就出现了最原始的状态，py27

```
xiaoyanMBP:~ yyy$ which python
/Library/Frameworks/Python.framework/Versions/2.7/bin/python
xiaoyanMBP:~ yyy$ python
Python 2.7.14 (v2.7.14:84471935ed, Sep 16 2017, 12:01:12) 
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> 

```



#### 少干了点啥

> 我目前还不知道自己的 Python 环境到底是啥样的。

发现了广鹤写的“将 .bash_profile 文件中的内容删除.”，认识到“ .bash_profile”里应该是有什么东西，于是搜索了(打开.bash_profile 文件的方法)：

```
在OSX下,我们用如下命令打开环境变量配置文件:

open ~/.bash_profile

最后,别忘了编译下：
source .bash_profile
```

通过上面这种打开方式，我发现我的.bash_profile配置如下：

```
# Setting PATH for Python 3.6
# The original version is saved in .bash_profile.pysave
PATH="/Library/Frameworks/Python.framework/Versions/3.6/bin:${PATH}"
export PATH

# Setting PATH for Python 2.7
# The original version is saved in .bash_profile.pysave
PATH="/Library/Frameworks/Python.framework/Versions/2.7/bin:${PATH}"
export PATH

# added by Anaconda3 5.0.1 installer
export PATH="/Applications/anaconda3/bin:$PATH"

# added by Anaconda3 5.3.1 installer
# >>> conda init >>>
# !! Contents within this block are managed by 'conda init' !!
__conda_setup="$(CONDA_REPORT_ERRORS=false '/anaconda3/bin/conda' shell.bash hook 2> /dev/null)"
if [ $? -eq 0 ]; then
    \eval "$__conda_setup"
else
    if [ -f "/anaconda3/etc/profile.d/conda.sh" ]; then
        . "/anaconda3/etc/profile.d/conda.sh"
        CONDA_CHANGEPS1=false conda activate base
    else
        \export PATH="/anaconda3/bin:$PATH"
    fi
fi
unset __conda_setup
# <<< conda init <<<
```

然后，这说明了什么呢》》》意思是说 我在这里文件里配置了一堆 python 路径，怎么办呢？（……20181226早上）。

## 进一步检查自己电脑中的 python版本

```
xiaoyanMBP:~ yyy$ python3
Python 3.6.1 (v3.6.1:69c0db5050, Mar 21 2017, 01:21:04) 
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> print
<built-in function print>
>>> print(2+3)
5
>>> exit()
xiaoyanMBP:~ yyy$ which python
/Library/Frameworks/Python.framework/Versions/2.7/bin/python
xiaoyanMBP:~ yyy$ which python3
/Library/Frameworks/Python.framework/Versions/3.6/bin/python3
```

看到了我电脑里除了 python（2.7）之外，还装了 python3（py36），地址是在下面这个路径下面

```
/Library/Frameworks/Python.framework/Versions/
```

也就是说不在我的用户 yyy（username）下面，而是在整个硬盘的根目录的Library文件夹下。

![image.png](https://upload-images.jianshu.io/upload_images/3785456-19bd12be950566ab.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这么说来，我还是没有删除干净，继续在 Application 中把 py37右键删除到垃圾桶里。



## 一个最小行动

- 在Applications里将/Applications/Python 3.6卸载掉。



## Python官网上介绍的虚拟环境安装方法

在安装 Anaconda3最新版本的同时，我研究一下官网推荐的安装环境和方法。

更多细节参见[venv地址](https://docs.python.org/3.7/tutorial/venv.html)，说：

> 必要性：
>
> Python 应用程序通常使用标准库中没有的包和模块。 应用程序有时需要一个特定版本的库，因为应用程序可能需要修复某个特定的错误，或者使用库接口的过时版本编写应用程序。这意味着一个 Python 安装可能无法满足每个应用程序的需求。 如果应用程序 a 需要某个特定模块的1.0版本，而应用程序 b 需要2.0版本，那么这两个要求之间存在冲突，安装1.0或2.0版本都会导致一个应用程序无法运行。这个问题的解决方案是创建一个虚拟环境，这是一个自包含的目录树，其中包含针对特定版本 Python 的 Python 安装，以及一些其他包。
>
> 不同的应用程序可以使用不同的虚拟环境。 为了解决早期的需求冲突示例，应用程序 a 可以拥有自己的安装了版本1.0的虚拟环境，而应用程序 b 拥有另一个安装了版本2.0的虚拟环境。 如果应用程序 b 需要将库升级到3.0版本，这不会影响应用程序 a 的环境。
>
> 安装方法—创建虚拟环境：
>
> 用于创建和管理虚拟环境的模块称为 venv。 Venv 通常会安装您现有的最新版本的 Python。 如果您的系统上有多个 Python 版本，可以通过运行 python3或任何您想要的版本来选择特定的 Python 版本。
>
> 要创建一个虚拟环境，选择一个你想要放置它的目录，并运行 venv 模块作为一个脚本和目录路径:
>
> ```
> python3 -m venv tutorial-env
> ```
>
> 这将创建不存在的 tutorial-env 目录，并在其中创建包含 Python 解释器副本、标准库和各种支持文件的目录。
>
> 一旦你创建了一个虚拟环境，你可以激活它。
>
> 在 Windows 上，运行:
>
> ```
> tutorial-env\Scripts\activate.bat
> ```
>
> 在 Mac 上，运行：
>
> ```
> source tutorial-env/bin/activate
> ```
>
> (此脚本是为 bash shell 编写的。 如果您使用 csh 或 fish shell，则应该使用 alternate activate.csh 和 activate.fish 脚本。)
>
> 激活虚拟环境将改变 shell 的提示，以显示您正在使用的虚拟环境，并修改环境，以便运行 Python 将获得特定版本和安装的 Python。 例如:
>
> ```
> $ source ~/envs/tutorial-env/bin/activate
> (tutorial-env) $ python
> Python 3.5.1 (default, May  6 2016, 10:59:36)
>   ...
> >>> import sys
> >>> sys.path
> ['', '/usr/local/lib/python35.zip', ...,
> '~/envs/tutorial-env/lib/python3.5/site-packages']
> >>>
> ```
>
>

根据上面的教程，我试图运行下面的代码：

- “python3 -m venv pyenv”
- “source pyenv/bin/activate”
- “source ~/envs/pyenv/bin/activate”

然而，报错了：

```
xiaoyanMBP:~ yyy$ python3 -m venv pyenv
Error: Command '['/Users/yyy/pyenv/bin/python3', '-Im', 'ensurepip', '--upgrade', '--default-pip']' returned non-zero exit status 1.
xiaoyanMBP:~ yyy$ 
```

将 python3命令换为python 依然不行。这个报了一个错误——“返回了一个非零的状态1”——然而这是什么意思呢？在文章“[zengrongBlog:Python 虚拟环境](https://blog.zengrong.net/post/2167.html)”中作者说：

>Python 从3.3 版本开始，自带了一个虚拟环境 [venv](https://docs.python.org/3/library/venv.html)，在 [PEP-405](http://legacy.python.org/dev/peps/pep-0405/) 中可以看到它的详细介绍。它的很多操作都和 virtualenv 类似。因为是从 3.3 版本开始自带的，这个工具也仅仅支持 python 3.3 和以后版本。所以，要在 python2 上使用虚拟环境，依然要利用 [virtualenv](http://www.virtualenv.org/) 。在 *nix 系统上，可以直接执行 `pyvenv /path/to/new/virtual/enviorment` 来创建一个虚拟环境，在 Windows 系统上，则可以使用 `python -m venv myenv` 来创建。

那么，就是说，如果按照官方的文档安装venv的话，也是无法支持2.x 版本的py 了，那么是这样吗？假设是这样的话，是否有更好的方案呢？--->看看俊宇是怎么装的？



## 俊宇的方案

[俊宇：Python环境出坑记](http://blog.junyu.io/posts/0707-python-env-config.html)中，作者最终是采用了[pyenv](https://github.com/pyenv/pyenv)，没看错，不是官方推荐的那个 venv。

他写到：

>  配置需要的环境:
>
> - pyenv：参考官方文档[pyenv](https://github.com/pyenv/pyenv)，注意环境变量的配置和启动后的环境检查。
> - ipython 安装：按照官方[文档](https://ipython.org/install.html)安装，令人发指的简单。
> - jupyter notebook 安装：按照官方[文档](http://jupyter.org/install.html)的介绍，同样是令人发指的简单。
>
> 注意，以上环境安装之前，先确认处于的python 环境是你需要的python 环境。

我看这个需要较高的学习曲线，那么，暂时先放放吧，还是再研究研究那个 Anaconda3。

## 常见命令备案

- “ pip list”或者“sudo -H pip list”命令可以获取当前 python 已经安装的包有哪些。
- “which python”：这个命令可以在终端里展示你这个终端调用的是哪个版本的 python（安装路径在哪里）。



## 有用信息

- [∞h[ASK]如何判定当前资料/图书靠谱度?](https://github.com/DebugUself/du4proto/issues/48)



## 参考资料

- [python官方帮助文档](https://docs.python.org/3/)
- [俊宇：Python环境出坑记](http://blog.junyu.io/posts/0707-python-env-config.html)
- [zengrongBlog:Python 虚拟环境](https://blog.zengrong.net/post/2167.html)
- [4d[BC]究竟 Python 都有什么运行姿势? 何时应用哪种?](https://github.com/DebugUself/du4proto/issues/227)
- [24h[TASK][WIKI]请指正该 wiki: python 环境管理之 pyenv](https://github.com/DebugUself/du4proto/issues/204)



## TimeLog

- 2018-12-24 小焱创建。
- 2018-12-25 一顿折腾大约5小时。
- 2018-12-26 发现了他们所说的“.bash_profile”内容，但是怎么删除和处置，还是不清楚。