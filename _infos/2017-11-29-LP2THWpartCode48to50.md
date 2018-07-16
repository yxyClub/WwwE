---
layout: post
title: 《笨办法学Python》记录-part6（习题48～50）
date: 2017-11-09
categories: blog
tags: [Python,笨办法学Python,LearPython2TheHardWay,LP2THW]
description: 立个Flag开始学Python。
---

> test

## 第48题

### CODE

```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第48题 更复杂的用户输入
# 以下是代码部分
你的游戏可能一路跑得很爽，不过你处理用户输入的方式肯定让你不胜其烦了。 每一个房间都需要一套自己的语句，而且只有用户完全输入正确后才能执行。你 需要一个设备，它可以允许用户以各种方式输入语汇。例如下面的机种表述都应 该被支持才对:
  open door
  open the door
  go THROUGH the door
  punch bear
  Punch The Bear in the FACE
也就是说，如果用户的输入和常用英语很接近也应该是可以的，而你的游戏要识 别出它们的意思。为了达到这个目的，我们将写一个模组专门做这件事情。这个 模组里边会有若干个类，它们互相配合，接受用户输入，并且将用户输入转换成 你的游戏可以识别的命令。
英语的简单格式是这个样子的:
  单词由空格隔开。
  句子由单词组成。
  语法控制句子的含义。
所以最好的开始方式是先搞定如何得到用户输入的词汇，并且判断出它们是什么。

# 我们的游戏语汇
我在游戏里创建了下面这些语汇:
  表示方向: north, south, east, west, down, up, left, right, back.
  动词: go, stop, kill, eat.
  修饰词: the, in, of, from, at, it
  名词: door, bear, princess, cabinet.
  数词: 由 0-9 构成的数字。
说到名词，我们会碰到一个小问题，那就是不一样的房间会用到不一样的一组名词，不过让我们先挑一小组出来写程序，以后再做改进把。

## 如何断句

我们已经有了词汇表，为了分析句子的意思，接下来我们需要找到一个断句的方法。我们对于句子的定义是“空格隔开的单词”，所以只要这样就可以了:

stuff = raw_input('> ')
words = stuff.split()

目前做到这样就可以了，不过这招在相当一段时间内都不会有问题。
我的问题：split()是个什么函数？另外，空格就断句嘛？空格不是代表下一格嘛？

## 语汇元组---元组 和 数组

一旦我们知道了如何将句子转化成词汇列表，剩下的就是逐一检查这些词汇，看它们是什么类型。为了达到这个目的，我们将用到一个非常好使的 Python数据结构，叫做”元组(tuple)”。
元组其实就是一个不能修改的列表。
创建它的方法和创建列表差不多，成员之间需要用逗号隔开，不过方括号要换成圆括号 () :

first_word = ('direction', 'north')
secon_word = ('verb', 'go')
sentence =[first_word,  second_word]

这样我们就创建了一个 (TYPE, WORD)组——「注意，逗号前面是类型，后面是类型的解释」，让你识别出单词，并且对它执行指 令。
这只是一个例子，不过最后做出来的样子也差不多。你接受用户输入，用 split将其分隔成单词列表，然后分析这些单词，识别它们的类型，最后重新组成一个句子。

## 扫描输入

现在你要写的是词汇扫描器。这个扫 器会将用户的输入字符串当做参数，然后返回由多个 (TOKEN, WORD) 组成的一个列表，这个列表实现类似句子的功能。如果一个单词不在预定的词汇表中，那它返回时 WORD 应该还在，但 TOKEN应该设置成一个专门的错误标记。这个错误标记将告诉用户哪里出错了。有趣的地方来了。我不会告诉你这些该怎样做，但我会写一个“单元测试(unit test)”，而你要把扫器写出来，并保证单元测试能够正常通过。

## “异常”和数字

有一件小事情我会先帮帮你，那就是数字转换。为了做到这一点，我们会作一点 弊，使用“异常(exceptions)”来做。“异常”指的是你运行某个函数时得到的错误。 你的函数在碰到错误时，就会“ 出(raise)”一个“异常”，然后你就要去处理(handle) 这个异常。假如你在 Python 里写了这些东西:

# 代码

~/projects/simplegame $ python
Python 2.6.5 (r265:79063, Apr 16 2010, 13:57:41)
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> int("hell")
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: 'hell' >>

# 文字

这个ValueError就是int()
函数抛出的一个异常。因为你给
int()
的参数不
是一个数字。   函数其实也可以返回一个值来告诉你它碰到了错误，不过 由于它只能返回整数值，所以很难做到这一点。它不能返回 -1，因为这也是一 个数字。 没有纠结在它“究竟应该返回什么”上面，而是 出了一个叫
做 的异常，然后你只要处理这个异常就可以了。
处理异常的方法是使用   和   这两个关键字:

def convert_nuber(s):
     try:
          return int(s)
     except ValueReeor:
          return None

你把要试着运行的代码放到try的区段里，再将出错后要运行的代码放到 except区段里。在这里，我们要试着调用 init() 去处理某个可能是数字的东西，如果中间出了错，我们就抓到这个错误，然后返回 None。
在你写的扫描器里面，你应该使用这个函数来测试某个东西是不是数字。做完这 个检查，你就可以声明这个单词是一个错误单词了。

# 你应该测试的东西

## 这里是你应该适应的测试文件test/lexicon_tests.py

## 记住你要使用你的项目骨架来创建新项目，将这个测试用例写下来(不许复制粘 贴!)，然后编写你的扫 器，直至所有的测试都能通过。注意细节并确认结果 一切工作良好。


# 设计的技巧

集中一次实现一个测试项目，尽量保持项目简单，只要把你的 lexicon.py 词汇 表中所有的单词放那里就可以了。不要修改输入的单词表，不过你需要创建自己 的新列表，里边包含你的语汇元组。另外，记得使用 in 关键字来检查这些语汇 列表，以确认某个单词是否在你的语汇表中。
'''

# 加分习题


1. 改进单元测试，让它覆盖到更多的语汇。
2. 向语汇列表添加更多的语汇，并且更新单元测试代码。
3. 让你的扫 器能够识别任意大小写的词汇。更新你的单元测试以确认其功能。 4. 找出另外一种转换为数字的方法。
5. 我的解决方案用了 37 行代码，你的是更长还是更短呢?


```

### RESULT


```
NO

```

---

## 第49题

### CODE

```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第49题 创建句子
# 以下是代码部分
## 从我们这个小游戏的词汇扫 器中，我们应该可以得到类似下面的列表:
>>> from ex48 import lexicon
>>> print lexicon.scan("go north")
[('verb','go'),('direction','north')]
>>> print lexicon.scan("kill the princess")
[('verb','kill'),('stop','the'),('noun','bear')]
>>> print lexicon.scan("open the door and smack the bear in the nose")
[('error','open'),('stop','the'),('noun','door'),('error','and'),('error', 'smack'), ('stop', 'the'), ('noun', 'bear'), ('stop', 'in'),
('stop', 'the'), ('error', 'nose')]
>>>

# 现在让我们把它转化成游戏可以使用的东西，也就是一个Sentence类。我们的目的是将上面的元组列表转换为一个Sentence对象，而这个对象又保安主谓宾各个成员。

## 匹配（Match）和窥视（Peek）


为了达到这个效果，你需要四样工具:
1. 循环访问元组列表的方法，这挺简单的。
2. 匹配我们的主谓宾设置中不同种类元组的方法。
3. 一个“窥视”潜在元组的方法，以便做决定时用到。
4. 跳过(skip)我们不在乎的内容的方法，例如形容词、冠词等没有用处的词汇。
 我们使用 peek 函数来查看元组列表中的下一个成员，做匹配以后再对它做下 一步动作。让我们先看看这个 peek 函数


## peek()函数
def peek(word_list):
	if word_list:
		word =word_list[0]
		return word[0]
	else:
		return None

# match()函数：
def match(word_list,expecting):
	if word_list:
		word = word_list.pop(0)

		if word[0]== expectiong:
			return word
		else:
			return None
	else:
		return None

#skip()函数

def skip(word_list,word_type):
	while peek(word_list)== word_type:
		match(word_list,word_type)

# 句子的语法：


有了工具，我们现在可以从元组列表来构建句子（sentence）对象了，我们的处理流程如下：
1.使用peek识别下一个单词。
2.如果这个单词和我们的语法匹配，我们就调用一个函数来处理这部分语法。假设函数的名称叫做parse_subject好了。
3.如果语法不匹配，我们就raise 一个错误，接下来你会学到这个方面的内容。
4.全部分析完以后，我们应该能得到一个　Sentence对象，然后可以将其应用在我们的游戏中。

演示这个过程最简单的方法是把代码韩式给你让你阅读，不过这节习题有个不一样的要求，前面是我给你测试代码，你照着写出程序来，而这次是我给你的程序，你要为他写出测试代码来。
以下就是我写的用来解析简单句子的代码，它使用了ex48.lexicon这个模组。


class ParserError(Exception):
	pass

class Sentence(object):

	def _init_(self,subject,verb,object):
		# remember we take('noun','princess')tuples and convert them
		self.subject = subject[1]
		self.verb = verb[1]
		self.object = object[1]

def peek(word_list):
	if word_list:
		word =word_list[0]
		return word[0]
	else:
		return None

def match(word_list,expecting):
	if word_list:
		word =word_list.pop(0)

		if word[0]== expecting:
			return word
		else:
			return None
	else:
		return None

def skip(word_list,word_type):
	while peek(word_list)== word_type:
		match(word_list,word_type)

def parse_verb(word_list):
	skip(word_list,'stop')

	if peek(word_list)=='verb':
		return match(word_list,'verb')
	else:
		raise ParserError(''Expected a verb next.'')

def parse_object(word_list):
	skip(word_list,'stop')
	next = peek(word_list)

	if next == 'noun':
		return match(word_list,'noun')
	if next == 'direction':
		return match(word_list,'direction')
	else:
		raise ParserError("Expected a noun or direction next.")

def parse_subject(word_list,subj):
	verb = parse_verb(word_list)
	obj =parse_object(word_list)

	return Sentence (subje,verb,obj)

def parse_sentence(word_list):
	skip(word_list,'stop')

	start = peek(word_list)

	if start =='noun':
		subj = match(word_list,'noun')
		return parse_subject(word_list,subj)
	elif start == 'verb':
		# assume the subject is the player then
		return parse_subject(word_list,('noun','player'))
	else:
		raise ParserError ("Must start with subject,object,or verb not: %s" % start)

# 关于异常(Exception)

你已经简单学过关于异常的一些东西，但还没学过怎样抛出(raise)它们。这节的 代码演示了如何 raise 前面定义的ParserError。注意   是一个定 义为Exception类型的 class。另外要注意我们是怎样使用   这个关键字 来抛出异常的。
你的测试代码应该也要测试到这些异常，这个我也会演示给你如何实现。

# 你应该测试的东西

为《习题 49》写一个完整的测试方案，确认代码中所有的东西都能正常工作， 其中异常的测试——输入一个错误的句子它会抛出一个异常来。
使用assert_raises这个函数来检查异常，在 nose 的文档里查看相关的内容， 学着使用它写针对“执行失败”的测试，这也是测试很重要的一个方面。从 nose 文档中学会使用 assert_raises，以及一些别的函数。
写完测试以后，你应该就明白了这段程序的工作原理，而且也学会了如何为别人 的程序写测试代码。 相信我，这是一个非常有用的技能。

## 加分习题

1. 修改parse_函数(方法)，将它们放到一个类里边，而不仅仅是独立的方法函数。 这两种程序设计你喜欢哪一种呢?
2.  高 parser 对于错误输入的抵御能力，这样即使用户输入了你预定义语汇之外的
词语，你的程序也能正常运行下去。
3. 改进语法，让它可以处理更多的东西，例如数字。
4. 想想在游戏里你的 Sentence 类可以对用户输入做哪些有趣的事情。

# 运行后的结果：

本题就是照着敲了代码，并没有进行进一步的测试和运行。

```

### RESULT

```
NO
```

---

## 第50题

### CODE

```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第50题 -你的第一个网站

# 以下是代码部分

这节以及后面的习题中，你的任务是把前面创建的游戏做成网页版。这是本书的 最后三个章节，这些内容对你来说难度会相当大，你要在上面花些时间才能做出 来。在你开始这节练习以前，你必须已经成功地完成过了《习题 46》的内容， 正确安装了 pip，而且学会了如何安装软件包以及如何创建项目骨架。如果你不 记得这些内容，就回到《习题 46》重新复习一遍。

# 安装lpthw.web

在创建你的第一个网页应用程序之前，你需要安装一个“Web 框架”，它的名字 叫 lpthw.web。所谓的“框架”通常是指“让某件事情做起来更容易的软件包”。在 网页应用的世界里，人们创建了各种各样的“网页框架”，用来解决他们在创建网 站时碰到的问题，然后把这些解决方案用软件包的方式发布出来，这样你就可以 利用它们引导创建你自己的项目了。
可选的框架类型有很多很多，不过在这里我们将使用   框架。你可以 先学会它，等到差不多的时候再去接触其它的框架，不过   本身挺不 错的，所以就算你一直使用也没关系。


## 使用pip安装 lpthw.web:

## 出现提示：
Last login: Mon Nov  6 10:49:31 on console
itifadeMacBook-Pro:~ yyy$ sudo pip install lpthw.web
Password:
The directory '/Users/yyy/Library/Caches/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
The directory '/Users/yyy/Library/Caches/pip' or its parent directory is not owned by the current user and caching wheels has been disabled. check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
Collecting lpthw.web
  Downloading lpthw.web-1.1.tar.gz (87kB)
    100% |████████████████████████████████| 92kB 650kB/s
Installing collected packages: lpthw.web
  Running setup.py install for lpthw.web ... done
Successfully installed lpthw.web-1.1
itifadeMacBook-Pro:~ yyy$


'''
##  由于我的安装不是在根目录里，所以经常会遇到上面的权限不足的问题。itifa当时告诉我，更换了账户后登陆“终端”可能会遇到一些问题，现在果然遇到问题了，就是所谓权限不足的问题。
## 解决方案1：
## 解决方案2:直接进入itifa账户然后将这个账户改名。把原来的文件重新 copy到初始账户里。

## 上面这个问题的解决方案参见

源自：http://blog.sina.com.cn/s/blog_a046022d0102w2ux.html

（1）使用命令：sudo pip install numpy时，可能遇到：
The directory '/Users/huangqizhi/Library/Caches/pip' or its parent directory is not owned by the current user and caching wheels has been disabled. check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
说得很清楚，是pip目录的属主不是sudo的root用户。如果必须用sudo pip，更改pip目录属主即可：
sudo chown root /Users/huangqizhi/Library/Caches/pip

（2）pip安装时，可能遇到：
/Library/Python/2.7/site-packages/pip/_vendor/requests/packages/urllib3/util/ssl_.py:90: InsecurePlatformWarning: A true SSLContext object is not available. This prevents urllib3 from configuring SSL appropriately and may cause certain SSL connections to fail. For more information, see https://urllib3.readthedocs.org/en/latest/security.html#insecureplatformwarning.
  InsecurePlatformWarning
解决方法：安装requests，注意后面带[security]：
pip install requests[security]


# 这个地方的氛围已经相当的压抑了


然后使用下面的方法来运行这个 web 程序:

$ python bin/app.py
http://0.0.0.0:8080/

最后，使用你的网页浏览器，打开 URL ，你应该看 到两样东西，首先是浏览器里显示了   ，然后是你的命令行终端 显示了如下的输出:
http://localhost:8080/
Hello, world!
$ python bin/app.py http://0.0.0.0:8080/
127.0.0.1:59542 - - [13/Jun/2011 11:44:43] "HTTP/1.1 GET /" - 200 OK
127.0.0.1:59542 - - [13/Jun/2011 11:44:43] "HTTP/1.1 GET /favicon.ico" - 404 Not Found
这些是lpthw.web打印出的 log 信息，从这些信息你可以看出服务器有在运行， 而且能了解到程序在浏览器背后做了些什么事情。这些信息还有助于你发现程序
的问题。例如在最后一行它告诉你浏览器试图获取 /favicon.ico，但是这个文 件并不存在，因此它返回的状态码是 404 Not Found。
到这里，我还没有讲到任何 web 相关的工作原理，因为首先你需要完成准备工 作，以便后面的学习能顺利进行，接下来的两节习题中会有详细的解释。我会要 求你用各种方法把你的 lpthw.web 应用程序弄坏，然后再将其重新构建起来: 这样做的目的是让你明白运行 lpthw.web 程序需要准备好哪些东西。


## 发生了什么事情？

在浏览器访问到你的网页应用程序时，发生了下面一些事情:

1. 浏览器通过网络连接到你自己的电脑，它的名字叫做localhost，这是一个标准 称谓，表示的谁就是网络中你自己的这台计算机，不管它实际名字是什么，你都可 以使用 localhost 来访问。它使用到的网络端口是 5000。
2. 连接成功以后，浏览器对bin/app.py这个应用程序发出了 HTTP 请求(request)， 要求访问 URL/，这通常是一个网站的第一个 URL。
3. 在bin/app.py里，我们有一个列表，里边包含了 URL 和类的匹配关系。我们 这里只定义了一组匹配，那就是 '/', 'index' 的匹配。它的含义是:如果有人 使用浏览器访问 / 这一级目录，lpthw.web 将找到并加载 class index，从而 用它处理这个浏览器请求。
4. 现在lpthw.web找到了classindex，然后针对这个类的一个实例调用 了 index.GET 这个方法函数。该函数运行后返回了一个字符串，以供 lpthw.web 将其传递给浏览器。
5. 最后lpthw.web完成了对于浏览器请求的处理，将响应(response)回传给浏览器， 于是你就看到了现在的页面。


确定你真的弄懂了这些，你需要画一个示意图，来理清信息是如何从浏览器传递 到 lpthw.web，再到 index.GET，再回到你的浏览器的。

## 修正错误

第一步，把第 11 行的greeting变量赋值删掉，然后刷新浏览器。你应该会看 到一个错误页面，你可以通过这一页丰富的错误信息看出你的程序崩溃的原因是 什么。当然你已经知道出错的原因是 greeting 的赋值丢失了，不
过 lpthw.web 还是会给你一个挺好的错误页面，让你能找到出错的具体位置。 试试在这个错误页面上做以下操作:
1. 检查每一段Localvars输出(用鼠标点击它们)，追踪里边 到的变量名称，以 及它们是在哪些代码文件中用到的。
2. 阅读RequestInformation一节，看看里边哪些知识是你已经熟悉了的。 Request 是浏览器发给你的gothonweb应用程序的信息。这些知识对于日常网页 浏览没有什么用处，但现在你要学会这些东西，以便写出 web 应用程序来。
3. 试着把这个小程序的别的位置改错，探索一下会发生什么事情。``lpthw.web`` 的会 把一些错误信息和堆栈跟踪(stack trace)信息显示在命令行终端，所以别忘了检查命 令行终端的信息输出。

##  创建基本的模版文件

你已经试过用各种方法把这个 lpthw.web 程序改错，不过你有没有注意到“Hello World”不是一个好 HTML 网页呢?这是一个 web 应用，所以需要一个合适的 HTML 响应页面才对。为了达到这个目的，下一步你要做的是将“Hello World” 以较大的绿色字体显示出来。
第一步是创建一个   文件，内容如下:
templates/index.html

#以下是HTML代码

$def with (greeting)

<html>
	<head>
		<title>Gothons Of Planet Percal #25</title>

	</head>
<body>

$if greeting:
	I just wanted to say <em style ="color:green;font-size:2em;">$greeting</em>.
$else:
	<em>Hello</em>,world!
</body>
</html>

# 代码

如果你学过 HTML 的话，这些内容你看上去应该很熟悉。如果你没学过 HTML， 那你应该去研究一下，试着用 HTML 写几个网页，从而知道它的工作原理。不 过我们这里的 HTML 文件其实是一个“模板(template)”，如果你向模板 供一些 参数，lpthw.web 就会在模板中找到对应的位置，将参数的内容填充到模板中。 例如每一个出现 $greeting 的位置，$greeting 的内容都会被替换成对应这个变量名的参数。
为了让你的 bin/app.py 处理模板，你需要写一写代码，告诉 lpthw.web 到哪 里去找到模板进行加载，以及如何渲染(render)这个模板，按下面的方式修改你 的 app.py:

特别注意render这个新变量名，注意我修改了index.GET的最后一行，让它返回了render.index()，并且将greeting变量作为参数传递给了这个函数。
改好上面的代码后，刷新一下浏览器网页妞就会看到一条和之间不同风绿色信息输出。你还可以在六拉起中查看源文件（View Source）,看到模版被渲染成了标准有效的HTML源码。
	1. 在bin/app.py里面你添加了一个叫做render的新变量，它本身是一 个 web.template.render 对象。
	2. 你将templates/作为参数传递给了这个对象，这样就让render知道了从哪里 去加载模板文件。
	3. 在你后面的代码中，当浏览器一如既往地触发了index.GET以后，它没有再返回 简单的 greeting 字符串，取而代之的是你调用了 render.index，而且将问候 语句作为一个变量传递给它。
	4. 这个render_template函数可以说是一个“魔法函数”，它看到了你需要的
	是 index.html，于是就跑到 templates/ 目录下，找到名字为 index.html 的 文件，然后就把它渲染(render)一遍(叫“转换一遍”也可以)。
	5. 在templates/index.html文件中，你可以看到初始定义一行中说这个模板需 要使用一个叫greeting的参数，这和函数定义中的格式差不多。另外和 Python 语法一样，模板文件是缩进敏感的，所以要确认自己弄对了缩进。
	6. 最后，你让templates/index.html去检查greeting这个变量，如果这个变
	量存在的话，就打印出变量的内容，如果不存在的话，就会打印出一个默认的问候 信息。

	要深入理解这个过程，你可以修改 greeting 变量以及 HTML 模板的内容，看 看会有什么效果。然后创建一个叫做 templates/foo.html 的模板，并且使用 一个新的 render.foo 去渲染它。从这个过程你也可以看出，render 调用的函 数名称只要跟templates/下的.html文件名匹配到，这个 HTML 模板就可以 被渲染到了。

#加分题
加分习题
1. 到http://webpy.org/阅读里边的文档，它其实和     是同一个项目。
lpthw.web
198
 2. 实验一下你在上述网站看到的所有的东西，包括里边的代码示例。
3. 阅读以下 HTML5 和 CSS3 相关的东西，自己练习着写几个 .html 和 .css 文件。 4. 如果你有一个懂 Django 朋友可以帮你的话，你可以试着使用 Django 完成一下习
题 50、51、52，看看结果会是什么样子的。

# 运行后的结果：

```

### RESULT

```
NO
```

---

## LOG

- 20171109中午 刷完了所有题，但是真心讲后面这些就是类似于抄写代码，本着先刷完第一遍再说的态度先刷下来再说，后面这些题还是有些理解难度的，当你投入的时间不够的话，还是比较难以理解的。
- 继续进步吧，死磕总是能磕下来的，等刷完 LP3THW了再来扣这些问题吧。由于 jianshu.com页面是有限制的，所有本文档只写了41-47，剩下的48-52题新启一个页面来填写。
