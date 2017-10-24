---
layout: post
title: 如何搭建一个独立博客——简明 GitHub Pages与 jekyll 教程
date: 2014-05-11
categories: blog
tags: [Hexo,GitHub,独立博客]
description: 这是一篇很详尽的独立博客搭建教程，里面介绍了域名注册、DNS设置、GitHub 和 jekyll 设置等过程，这是我写得最长的一篇教程。我想将我搭建独立博客的过程在一篇文章中尽可能详细地写出来，希望能给后来者一个明确的指引，同时用这篇教程开篇，正式开始我的第八大洲之旅。
---



摘要：这是一篇很详尽的独立博客搭建教程，里面介绍了域名注册、DNS 设置、GitHub 和 Jekyll 设置等过程，这是我写得最长的一篇教程。我想将我搭建独立博客的过程在一篇文章中尽可能详细地写出来，希望能给后来者一个明确的指引，同时用这篇教程开篇，正式开始我的[第八大洲之旅](http://www.douban.com/note/523589521/)。

## 前言

作为一个技术小白，没有技术基础，看网上的教程也云里雾里，看程序员的教程相当不容易，稍微有些细节描述得不清楚自己就要绕弯路去找答案（善用搜索引擎），所以，在自己的博客搭建完成之后，我决定要将我搭建博客的过程全记录下来，以供后期和我一样的小白参考（是的，我坚信还有很多一样和我一样的人），我会尽可能详细的整理这个教程，其中的资料可能会摘录到其他人的教程，我会在后面列出了参考资料，感谢这些作者们。

为什么要开博客？可以看看我的这篇[《为什么你要写博客？》](http://zhuanlan.zhihu.com/cnfeat/19743861)

也可以看看这篇[《我的博客时代》](http://zhuanlan.zhihu.com/cnfeat/19743255)

以下以我的博客：www.cnfeat.com为例，教大家如何搭建一个独立博客。

## 为什么要搭建一个独立博客?

独立的才是自己的。

## 小白进入门槛

- 1、非常折腾，需要耐心；
- 2、也需要一定的学习能力和钻研精神；
- 3、懂一些网页基础知识，不懂也重要，参看第二和第三条；


## 为什么选择 [GitHub Pages](https://pages.github.com/) ？

很多人用 Wordpress，你为什么要用 GitHub Pages 来搭建？

- 1、GitHub Pages 有 300M 免费空间，资料自己管理，保存可靠；
- 2、学着用 GitHub，享受 GitHub 的便利，上面有很多大牛，眼界会开阔很多；
- 3、顺便看看 GitHub 工作原理，最好的团队协作流程；
- 4、GitHub 是趋势；
- 5、你不觉得一个文科生用 GitHub 很 Geek 吗？瞬间跻身技术界；

![> 01 GitHub Pages 图片](http://openmindclub.qiniudn.com/omt/BuildBlog01.jpg)

## GitHub Pages 是什么？

[GitHub Pages ](https://pages.github.com/)本用于介绍托管在 GitHub 的项目， 不过，由于他的空间免费稳定，用来做搭建一个博客再好不过了。

> GitHub Pages 可以被认为是用户编写的、托管在 GitHub 上的静态网页。

官方介绍可以看这个视频（需科学上网）

<div style="position:relative;height:0;padding-bottom:56.27%"><iframe src="https://www.youtube.com/embed/2MsN8gpT6jY?ecver=2" style="position:absolute;width:100%;height:100%;left:0" width="640" height="360" frameborder="0" allowfullscreen></iframe></div>

## 购买域名

只推荐上 [GoDaddy](https://www.GoDaddy.com/) 购买，安全，而且可以使用支付宝。

现在 GoDaddy 已经有[中文版](https://sg.godaddy.com/zh/)了，虽然国家显示是新加坡，但不影响使用。


![> 02 GoDaddy 主页界面](http://openmindclub.qiniudn.com/omt/BuildBlog02.jpg)

教程（截止至 2017 年 06 月 21 日）如下


**1、查你想要的域名**；


![> 03 GoDaddy cnfeat 2017 搜索](http://openmindclub.qiniudn.com/omt/BuildBlog03.jpg)


**2、查到适合的域名之后选择「添加到购物车」**；

![> 04 添加到购物车](http://openmindclub.qiniudn.com/omt/BuildBlog04.jpg)

**3、GoDaddy 其他域名收费服务，不要管，继续「进入购物车」**；

![> 05 进入购物车](http://openmindclub.qiniudn.com/omt/BuildBlog05.jpg)

后面的服务全部点击「不，谢谢」，免费的服务也不要用



**4、确认购买** 修改购买年限，默认是两年，可以修改成 1/2/3/5/10 年，随自己喜欢。现在 GoDaddy 上 .com 每年的默认费用是 7元/年。

但实际上，你看到我现在购买的是 第 1 年：​¥5.86/年
第 2 年后：​¥101.00/﻿年，GoDaddy 的域名价格时常有波动，以当时为准即可。

个人博客，建议购买 5 年限，等到你 5 年后觉得还有必要，再 10 年续下去。

![> 06 购物车界面](http://openmindclub.qiniudn.com/omt/BuildBlog06.jpg)



如果你不是土豪，可以上网搜 [GoDaddy 优惠码](https://www.google.com/search?q=GoDaddy%20%E7%9A%84%E4%BC%98%E6%83%A0%E7%A0%81)，一般优惠幅度是 20%~ 30% 不等


填完之后，五年的费用就从 415.56 会变成 333.95 元。

![> 07 价格变动图](http://openmindclub.qiniudn.com/omt/BuildBlog07.jpg)


**说明一下**：网上的优惠码优惠不一，你可以逐个尝试拿个最低价，这里就不一一测试了。

如图，我买了五年的费用就是 333.95 元，随后点击「前去付款」

![> 08 前去付款](http://openmindclub.qiniudn.com/omt/BuildBlog08.jpg)


**5、结算。**登录或注册界面，填完必要的信息之后，选择用支付宝结算。

![> 09 结算前必须注册个账户](http://openmindclub.qiniudn.com/omt/BuildBlog09.jpg)

注册后页面跳转到结算页面


![> 10 下订单](http://openmindclub.qiniudn.com/omt/BuildBlog010.jpg)


如果结算出现问题，可以[查看这个页面](https://www.dute.me/godaddy-alipay.html)。

**6、检查。**结算后，重新登录，去「我的账户 > 我的产品」，域名已经显示在你的账户了。



**7、补充一些注意事项：**

- 输入优惠码没有优惠或者优惠幅度较低，请清除浏览器 cookies 再尝试；
- 如果没有支付宝支付选项，有可能是使用的优惠码不支持支付宝，请重新清除浏览器 cookies 再尝试；
- 注册时用户填写信息时一定要输入正确的邮箱名字，否则修改十分麻烦。
- 买完域名之后一定要记得去自己的邮箱查看激活邮件，否则域名激活不了。

## 安装准备软件

依次下载安装。

- 1、[Node.js](http://nodejs.org/)
- 2、[Git](http://git-scm.com/)

## 怎么打开 Git ？


### Win 平台操作 

- 1、开始菜单 Git Bash
- 2、鼠标右键打开 Git Bash

![> 12 鼠标右键打开 Git Bash](http://openmindclub.qiniudn.com/omt/BuildBlog012.jpg)

### Mac 平台操作

安装 Git 之后可直接在 Terminal 操作


## 注册 GitHub

访问：http://www.GitHub.com/ 

注册你的 username 和邮箱，邮箱十分重要，GitHub 上很多通知都是通过邮箱发送。

注册过程比较简单，详细也可以看：

[一步步在 GitHub上创建博客主页 全系列](http://www.pchou.info/ssgithubPage/2013-01-03-build-github-blog-page-01.html) by pchou（推荐）

## 配置和使用 GitHub

以下教程主要参考 beiyuu 的[《使用GitHub Pages建独立博客》](http://beiyuu.com/github-pages)写成。

## 配置 SSH keys

我们如何让本地 git 项目与远程的 GitHub 建立联系呢？用 SSH keys。

### 检查 SSH keys的设置

首先我们需要检查你电脑上现有的 ssh key：

    $ cd ~/.ssh 检查本机的ssh密钥

如果提示：No such file or directory 说明你是第一次使用 git。

### 生成新的 SSH Key：

    $ ssh-keygen -t rsa -C "邮件地址@youremail.com"
    Generating public/private rsa key pair.
    Enter file in which to save the key (/Users/your_user_directory/.ssh/id_rsa):<回车就好>

* 注意 1: 此处的邮箱地址，你可以输入自己的邮箱地址；
* 注意2: 此处的「-C」的是大写的「C」

然后系统会要你输入密码：

    Enter passphrase (empty for no passphrase):<输入加密串>
    Enter same passphrase again:<再次输入加密串>

在回车中会提示你输入一个密码，这个密码会在你提交项目时使用，如果为空的话提交项目时则不用输入。这个设置是防止别人往你的项目里提交内容。

注意：输入密码的时候没有 * 字样的，你直接输入就可以了。

最后看到这样的界面，就成功设置ssh key了：

![> 13 终端设置成功](http://openmindclub.qiniudn.com/omt/BuildBlog013.jpg)

### 添加 SSH Key 到 GitHub

在本机设置 SSH Key 之后，需要添加到 GitHub上，以完成 SSH 链接的设置。

- 1、打开本地 id_rsa.pub 文件（ 参考地址 C:\Documents and Settings\Administrator\.ssh\id_rsa.pub）。此文件里面内容为刚才生成的密钥。如果看不到这个文件，你需要设置显示隐藏文件。准确的复制这个文件的内容，才能保证设置的成功。

- 2、登陆 GitHub 系统。点击右上角的 Account Settings--->SSH Public keys ---> add another public keys

- 3、把你本地生成的密钥复制到里面（ key 文本框中）， 点击 add key 就ok了

![> 14 添加 SSH Key 到 GitHub](http://openmindclub.qiniudn.com/omt/BuildBlog014.jpg)


### 测试

可以输入下面的命令，看看设置是否成功，git@GitHub.com 的部分不要修改：

    $ ssh -T git@GitHub.com

如果是下面的反馈：

    The authenticity of host 'GitHub.com (207.97.227.239)' can't be established.
    RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
    Are you sure you want to continue connecting (yes/no)?

不要紧张，输入 yes 就好，然后会看到：

    Hi cnfeat! You've successfully authenticated, but GitHub does not provide shell access.

### 设置用户信息

现在你已经可以通过 SSH 链接到 GitHub 了，还有一些个人信息需要完善的。

Git 会根据用户的名字和邮箱来记录提交。GitHub 也是用这些信息来做权限的处理，输入下面的代码进行个人信息的设置，把名称和邮箱替换成你自己的，名字必须是你的真名，而不是GitHub的昵称。

    $ git config --global user.name "cnfeat"//用户名
    $ git config --global user.email  "cnfeat@gmail.com"//填写自己的邮箱

### SSH Key 配置成功

本机已成功连接到 GitHub。

若有问题，请重新设置。常见错误请参考：

* [GitHub Help - Generating SSH Keys](http://help.GitHub.com/articles/generating-ssh-keys)
* [GitHub Help - Error Permission denied (publickey)](http://help.GitHub.com/articles/error-permission-denied-publickey)



## 将独立域名与 GitHub Pages 的空间绑定


### DNS 设置

用 DNSpod，快，免费，稳定。

注册[DNSpod](www.dnspod.cn)，添加域名，如下图设置。

![> 15 域名解析图](http://openmindclub.qiniudn.com/omt/BuildBlog015.jpg)


其中 A 的两条记录指向的ip地址是 GitHub Pages 的提供的 ip 

- 192.30.252.153
- 192.30.252.154

如博客不能登录，有可能是 GitHub 更改了空间服务的 ip 地址，记得及时到在[GitHub Pages](https://help.GitHub.com/articles/setting-up-a-custom-domain-with-GitHub-Pages)查看最新的 ip 即可

www 指定的记录是你在 GitHub 注册的仓库。

### 去 GoDaddy 修改 DNS 地址

更改 [GoDaddy](https://mya.godaddy.com) 的 Nameservers 为 DNSpod 的 NameServers。



1、点击你的账户，管理我的域名。

![> 16 管理我的域名](http://openmindclub.qiniudn.com/omt/BuildBlog016.jpg)


2、点击域名。

![> 17 管理 DNS](http://openmindclub.qiniudn.com/omt/BuildBlog017.jpg)



3、将 GoDaddy 的 Nameservers 更改成 f1g1ns1.dnspod.net 和 f1g1ns2.dnspod.net


![> 18 更改成 f1g1ns1.dnspod.net](http://openmindclub.qiniudn.com/omt/BuildBlog018.jpg)

如有不详可以看[DNSpod提供的官方帮助](https://support.dnspod.cn/Kb/showarticle/tsid/42/)

也可以看这里：[一步步在GitHub上创建博客主页(3)](http://pchou.info/web-build/2013/01/05/build-GitHub-blog-page-03.html)

## 使用 GitHub Pages 建立博客

与 GitHub 建立好链接之后，就可以方便的使用它提供的 Pages 服务，GitHub Pages 分两种，一种是你的 GitHub 用户名建立的 username.GitHub.io 这样的用户&组织页（站），另一种是依附项目的 Pages。

想建立个人博客是用的第一种，形如 cnfeat.GitHub.io 这样的可访问的站，每个用户名下面只能建立一个。



### Fork 已设置好的仓库

点击 [cnfeat/blog.io](https://GitHub.com/cnfeat/blog.io/tree/master)

点击右上角的 Fork 

![> 19 Fork blog.io](http://openmindclub.qiniudn.com/omt/BuildBlog019.jpg)

这样，你就得到我的博客仓库了。

你可以到

https://GitHub.com/你的用户名/blog.io

确认一下


然后将 blog.io 改成 你的 GitHub 用户名.GitHub.io

例如我的就改成 cnfeat.GitHub.io

改好之后，可以发现，'你的 GitHub 用户名.GitHub.io' 已经可以访问了。


P.S.更多博客模板请见 [GoodThingList/GoodJekyllBlogList.md at master · cnfeat/GoodThingList](https://github.com/cnfeat/GoodThingList/blob/master/GoodJekyllBlogList.md)


## 将独立域名与 GitHub Pages 的空间绑定

### GitHub Pages 的设置


去到你的 blog.io 仓库，点击 CNAME ,再点击右下角的 铅笔 编辑，将 cnfeat.com 改成你的域名


![> 20 修订 CNAME](http://openmindclub.qiniudn.com/omt/BuildBlog020.jpg)

这样，你再去你绑定的域名看看，估计已经导向到 '你的 GitHub 用户名.GitHub.io' 了。

## 搭建完成

至此，独立博客就算搭建完成，如需进步一完善请在参看以下文章或博客下留言。

## 如何更新博文


### 安装 GitHub desktop 

下载地址：[GitHub Desktop](https://desktop.GitHub.com/)


### 找你的仓库 Git 地址

去到你的博客仓库：https://GitHub.com/你的用户名/blog.io 

复制 clone 地址

例如我的就是

> https://github.com/cnfeat/blog.io.git


![> 22 复制 clone 地址 图](http://openmindclub.qiniudn.com/omt/BuildBlog022.jpg)


### clone 你仓库到本地

点击左上角的「+」号，选择 add，choose '你的 GitHub 用户名.GitHub.io' 文件夹。

如此，你的本地博客仓库就已经和 GitHub 的仓库同步起来了。


![> 21 clone 你仓库到本地](http://openmindclub.qiniudn.com/omt/BuildBlog021.jpg)


### 修订 _posts 文件夹中的 md 文件

blog.io 仓库已经自带两篇文章模板，按照模板修改即可。

![> 23 按照模板修改](http://openmindclub.qiniudn.com/omt/BuildBlog023.jpg)


### 推送文章更新

修订或新增完文章，再回到 GitHub desktop，点击同步更新即可。

![24 GitHub desktop 同步](http://openmindclub.qiniudn.com/omt/BuildBlog024.jpg)


## 更新个人博客信息配置

自己把 blog.io 中文件都点开看一遍，主要配置文件是 _config.yml ，推荐使用 sublime 打开。

修订清单如下，文档内有详细注释，可按注释逐个修订

* 博客名字及作者信息：_config.yml 
* 个人介绍页面：about.md
* 代表作页面：milestone.md
* 文章模板：blog.io/_posts/2015-03-02-how-to-write.md 


## 404页面

GitHub Pages有提供制作404页面的指引：[Custom 404 Pages](https://help.GitHub.com/articles/custom-404-Pages)。

直接在根目录下创建自己的 404.html 或者 404.md 就可以。但是自定义404页面仅对绑定顶级域名的项目才起作用。

推荐使用[腾讯公益404](http://www.qq.com/404)。

## 图床

推荐使用七牛（10G空间，免费）。



## 参考资料：

* [1][一步步在GitHub上创建博客主页 全系列](http://pchou.info/web-build/2013/01/03/build-GitHub-blog-page-01.html) by pchou（推荐）
* [2]网站优化：[一步步在GitHub上创建博客主页(6)](http://pchou.info/web-build/2013/01/09/build-GitHub-blog-page-06.html) by pchou （推荐）
* [3][搭建一个免费的，无限流量的Blog----GitHub Pages和Jekyll入门](http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html) by 阮一峰（推荐）
* [4][hexo系列教程：（二）搭建hexo博客](http://zipperary.com/2013/05/28/hexo-guide-2/) by zippera（推荐）
* [5][hexo系列教程：（三）hexo博客的配置、使用](http://zipperary.com/2013/05/29/hexo-guide-3/)by zippera（推荐）
* [6][hexo系列教程：（四）hexo博客的优化技巧](http://zipperary.com/2013/05/30/hexo-guide-4/) by zippera（推荐）
* [7][hexo你的博客](http://ibruce.info/2013/11/22/hexo-your-blog/) by ibruce（推荐） 
* [8][Pacman主题介绍](http://yangjian.me/workspace/introducing-pacman-theme/) by yangjian（推荐）
* [9][使用hexo搭建博客](http://yangjian.me/workspace/building-blog-with-hexo/) by yangjian（推荐）
* [10][折腾了个Pacman主题](http://wuchong.me/blog/2014/01/24/change-to-pacman/) by wuchong（推荐）
* [11]hexo官方写作教程[「Writing」](http://hexo.io/docs/writing.html)
* [12]知乎上的教程：[如何搭建个人独立博客？](http://www.zhihu.com/question/20463581)
* [13]在GitHub Pages设置独立域名的官方教程：[[Setting up a custom domain with GitHub Pages]](https://help.GitHub.com/articles/setting-up-a-custom-domain-with-GitHub-Pages)
* [14][使用GitHub Pages建独立博客](http://beiyuu.com/GitHub-Pages/) by beiyuu
* [15][git/GitHub初级运用自如](http://www.cnblogs.com/fnng/archive/2012/01/07/2315685.html) by 虫师
* [16][hexo搭建静态博客以及优化](http://code.wileam.com/build-a-hexo-blog-and-optimize/) by Joanna Wu
* [17][使用Hexo搭建个人博客](http://c4fun.cn/blog/2014/03/03/use-hexo-blog/) by c4fun
* [18][GitHub Pages与Hexo建个人博客流程](http://kescoode.com/2013/11/17/GitHub-page-and-hexo-guide/) by Kesco
* [19][Git push时重复输入用户名密码的问题](http://zipperary.com/2013/05/26/ssh-errors-with-GitHub/) by zippera
* [20][hexo文件结构及网站优化](http://www.solarck.com/) by kevin chen


## 相关链接

* [1][GitHub Pages主页](https://Pages.GitHub.com/)
* [2][GoDaddy域名商](http://www.GoDaddy.com/)
* [3][DNSPOD](www.dnspod.cn)
* [4][Hexo官方主页](http://hexo.io/)
* [5][GotGitHub：GitHub介绍](http://www.worldhello.net/gotGitHub/index.html)（推荐）
* [5][图标制作网站：faviconer](http://www.faviconer.com/)
* [6]本地测试页[localhost:4000](http://localhost:4000/)


## [关于我](http://cnfeat.com/about/)

这里有我的个人简介：[关于我](http://cnfeat.com/about/)

如果你想看到我最新的文章，可以关注我的微信公众号「cnfeat」。


### ChangeLog

- 2017-06-21 修订盘古之白，文字说明，修复失效图片
- 2015-11-10 01:07:55
- 2015-11-06 01:21:21





