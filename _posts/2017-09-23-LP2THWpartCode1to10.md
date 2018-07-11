---
layout: post
title: 《笨办法学Python》记录-part1（习题1～10）
date: 2017-09-23
categories: blog
tags: [Python,笨办法学Python,LearnPython2TheHardWay,LP2THW]
description: 立个Flag开始学Python。
---
> 后续练习的习题均为《笨办法学Python》（Learn Python 2 The Hard Way，LP2THW）的练习代码，所用的是Python2.7版本。后续我会再刷一遍

## 例题复现：

> 先把原来的2和3夹生的代码转换成纯正的2代码（1～11题）

## 1.0 习题一
### 代码
```
print "Hello World!"
print "Hello Again"
print "I like typing this."
print "This is fun."
print "Yay! Printing."
print "I'd much rather you 'not'."
print 'I "said" do not touch this.'
#!/usr/bin/env python2
```
> 注：找到编辑好的文件（x.py）之后，右键采用IDLE.app（2.7）打开，按F5运行。

### 运行结果
```
Python 2.7.14 (v2.7.14:84471935ed, Sep 16 2017, 12:01:12)
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "copyright", "credits" or "license()" for more information.
>>> WARNING: The version of Tcl/Tk (8.5.9) in use may be unstable.
Visit http://www.python.org/download/mac/tcltk/ for current information.

=========== RESTART: /Users/yyy/Documents/Python_LP2THW/ex1py2.py ===========
Hello World!
Hello Again
I like typing this.
This is fun.
Yay! Printing.
I'd much rather you 'not'.
I "said" do not touch this.
>>>
```
---
## 2.0 习题一
### 代码
```
# A comment, this is so you can read your program later.
# Anything after the # is ignored by python.

print  "I could have code like this.测试拷贝中文到这里。"# and the comment after is ignored
# Pay attention that: In Python3 ,print() is a kind of "hanshu",don't forget the (),but in python2 the print do not need the ().
# You can also use a comment to "disable" or coment out a piece of code:

# print "This won't run."
print "This will run."
# I also try no "space" between the Print and the(),look what happend.


```

### 运行结果
```
Python 2.7.14 (v2.7.14:84471935ed, Sep 16 2017, 12:01:12)
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "copyright", "credits" or "license()" for more information.
>>> WARNING: The version of Tcl/Tk (8.5.9) in use may be unstable.
Visit http://www.python.org/download/mac/tcltk/ for current information.

=========== RESTART: /Users/yyy/Documents/Python_LP2THW/ex2py2.py ===========
I could have code like this.测试拷贝中文到这里。
This will run.
>>>
```
## 3.0 习题三
### 代码
```
print "I will now count my chickens:"

print "Hens",25+30/6# In Print,in python3 ,the result is 30.0,but in python2.0 it is 30.

# print 30／6

print "30／6"


print 30/6# The is a point float number

print 30.000/6.21# The is a point float number,more zero.

print "Roosters",100-25*3%4# I forget the function of % ，what the usage of it？#Attention that % is "qu yu shu"

print "Now I will count the eggs:"

print 3+2+1-5+4%2-1/4+6 # In python3 the result is 6.75,but in python it is 7.

print "Is it true that 3+2 < 5-7?"

print 3+2<5-7

print "what is 3+2?",3+2
print "what is 5-7?",5-7

print "Oh,tha's why it's False."
print "How about some more."

print "Is it greater?", 5 > -2
print "Is it greater or eaqual?" , 5 >= -2
print "Is it less or equal?", 5 <=- 2

## the cod below is for plus bonus。

```
### 结果
 ```
Python 2.7.14 (v2.7.14:84471935ed, Sep 16 2017, 12:01:12)
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "copyright", "credits" or "license()" for more information.
>>> WARNING: The version of Tcl/Tk (8.5.9) in use may be unstable.
Visit http://www.python.org/download/mac/tcltk/ for current information.

=========== RESTART: /Users/yyy/Documents/Python_LP2THW/ex3py2.py ===========
I will now count my chickens:
Hens 30
30／6
5
4.8309178744
Roosters 97
Now I will count the eggs:
7
Is it true that 3+2 < 5-7?
False
what is 3+2? 5
what is 5-7? -2
Oh,tha's why it's False.
How about some more.
Is it greater? True
Is it greater or eaqual? True
Is it less or equal? False
>>>
```

## 4.0习题4
### 代码
```
#  设置：给变量 车（cars）赋值100，每量车的空是4.0，司机是30个，旅客是90个。
# 车数量为100
cars = 100
# 每辆车里等空位是4
space_in_a_car = 4.0 #思考：这里为什么要用4.0浮点计算而不是4？
# 司机数量是30个。
drivers = 30
# 旅客人数为90个。
passengers =90

# 参数设置&参数计算：没有人开的车=车总数-司机数；有人开的车数=司机数量；有效空间数量=有人开的车数*每量车上的空。每辆车桑拿的平均旅客数=旅客总数／有人开的车数。

cars_not_driven = cars -drivers

cars_driven = drivers

carpool_capacity= cars_driven * space_in_a_car

average_passengers_per_car= passengers / cars_driven

# 打印 （字符串，变量-车总数，字符串）

print "There are", cars, "cars available."

print "There are only",drivers, "drivers available."

print "There will be", cars_not_driven,"empty cars today."

print "We can transport",carpool_capacity,"people today."

print "we have",passengers,"to carpool today."

print "We need to put about",average_passengers_per_car,"in each car.hahaha"

print "数学是一切科学的源头和归宿，Turtules乌龟程序“”"
```
### 结果
```
Python 2.7.14 (v2.7.14:84471935ed, Sep 16 2017, 12:01:12)
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "copyright", "credits" or "license()" for more information.
>>> WARNING: The version of Tcl/Tk (8.5.9) in use may be unstable.
Visit http://www.python.org/download/mac/tcltk/ for current information.

=========== RESTART: /Users/yyy/Documents/Python_LP2THW/ex3py2.py ===========
I will now count my chickens:
Hens 30
30／6
5
4.8309178744
Roosters 97
Now I will count the eggs:
7
Is it true that 3+2 < 5-7?
False
what is 3+2? 5
what is 5-7? -2
Oh,tha's why it's False.
How about some more.
Is it greater? True
Is it greater or eaqual? True
Is it less or equal? False
>>>
```

## 5.0 习题5
### CODE
```
# -- coding: utf-8 --
## 以下代码在py2下调试通过
my_name = "Zed A.Shaw"

my_age = 35 # not a lie

my_height = 74 #inches

my_weight = 180 #lbs

my_eyes = 'Blue' #注意：字符串内容可以选择单引号或者双引号。放在print函数后面加上括号就可以被打印出来。


my_teeth = 'White'

my_hair = 'Brown'

print "Let's talk about %s ." % my_name#格式化字符%s、%d。
# !!!只要将格式化的变量放到字符串中，再紧跟着一个百分号%，再紧跟着变量名即可。唯一要注意的地方是：如果你想要在字符串中通过格式化字符放入多个变量的时候，你需要将变量放到（）圆括号里，变量之间采用逗号，隔开。

print "He's %d inches tall." %my_height # Attention the words after % can be very nearby or canbe a SPACE in it.

print "He's %d pounds heavy." % my_weight

print "Actually that's not too heavy."

print "He's got %s eyes and %s hair."  %(my_eyes,my_hair)#在pyhon3中将%号转移到括号之外，最左端，而且左右参数可以塞到一个括号里，右侧可以有两个括号。

print "His teeth are usually %s depending on the coffee."  % my_teeth

# this line is tricky,try to get it exactly right

print "If I add %d,%d,and %d I get %d." %(my_age,my_height,my_weight,my_age+my_height + my_weight)
# 在26行受到32行的启发，知道了Py3下如何表示。
# 程序员喜欢用恼人的难度大简写来节约打字事件，我们尽早学会就可以读懂这些东西。

#Log
#本文件于20170928建立，20171023 Changed to 2.0 format.
```

### 运行结果
```
Python 2.7.14 (v2.7.14:84471935ed, Sep 16 2017, 12:01:12)
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "copyright", "credits" or "license()" for more information.
>>>
=========== RESTART: /Users/yyy/Documents/Python_LP2THW/ex5py3.py ===========
Let's talk about Zed A.Shaw .
He's 74 inches tall.
He's 180 pounds heavy.
Actually that's not too heavy.
He's got Blue eyes and Brown hair.
His teeth are usually White depending on the coffee.
If I add 35,74,and 180 I get 289.
>>>
```
## 6.0 习题6
### 代码
```
# 将“字符串”赋值给"变量x"，该字符串中有个位置是用“%d”（包含格式）来代替的。%d这个符号看起来有两个作用：第一个作用是“占位符”——证明这个位置将来会有个东西放在这里；第二个作用是“这个东西的格式”，既然其使用了%d，我认为其应该是digital——数字的。

x= "There are %d types of people." %10

# 建立了给新的变量binary,将字符串“binary”赋值给了它。一般来说，变量会用简单的写法，竟然也可以直接使用单词。
binary="binary"

do_not="don't"

y="Those who know %s and those who %s."%(binary,do_not)#如果你想要在字符串中通过格式化字符放入多个变量的时候，你需要将变量放到（）圆括号里，变量之间采用逗号，隔开。

print x# print() 是个函数，必须有（），在2.0系列里print不用（）；x变量是字符串。


print y #y变量也是字符串。

print "I said: %r."% x# 我想的出来%d= digital %s=string 那么%r是什么鬼？百分号%确实是连续出现的，前面是格式，后面是变量（输入）。【例如 %r%r就是是非常有用的一个，它的含义是“不管什 么都打印出来”】

print "I also said:'%s'."%y#百分号%确实是连续出现的，前面是格式，后面是变量（输入）。

hilarious = False #hilarious 是欢闹的意思，这是个布尔变量，这里给他赋值 false。

joke_evaluation = "Isn't that joke so funny?! %r"#这里只有一个格式和占位符，没有变量输入？

print (joke_evaluation% hilarious)#第一个%前面是个字符窜变量，紧跟一个布尔变量是要做啥？

w="This is the left side of..." # 字符串1

e= "a string with a right side." # 字符串2

print w+e # 中间用+号 将两个字符串连接起来。


 # 只要将格式化的变量放到字符串中，再紧跟着一个百分号%，再紧跟着变量名即可。唯一要注意的地方，是如果你想要在字符串中通过格式化字符放入多个变量的时候，[你需要将变量放到（）圆括号里，变量之间采用逗号，隔开。]
 #试着使用更多的格式化字符，例如%s、%d、%r。例如 %r%r就是是非常有用的一个，它的含义是“不管什 么都打印出来”。

```

### 结果
```
Python 2.7.14 (v2.7.14:84471935ed, Sep 16 2017, 12:01:12)
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "copyright", "credits" or "license()" for more information.
>>> WARNING: The version of Tcl/Tk (8.5.9) in use may be unstable.
Visit http://www.python.org/download/mac/tcltk/ for current information.

=========== RESTART: /Users/yyy/Documents/Python_LP2THW/ex6py2.py ===========
There are 10 types of people.
Those who know binary and those who don't.
I said: 'There are 10 types of people.'.
I also said:'Those who know binary and those who don't.'.
Isn't that joke so funny?! False
This is the left side of...a string with a right side.
>>>
```

## 7.0 习题7

### CODE
```
# -*- coding: utf-8 -*- #

print  "Mary had a little lamb."
print "Its fleece was white as %s."%'snow'#这里告诉我们，“”双引号和‘’单引号的作用是一样的？
print "And everywhere that Mary went."
print "."*10#what'd that do?字符串*10，惊叹可以连续出10个字符串……

end1="C"
end2="h"
end3="e"
end4="e"
end5="s"
end6="e"
end7="B"
end8="u"
end9="r"
end10="g"
end11="e"
end12="r"
end0= " "# 我新加的一个字符串---“空格”

#watch that comma at the end. try removing it to see what happens.在Py3里，更改了逗号的位置（无论是括号内外都没有什么影响，都不能使得 英文的姓名 之间出现 空格）；但是
print end1 + end2 + end3 + end4 + end5 + end6 ,#Why should press ENTER to change a line?
print end7 + end8 + end9 + end10 + end11 +end12

print ("------我们是有底线的------")
# 运行结果证明，我在两段文字之间加上空格字符串的方法是可以实现 原文py中的案例的。
print end1 + end2 + end3 + end4 + end5 + end6+end0+end7 + end8 + end9 + end10 + end11 +end12

```
## RESULT
```
Python 2.7.14 (v2.7.14:84471935ed, Sep 16 2017, 12:01:12)
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "copyright", "credits" or "license()" for more information.
>>> WARNING: The version of Tcl/Tk (8.5.9) in use may be unstable.
Visit http://www.python.org/download/mac/tcltk/ for current information.

=========== RESTART: /Users/yyy/Documents/Python_LP2THW/ex7py2.py ===========
Mary had a little lamb.
Its fleece was white as snow.
And everywhere that Mary went.
..........
Cheese Burger
------我们是有底线的------
Cheese Burger
>>>
```
---
## 8.0 题目8
### 代码
```
formatter ="%r %r %r %r"#注意：貌似这里定义了一个字符串格式的变量 formatter
# 下面这个是4个数字按照上面这个样子的格式打出来。
print formatter % (1,2,3,4)# 经过py3改造的代码，原来是{print formatter % (1, 2, 3, 4)}这明显是不行的。
# 下面这四个英文单词是按照上面的既定格式打出来的。
print formatter % ('one',"two","three","four")#字符串里可以用单引号或者双引号，都是可以的。但是为什么打印出来的one two等是带单引号的呢？
print formatter %(True,False,False,True)

print formatter% (formatter,formatter,formatter,formatter)
# 注意：%号后看是给某个格式，提供素材的，
print formatter %("I had this thing.","That you could type up right.","But it didn't sing.","So I said goodnight.")# 为什么倒数第二个是双引号？其他都是单引号？-作者提出了这个问题，当然我也发现了，但是经过观察和思考，我依然没有答案。



# LOG 20170929 测试通过。
#LOG 20171023 发现，在PY2里print("Hello!")和print"Hello!"都可以调试通过，但是PY3里只允许使用Print("Hello!")这样的方式。于是在本次，我将括号给去掉了。

```
### 测试结果

```
Python 2.7.14 (v2.7.14:84471935ed, Sep 16 2017, 12:01:12)
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "copyright", "credits" or "license()" for more information.
>>> WARNING: The version of Tcl/Tk (8.5.9) in use may be unstable.
Visit http://www.python.org/download/mac/tcltk/ for current information.

=========== RESTART: /Users/yyy/Documents/Python_LP2THW/ex8py2.py ===========
1 2 3 4
'one' 'two' 'three' 'four'
True False False True
'%r %r %r %r' '%r %r %r %r' '%r %r %r %r' '%r %r %r %r'
'I had this thing.' 'That you could type up right.' "But it didn't sing." 'So I said goodnight.'
>>>
```
---
## 9.0 第9题

###CODE
```
# Here's some new strange stuff, remember type it exactly.

days = "Mon Tue Wed Thu Fri Sat Sun"
# 注意：\n 应该是一个换行符号，新起一行的意思。即使是子啊字符串中，这个规定也是有用的。
months="Jan\nFeb\nMar\nApr\nMay\nJun\nJul\nAug"

print "Here are the days:",days
print "Here are the months:",months

# 打印一段字符串的情况是出现在——一段文字最前面打出3个双引号，最后面打出3个双引号。

print ("""
There's something going on here.
With the three double-quotes.
We'll be able to type as much as we like.
Even 4 lines if we want,or 5,or 6.
""")# 注意：这是打印一段文字的方法。

# LOG：20171023 在PY2中调试通过。

```
### RESULT
```
=========== RESTART: /Users/yyy/Documents/Python_LP2THW/ex9py2.py ===========
Here are the days: Mon Tue Wed Thu Fri Sat Sun
Here are the months: Jan
Feb
Mar
Apr
May
Jun
Jul
Aug

There's something going on here.
With the three double-quotes.
We'll be able to type as much as we like.
Even 4 lines if we want,or 5,or 6.

>>>
```
---
## 10 第10题
### CODE
```
# 让字符扩展到多行的方法一： 采用 \n 隔开，这是一个放入“新行”的作用。
# “转义序列(escape sequences)”-----\  and  \\ and ' ' and " "。
# 你需要告诉Python----- "I "understand" joe."   到底哪个是哪个的边界。——其实你是想让中间的“”也表达是 字符串，而不是真正的双引号。

# 方法1:" I am 6'2\" tall.' # 将 字符串中的“双引号”转意义了;'I am 6\'2" tall.'# 将 字符串中的单引号转意义了。

# 方法2: 使用三引号，在一组三引号"""之间放入任意多行文字。
tabby_cat ="\t I'm tabbed in."# \t 在这里是啥意义？感觉\t 的作用是往里面缩进了几个格子?
persian_cat= "I'm split \non a line."#(注意 此处的\n是新起一行的意思，和on混在一起容易发生混淆)发现\n前面加空格对显示没有影响，但是右侧加空格确有很大影响  打印的时候怎个行都向右移动了（多了个空格而已）。
backslash_cat = "I'm\\a\\cat."# 明明是打了双反斜杠，但是打印的时候就出现了一个反斜杠而已。
# 下面可以看到，要打印一段文字的话，段上端和下端各用三个双引号。
fat_cat="""
I'll do a list: # 这一行没有转义字符的时候就会靠最左侧。
\t* Cat food   # 发现了没有【\  t 】出来之后，其后面的字符都缩进了若干个字符。
\t* Fishies # 有了\t之后，统一缩进
\t* Catnip\n\t* Grass #Catnip和Grass本来是在一行的但是由于中间增加了一个转义字符【\  n】所以就另外起了一行文字。
"""
print tabby_cat
print persian_cat
print backslash_cat
print fat_cat

# 转义序列和格式化字符串放到一起，可以创建一种更复杂的格式。

#%r 打印出来的是你写在脚本里的内容，而%s打印出来的是你应该看到的内容。

```
### RESULT
```
=========== RESTART: /Users/yyy/Documents/Python_LP2THW/ex10py2.py ===========
	 I'm tabbed in.
I'm split
on a line.
I'm\a\cat.

I'll do a list: # 这一行没有转义字符的时候就会靠最左侧。
	* Cat food   # 发现了没有【\  t 】出来之后，其后面的字符都缩进了若干个字符。
	* Fishies # 有了	之后，统一缩进
	* Catnip
	* Grass #Catnip和Grass本来是在一行的但是由于中间增加了一个转义字符【\  n】所以就另外起了一行文字。

>>>
```





---
## x.题记、编辑器和参考资料
> **题记**：Python2.x和Python3.x在语法规则中发生了变化。鉴于大量的库采用了Python2.x，以及从对初学者的学习曲线的角度上讲（从Python2.x到Python3.x容易，反过来则坑多--沥川语），从2.x开始学还是有必要的。因此，LP2THW和LP3THW习题各刷一遍题还是很有必要的。好的，那么下边咱开始吧。
- **代码编辑器**：我喜欢用TextMate(在MacOS系统下写起来比较爽，而且输入中文的时候比较友好)，另安装了IDLE.app(2.7和3.6，两种运行环境，可以分别运行2.x和3.x的代码，打开之后按F5)。
- **参考资料**：《LP2THW（中文）》、《LP3THW》、[Practice Python网站](http://www.practicepython.org)、《教孩子学Python》（里面的画画和游戏程序很酷）。



## LOG
- 20170927 建立了此文件。
- 20170928 将前面做的几道例题（1～6）搬过来，以陈述的方式讲给大家听。本文件将持续更新。
- 20170929 在火车上创建了这习题7、8、9 、10这三个习题
- 20171022 创建了本文档，创建了 题记、编辑器、参考资料初稿。完成了1～4例题的转化和调试。
- 20171023 早上完成了5～7题的转化和调试并上传简书中。
- 20171023 白天完成了8～14题，并于晚上上传。每10道题成为一个文件。
- 20180711从简书转过来。
