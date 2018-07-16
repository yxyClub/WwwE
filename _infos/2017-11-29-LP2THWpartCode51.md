---
layout: post
title: 《笨办法学Python》记录-part7（习题51）
date: 2017-11-09
categories: blog
tags: [Python,笨办法学Python,LearPython2TheHardWay,LP2THW]
description: 立个Flag开始学Python。
---

> test

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

form = web.input(name="Nobody", greet=None)

 if form.greet:
	 greeting ="%s, %s" % (form.greet, form.name)
	 return render.index(greeting =greeting)
else:
	return "ERROR:greet is required."

# 创建HTML表单

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


# 然后将bin/app.py改成这样：

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

#将template/index.html  改成这样：

$def with (greeting)

$if greeting:
	I just wanted to say <em style="color:green;font-size:2em;">$greeting</em>
$else:

	<em>Hello</em>,world!

#然后把templates/hello_form.html改成这样：


<h1>Fill Out This Form</h1>
<form action="/hello" method="POST">
	A Greeting: <input type= "text" name ="greet">
	<br/>
	Your Name:<input type="text" name= "name">
	<br/>
	<input type="submit">
</form>

上面这些修改的目的，是将每一个页面顶部和底部的反复用到的“boilerplate”代 码剥掉。这些被剥掉的代码会被放到一个单独的 templates/layout.html 文件 中，从此以后，这些反复用到的代码就由 layout.html 来 供了


# 上面的都改好以后，创建一个 templates/layout.html 文件，内容如下:


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


# 为表单撰写自动测试代码

使用浏览器测试web程序是很容易的，只要点刷新按钮就可以了。不过毕竟我们是程序员嘛，如果我们可以歇一歇代码来测试我们的程序，为什么还要重复手动测试呢？接下来，你要做的是，就是为你的 web 程序写一个小测试。这回用到你在ex47里学到的东西，如果不记得的话，可以回去复习一下。

为了让 Python 加载bin/app.py并进行测试，你需要先做一点准备工作。首先是创建一个bin/__init__.py空文件，这样 Python 就会将 bin/ 当做一个目录了。(在《习题 52》中你会去修改 __init__.py，不过这是后话。)
我还为 lpthw.web创建了一个简单的小函数，让你判断(assert)web程序的响应，这个函数有一个很合适的名字，叫做assert_response.创建一个tests/tools.py文件，内容如下：

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

$ nosetests
.
.............................
Ran 1 test in 0.059s

OK


# 文字部分

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


# 加分习题

1. 阅读和 HTML 相关的更多资料，然后为你的表单设计一个更好的输出格式。你可 以先在纸上设计出来，然后用 HTML 去实现它。
2. 这是一道难题，试着研究一下如何进行文件上传，通过网页上传一张图像，然后将 其保存到磁盘中。
 3. 更难的难题，找到 HTTP RFC 文件(讲述 HTTP 工作原理的技术文件)，然后努 力阅读一下。这是一篇很无趣的文档，不过偶尔你会用到里边的一些知识。
4. 又是一道难题，找人帮你设置一个 web 服务器，例如 Apache、Nginx、或者 thttpd。 试着让服务器伺服一下你创建的 .html 和 .css 文件。如果失败了也没关系，web 服务器本来就都有点挫。
5. 完成上面的任务后休息一下，然后试着多创建一些 web 程序出来。你应该仔细阅 读 web.py (它和 lpthw.web 是同一个程序)中关于会话(session)的内容，这样你可 以 明白如何保持用户的状态信息。
'''
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
