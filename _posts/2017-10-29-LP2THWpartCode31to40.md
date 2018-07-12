---
layout: post
title: 《笨办法学Python》记录-part4（习题31～40）
date: 2017-10-29
categories: blog
tags: [Python,笨办法学Python,LearPython2TheHardWay,LP2THW]
description: 立个Flag开始学Python。
---

> 本文件是“《笨办法学Python2.x》教&学记录”的第4部分，记录31-40题的教学。

---

## 第31题

### CODE

```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第31题 作出决定
print "You enter a dark room with two doors.Do you go through door #1 or door #2?"

door = raw_input(">")

if door == "1":
	print "There's a giant bear here eating a cheese cake.What do you do ?"
	print "1.Take the cake."
	print "2.Scream at the bear."

	bear = raw_input(">")

	if bear=="1":#你可以在“if 语句”内部再放一个“if语句”。这是一个很强大的功能，可以用来创建嵌套(nested)的决定，其中的一个分支将引向另一个分支的子分支。
		print "The bear eats your face off.Good job!"
	elif bear=="2":
		print "The bear eats your legs off.Good job!"
	else:
		print"Well,doing %s is probably better.Bear runs away."% bear

elif door=="2":
	print "You stare into the endless abyss at Cthlhu's retina."
	print "1.Blueberries"
	print "2.Yellow jacket clothespins."
	print "3.Understanding revolvers yelling melodies."

	insanity = raw_input(">")

	if insanity =="1" or insanity =="2":
		print "Your body survives powered by a mind of jello.Good job!"
	else:
		print "The insanity rots your eyes into a pool of muck.Good job!"
else:
	print"You stumble around and fall on a knife and die.Good job!"
```
### RESULT

```
# 运行后的结果：
'''
It could fun freely nice！

'''
```
---
## 第32题
### CODE

```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第32题 循环和列表（for-loop）
'''
这里有个例子，关于列表：
hairs = ['brown','blond','red']#左方括号是“打开”列表，右括号是“结束”。将变量赋于等号左侧的变量。
eyes = ['brown','blue','green']
weights = [1,2,3,4]
'''
# 编程代码开始：
the_count = [1,2,3,4,5]
fruits = ['apples','oranges','pears','apricots']
change = [1,'pennies',2,'dimes',3,'quarters']
#this first kind of for-loop goes through a list

for number in the_count:
	print "This is count %d"%number

# same as above
for fruit in fruits:
	print "A fruit of type: %s"% fruit

#also we can go through mixed lists too
# notice we have to use %r since we don't know what's in it
for i in change:
	print"I got %r" % i

#we can also build listd,first start with an empty one
elements = []

# then use the range function to do 0 to 5 counts
for i in range(0,6):#此处，可以将element赋值为range(0,6) 而无需使用for循环？
	print "Adding %d to the list."%i
	# append is a function that lists understand
	elements.append(i)#在Python文档中找到关于列表的内容，仔细阅读看看支持哪些操作？这里的操作是往列表变量elements中使用range()函数，依次添加。

# now we can print them out too
for i in elements:# 有没有发现，此处的循环函数中没有next。
	print "Element was: %d"%i
'''
```
### RESULT

```
# 运行后的结果：
'''
Python 2.7.14 (v2.7.14:84471935ed, Sep 16 2017, 12:01:12)
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "copyright", "credits" or "license()" for more information.
>>> WARNING: The version of Tcl/Tk (8.5.9) in use may be unstable.
Visit http://www.python.org/download/mac/tcltk/ for current information.

============ RESTART: /Users/yyy/Documents/Python_LP2THW/ex32.py ============
This is count 1
This is count 2
This is count 3
This is count 4
This is count 5
A fruit of type: apples
A fruit of type: oranges
A fruit of type: pears
A fruit of type: apricots
I got 1
I got 'pennies'
I got 2
I got 'dimes'
I got 3
I got 'quarters'
Adding 0 to the list.
Adding 1 to the list.
Adding 2 to the list.
Adding 3 to the list.
Adding 4 to the list.
Adding 5 to the list.
Element was: 0
Element was: 1
Element was: 2
Element was: 3
Element was: 4
Element was: 5
>>>

```
---

## 第33题

### CODE
```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第33题 While循环（while-loop循环）
'''
如果，某一行是以冒号（colon）结尾，意味着接下来的内容是一个新的代码片段，新的代码片段是需要被缩进的。
上一题说是for loop循环，但是实际上并没有发现loop。
本题诗练习 while-loop循环，这里说到while有一个问题就是有时候它永远不会结束，所以做了如下规定：
1尽量少用while-loop,大部分时候使用for-loop比较好。
2重复检查你的while 语句，确保布尔表达式最终会变成False
3如果不确定，就在while-loop结尾打印出你想要测试的值，看看变化
'''
# 好了，现在开始编程

i=0

numbers=[]

while i < 6:
	print "At the top i is %d"% i
	numbers.append(i)
	i = i + 1
	print "Number now:",numbers
	print "At the bottom i is %d"% i

print  "The numbers:"

for num in numbers:
	print num
```
### RESULT

```
# 运行后的结果：
'''
Python 2.7.14 (v2.7.14:84471935ed, Sep 16 2017, 12:01:12)
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "copyright", "credits" or "license()" for more information.
>>>
============ RESTART: /Users/yyy/Documents/Python_LP2THW/ex33.py ============
At the top i is 0
Number now: [0]
At the bottom i is 1
At the top i is 1
Number now: [0, 1]
At the bottom i is 2
At the top i is 2
Number now: [0, 1, 2]
At the bottom i is 3
At the top i is 3
Number now: [0, 1, 2, 3]
At the bottom i is 4
At the top i is 4
Number now: [0, 1, 2, 3, 4]
At the bottom i is 5
At the top i is 5
Number now: [0, 1, 2, 3, 4, 5]
At the bottom i is 6
The numbers:
0
1
2
3
4
5
>>>
'''
#加分习题
#> 下述加分题，并没有做，将来再刷的时候再做吧？
''''
1. 将这个 while 循环改成一个函数，将测试条件(i < 6)中的 6 换成一个变量。 2. 使用这个函数重写你的脚本，并用不同的数字进行测试。

3. 为函数添加另外一个参数，这个参数用来定义第 8 行的加值 + 1 ，这样你就可以 让它任意加值了。
4. 再使用该函数重写一遍这个脚本。看看效果如何。
5. 接下来使用 for-loop 和 range 把这个脚本再写一遍。你还需要中间的加值操作
  吗?如果你不去掉它，会有什么样的结果?

# 解释：很有可能你会碰到程序跑着停不下来了，这时你只要按着 CTRL 再敲 c (CTRL-c)， 这样程序就会中断下来了。
# 加分题：
'''
```
---

## 第34题

### CODE

```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第34题 函数和文件--序数和基数
'''
由于你一辈子都在跟序数打交道，所以你需要用这种方式来获得基数，只要减 1 就都搞定了。
记住:ordinal==有序，以1开始：cardinal==随机选取，以0开始。（随机？选取？？）
'''
# 编程开始：
code-block:: python#这是要怎样？
animals=['bear','python','peacock','kangaroo','whale','platypus']
1. The animal at 1.
2. The 3rd animal.
3. The 1st animal.
4. The animal at 3.
5. The 5th animal.
6. The animal at 2.
7. The 6th animal.
8. The animal at 4.

```
### RESULT

```
# 运行后的结果：
'''
运行该程序提示 code-block后的冒号“：”是拼写错误。
这个程序貌似不用运行？
是不是，这个题只是告诉你：按照人类的顺序习惯是从1开始的，1-2-3-4-5，按照机器的习惯是索引的，所以从0开始编号，index(0)、index(1)、index(2)....

# 加分习题
1.上网搜索一下关于序数(ordinalnumber)和基数(cardinalnumber)的知识并阅读一下。
2. 以你对于这些不同的数字类型的了解，解释一下为什么 “January 1, 2010” 里是2010 而不是2009?(提示:你不能随机挑选年份。)
3.再写一些列表，用一样的方式作出索引，确认自己可以在两种数字之间互相翻译。
4. 使用 python 检查自己的答案。

上述「加分题」，我并没有做，因为我没看明白作者到底在说什么？

警告：会有程序员告诉你让你去阅读一个叫“Dijkstra”的人写的关于数字的话题。我建议你 还是不读为妙。除非你喜欢听一个在编程这一行刚兴起时就停止从事编程了的人对 你大喊大叫。

'''
```
---

## 第35题

### CODE

```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第35题 分支和函数

from sys import exit

def glod_room():
	print"This room is full of gold. How much do you take?"

	next = raw_input(">")
	if  "0" in next or "1" in next:
		how_much = int(next)
	else:
		dead("Man,learn to type a number.")

	if how_much< 50:
		print"Nice,you're not greedy,you win!"
		exit(0)
	else:
		dead("You greedy bastard!")


def bear_room():
	print "There is a bear here."
	print "The bear has a bunch of honey."
	print "The fat bear is in front of another door."
	print "How are you going to move the bear?"#?
	bear_moved=False

	while True:
		next = raw_input (">")

		if next == "take honey":
			dead("The bear looks at you then slaps your face off.")
		elif next=="taunt bear" and not bear_moved:
			print "The bear has moved from the door.You can go through it now."
			bear_moved= True
		elif next=="taunt bear" and bear_moved:
			dead("The bear gets pissed off and chews your leg off.")
		elif next=="open door" and bear_moved:
			glod_room()
		else:
			print"I got no idea what that means."

def cthulhu_room():
	print "Here you see the great evil Cthulhu."
	print "He,it,whatever stares at you and you go insane."
	print "Do you flee for your life or eat your head?"

	next = raw_input(">")

	if "flee" in next:
		start()
	elif "head" in next:
		dead("Well that was tasty!")
	else:
		cthulhu_room()


def dead(why):
	print why ,"Good job!"
	exit(0)

def start():
	print "You are in a dark room."
	print "There is a door to your right and left."
	print "Which one do you take?"

	next= raw_input(">")

	if next == "left":
		bear_room()#
	elif next == "right":
		cthulhu_room()
	else:
		dead("You stumble around the room untill you starve.")


start ()#

```
### RESULT

```
# 运行后的结果：
'''
Python 2.7.14 (v2.7.14:84471935ed, Sep 16 2017, 12:01:12)
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "copyright", "credits" or "license()" for more information.
>>> WARNING: The version of Tcl/Tk (8.5.9) in use may be unstable.
Visit http://www.python.org/download/mac/tcltk/ for current information.

============ RESTART: /Users/yyy/Documents/Python_LP2THW/ex35.py ============
You are in a dark room.
There is a door to your right and left.
Which one do you take?
>left
There is a bear here.
The bear has a bunch of honey.
The fat bear is in front of another door.
How are you going to move the bear?
>taunt bear
The bear has moved from the door.You can go through it now.
>open door
This room is full of gold. How much do you take?
>ak47
Man,learn to type a number. Good job!
>>>

'''
#加分习题:

'''
1. 把这个游戏的地图画出来，把自己的路线也画出来。

2. 改正你所有的错误，包括拼写错误。

3. 为你不懂的函数写注解。记得文档注解该怎么写吗?

4. 为游戏添加更多元素。通过怎样的方式可以简化并且扩展游戏的功能呢?

5. 这个 gold_room 游戏使用了奇怪的方式让你键入一个数字。这种方式会导致什么
样的 bug? 你可以用比检查 0、1 更好的方式判断输入是否是数字吗?int()这 个函数可以给你一些头绪。

'''
# 我的常见错误：
# 加分题，我这次没做，2刷的时候做吧。
'''
在我输入这些代码的时候，我经常会把False输错成Flase,立此存照，以后要改过来。
'''
```
---

## 第36题

### CODE

```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第36题 设计和调试
'''
# If 语句的规则
1.每个if语句必须包含一个else.
2. 如果这个else永远都不应该被执行到，因为它本身没啥意义，，
那么你必须在else后使用一个叫做die到函数，让他打印出错误信息并四给你看。
3.If语句嵌套不要超过2层，尽量保持1层。如果if里还有if，那你就需要把第二个if移动到另一个函数里。
4.将if语句当作段落来对待，其中每一个if，elif,else组合就跟一个段落的句子组合一样，在这种组合的最前面和最后面留一个空行做区分。
5.你的布尔测试应该很简单，如果他们很复杂的话，你需要将她们的元算是钱放到一个变量里，并为变量取一个好名字。

# 循环的规则
1.只有在循环永不停止时候使用while循环，着意味着你可能永远都用不到，这条只在Python中成立。
2.其他类型的循环都使用“for循环”，尤其是在循环的对象数量固定或者有限的情况下。

# 调试（debug）的小技巧

1.不要使用debugger,这些只会让你更困惑。
2.最好的调试方法是使用print在你各个想要检查的关键环节，将关键变量打印出来，从而检查哪些是否有错。
3.让程序一部分一部分地运行起来。不要等一个很长的脚本写完了才去运行它，写一点，运行一点，再修改一点。

# 家庭作业
写一个和上节练习类似的游戏。同类的任何题材游戏都可以。作为加分习题，你可以尽量多使用列表 函数 模组（习题13）
先画地图，再写代码。
最后一个建议：美个程序员在开始一个新的大项目的时候，都会被非理性的恐惧影响到，为了避免这种恐惧，她们会拖延时间，到最后一事无成。我有时候也会这样，每个人都会有这样的经历，避免这种情况的最好的方法是把自己要做的事情列表出来，每次完成一样。
开始做吧。先做一个小一点的版本，扩充它让它变大，把自己要完成的事情一一列出来，然后逐个完成就可以了。
'''


```

### RESULT

```
# 运行后的结果：
'''
itifadeMacBook-Pro:~ yyy$ python  


'''
```
---

## 第37题
### CODE

```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第37题 复习各种符号
##Keywords（关键字）
 - and
 - del
 - from
 - not
 - while
 - as
 - elif
 - global
 - or
 - with
 - assert
 - else
 - if
 - pass
 - yield
 - break
 - except
 - import
 - print
 - class
 - exec
 - in
 - raise
 - continue
 - finally
 - is
 - return
 - def
 - for
 - lambda
 - try

 ## 数据类型

 True
 False
 None
 strings
 numbers
 floats
 lists

 ## 字符串转义序列（Escape Sequences）

 - \\ #啥意思？
 - \'  #啥意思？
 -\'' #啥意思？
 -\a#啥意思？
 -\b#啥意思？
 -\f#啥意思i？
 -\n#啥意思？
 -\r# 啥意思？
 -\t# 啥意思？
 -\v#啥意思？

 ##字符格式化（String Formats）
 - %d
 - % i
 - %o
 - %u
 - %x
 - %X
- %e
- %E
- %f
- %g
- %G
- %c
- %r
- %s
- %%
#上面都是啥意思？

# 操作符号
优秀符号你可能还不熟悉，不过还是意义看过去，研究一下她们的功能，记录下来日后解决。

+
-
*
**
/
//
%
<
>
<=
>=
==
!=
< >
( )
[ ]
{ }
@
,
:
.
=
;
+=
-=
*=
/=
//=
%=
**=

#花一个星期学习这些东西，如果你能 前完成就更好了。我们的目的是覆盖到所 有的符号 类型，确认你已经牢牢记住它们。另外很重要的一点是这样你可以找出自己还不知道哪些 东西，为自己日后学习找到一些方向。

```

### RESULT

```
# 运行后的结果：


itifadeMacBook-Pro:~ yyy$
'''

```
---

## 第38题

### CODE
```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第38题 阅读代码-如何运用你学到的东西理解别人的代码
-首先把你想要理解的代码打印到纸上。没错，你需要打印出来，因为和屏幕输出相比，你的眼睛和大脑更习惯于接受纸质打印的内容。一次最多打印几页就可以 了。
-通读你打印出来的代码并做好标记，标记的内容包括以下几个方面:
1. 函数以及函数的功能。
2. 每个变量的初始赋值。
3.每个在程序的各个部分中多次出现的变量。它们以后可能会给你带来麻烦。
4. 任何不包含 else 的if语句。它们是正确的吗?
5. 任何可能没有结束点的while循环。
6. 最后一条，代码中任何你看不懂的部分都记下来。

接下来你需要通过注解的方式向自己解释代码的含义。解释各个函数的使用方法，各个变量的用途，以及任何其它方面的内容，只要能帮助你理解代码即可。
最后，在代码中比较难的各个部分，逐行或者逐个函数跟踪变量值。你可以再打印一份出来，在空白处写出你要“追踪”的每个变量的值。
一旦你基本理解了代码的功能，回到电脑面前，在屏幕上重读一次，看看能不能找到新的问题点。然后继续找新的代码，用上述的方法去阅读理解，直到你不再 需要纸质打印为止。

# 加分习题
1. 研究一下什么是“流程图(flow chart)”，并学着画一下。
2.如果你在读代码的时候找出了错误，试着把它们改对，并把修改内容发给作者。
3.不使用纸质打印时，你可以使用注解符号#在程序中加入笔记。有时这些笔记会对后来的读代码的人有很大的帮助。


```

### RESULT

```
# 运行后的结果：
'''
本题不需要写代码。
'''
```
---

## 第39题

### CODE
```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第39题 列表的操作
''''
你看到像mystuff.append('hello')这样的代码，实际上在Python内部激发了一个连锁反应。原理：
括号-（parenthesis）
append(mustuff,'hello')==mystuff.append('hello')

'''
# 练习
ten_things="Apples Oranges Crow Telephone Light Sugar"

print "Wait there's not 10 things in that list,let's fix that."

stuff = ten_things.split(' ')
more_stuff =["Day","Night","Song","Frisbee","Corn","Banana","Girl","Boy"]

while len(stuff)!=10:
	next_one = more_stuff.pop()
	print"Adding:",next_one
	stuff.append(next_one)
	print "There's %d item now."% len(stuff)

print "There we go:",stuff

print "Let's do some things with stuff."

print stuff[1]
print stuff[-1]#whoa! fancy
print stuff.pop()
print ' '.join(stuff)# what? cool?
print '#'.join(stuff[3:5])#super stellar!

```

### RESULT

```


# 运行后的结果：

'''
Python 2.7.14 (v2.7.14:84471935ed, Sep 16 2017, 12:01:12)
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "copyright", "credits" or "license()" for more information.
>>> WARNING: The version of Tcl/Tk (8.5.9) in use may be unstable.
Visit http://www.python.org/download/mac/tcltk/ for current information.

============ RESTART: /Users/yyy/Documents/Python_LP2THW/ex39.py ============
Wait there's not 10 things in that list,let's fix that.
Adding: Boy
There's 7 item now.
Adding: Girl
There's 8 item now.
Adding: Banana
There's 9 item now.
Adding: Corn
There's 10 item now.
There we go: ['Apples', 'Oranges', 'Crow', 'Telephone', 'Light', 'Sugar', 'Boy', 'Girl', 'Banana', 'Corn']
Let's do some things with stuff.
Oranges
Corn
Corn
Apples Oranges Crow Telephone Light Sugar Boy Girl Banana
Telephone#Light
>>>
======
# 加分题
加分习题
1. 将每一个被调用的函数以上述的方式翻译成 Python 实际执行的动作。例 如: ' '.join(things) 其实是 join(' ', things) 。
2. 将这两种方式翻译为自然语言。例如，   可以翻译成“用 ‘ ‘ 连
' '.join(things)
接(join) things”，而 join(' ', things) 的意思是“为 ‘ ‘ 和 things 调用 join
函数”。这其实是同一件事情。
3. 上网阅读一些关于“面向对象编程(ObjectOrientedProgramming)”的资料。晕了吧?
嗯，我以前也是。别担心。你将从这本书学到足够用的关于面向对象编程的基础知
  识，而以后你还可以慢慢学到更多。
4. 查一下 Python 中的 “class” 是什么东西。不要阅读关于其他语言的 “class” 的用
法，这会让你更糊涂。
5. dir(something)和something的 class 有什么关系?
6. 如果你不知道我讲的是些什么东西，别担心。程序员为了显得自己聪明，于是就发
明了 Opject Oriented Programming，简称为 OOP，然后他们就开始滥用这个东西 了。如果你觉得这东西太难，你可以开始学一下 “函数编程(functional programming)”。

'''

```
---

## 第40题
### CODE

```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第40题 字典，可爱的字典
'''
容器型数据结构——字典（dictionary）。这种数据类型在Python中叫"dict",有的语言里叫hash。注意它们和列表的区别。

你可以使用数字作为列表的索引，也就是你可以通过数字找到列表中的元素。而dict所做的，是让你可以通过任何东西找到元素，不只是数字。使得，子弟爱你可以将一个物体和另外的一个东西关联，不管他们的类型是什么。
'''
# 练习：
# 疑问，这个大括号{}和中括号[]在一个“字典”里是啥关系？
# 列表里用中括号[ ]?字典里用大括号{}?

cities = {'CA':'San Francisco','MI':'Detroit','FL':'Jacksonville'}

#上一行：大括号和小括号啥区别呢？将“字典”里的三个系列赋值给了cities.我现在看cities这个变量现在是以字典的格式存了一些东西，这些东西是以A：B的单元形式存储的，每个单元之间使用逗号“，”隔开。其中A是B的索引，也就说说通过pring cities['CA'] 可以打印出SanFrancisco来。而且这个“字典”里的元素是可以增删的，直接通过cities[Ai]="Bi"代码，可以把'Ai':'Bi'作为一组数据元素引入到字典中来，但是这一组数据是以什么样的顺序存在这个库里，就不得而知了。

# 背景知识：CA= California State of USA,SanFrancisco=旧金山、三藩市、圣弗朗西斯科，加州大学伯克利分校和斯坦福的所在地。NY是纽约州，MI是密西西比州的意思，州简称：对应的后面是这个州里最大的城市？

cities['NY']='New York'
#把字符串New York赋值给了NY ?不是的，这里的意思是将'NY':'New York'这一组数据 增加到cities这个字典里。

cities['OR']='Porland'
# 把字符串 Porland 赋值给了OR？NO，这里的意思是，给你字典cities里面增加了新的一组数据  'OR':'Porland'

#对了，加完了之后，现在，这个cities字典的内容库就是{'CA':'San Francisco','MI':'Detroit','FL':'Jacksonville','NY':'New York','OR':'Porland'}



def find_city(themap,state): #定义了一个函数，这个函数有2个参数：参数A和参数B

	if state in themap:# 如果参数2在参数1里,这里用到一个关键词in,查查怎么用。
		return themap[state]# 就返回 参数1# 这里明明要求的返回前一个参数的值，为啥运行的时候返回的是后一个参数的值？
		#我怎么记得中括号[]不是字典而是列表到意思呢？
		# 注意，在“字典”型变量的背后使用单个中括号[]的意思好像是要对其中一个元素动手。问题是temap{} 是个字典么？也许是，哪state是什么？其中一个元素？怎么看出来themap是个字典类的变量？
		#注意[ ]中的值是一个索引值么，看到前面的例子里也是 stuff={'name':'Zed'}  print stuff['name'] 返回的就是 Zed。
		#如果输入stuff[1]="Wow"，就是在原来的字典里增加了一条：1:'Wow'——这里返回的不是一个函数，这里themap[state]的意思是themap={'themap':'state'}，对？。这里的意思是，返回以state变量输入代表的这个字符串对应的元素，应该是temap{state:something?}我想这里的state其实是美国某个州的简称，比如CA。


	else:
		return "Not found."# 否则就返回NF

# ok pay attention!

cities['_find']=find_city# 注意：将字符串find_city 获得的一对值，赋值给_find？——例如CA？，就是说变成了cities['_find'](themap,state)，find_city；不对，这里的意思是往cities{A:B……}里增加一对数据？新增加了{A:B……_find:find_city}?


while True: #如果为真？谁为真？上面这一条？
	print"State?(ENTER to quit)",#打印出来：State？回车后取消。

	state= raw_input(">")#使用raw_input()函数，将“>”替代state

	if not state:break#如果state(>)后面不是break，这里有一个判断语句就是if not ***,这里state这个变量接受了用户在>后面的输入，state变量后面跟着：+break?这里怎么理解？是个什么意思？

	# this line is the most important ever!study!这一行最重要，注意注意注意！

	city_found = cities['_find'](cities,state) # 使用cities[_find'](其本质上是find_city ),即 find_city(cities,state)    citi_found这个变量的返回值有2种情况，1种是themap(citied), 另一种是Not found。如果state 是在cities里面的话，就返回cities[state]返回一个城市。
	#cities[ ] 是以「列表」而不是「字典」的形式来进行的，怎么进行的呢？列表后面紧跟[]（A，B）是怎么个意思？
	print city_found#city 有可能打字出来是citi
# 注意到我用了themap而不是map了吧？这是因为Python已经又一个函数叫做map了，如果你用map做变量，后面可能出问题。#这里只有两种情况了，或者是themap或者是Not Found.

```
### RESULT

```
# 运行后的结果：
'''
Python 2.7.14 (v2.7.14:84471935ed, Sep 16 2017, 12:01:12)
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "copyright", "credits" or "license()" for more information.
>>> WARNING: The version of Tcl/Tk (8.5.9) in use may be unstable.
Visit http://www.python.org/download/mac/tcltk/ for current information.

============ RESTART: /Users/yyy/Documents/Python_LP2THW/ex40.py ============
State?(ENTER to quit) >New York
Not found.
State?(ENTER to quit) >San Francisco
Not found.
State?(ENTER to quit) >MI
Detroit
State?(ENTER to quit) >CA
San Francisco
State?(ENTER to quit) >NY
New York
State?(ENTER to quit) >OR
Porland
State?(ENTER to quit) >FL
Jacksonville
State?(ENTER to quit) >
'''
#加分习题
'''
1. 在 Python 文档中找到 dictionary (又被称作 dicts, dict)的相关的内容，学着对 dict 做更多的操作。
2. 找出一些 dict 无法做到的事情。例如比较重要的一个就是 dict 的内容是无序的， 你可以检查一下看看是否真是这样。
3. 试着把for-loop执行到 dict 上面，然后试着在 for-loop 中使用 dict 的items()函数，看看会有什么样的结果。

'''
# LOG
# 20171101 用了比较多的心思来理解这些代码。
```

## LOG

- 20171029 创建本文件，更新了31题。下午更新了32～35题，加分题基本没做。
- 20171030 完成了36-38题，基本没啥代码，就是看看而已。
- 20171031 早上没起来，中午忙着**认证的事，也拖延着不去做，结果是进度很慢。中午草草看了29题，先更新了再说，但是这题我看的云里雾里，比如：len(stuff)是个什么鬼，print stuff.pop() ； print ' '.join(stuff)# what? cool?
print '#'.join(stuff[3:5])#super stellar! 这些都挺操蛋的，将来再说，暂且更新到这里。
- 20171106早上粘贴了这些代码。这写代码是201711月初陆续完成的但是没有上传。
