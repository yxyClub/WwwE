---
layout: post
title: 《笨办法学Python》记录-part6（习题48～52）
date: 2017-10-23
categories: blog
tags: [Python,笨办法学Python,LearPython2TheHardWay,LP2THW]
description: 立个Flag开始学Python。
---

## 第48题
### CODE
```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第48题 更复杂的用户输入
# 以下是代码部分
'''
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

'''
# 我们的游戏语汇
'''
我在游戏里创建了下面这些语汇:
  表示方向: north, south, east, west, down, up, left, right, back.
  动词: go, stop, kill, eat.
  修饰词: the, in, of, from, at, it
  名词: door, bear, princess, cabinet.
  数词: 由 0-9 构成的数字。
说到名词，我们会碰到一个小问题，那就是不一样的房间会用到不一样的一组名词，不过让我们先挑一小组出来写程序，以后再做改进把。
'''
## 如何断句
'''
我们已经有了词汇表，为了分析句子的意思，接下来我们需要找到一个断句的方法。我们对于句子的定义是“空格隔开的单词”，所以只要这样就可以了:

stuff = raw_input('> ')
words = stuff.split()

目前做到这样就可以了，不过这招在相当一段时间内都不会有问题。
我的问题：split()是个什么函数？另外，空格就断句嘛？空格不是代表下一格嘛？

'''

## 语汇元组---元组 和 数组
'''
一旦我们知道了如何将句子转化成词汇列表，剩下的就是逐一检查这些词汇，看它们是什么类型。为了达到这个目的，我们将用到一个非常好使的 Python数据结构，叫做”元组(tuple)”。
元组其实就是一个不能修改的列表。
创建它的方法和创建列表差不多，成员之间需要用逗号隔开，不过方括号要换成圆括号 () :

first_word = ('direction', 'north')
secon_word = ('verb', 'go')
sentence =[first_word,  second_word]

这样我们就创建了一个 (TYPE, WORD)组——「注意，逗号前面是类型，后面是类型的解释」，让你识别出单词，并且对它执行指 令。
这只是一个例子，不过最后做出来的样子也差不多。你接受用户输入，用 split将其分隔成单词列表，然后分析这些单词，识别它们的类型，最后重新组成一个句子。
'''
## 扫描输入
'''
现在你要写的是词汇扫描器。这个扫 器会将用户的输入字符串当做参数，然后返回由多个 (TOKEN, WORD) 组成的一个列表，这个列表实现类似句子的功能。如果一个单词不在预定的词汇表中，那它返回时 WORD 应该还在，但 TOKEN应该设置成一个专门的错误标记。这个错误标记将告诉用户哪里出错了。有趣的地方来了。我不会告诉你这些该怎样做，但我会写一个“单元测试(unit test)”，而你要把扫器写出来，并保证单元测试能够正常通过。
'''
## “异常”和数字
'''
有一件小事情我会先帮帮你，那就是数字转换。为了做到这一点，我们会作一点 弊，使用“异常(exceptions)”来做。“异常”指的是你运行某个函数时得到的错误。 你的函数在碰到错误时，就会“ 出(raise)”一个“异常”，然后你就要去处理(handle) 这个异常。假如你在 Python 里写了这些东西:
'''
# 代码
'''
~/projects/simplegame $ python
Python 2.6.5 (r265:79063, Apr 16 2010, 13:57:41)
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> int("hell")
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: 'hell' >>



'''
# 文字

''''
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

'''
# 你应该测试的东西
##这里是你应该适应的测试文件test/lexicon_tests.py

## 记住你要使用你的项目骨架来创建新项目，将这个测试用例写下来(不许复制粘 贴!)，然后编写你的扫 器，直至所有的测试都能通过。注意细节并确认结果 一切工作良好。


# 设计的技巧
'''
集中一次实现一个测试项目，尽量保持项目简单，只要把你的 lexicon.py 词汇 表中所有的单词放那里就可以了。不要修改输入的单词表，不过你需要创建自己 的新列表，里边包含你的语汇元组。另外，记得使用 in 关键字来检查这些语汇 列表，以确认某个单词是否在你的语汇表中。
'''
# 加分习题

'''
1. 改进单元测试，让它覆盖到更多的语汇。
2. 向语汇列表添加更多的语汇，并且更新单元测试代码。
3. 让你的扫 器能够识别任意大小写的词汇。更新你的单元测试以确认其功能。 4. 找出另外一种转换为数字的方法。
5. 我的解决方案用了 37 行代码，你的是更长还是更短呢?
'''
```
###RESULT
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
'''
为了达到这个效果，你需要四样工具:
1. 循环访问元组列表的方法，这挺简单的。
2. 匹配我们的主谓宾设置中不同种类元组的方法。
3. 一个“窥视”潜在元组的方法，以便做决定时用到。
4. 跳过(skip)我们不在乎的内容的方法，例如形容词、冠词等没有用处的词汇。
 我们使用 peek 函数来查看元组列表中的下一个成员，做匹配以后再对它做下 一步动作。让我们先看看这个 peek 函数
'''
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
'''
有了工具，我们现在可以从元组列表来构建句子（sentence）对象了，我们的处理流程如下：
1.使用peek识别下一个单词。
2.如果这个单词和我们的语法匹配，我们就调用一个函数来处理这部分语法。假设函数的名称叫做parse_subject好了。
3.如果语法不匹配，我们就raise 一个错误，接下来你会学到这个方面的内容。
4.全部分析完以后，我们应该能得到一个　Sentence对象，然后可以将其应用在我们的游戏中。

演示这个过程最简单的方法是把代码韩式给你让你阅读，不过这节习题有个不一样的要求，前面是我给你测试代码，你照着写出程序来，而这次是我给你的程序，你要为他写出测试代码来。
以下就是我写的用来解析简单句子的代码，它使用了ex48.lexicon这个模组。
'''
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
'''
你已经简单学过关于异常的一些东西，但还没学过怎样抛出(raise)它们。这节的 代码演示了如何 raise 前面定义的ParserError。注意   是一个定 义为Exception类型的 class。另外要注意我们是怎样使用   这个关键字 来抛出异常的。
你的测试代码应该也要测试到这些异常，这个我也会演示给你如何实现。
'''
# 你应该测试的东西
'''
为《习题 49》写一个完整的测试方案，确认代码中所有的东西都能正常工作， 其中异常的测试——输入一个错误的句子它会抛出一个异常来。
使用assert_raises这个函数来检查异常，在 nose 的文档里查看相关的内容， 学着使用它写针对“执行失败”的测试，这也是测试很重要的一个方面。从 nose 文档中学会使用 assert_raises，以及一些别的函数。
写完测试以后，你应该就明白了这段程序的工作原理，而且也学会了如何为别人 的程序写测试代码。 相信我，这是一个非常有用的技能。
'''
## 加分习题
'''
1. 修改parse_函数(方法)，将它们放到一个类里边，而不仅仅是独立的方法函数。 这两种程序设计你喜欢哪一种呢?
2.  高 parser 对于错误输入的抵御能力，这样即使用户输入了你预定义语汇之外的
词语，你的程序也能正常运行下去。
3. 改进语法，让它可以处理更多的东西，例如数字。
4. 想想在游戏里你的 Sentence 类可以对用户输入做哪些有趣的事情。
'''



# 运行后的结果：
'''
本题就是照着敲了代码，并没有进行进一步的测试和运行。
'''



```
###RESULT
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
'''
这节以及后面的习题中，你的任务是把前面创建的游戏做成网页版。这是本书的 最后三个章节，这些内容对你来说难度会相当大，你要在上面花些时间才能做出 来。在你开始这节练习以前，你必须已经成功地完成过了《习题 46》的内容， 正确安装了 pip，而且学会了如何安装软件包以及如何创建项目骨架。如果你不 记得这些内容，就回到《习题 46》重新复习一遍。
'''
# 安装lpthw.web
'''
在创建你的第一个网页应用程序之前，你需要安装一个“Web 框架”，它的名字 叫 lpthw.web。所谓的“框架”通常是指“让某件事情做起来更容易的软件包”。在 网页应用的世界里，人们创建了各种各样的“网页框架”，用来解决他们在创建网 站时碰到的问题，然后把这些解决方案用软件包的方式发布出来，这样你就可以 利用它们引导创建你自己的项目了。
可选的框架类型有很多很多，不过在这里我们将使用   框架。你可以 先学会它，等到差不多的时候再去接触其它的框架，不过   本身挺不 错的，所以就算你一直使用也没关系。

'''
## 使用pip安装 lpthw.web:
'''
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
'''
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

'''
# 这个地方的氛围已经相当的压抑了
'''

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
'''

## 发生了什么事情？
'''
在浏览器访问到你的网页应用程序时，发生了下面一些事情:

1. 浏览器通过网络连接到你自己的电脑，它的名字叫做localhost，这是一个标准 称谓，表示的谁就是网络中你自己的这台计算机，不管它实际名字是什么，你都可 以使用 localhost 来访问。它使用到的网络端口是 5000。
2. 连接成功以后，浏览器对bin/app.py这个应用程序发出了 HTTP 请求(request)， 要求访问 URL/，这通常是一个网站的第一个 URL。
3. 在bin/app.py里，我们有一个列表，里边包含了 URL 和类的匹配关系。我们 这里只定义了一组匹配，那就是 '/', 'index' 的匹配。它的含义是:如果有人 使用浏览器访问 / 这一级目录，lpthw.web 将找到并加载 class index，从而 用它处理这个浏览器请求。
4. 现在lpthw.web找到了classindex，然后针对这个类的一个实例调用 了 index.GET 这个方法函数。该函数运行后返回了一个字符串，以供 lpthw.web 将其传递给浏览器。
5. 最后lpthw.web完成了对于浏览器请求的处理，将响应(response)回传给浏览器， 于是你就看到了现在的页面。


确定你真的弄懂了这些，你需要画一个示意图，来理清信息是如何从浏览器传递 到 lpthw.web，再到 index.GET，再回到你的浏览器的。
'''
## 修正错误
'''
第一步，把第 11 行的greeting变量赋值删掉，然后刷新浏览器。你应该会看 到一个错误页面，你可以通过这一页丰富的错误信息看出你的程序崩溃的原因是 什么。当然你已经知道出错的原因是 greeting 的赋值丢失了，不
过 lpthw.web 还是会给你一个挺好的错误页面，让你能找到出错的具体位置。 试试在这个错误页面上做以下操作:
1. 检查每一段Localvars输出(用鼠标点击它们)，追踪里边 到的变量名称，以 及它们是在哪些代码文件中用到的。
2. 阅读RequestInformation一节，看看里边哪些知识是你已经熟悉了的。 Request 是浏览器发给你的gothonweb应用程序的信息。这些知识对于日常网页 浏览没有什么用处，但现在你要学会这些东西，以便写出 web 应用程序来。
3. 试着把这个小程序的别的位置改错，探索一下会发生什么事情。``lpthw.web`` 的会 把一些错误信息和堆栈跟踪(stack trace)信息显示在命令行终端，所以别忘了检查命 令行终端的信息输出。
'''
##  创建基本的模版文件
'''
你已经试过用各种方法把这个 lpthw.web 程序改错，不过你有没有注意到“Hello World”不是一个好 HTML 网页呢?这是一个 web 应用，所以需要一个合适的 HTML 响应页面才对。为了达到这个目的，下一步你要做的是将“Hello World” 以较大的绿色字体显示出来。
第一步是创建一个   文件，内容如下:
templates/index.html
'''
#以下是HTML代码
'''
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
'''
# 代码
'''
如果你学过 HTML 的话，这些内容你看上去应该很熟悉。如果你没学过 HTML， 那你应该去研究一下，试着用 HTML 写几个网页，从而知道它的工作原理。不 过我们这里的 HTML 文件其实是一个“模板(template)”，如果你向模板 供一些 参数，lpthw.web 就会在模板中找到对应的位置，将参数的内容填充到模板中。 例如每一个出现 $greeting 的位置，$greeting 的内容都会被替换成对应这个变量名的参数。
为了让你的 bin/app.py 处理模板，你需要写一写代码，告诉 lpthw.web 到哪 里去找到模板进行加载，以及如何渲染(render)这个模板，按下面的方式修改你 的 app.py:
'''
'''
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
###RESULT
```
NO
```
---
## 第51题
### CODE
```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第51题 从浏览器中获取输入
'''
虽然能让浏览器显示“Hello World”是很有趣的一件事情，但是如果能让用户通过 表单(form)向你的应用程序 交文本就更有趣了。这节习题中，我们将使用 form 改进你的 web 程序，并且将用户相关的信息保存到他们的“会话(session)”中。

'''
# Web工作原理
'''
该学点无趣的东西了。在创建 form 前你需要先多学一点关于 web 的工作原理。 这里讲并不完整，但是相当准确，在你的程序出错是，它会帮你找到出错的原因。 另外，如果你理解了 form 的应用，那么创建 form 对你来说就会更容易了。
我将以一个简单的图示讲起，它向你展示了 web 请求的各个不同的部分，以及 信息传递的大致流程:


为了方便讲述 HTTP 请求(request) 的流程，我在每条线上面加了字母标签以 作区别。

1. 你在浏览器中输入网址http://learnpythonthehardway.org/，然后浏览器 会通过你的电脑的网络设备发出 request(线路 A)。
2. 你的 request 被传送到互联网(线路 B)，然后再抵达远端服务器(线路 C)，然 后我的服务器将接受这个 request。
3. 我的服务器接受 request 后，我的 web 应用程序就去处理这个请求(线路 D)， 然后我的 Python 代码就会去运行index.GET这个“处理程序(handler)”。
4. 在代码return的时候，我的 Python 服务器就会发出响应(response)，这个响应 会再通过线路 D 传递到你的浏览器。
5. 这个网站所在的服务器将响应由线路 D 获取，然后通过线路 C 传至互联网。
6. 响应通过互联网由线路 B 传至你的计算机，计算机的网卡再通过线路 A 将响应传
给你的浏览器。
7. 最后，你的浏览器显示了这个响应的内容。

这段详解中用到了一些术语。你需要掌握这些术语，以便在谈论你的 web 应用 时你能明白而且应用它们:

浏览器(browser)

这是你几乎每天都会用到的软件。大部分人不知道它真正的原理，他们只会把它叫 作“网”。它的作用其实是接收你输入到地址栏网址(例如 http://learnpythonthehardway.org)，然后使用该信息向该网址对应的服务器 出请 求(request)。


地址(address)

通 常 这 是 一 个 像 http://learnpythonthehardway.org/ 一 样 的 URL (Uniform Resource Locator，统一资源定位器)，它告诉浏览器该打开哪个网站。前面 的 http 指出了你要使用的协议(protocol)，这里我们用的是“超文本传输协议 (Hyper-Text Transport Protocol)”。你还可以试试 ftp://ibiblio.org/ ，这是一个“FTP 文 件传输协议(File Transport Protocol)”的例子。learnpythonthehardway.org 这 部分是“主机名(hostname)”，也就是一个便于人阅读和记忆的字串，主机名会被匹 配到一串叫作“IP 地址”的数字上面，这个“IP 地址”就相当于网络中一台计算机的电 话号码，通过这个号码可以访问到这台计算机。最后，URL 中还可以尾随一个“路 径”，例如 http://learnpythonthehardway.org/book/ 中的 /book/，它对应的是服务 器上的某个文件或者某些资源，通过访问这样的网址，你可以向服务器发出请求， 然后获得这些资源。网站地址还有很多别的组成部分，不过这些是最主要的。

连接(connection)
一旦浏览器知道了协议(http)、服务器(learnpythonthehardway.org)、以及要获得的 资源，它就要去创建一个连接。这个过程中，浏览器让操作系统(Operating System, OS)打开计算机的一个“端口(port)”(通常是 80 端口)，端口准备好以后，操作系统 会回传给你的程序一个类似文件的东西，它所做的事情就是通过网络传输和接收数 据，让你的计算机和 learnpythonthehardway.org 这个网站所属的服务器之间实现
数据交流。 当你使用 http://localhost:8080/ 访问你自己的站点时，发生的事情其实 是一样的，只不过这次你告诉了浏览器要访问的是你自己的计算机(localhost)，要使 用的端口 不是默认的 80，而是 8080。你还可以直接访 问 http://learnpythonthehardway.org:80/， 这和不输入端口效果一样，因为 HTTP 的默认端口本来就是 80。


请求(request)
你的浏览器通过你 供的地址建立了连接，现在它需要从远端服务器要到它(或你) 想要的资源。如果你在 URL 的结尾加了/book/，那你想要的就是 /book/ 对应 的文件或资源，大部分的服务器会直接为你调用 /book/index.html 这个文件，不过 我们就假装不存在好了。浏览器为了获得服务器上的资源，它需要向服务器发送一 个“请求”。这里我就不讲细节了，为了得到服务器上的内容，你必须先向服务器发 送一个请求才行。有意思的是，“资源”不一定非要是文件。例如当浏览器向你的应用程序 出请求的时候，服务器返回的其实是你的 Python 代码生成的一些东西。


服务器(server)
服务器指的是浏览器另一端连接的计算机，它知道如何回应浏览器请求的文件和资 源。大部分的 web 服务器只要发送文件就可以了，这也是服务器流量的主要部分。 不过你学的是使用 Python 组建一个服务器，这个服务器知道如何接受请求，然后 返回用 Python 处理过的字符串。当你使用这种处理方式时，你其实是假装把文件 发给了浏览器，其实你用的都只是代码而已。就像你在《习题 50》中看到的，要构 建一个“响应”其实也不需要多少代码。

响应(response)
这就是你的服务器回复你的请求，发回至浏览器的 HTML，它里边可能有 css、 javascript、或者图像等内容。以文件响应为例，服务器只要从磁盘读取文件，发送 给浏览器就可以了，不过它还要将这些内容包在一个特别定义的“头部信息(header)” 中，这样浏览器就会知道它获取的是什么类型的内容。以你的 web 应用程序为例， 你发送的其实还是一样的东西，包括 header 也一样，只不过这些数据是你用 Python 代码即时生成的。

 这个可以算是你能在网上找到的关于浏览器如何访问网站的最快的快速课程了。 这节课程应该可以帮你更容易地理解本节的习题，如果你还是不明白，就到处找 资料多多了解这方面的信息，知道你明白为止。有一个很好的方法，就是你对照 着上面的图示，将你在《习题 50》中创建的 web 程序中的内容分成几个部分， 让其中的各部分对应到上面的图示。如果你可以正确地将程序的各部分对应到这 个图示，你就大致开始明白它的工作原理了。


'''
'''
## 表单（form）的工作原理
熟悉表单的最好方法是写一个可以接受表单数据的程序出来，然后看你可以对它做些什么。先将你的bin/app.py改成下面的样子。


重启你的 web 程序(按 CTRL-C 后重新运行)，确认它有运行起来，然后使 用浏览器访问 http://localhost:8080/hello，这时浏览器应该会显示“I just wanted to say Hello, Nobody.”，接下来，将浏览器的地址改
成 http://localhost:8080/hello?name=Frank，然后你可以看到页面显示为
“Hello, Frank.”，最后将 name=Frank 修改为你自己的名字，你就可以看到它对 你说“Hello”了。


让我们研究一下你的程序里做过的修改。
1. 我们没有直接为greeting赋值，而是使用了web.input从浏览器获取数据。这 个函数会将一组 key=value 的表述作为默认参数，解析你 供的 URL 中
的 ?name=Frank 部分，然后返回一个对象，你可以通过这个对象方便地访问到表 单的值。
2. 然后我通过form对象的form.name属性为greeting赋值，这句你应该已经熟 悉了。
3. 其他的内容和以前是一样的，我们就不再分析了。

URL 中该还可以包含多个参数。将本例的 URL 改成这样
子: http://localhost:8080/hello?name=Frank&greet=Hola。然后修改代 码，让它去获取 form.name 和 form.greet，如下所示:
greeting = "%s, %s" % (form.greet, form.name)

修改完毕后，试着访问新的 URL。然后将 到什么样的错误信息。由于我们在
为   设定默认值，这样
部分删除，看看你会得 中没有
就变成了一个必须的参数，如果没有这个参
&greet=Hola
 web.input(name="Nobody")
 greet
greet
 数程序就会报错。现在修改一下你的程序，在   中为 设一个默 认值试试看。另外你还可以设 greet=None，这样你可以通过程序检查 的 值是否存在，然后 供一个比较好的错误信息出来，例如:

'''
form = web.input(name="Nobody", greet=None)

 if form.greet:
	 greeting ="%s, %s" % (form.greet, form.name)
	 return render.index(greeting =greeting)
else:
	return "ERROR:greet is required."

# 创建HTML表单
'''
你可以通过URL参数实现表单提交，不过这样看上去有些丑陋，而且不方便一般人使用，你真正需要的是一个“POST表单”，这是一种包含了<form>标签的特殊HTML文件。这种表单收集用语输入并将其船体给你的web程序，这和你上面实现的目的基本是一样的。

让我们来快速创建一个，从中你可以看出它的工作原理。你需要创建一个新的HTML文件，叫做templates/hello_form.html:
<html>
	<head>
		<title>Sample Web Form</title>
	</head>
<body>

<h1>Fill Out This Form</h1>

<form action = "/hello" method ="POST">
	A Greeting:<input type="text" name="greet">
	<br/>
	Your Name:<input type="text" name="name">
	<br/>
	<input type="submit">
</form>

</body>
</html>
'''

# 然后将bin/app.py改成这样：
'''
import web

urls = ('/hello','Index')

app = web.application(urls,globals())

render = web.template.render('templates/')

class Index(object):
	def GET(self):

		return render.hello_form()

	def POST(self):

		form = web.input(name='Nobody',greet ="Hello")
		#greeting = "Hello World,%s"%form.name#修改代码成为多参数：greeting = "%s, %s" % (form.greet, form.name)
		greeting="%s, %s" % *(form.greet, form.name)

		return render.index(greeting =greeting)

if __name__ == "_main_":
	app.run()
'''
'''
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
'''
#将template/index.html  改成这样：
''''
$def with (greeting)

$if greeting:
	I just wanted to say <em style="color:green;font-size:2em;">$greeting</em>
$else:

	<em>Hello</em>,world!
'''
#然后把templates/hello_form.html改成这样：

'''
<h1>Fill Out This Form</h1>
<form action="/hello" method="POST">
	A Greeting: <input type= "text" name ="greet">
	<br/>
	Your Name:<input type="text" name= "name">
	<br/>
	<input type="submit">
</form>

上面这些修改的目的，是将每一个页面顶部和底部的反复用到的“boilerplate”代 码剥掉。这些被剥掉的代码会被放到一个单独的 templates/layout.html 文件 中，从此以后，这些反复用到的代码就由 layout.html 来 供了

'''
#上面的都改好以后，创建一个 templates/layout.html 文件，内容如下:
'''
$def with (content)

<html>
<head>
	<title>Gothons From Planet Percal #25</title>
</head>
<body>

$:content

</body>
</html>

#这个文件和普通的模板文件类似，不过其它的模板的内容将被传递给它，然后它 会将其它 模板的内容“包裹”起来。任何写在这里的内容多无需写在别的模板中 了。你需要注意$:content 的用法，这和其它的模板变量有些不同。
最后一步，就是将 render 对象改成这样:

render =web.template.render('templates/',base="layout")

#这会告诉   让它去使用   作为其它模板的基 础模板。重启你的程序观察一下，然后试着用各种方法修改你的 layout 模板， 不要修改你别的模板，看看输出会有什么样的变化。

'''

# 为表单撰写自动测试代码
'''
使用浏览器测试web程序是很容易的，只要点刷新按钮就可以了。不过毕竟我们是程序员嘛，如果我们可以歇一歇代码来测试我们的程序，为什么还要重复手动测试呢？接下来，你要做的是，就是为你的 web 程序写一个小测试。这回用到你在ex47里学到的东西，如果不记得的话，可以回去复习一下。

为了让 Python 加载bin/app.py并进行测试，你需要先做一点准备工作。首先是创建一个bin/__init__.py空文件，这样 Python 就会将 bin/ 当做一个目录了。(在《习题 52》中你会去修改 __init__.py，不过这是后话。)
我还为 lpthw.web创建了一个简单的小函数，让你判断(assert)web程序的响应，这个函数有一个很合适的名字，叫做assert_response.创建一个tests/tools.py文件，内容如下：
'''
from nose.tools import *
import re

def assert_response(resp,contains=None,matches=None,headers=None,status="200"):

	assert status in resp.status,"Expected response %r not in %r "% (status,resp.status)

	is status =="200":
		assert resp.data,"Response data is empty."

	if contains:
		assert contains in resp.data,"Response does not contain %r" % contains
	if matches:
		reg = re.compile(matches)
		assert reg.matches(resp.data),"Response does not match %r " % matches

	if headers:
		assert_equal(resp.headers, headers)

# 准备好这个文件以后，你就可以为的bin/app.py 写自动测试代码了，床架哪一个新文件叫做tests/app_tests.py
from nose.tools import *
from bin.app import app
from tests.tools import assert_response

def test_index():
	#check that we get a 404 on the /URL
	resp = app.request("/")
	assert_response(resp,status="404")

	# test our first GET request to/hello
	resp = app.request("/hello")
	assert_response(resp)

	# make sure default values work for the form
	resp = app.request("/hello",method ="POST")
	assert_response(resp,contains ="Nobody")

	#test that we get expected values
	data = {'name':'Zed','greet':'Hola'}
	resp = app.request("/hello",method="POST",data=data)
	assert_response(resp,contains ="Zed")

#最后，使用nosetests 运行测试脚本，然后测试你的 web 程序。
''''
$ nosetests
.
.............................
Ran 1 test in 0.059s

OK

'''
# 文字部分
'''
 这里我所做的，是将bin/app.py这个模块中的整个 web 程序都 import 进来， 然后手动运行这个 web 程序。lpthw.web 有一个非常简单的 API 用来处理请 求，看上去大致是这样子的:
   app.request(localpart='/', method='GET', data=None,
   host='0.0.0.0:8080',
   headers=None, https=False)

你可以将 URL 作为第一个参数，然后你可以修改修改 request 的方法、form 的数据、以及 header 的内容，这样你无须启动 web 服务器，就可以使用自动 测试来测试你的 web 程序了。
为了验证函数的响应，你需要使用 tests.tools 中定义的 assert_response 函 数，用法属下:

assert_response(resp, contains=None, matches=None, headers=None, status="200")

把你调用app.request得到的响应传递给这个函数，然后将你要检查的内容作 为参数传递给诶这个函数。你可以使用contains参数来检查响应中是否包含指 定的值，使用 status 参数可以检查指定的响应状态。这个小函数其实包含了很 多的信息，所以你还是自己研究一下的比较好。
在 tests/app_tests.py 自动测试脚本中，我首先确认 / 返回了一个“404 Not Found”响应，因为这个 URL 其实是不存在的。然后我检查了/hello在
GET 和 POST 两种请求的情况下都能正常工作。就算你没有弄明白测试的原理， 这些测试代码应该是很好读懂的。


花一些时间研究一下这个最新版的 web 程序，重点研究一下自动测试的工作原 理。确认你理解了将 bin/app.py 做为一个模块导入，然后进行自动化测试的流 程。这是一个很重要的技巧，它会引导你学到更多东西。

'''
#加分习题
'''
1. 阅读和 HTML 相关的更多资料，然后为你的表单设计一个更好的输出格式。你可 以先在纸上设计出来，然后用 HTML 去实现它。
2. 这是一道难题，试着研究一下如何进行文件上传，通过网页上传一张图像，然后将 其保存到磁盘中。
 3. 更难的难题，找到 HTTP RFC 文件(讲述 HTTP 工作原理的技术文件)，然后努 力阅读一下。这是一篇很无趣的文档，不过偶尔你会用到里边的一些知识。
4. 又是一道难题，找人帮你设置一个 web 服务器，例如 Apache、Nginx、或者 thttpd。 试着让服务器伺服一下你创建的 .html 和 .css 文件。如果失败了也没关系，web 服务器本来就都有点挫。
5. 完成上面的任务后休息一下，然后试着多创建一些 web 程序出来。你应该仔细阅 读 web.py (它和 lpthw.web 是同一个程序)中关于会话(session)的内容，这样你可 以 明白如何保持用户的状态信息。
'''
# 运行后的结果：
```
###RESULT
```
NO
```
---
## 第52题
### CODE
```
#!/usr/bin/python
# -*- coding: utf-8 -*-

# 第52题 创建你的web游戏

# 以下是{文章文字}部分
''''
这本书马上就要结束了。本章的练习对你是一个真正的挑战。当你完成以后，你 就可以算是一个能力不错的 Python 初学者了。为了进一步学习，你还需要多 读一些书，多写一些程序，不过你已经具备进一步学习的技能了。接下来的学习 就只是时间、动力、以及资源的问题了。
在本章习题中，我们不会去创建一个完整的游戏，取而代之的是我们会为《习题 42》中的游戏创建一个“引擎(engine)”，让这个游戏能够在浏览器中运行起来。
这会涉及到将《习题 42》中的游戏“重构(refactor)”，将《习题 47》中的架构混 合进来，添加自动测试代码，最后创建一个可以运行游戏的 web 引擎。
这是一节很庞大的习题。我预测你要花一周到一个月才能完成它。最好的方法是 一点一点来，每晚上完成一点，在进行下一步之前确认上一步有正确完成。
'''


# 重构 ex42的游戏
'''
你已经在两个练习中修改了 gothonweb 项目，这节习题中你会再修改一次。这 种修改的技术叫做“重构(refactoring)”，或者用我喜欢的讲法来说，叫“修修补补 (fixing stuff)”。重构是一个编程术语，它指的是清理旧代码或者为旧代码添加新 功能的过程。你其实已经做过这样的事情了，只不过不知道这个术语而已。这是 写软件过程的第二个自然属性。
你在本节中要做的，是将《习题 47》中的可以测试的房间地图，以及《习题 42》 中的游戏这两样东西归并到一起，创建一个新的游戏架构。游戏的内容不会发生 变化，只不过我们会通过“重构”让它有一个更好的架构而已。

 第一步是将ex47/game.py的内容复制到gothonweb/map.py中，然后将
tests/ex47_tests.py的内容复制到tests/map_tests.py中，然后再次运行nosetests，确认他们还能正常工作。

Note：
从现在开始我不会再向你展示运行测试的输出了，我就假设你回去运行这些测试，
 而且知道怎样的输出是正确的。

'''
## 架构
''''
将《习题 47》的代码拷贝完毕后，你就该开始重构它，让它包含《习题 42》 中的地图。我一开始会把基本架构为你准备好，然后你需要去完成map.py
和map_tests.py 里边的内容。
 首先要做的是使用 Room类来构建基本的地图架构:
'''
class Room(object):

	def __init__(self, name, description):
		self.name =name
		self.description = description
		self.paths = {}

	def go(self,direction):
		return self.paths.get(direction,None)

	def add_paths(self, paths):
		self.paths.update(paths)

central_corridor = Room ("Central Corridor",

"""
The Gothons of Planet Percal #25 have invaded your ship and
destroyed
your entire crew. You are the last surviving member and your last
mission is to get the neutron destruct bomb from the Weapons Armory,
put it in the bridge, and blow the ship up after getting into an
escape pod.
You're running down the central corridor to the Weapons Armory
when
a Gothon jumps out, red scaly skin, dark grimy teeth, and evil clown costume
flowingaroundhishatefilledbody. He'sblockingthedoor to the
Armory and about to pull a weapon to blast you.
""")

laser_weapon_armory = Room("Laser Weapon Armory",
 """
Lucky for you they made you learn Gothon insults in the academy.
You tell the one Gothon joke you know:
Lbhe zbgure vf fb sng, jura fur fvgf nebhaq gur ubhfr, fur fvgf nebhaq gur ubhfr.
The Gothon stops, tries not to laugh, then busts out laughing and can't move.
While he's laughing you run up and shoot him square in the
head
putting him down, then jump through the Weapon Armory door.
You do a dive roll into the Weapon Armory, crouch and scan the room
formoreGothonsthatmightbehiding. It'sdeadquiet,too quiet.
You stand up and run to the far side of the room and find the neutronbombinitscontainer. There'sakeypadlockonthebox
andyouneedthecodetogetthebombout. Ifyougetthecode wrong 10 times then the lock closes forever and you can't get the bomb. The code is 3 digits.
"""
)

the_bridge = Room("The Bridge", """
The container clicks open and the seal breaks, letting gas out.
You grab the neutron bomb and run as fast as you can to the bridge where you must place it in the right spot.
You burst onto the Bridge with the netron destruct bomb under your arm and surprise 5 Gothons who are trying to take control of the ship. Each of them has an even uglier
clown costume than the last. They haven't pulled their weapons out yet, as they see the active bomb under your arm and don't want to set it off.
""")

escape_pod = Room("Escape Pod", """You point your blaster at the bomb under your arm
and the Gothons put their hands up and start to sweat. You inch backward to the door, open it, and then carefully place the bomb on the floor, pointing your blaster at it. You then jump back through the door, punch the close button
and blast the lock so the Gothons can't get out.
Now that the bomb is placed you run to the escape pod to get off this tin can.
You rush through the ship desperately trying to make it to
theescapepodbeforethewholeshipexplodes. Itseemslike
hardly any Gothons are on the ship, so your run is clear of
interference. You get to the chamber with the escape pods, and
nowneedtopickonetotake. Someofthemcouldbedamaged but you don't have time to look. There's 5 pods, which one do you take?
""")
the_end_winner = Room("The End",
"""
You jump into pod 2 and hit the eject button.
The pod easily slides out into space heading to
the planet below. As it flies to the planet, you lookback and see your ship implode then explode like a
bright star, taking out the Gothon ship at the same time. You won!
""")

the_end_loser = Room("The End",
"""
You jump into a random pod and hit the eject button. The pod escapes out into the void of space, then implodes as the hull ruptures, crushing your body into jam jelly.
"""
)

escape_pod.add_paths({ '2': the_end_winner,
'*': the_end_loser })

generic_death = Room("death", "You died.")
the_bridge.add_paths({
'throw the bomb': generic_death, 'slowly place the bomb': escape_pod
})
laser_weapon_armory.add_paths({
'0132': the_bridge,
'*': generic_death
})

central_corridor.add_paths({ 'shoot!': generic_death, 'dodge!': generic_death,
'tell a joke': laser_weapon_armory
})

START = central_corridor

# 我们会发现我们的 Room 类和地图存在一些问题
'''
  1. 在进入一个房间以前会打印出一段文字作为房间的 述，我们需要将这些 述和每 个房间关联起来，这样房间的次序就不会被打乱了，这对我们的游戏是一件好事。这些 述本来是在 if-else 结构中的，这是我们后面要修改的东西。
  2.原版游戏中我们使用了专门的代码来生成一些内容，例如炸弹的激活键码，舰舱的 选择等，这次我们做游戏时就先使用默认值好了，不过后面的加分习题里，我会要
    求你把这些功能再加到游戏中。
 3. 我为所有的游戏中的失败结尾写了一个generic_death，你需要去补全这个函数。
 你需要把原版游戏中所有的失败结尾都加进去，并确保代码能正确运行。
 4. 我添加了一种新的转换模式，以"*"为标记，用来在游戏引擎中实现“catch-all”动
 作。

  等你把上面的代码基本写好以后，接下来就是引导你继续写下去的自动测试的内容 tests/map_test.py 了:
'''

from nose.tools import *
from gothonweb.map import *

def test_room():
	gold = Room("GoldRoom",
"""This room has gold in it you can grab.There's a
door to the north.""")
	assert_equal(gold.name, "GoldRoom")
	assert_equal(gold.paths, {})

def test_room_paths():
	center = Room("Center", "Test room in the center.")
	north = Room("North", "Test room in the north.")
	south = Room("South", "Test room in the south.")
	center.add_paths({'north': north, 'south': south})

	assert_equal(center.go('north'), north)
	assert_equal(center.go('south'), south)

def test_map():
	start = Room("Start", "You can go west and down a hole.")
	west = Room("Trees", "There are trees here, you can go east.")
	down = Room("Dungeon", "It's dark down here, you can go up.")
	start.add_paths({'west': west, 'down': down})
	west.add_paths({'east': start})
	down.add_paths({'up': start})
	assert_equal(start.go('west'), west)
	assert_equal(start.go('west').go('east'), start)
	assert_equal(start.go('down').go('up'), start)

def test_gothon_game_map():
	assert_equal(START.go('shoot!'), generic_death)
	assert_equal(START.go('dodge!'), generic_death)
	room = START.go('tell a joke')
	assert_equal(room, laser_weapon_armory)

''''
你在这部分练习中的任务是完成地图，并且让自动测试可以完整地检查过整个地
图。这包括将所有的 generic_death 对象修正为游戏中实际的失败结尾。让你 的代码成功运行起来，并让你的测试越全面越好。后面我们会对地图做一些修改， 到时候这些测试将保证修改后的代码还可以正常工作。
'''
# 会话（session）和用户跟踪
'''
在你的 web 程序运行的某个位置，你需要追踪一些信息，并将这些信息和用户 的浏览器关联起来。在 HTTP 协议的框架中，web 环境是“无状态(stateless)” 的，这意味着你的每一次请求和你其它的请求都是相互独立的。如果你请求了页 面 A，输入了一些数据，然后点了一个页面 B 的链接，那你在页面 A 输入的 数据就全部消失了。
'''
####解决问题的方法
''''
解决这个问题的方法是为 web 程序建立一个很小的数据存储功能，给每个浏览 器进程赋予一个独一无二的数字，用来跟踪浏览器所作的事情。这个存储通常用 数据库或者存储在磁盘上的文件来实现。在 lpthw.web 这个小框架中实现这样 的功能是很容易的，以下就是一个这样的例子:
'''

import web

web.config.debug = False

urls = (
	"/count", "count",
	"/reset", "reset"
)
app = web.application(urls, locals())
store = web.session.DiskStore('sessions')
session = web.session.Session(app, store, initializer={'count': 0})


class count:
	def GET(self):
		session.count += 1
		return str(session.count)


class reset:
	def GET(self):
		session.kill()
		return " "

if __name__ == "__main__":
app.run()

''''
为了实现这个功能，你需要创建一个sessions/ 文件夹作为程序的会话存储位置，建好以后运行合格程序，然后检查/coint 页面，刷新一下这个页面看看计数会不会累加上去。关掉浏览器，程序就会“忘掉”之前的位置，这也是我们的游戏所需的功能。有一种方法可以让浏览器永远记住一些信息，不过这回让测试和开发变得更困难。如果你回到/reset/ 页面，然后在访问/count 页面，你可以看到你的计数器被重置了，因为你已经把会话傻掉了。

你需要花点时间弄懂这段代码，注意会话开始时 count 值是如何设定为0 的，另外再看看 session/ 下面的文件，看看你能不能把他们打开。下面是我把一个 Python 会话打开并且解码的过程：

>>> import pickle
>>> import base64
>>> base64.b64decode(open("sessions/XXXXX").read())
"(dp1\nS'count'\np2\nI1\nsS'ip'\np3\nV127.0.0.1\np4\nsS' session_id'\np5\nS'XXXX'\np6\ns."
>>>
>>> x = base64.b64decode(open("sessions/XXXXX").read())
>>>
>>> pickle.loads(x)
{'count': 1, 'ip': u'127.0.0.1', 'session_id': 'XXXXX'}

 所以会话其实就是使用   和   这些库写到磁盘上的字典。存储和管 理会话的方法很多，大概和 Python 的 web 框架那么多，所以了解它们的工作 原理并不重要。当然如果你需要调试或者清空会话时，知道点原理还是有用的。
'''

# 创建引擎

''''
你应该已经写好了游戏地图和它的单元测试代码。现在我要求你制作一个简单的 游戏引擎，用来让游戏中的各个房间运转起来，从玩家收集输入，并且记住玩家 到了那一幕。我们将用到你刚学过的会话来制作一个简单的引擎，让它可以:
1. 为新用户启动新的游戏。 2. 将房间展示给用户。
3. 接受用户的输入。
4. 在游戏中处理用户的输入。
5. 显示游戏的结果，继续游戏的下一幕，知道玩家角色死亡为止。

为了创建这个引擎，你需要将我们久经考验的   搬过来，创建一个功 能完备的、基于会话的游戏引擎。这里的难点是我会先使用基本的 HTML 文件 创建一个非常简单的版本，接下来将由你完成它，基本的引擎是这个样子的:
'''
import web
from gothonweb import map

urls = (
'/game', 'GameEngine',
'/', 'Index',
)

app = web.application(urls, globals())
# little hack so that debug mode works with sessions
if web.config.get('_session') is None:
	store = web.session.DiskStore('sessions')
	session = web.session.Session(app,store,initializer={'room': None})
	web.config._session = session

else:
	session = web.config._session
	render = web.template.render('templates/', base="layout")

class Index(object):
	def GET(self):
			# this is used to "setup" the session with starting values
			session.room = map.START
			web.seeother("/game")

class GameEngine(object):
	def GET(self):
		if session.room:
			return render.show_room(room=session.room)
		else:
			# why is there here? do you need it?
		return render.you_died()

	def POST(self):
		form = web.input(action=None)
		# there is a bug here, can you fix it?
		if session.room and form.action:
			session.room = session.room.go(form.action)

		web.seeother("/game")

if __name__ == "__main__":
	app.run()

'''
这个脚本里你可以看到更多的新东西，不过了不起的事情是，整个基于网页的游 戏引擎只要一个小文件就可以做到了。这段脚本里最有技术含量的事情就是将会 话带回来的那几行，这对于调试模式下的代码重载是必须的，否则每次你刷新网 页，会话就会消失，游戏也不会再继续了。
在你运行 bin/app.py 之前，你需要修改 PYTHONPATH 环境变量。不知道什 么是环境变量?为了运行一个最基本的 Python 程序，你就得学会环境变量， Python 的这一点确实有点挫。不过没办法，用 Python 的人就喜欢这样:
在你的命令行终端，输入下面的内容:
	export PYTHONPATH=$PYTHONPATH:.
如果你用的是 Windows，那就输入以下内容:

	set PYTHONPATH=%PYTHONPATH%;.

你只要针对每一个命令行会话界面输入一次就可以了，不过如果你运行 Python 代码时看到了 import 错误，那你就需要去执行一下上面的命令，或者也许是因 为你上次执行的 有错才导致 import 错误的。

 接下来你需要删掉 templates/hello_form.html 和 templates/index.html， 然后重新创建上面代码中 到的两个模板。这里是一个非常简单的 templates/show_room.html 供你参考:

$def with (room)
<h1> $room.name </h1>
<pre> $room.description </pre>
$if room.name == "death":
	<p><a href="/">Play Again?</a></p>
$else:
	<p>
	<form action="/game" method="POST">
		- <input type="text" name="action"> <input
	type="SUBMIT"> </form>
	</p>

 这就用来显示游戏中的房间的模板。接下来，你需要在用户跑到地图的边界时， 用一个 模板告诉用户他的角色的死亡信息，也就是 templates/you_died.html 这个模板:

<h1>You Died!</h1>
<p>Looks like you bit the dust.</p>
<p><a href="/">Play Again</a></p>


准备好了这些文件，你现在可以做下面的事情了:
1. 让测试代码tests/app_tests.py再次运行起来，这样你就可以去测试这个游戏。 由于会话的存在，你可能顶多只能实现几次点击，不过你应该可以做出一些基本的 测试来。
2. 删除sessions/*下的文件，再重新运行一遍游戏，确认游戏是从一开始运行起 来的。
3. 执行pythonbin/app.py脚本，试玩一下你的游戏。
你需要和往常一样刷新和修正你的游戏，慢慢修改游戏的 HTML 文件和引擎，
直到你实现游戏需要的所有功能为止。

'''
#你的期末考试
'''
你有没有觉着我一下子给了你超多的信息呢?那就对了，我想要你在学习技能的 同时可以有一些可以用来鼓捣的东西。为了完成这节习题，我将给你最后一套需 要你自己完成的练习。你将注意到，到目前为止你写的游戏并不是很好，这只是 你的第一版代码而已。你现在的任务是让游戏更加完善，实现下面的这些功能:
'''

'''
1. 修正代码中所有我 到和没 到的 bug，如果你发现了新的 bug，你可以告诉我。
2. 改进所有的自动测试，让你可以测试更多的内容，直到你可以不用浏览器就能测到
所有的内容为止。
3. 让 HTML 页面看上去更美观一些。
4. 研究一下网页登录系统，为这个程序创建一个登录界面，这样人们就可以登录这个
   游戏，并且可以保存游戏高分。
5. 完成游戏地图，尽可能地把游戏做大，功能做全。
6. 给用户一个“帮助系统”，让他们可以查询每个房间里可以执行哪些命令。
7. 为你的游戏添加新功能，想到什么功能就添加什么功能。
8. 创建多个地图，让用户可以选择他们想要玩的一张来进行游戏。你
的 bin/app.py 应该可以运行 供给它的任意的地图，这样你的引擎就可以支持 多个不同的游戏。
9. 最后，使用你在习题 48 和 49中学到的东西来创建一个更好的输入处理器。你手 头已经有了大部分必要的代码，你只需要改进语法，让它和你的输入表单以及游戏 引擎挂钩即可。
祝你好运!
'''
#  下一步
'''
现在还不能说你是一个程序员。这本书的目的相当于给你一个“编程棕带”。你已 经了解了足够的编程基础，并且有能力阅读别的编程书籍了。读完这本书，你应 该已经掌握了一些学习的方法，并且具备了该有的学习态度，这样你在阅读其他 Python 书籍时也许会更顺利，而且能学到更多东西。
在 http://learnpythonthehardway.org/ 网站列出了一些你可以进一步阅读的免费 书籍，试着阅读它们，看看自己可以走多远。
或许，你现在已经可以开始鼓捣一些程序出来了。如果你手上有需要解决的问题， 试着写个程序解决一下。你一开始写的东西可能很挫，不过这没有关系。以我为 例，我在学每一种语言的初期都是很挫的。没有哪个初学者能写出完美的代码来， 如果有人告诉你他有这本事，那他只是在厚着脸皮撒谎而已。
最后，记住学习编程是要投入时间的，你可能需要至少每天晚上练习几个小时。 顺便告诉你，当你每晚学习 Python 的时候，我在努力学习弹吉他。我每天练 习 2 到 4 小时，而且还在学习基本的音阶。
每个人都是某一方面的菜鸟。
'''
#老程序员的建议		
'''
你已经完成了这本书而且打算继续编程。也许这会成为你的一门职业，也许你只 是作为业余爱好玩玩。无论如何，你都需要一些建议以保证你在正确的道路上继 续前行，并且让这项新的爱好为你带来最大程度的享受。
我从事编程已经太长时间，长到对我来说编程已经是非常乏味的事情了。我写这 本书的时候，已经懂得大约 20 种编程语言，而且可以在大约一天或者一个星 期内学会一门编程语言(取决于这门语言有多古怪)。现在对我来说编程这件事情
已经很无聊，已经谈不上什么兴趣了。当然这不是说编程本身是一件无聊的事情， 也不是说你以后也一定会这样觉得，这只是我个人在当前的感觉而已。
在这么久的旅程下来我的体会是:编程语言这东西并不重要，重要的是你用这些 语言做的事情。事实上我一直知道这一点，不过以前我会周期性地被各种编程语 言分神而忘记了这一点。现在我是永远不会忘记这一点了，你也不应该忘记这一 点。
你学到和用到的编程语言并不重要。不要被围绕某一种语言的宗教把你扯进去，
这只会让你忘掉了语言的真正目的，也就是作为你的工具来实现有趣的事情。
编程作为一项智力活动，是唯一一种能让你创建交互式艺术的艺术形式。你可以 创建项目让别人使用，而且你可以间接地和使用者沟通。没有其他的艺术形式能 做到如此程度的交互性。电影领着观众走向一个方向，绘画是不会动的。而代码 却是双向互动的。
编程作为一项职业只是一般般有趣而已。编程可能是一份好工作，但如果你想赚 更多的钱而且过得更快乐，你其实开一间快餐分店就可以了。你最好的选择是将 你的编程技术作为你其他职业的秘密武器。
技术公司里边会编程的人多到一毛钱一打，根本得不到什么尊敬。而在生物学、 医药学、政府部门、社会学、物理学、数学等行业领域从事编程的人就能得到足 够的尊敬，而且你可以使用这项技能在这些领域做出令人惊异的成就。
当然，所有的这些建议都是没啥意义的。如果你跟着这本书学习写软件而且觉得 很喜欢这件事情的话，那你完全可以将其当作一门职业去追求。你应该继续深入 拓展这个近五十年来极少有人探索过的奇异而美妙的智力工作领域。若能从中得 到乐趣当然就更好了。
最后我要说的是学习创造软件的过程会改变你而让你与众不同。不是说更好或更 坏，只是不同了。你也许会发现因为你会写软件而人们对你的态度有些怪异，也 许会用“怪人”这样的词来形容你。也许你会发现因为你会戳穿他们的逻辑漏洞而
他们开始讨厌和你争辩。甚至你可能会发现有人因为你懂得计算机怎么工作而觉 得你是个讨厌的怪人。
对于这些我只有一个建议: 让他们去死吧。这个世界需要更多的怪人，他们知道 东西是怎么工作的而且喜欢找到答案。当他们那样对你时，只要记住这是你的旅 程，不是他们的。“与众不同”不是谁的错，告诉你“与众不同是一种错”的人只是 嫉妒你掌握了他们做梦都不能想到的技能而已。
你会编程。他们不会。这真他妈的酷。
'''
```
###RESULT
```
NO
```
# LOG
20171109中午 刷完了所有题，但是真心讲后面这些就是类似于抄写代码，本着先刷完第一遍再说的态度先刷下来再说，后面这些题还是有些理解难度的，当你投入的时间不够的话，还是比较难以理解的。继续进步吧，死磕总是能磕下来的，等刷完 LP3THW了再来扣这些问题吧。由于 jianshu.com页面是有限制的，所有本文档只写了41-47，剩下的48-52题新启一个页面来填写。
