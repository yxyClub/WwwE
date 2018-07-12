---
layout: post
title: 《笨办法学Python》记录-part3（习题21～40）
date: 2017-10-27
categories: blog
tags: [Python,笨办法学Python,LearPython2TheHardWay,LP2THW]
description: 立个Flag开始学Python。
---

> 后续练习的习题均为《笨办法学Python》的练习代码，所用的是Python2.7版本。

> 本文件是“《笨办法学Python2.x》教&学记录”的第二部分，记录11-20题的教学。

> 本文件是“《笨办法学Python2.x》教&学记录”的第3部分，记录21-30题的教学。

## 第21题

### CODE

```
#!/usr/bin/python
# -*- coding: utf-8 -*-
#第21题
# 学会用return来将变量设置为“一个函数的值”
def add(a,b):
	print "ADDING %d + %d"%(a,b)
	return a+b

def subtract(a,b):
	print "SUBTRACTING %d-%d"%(a,b)
	return a-b

def multiply(a,b):
	print "MULTIPLYING %d * %d"%(a,b)
	return a*b

def divide(a,b):
	print "DIVIDING %d/%d"%(a,b)
	return a/b

print "Let's do some math with just functions!"

age = add(30,5)

height= subtract(78,4)

weight=multiply(90,2)

iq=divide(100,2)

print "Age:%d,Height:%d,Weight:%d,IQ:%d"%(age,height,weight,iq)

# A puzzle for the extra credit,type it in anyway.
print "Here is a puzzle."
what=add(age,subtract(height,multiply(weight,divide(iq,2))))#这里是函数套函数，以某个函数的返回值当作输入参量。

print "That becomes:",what,"Can you do it by hand?"



```

### RESULT

```

# 以下是代码运行后所显示的结果
'''
Python 2.7.14 (v2.7.14:84471935ed, Sep 16 2017, 12:01:12)
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "copyright", "credits" or "license()" for more information.
>>>
============ RESTART: /Users/yyy/Documents/Python_LP2THW/ex21.py ============
Let's do some math with just functions!
ADDING 30 + 5
SUBTRACTING 78-4
MULTIPLYING 90 * 2
DIVIDING 100/2
Age:35,Height:74,Weight:180,IQ:50
Here is a puzzle.
DIVIDING 50/2
MULTIPLYING 180 * 25
SUBTRACTING 74-4500
ADDING 35 + -4426
That becomes: -4391 Can you do it by hand?
>>>
'''
```
---

## 第22题

### CODE
```
#!/usr/bin/python
# -*- coding: utf-8 -*-
#第22题
# 学会用return来将变量设置为“一个函数的值”

#本节的任务

- 这节以及下一节的习题中不会有任何代码，所以也不会有习题答案或者加分习题。
- 其实这节习题可以说是一个巨型的加分习题。
- 我将让你完成一个表格，让你回顾 你到现在学到的所有东西。
- 首先，回到你的每一个习题的脚本里，把你碰到的每一个词和每一个符号 (symbol，character 的别名)写下来。
- 确保你的符号列表是完整的。
- 下一步，在每一个关键词和字符后面写出它的名字，并且说明它的作用。
- 如果你 在书里找不到符号的名字，就上网找一下。
- 如果你不知道某个关键字或者符号的 作用，就回到用到该字符的章节通读一下，并且在脚本中测试一下这个字符的用 处。
- 你也许会碰到一些横竖找不到答案的东西，只要把这些记在列表里，它可以提示 你让你知道还有哪些东西不懂，等下次碰到的时候，你就不会轻易跳过了。
- 你的列表做好以后，再花几天时间重写一遍这份列表，确认里边的东西都是正确 的。
- 你可能觉得这很无聊，不过你还是需要坚持完成任务。
- 等你记住了这份列表中的所有内容，就试着把这份列表默写一遍。
- 如果发现自己 漏掉或者忘记了某些内容，就回去再记一遍。

# 你学到的东西
- 这种记忆练习是枯燥无味的，所以知道它的意义很重要。
- 它会让你明确目标，让 你知道你所有努力的目的。
- 在这节练习中你学会的是各种符号的名称，这样读代码对你来说会更加容易。
- 这 和学英语时记忆字母表和基本单词的意义是一样的，不同的是 Python 中会有 一些你不熟悉的字符。
- 慢慢做，别让它成为你的负担。
- 这些符号对你来说应该比较熟悉，所以记住它们 应该不是很费力的事情。
- 你可以一次花个 15 分钟，然后休息一下。
- 作息结合 可以让你学得更快，而且可以让你保持士气。
```
### RESULT

```

# 以下是代码运行后所显示的结果

```
---

## 第23题

### CODE
```
#!/usr/bin/python
# -*- coding: utf-8 -*-
#第23题
# 学会用return来将变量设置为“一个函数的值”
---
习题 23: 读代码
- 上一周你应该已经牢记了你的符号列表。
- 现在你需要将这些运用起来，再花一周的时间，在网上阅读代码。
- 这个任务初看会觉得很艰巨。
- 我将直接把你丢到深水 区呆几天，让你竭尽全力去读懂实实在在的项目里的代码。
- 这节练习的目的不是 让你读懂，而是让你学会下面的技能:
- 1. 找到你需要的 Python 代码。
- 2. 通读代码，找到文件。
- 3. 尝试理解你找到的代码。
- 以你现在的水平，你还不具备完全理解你找到的代码的能力，不过通过接触这些 代码，你可以熟悉真正的编程项目会是什么样子。
- 当你做这节练习时，你可以把自己当成是一个人类学家来到了一片陌生的大陆， 你只懂得一丁点本地语言，但你需要接触当地人并且生存下去。
- 当然做练习不会 碰到生存问题，这毕竟这不是荒野或者丛林。
- 你要做的事情如下:
- 1. 使用你的浏览器登录 bitbucket.org，搜索 “python”。
- 2. 忽略那些提到 “Python 3” 的项目，它们只会让你变迷糊。
- 3. 随便找一个项目，然后点进去。
- 4. 点击Source标签，浏览目录和文件列表，直到你看到以.py结尾的文件(setup.py 就别看了，这样的文件看了也没用)。
- 5. 从头开始阅读你找到的代码。把它的功能用笔记记下来。
- 6. 如果你看到一些有趣的符号或者奇怪的字串，你可以把它们记下来，日后再进行研究。
- 就是这样，你的任务是使用你目前学到的东西，看自己能不能读懂一些代码，看 出它们的功能来。
- 你可以先粗略地阅读，然后再细读。
- 也许你还可以试试将难度 比较大的部分一字不漏地朗读出来。
- 现在再试试其它三个站点:
 github.com
 launchpad.net
 koders.com

- 在这些网站你可能还会看到以.c结尾的奇怪文件，不过你只需要看.py结尾的 文件就可以了。

- 最后一个有趣的事情是你可以在这四个网站搜索“python”以外的你感兴趣的话 题，
- 例如你可以搜索“journalism(新闻)”，“cooking(厨艺)”，“physics(物理)”， 或者任何你感兴趣的话题。
- 你也许会找到一些你对你有用的，可以直接拿来用的 代码。
```
### RESULT

```

# 以下是代码运行后所显示的结果

```

----

## 第24题 更多练习

### CODE

```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第24题 更多练习

print "Let's practice everything."
print 'You\'d need to know \' bout escapes with \\ that do \n newlines and \t tabs.'#\是个转义字符，意思说：嘿 我后面这个 '单引号是个单独的单引号，不能和前面后面的单引号结合组成什么引号组。两个\\时候，前面的那个\是个转义字符，后面这个是被转意的对象；\n 这个转义字符不仅仅是转换意思的作用，更重要的是\n代表了新起一行；\t代表往后退一格。


poem = """
\tThe Lovely world
with logic so firmly planted
cannot discern \n the needs of love
nor comprehend passion from intuition
and requires an explanation
\n\t where there is none.
"""#注意连续的三对双引号是用来饮用一段文字的。忘记\t是啥意思了，但是从打印出来的样子来看前面是空出来几个格的。在源代码段落里新起的一行，其打印出来的样子依然是另起一行。但是，如果在代码里，同一行里如果出来了\n则在打印的时候会单独起一行。\n\t连用的时候，代表另起一行，并且前面空出几个格？

print "----------------------"
print poem
print "----------------------"

five= 10-2+3-6
print"This should be five: %s"% five#这里还是说占位符的事，在字符串里包含一个占位符，这个占位符是带格式的，注意后面是%加一个变量。

def secret_formula(started):#这里定义了一个函数secret_formula()
	jelly_beans= started*500#下面制造了3个变量jelly_beans,jars,crates，函数要求输入一个值started,函数最后返回了3个值。
	jars=jelly_beans/1000
	crates=jars/100
	return jelly_beans,jars,crates

start_point= 10000
#定义了一个变量名称为start_point的变量，这个变量被赋予了一个值。这个值被secret_formula()函数作为输入量引用，返回的三个量分别存在beans(和上面代码里的jelly_beans是啥关系？)、jars、crates中。
beans,jars,crates= secret_formula(start_point)

print "With a starting point of: %d"% start_point#start_point变量可以被引用到代码中。
print "We'd have %d beans,%d jars, and %d crates."%(beans,jars,crates)#上面的三个变量获得了值之后，分别赋给了3个变量。这3个变量外面包含了括号。

start_point = start_point/10#这里把start_point变量变为原来的1/10.

print "We can also do that this way:"
print "We'd have %d beans,%d jars,and %d crates."%secret_formula(start_point)#这里用函数返回的三个数值，外面不包含括号。



```

### RESULT

```
# 运行后的结果：
'''
============ RESTART: /Users/yyy/Documents/Python_LP2THW/ex24.py ============
Let's practice everything.
You'd need to know ' bout escapes with \ that do
 newlines and 	 tabs.
----------------------

	The Lovely world
with logic so firmly planted
cannot discern
 the needs of love
nor comprehend passion from intuition
and requires an explanation

	 where there is none.

----------------------
This should be five: 5
With a starting point of: 10000
We'd have 5000000 beans,5000 jars, and 50 crates.
We can also do that this way:
We'd have 500000 beans,500 jars,and 5 crates.
>>> ∂
'''
```
---

## 第25题

### CODE

```
'''
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第25题 更多更多练习

def break_words(stuff):
	""" This function will break up words for us."""
	words= stuff.split(' ')#这里是啥意思？
	return words

def sort_words(words):#sort mean:make the sequence of words.
	""" Sorts the words."""
	return sorted(words)

def print_first_word(words):
	"""Prints the first word after popping it off"""
	word=words.pop( 0 )#word to words
	print word

def print_last_word(words):
	"""Print the last word after poping it off."""
	word=words.pop(-1)
	print word

def sort_sentence(sentence):
	"""Takes in a full sentence and returns the sorted words."""
	words= break_words(sentence)
	return sort_words(words)

def print_first_and_last(sentence):
	"""Prints the first and last words of the sentence."""
	words=break_words(sentence)#NameError: global name 'sentence' is not defined
#ex25.print_first_and_last(sentence):WRONG#at last ,the debug pass.
	#print_first_and_last(sentence):OK!whats wrong?
	print_first_word(words)
	print_last_word(words)

def print_first_and_last_sorted(sentence):
	"""Sort the words then prints the first and last one."""
	words=sort_sentence(sentence)#This sentence can be debug nice，but the up one can not pass the debug。
	print_first_word(words)
	print_last_word(words)

```
## RESULT

```
Python 2.7.14 (v2.7.14:84471935ed, Sep 16 2017, 12:01:12)
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "copyright", "credits" or "license()" for more information.
>>>
============ RESTART: /Users/yyy/Documents/Python_LP2THW/ex25.py ============
>>>
>>> import ex25
>>> sentence = "All good things come to those who wait."
>>> words = ex25.break_words(sentence)
>>> words
['All', 'good', 'things', 'come', 'to', 'those', 'who', 'wait.']
>>> sorted_words = ex25.sort_words(words)
>>> sorted_words
['All', 'come', 'good', 'things', 'those', 'to', 'wait.', 'who']
>>> ex25.print_first_word(words)
All
>>> ex25.print_last_word(words)
wait.
>>> words
['good', 'things', 'come', 'to', 'those', 'who']
>>> ex25.print_first_word(sorted_words)
All
>>> ex25.print_last_word(sorted_words)
who
>>> sorted_words
['come', 'good', 'things', 'those', 'to', 'wait.']
>>>  sorted_words = ex25.sort_sentence(sentence)

  File "<pyshell#13>", line 2
    sorted_words = ex25.sort_sentence(sentence)
    ^
IndentationError: unexpected indent
>>> sorted_words = ex25.sort_sentence(sentence)
>>> sorted_words
['All', 'come', 'good', 'things', 'those', 'to', 'wait.', 'who']
>>> ex25.print_first_and_last(sentence)
All
wait.
>>> ex25.print_first_and_last_sorted(sentence)
All
who
>>>
'''
---------------------------加分题------------------------------

Python 2.7.14 (v2.7.14:84471935ed, Sep 16 2017, 12:01:12)
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "copyright", "credits" or "license()" for more information.
>>> WARNING: The version of Tcl/Tk (8.5.9) in use may be unstable.
Visit http://www.python.org/download/mac/tcltk/ for current information.

============ RESTART: /Users/yyy/Documents/Python_LP2THW/ex25.py ============
>>> import ex25
>>> help(ex25)
Help on module ex25:

NAME
    ex25

FILE
    /Users/yyy/Documents/Python_LP2THW/ex25.py

DESCRIPTION
    # -*- coding: utf-8 -*-
    # 第25题 更多更多练习

FUNCTIONS
    break_words(stuff)
        This function will break up words for us.

    print_first_and_last(sentence)
        Prints the first and last words of the sentence.

    print_first_and_last_sorted(sentence)
        Sort the words then prints the first and last one.

    print_first_word(words)
        Prints the first word after popping it off

    print_last_word(words)
        Print the last word after poping it off.

    sort_sentence(sentence)
        Takes in a full sentence and returns the sorted words.

    sort_words(words)
        Sorts the words.


>>> help(ex25.break_words)
Help on function break_words in module ex25:

break_words(stuff)
    This function will break up words for us.

>>> from ex25 import
SyntaxError: invalid syntax
>>> from ex25 import *
>>> brake_words("My Name is Andy Duffren ！")
Unsupported characters in input
```
----

## 第26题

### CODE

```
#!/usr/bin/python
# -*- coding: utf-8 -*-
-------------------------
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第26题 恭喜你，现在可以考试了!
##下面这是本节课的原文。
>'''
你已经差不多完成这本书的前半部分了，不过后半部分才是更有趣的。你将学到逻辑，并通过条件判断实现有用的功能。

在你继续学习之前，你有一道试题要做。这道试题很难，因为它需要你修正别人写的代码。当你成为程序员以后，你将需要经常面对别的程序员的代码，也许还 有他们的傲慢态度，他们会经常说自己的代码是完美的。

这样的程序员是自以为是不在乎别人的蠢货。优秀的科学家会对他们自己的工作持怀疑态度，同样，优秀的程序员也会认为自己的代码总有出错的可能，他们会先假设是自己的代码有问题，然后用排除法清查所有可能是自己有问题的地方，最后才会得出“这是别人的错误”这样的结论。在这节练习中，你将面对一个水平糟糕的程序员，并改好他的代码。

我将习题 24 和 25胡乱拷贝到了一个文件中，随机地删掉了一些字符，然后添加了一些错 误进去。大部分的错误是 Python在执行时会告诉你的，还有一些算术错误是你 要自己找出来的。再剩下来的就是格式和拼写错误了。

所有这些错误都是程序员很容易犯的，就算有经验的程序员也不例外。

【你的任务】是将此文件修改正确，用你所有的技能改进这个脚本。你可以先分析这个文件，或者你还可以把它像学期论文一样打印出来，修正里边的每一个缺陷，重复修正和运行的动作，直到这个脚本可以完美地运行起来。在整个过程中不要寻求帮助，如果你卡在某个地方无法进行下去，那就休息一会晚点再做。

就算你需要几天才能完成，也不要放弃，直到完全改对为止。

最后要说的是，这个练习的目的不是写程序，而是修正现有的程序，你需要访问下面的网站: http://learnpythonthehardway.org/exercise26.txt从那里把代码复制粘贴过来，命名为ex26.py，这也是本书唯一一处允许你复制 粘贴的地方。
'''




##下面这个是粘贴来的代码原文：(修改前)



'''
def break_words(stuff):
    """This function will break up words for us."""
    words = stuff.split(' ')
    return words

def sort_words(words):
    """Sorts the words."""
    return sorted(words)

def print_first_word(words)
    """Prints the first word after popping it off."""
    word = words.poop(0)
    print word

def print_last_word(words):
    """Prints the last word after popping it off."""
    word = words.pop(-1
    print word

def sort_sentence(sentence):
    """Takes in a full sentence and returns the sorted words."""
    words = break_words(sentence)
    return sort_words(words)

def print_first_and_last(sentence):
    """Prints the first and last words of the sentence."""
    words = break_words(sentence)
    print_first_word(words)
    print_last_word(words)

def print_first_and_last_sorted(sentence):
    """Sorts the words then prints the first and last one."""
    words = sort_sentence(sentence)
    print_first_word(words)
    print_last_word(words)


print "Let's practice everything."
print 'You\'d need to know \'bout escapes with \\ that do \n newlines and \t tabs.'

poem = """
\tThe lovely world
with logic so firmly planted
cannot discern \n the needs of love
nor comprehend passion from intuition
and requires an explantion
\n\t\twhere there is none.
"""


print "--------------"
print poem
print "--------------"

five = 10 - 2 + 3 - 5
print "This should be five: %s" % five

def secret_formula(started):
    jelly_beans = started * 500
    jars = jelly_beans \ 1000
    crates = jars / 100
    return jelly_beans, jars, crates


start_point = 10000
beans, jars, crates == secret_formula(start-point)

print "With a starting point of: %d" % start_point
print "We'd have %d jeans, %d jars, and %d crates." % (beans, jars, crates)

start_point = start_point / 10

print "We can also do that this way:"
print "We'd have %d beans, %d jars, and %d crabapples." % secret_formula(start_pont


sentence = "All god\tthings come to those who weight."

words = ex25.break_words(sentence)
sorted_words = ex25.sort_words(words)

print_first_word(words)
print_last_word(words)
.print_first_word(sorted_words)
print_last_word(sorted_words)
sorted_words = ex25.sort_sentence(sentence)
prin sorted_words

print_irst_and_last(sentence)

   print_first_a_last_sorted(senence)

'''

## 下面这个是修改后的代码：


```
### RESULT

```
这里我不准备修改了，直接进入下一题。
```
---

## 第27题

### CODE

```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第27题 ：记住逻辑关系
###书中原文：
''' 这里告诉你一个记住某样东西，而不让自己抓狂的方法:在一整天里，每次记忆一小部分，把你最需要加强的部分标记起来。不要想着在两小时内连续不停地背诵，这不会有什么好的结果。不管你花多长时间，你的大脑也只会留住你在前 15 或者 30 分钟内看过的东西。
取而代之，你需要做的是创建一些索引卡片，卡片有两列内容，正面写下逻辑关系，反面写下答案。你需要做到的结果是:拿出一张卡片来，看到正面的表达式， 例如 “True or False”，你可以立即说出背面的结果是 “True”!坚持练习，直到 你能做到这一点为止。
一旦你能做到这一点了，接下来你需要每天晚上自己在笔记本上写一份真值表出来。不要只是抄写它们，试着默写真值表，如果发现哪里没记住的话，就飞快地撇一眼这里的答案。这样将训练你的大脑让它记住整个真值表。
'''
### 真值表
NOT --------------------- True?

not False---------------True
not True----------------False

-------------------------------------------
OR------------------------True?

True or False-----------True

True or True------------True

False or True----------True

False or False---------False


--------------------------------------------
AND-----------------------True?
True and False---------False
True and True-----------True
False and True----------False
False and False---------False


----------------------------------------
NOT OR---------------------True?

not(True or False)-------False
not(True or True)--------False
not(False or True)-------False
not(False or False)-------True


----------------------------------------
NOT AND--------------------True?

not(True and False)------True
not(True and True)-------False
not(False and True)------True
not(False and False)-----True

-----------------------------------------
!=      ------------------------True?
1!=0 ------------------------True
1!=1-------------------------False
0!=1------------------------True
0!=1------------------------False

------------------------------------------
==        ------------------   True?#在Python中“=”表示赋值；“==”表示相等。
1==0 ------------------False
1==1-------------------True
0==1-------------------False
0==0-------------------True

本书不要求你成功或者失败，只要每天尽力去学，在尽力的基础上，多花一点功夫就可以了。

```
### RESULT

```
尽快记住这些逻辑关系。
但是我一看一眼我也知道，True or Flase。
别问我为啥，我就是知道。

```
---
## 第28题

> 这里作者试图告诉我们，怎么进行逻辑判断，我这里掌握的没有问题，感觉比较简单，一次通过。

### CODE

```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第28题 布尔表达式练习
'''
下面每一个练习，请你写出你认为的答案：
1.True and True=True
2.False and True=False
3.1==1 and 2==1    False
4."test"=="test"  True
5.1==1  or 2!=1    True
6.True and 1==1    True
7.False and 0!=0    False
8.True or 1==1  True
9."test"=="testing"   False
10.1!=0 and 2==1  False
11."test"!="testing"  True
12."test"==1   False
13. not(True and False)   True
14.not(1==1 and 0!=1) False
15.not(10==1 or 1000==1000) False
16.not(1!=10 or 3==4) False
17.not ("testing"=="testing" and "Zed"=="Cool Guy") True
18.1==1 and not("testing"==1 or 1==0)  True
19."chunky"=="bacon" and not(3==4 or 3==3)  False
20.3==3 and not("testing"=="testing" or "Python"=="Fun")   False
'''
```
### RESULT

```
## 执行结果,如下：
'''
Last login: Sat Oct 28 14:26:32 on ttys000
itifadeMacBook-Pro:~ yyy$ python
Python 2.7.14 (v2.7.14:84471935ed, Sep 16 2017, 12:01:12)
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> True and True
True
>>> False and True
False
>>> 1==1 and 2==1
False
>>> "test"=="test"
True
>>> 1==1  or 2!=1
True
>>> rue and 1==1
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'rue' is not defined
>>> True and 1==1
True
>>> False and 0!=0
False
>>> True or 1==1
True
>>> "test"=="testing"
False
>>> 1!=0 and 2==1
False
>>> "test"!="testing"
True
>>> "test"==1
False
>>> not(True and False)
True
>>> not(1==1 and 0!=1)
False
>>> not(10==1 or 1000==1000)
False
>>> not(1!=10 or 3==4)
False
>>> not ("testing"=="testing" and "Zed"=="Cool Guy")
True
>>> 1==1 and not("testing"==1 or 1==0)
True
>>> "chunky"=="bacon" and not(3==4 or 3==3)
False
>>> 3==3 and not("testing"=="testing" or "Python"=="Fun")
False
>>>
'''


```
---

## 第29题

### CODE
```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第29题 if 语句
people=20
cats=30
dogs=15


if people < cats:
	print"Too many cats! The world is doomed!"

if people > cats:
	print "Not many cats! The world is saved!"

if people > dogs:
	print "The world is dry!"

dogs += 5

if people>=dogs:
	print "People are greater than or equal to dogs."

if people<= dogs:
	print"People are less than or equal to dogs."


if people==dogs:
	print"People are dogs."
```
### RESULT

```
# 运行后的结果：
'''
Python 2.7.14 (v2.7.14:84471935ed, Sep 16 2017, 12:01:12)
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "copyright", "credits" or "license()" for more information.
>>>
============ RESTART: /Users/yyy/Documents/Python_LP2THW/ex29.py ============
Too many cats! The world is doomed!
The world is dry!
People are greater than or equal to dogs.
People are less than or equal to dogs.
People are dogs.
>>>
'''
```
---

## 第30题

### CODE
```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第30题:Else 和If
people=30

cars=40

buses=15


if cars> people:
	print"We should take the cars."#此行被打印。
elif cars< people:
	print "We should not take the cars."
else:
	print "We can't decide."

if buses > cars:
	print "That's too many buses."
elif buses< cars:# 此行被打印。
	print "Maybe we could take the buses."
else:
	print "We still can't decide."

if people > buses:
	print "Alright,let's just tkae the buses."#打印
else:
	print "Fine,let's stay home then."
```
### RESULT

```

# 运行后的结果：
'''
Python 2.7.14 (v2.7.14:84471935ed, Sep 16 2017, 12:01:12)
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "copyright", "credits" or "license()" for more information.
>>> WAR-NING: The version of Tcl/Tk (8.5.9) in use may be unstable.
Visit http://www.python.org/download/mac/tcltk/ for current information.

============ RESTART: /Users/yyy/Documents/Python_LP2THW/ex30.py ============
We should take the cars.
Maybe we could take the buses.
Alright,let's just tkae the buses.
>>>
'''
```
---

## LOG

- 20171027 创建。早上做了3题，其实前2题也不算做，根本没敲代码。
- 20171027 反思，中午闲聊，玩农场游戏，结果只剩下30分时间来敲代码。这样下去，所有的计划和目标都是不可能完成的。
- 20171028 增加了24-25题的练习，其中25题反复出现问题，调试了4～5个回合，才调试完。
- 20171029 从28日完开始写26～28，半夜一直调试到凌晨12点半，做完了28题，感觉还行。（以后不能熬夜，告诉你好多次了，每次总是违背。）
- 20171029 更新了29和30题，感想：以前还是有一定的编程基础的，所以这里提到fen zhi yu ju
