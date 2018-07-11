---
layout: post
title: 《笨办法学Python》记录-part2（习题11～20）
date: 2017-10-23
categories: blog
tags: [Python,笨办法学Python,LearPython2TheHardWay,LP2THW]
description: 立个Flag开始学Python。
---

> 后续练习的习题均为《笨办法学Python》的练习代码，所用的是Python2.7版本。

> 本文件是“《笨办法学Python2.x》教&学记录”的第二部分，记录11-20题的教学。

## 第11题
### CODE
```
# 第11题

print "Hello old are you?",#注意：这里语句的最后多了一个逗号（Comma）这样print就不会输出新行符号，而结束这一行跑到下一行了。
age= raw_input()#在py2里有raw_input（）函数，py3里没有，直接用input()
print "How tall are you?" #这个看看，如果语句后面没有Comma会发生什么状况？答案是：若果没加逗号的话，程序提示这个问题之后，接受用户输入需要另外起一行。加逗号的话，就是和这个问句的同一行。
height= raw_input()
print "How much do you weight?",
weight= raw_input()

print "So, you're %r old,%r tall and %r heavy." %(age,height,weight)#注意，这里前面的3个占位符分别和后面的3个变量相互配合。思考：为什么打印出来的时候age\weight\height, 上面都会使用单引号引用上呢？
# 运行完，并未见到例题中出现的【'6\'2"' 】而是【"6'22''" 】；另注意，当程序运行的时候输入【6'22''】这几个字是绿色的。和转义序列有关的，想想为什么最后一行 '6\'2"' 里边有一个 \' 序列。单引号需
#要被转义，从而防止它被识别为字符串的结尾。有没有注意到这一点？注意到了，但是，看样子还是单引号问题引起的混乱。我想如果转换了数据类型可能会好一些吧。
# LOG
# 20171023 从windows 端创建。

```

###RESULT
```
>>>
=========== RESTART: /Users/yyy/Documents/Python_LP2THW/ex11py2.py ===========
Hello old are you? 35
How tall are you?
195
How much do you weight? 75kg
So, you're '35' old,'195' tall and '75kg' heavy.
>>>

```
---
## 第12题
###CODE
```
# 习题12 提示别人
#y= raw_input("Name?")#在括号里可以放入提示的问题。用户输入就赋值给了y.
#  这里的意思是，习题11可以用更加简洁的方法表达出来。
''' 注意，这里发现，整整一段注释掉的话，用的是3个单引号，而不是在jianshu.com里面的三个【```】_键盘中1左上角的这个键。
age= raw_input("How old are you?")
height= raw_input("How tall are you?")
weight= raw_input("How much do you weight?")

print "So, you're %r old ,%r tall and %r heay."%(age,height,weight)
'''
# 上面被注释掉的一段在py2下测试通过。下面改成中文试试。

age= raw_input("您多大了？")
height= raw_input("你多高?")
weight= raw_input("你多重?")#中文字符可能出现问题，例如，如果本字符串如果携程“你有多种”则会出现乱码，所以尽量减少中文的使用。

print "所以，您的年龄是 %r ，高度是%r ，体重是 %r。"%(age,height,weight)# 在输入的时候，如果输入了中文也是会报错的，比如你需要输入的数字，你身高是175cm而不能输入175厘米，否则会报错。

''' #按照课后习题的加分题输入，报错，不知是怎么回事，回头再解决这个问题。
>>> pydoc raw_input
SyntaxError: invalid syntax
>>> python -m pydocraw_input
SyntaxError: invalid syntax
'''

```
###RESULT
```
=========== RESTART: /Users/yyy/Documents/Python_LP2THW/ex12py2.py ===========
您多大了？15
你多高?180cm
你多重?70kg
所以，您的年龄是 '15' ，高度是'180cm' ，体重是 '70kg'。
>>>
```
---
## 第13题
###CODE
```
# 习题13：参数(argument)、解包、变量

from sys import argv# import 是引入功能

script,first,second,third = argv
#argv 是所谓参数变量(argument variable)这个变量包含了你传递给Python的参数
# 上面这一行是解包，将其所有参数放到同一个变量下面，我们将每个参量赋予一个变量名：scipt~first~。所谓解开包的意思是：把argv中的东西解包，将所有参数依次赋予左边的变量名中。
# 其实import导入的是一个模组（modules）或者叫做库（libraries）,意思是你要把sys模组（库）inport进来。

print "The scipt is called:",script # script这个参数其实是某一个路径下的一个文件。

print "Your first variable is:",first

print"Your second variable is:",second

print  "Your third variable is:",third

'''
# ！！重要发现，由于一直没搞清楚命令行怎么运行Python程序，而这里又设计到带参数的Python运行，所以这里一直错误。
# ！现在我将讲讲错在哪里，并且怎么解决的。教材中说，只需要python ex13.py first 2nd 3rd(后面这三个是参数)
# 但是我一直也调用不出来。关键是命令行怎么调用这个程序就搞不清。
#好吧，在windows 运行下输入powershell （貌似直接输入python 也可以调用出来c:\python27\python.exe）， 然后出现了命令行窗口（很丑，搞不清楚他们为啥要用），
#  在powershell里直接输入python进入了python2.7 然后输入ex13py2.py没反应,ex13py2.py报错。想办法返回上一级。
#  直接在python界面里是无法带参数运行这个.py程序的。现在需要的是点Ctrl+Z返回到上一层，对于我来说也就是
# 也就是路径“PS C:\Users\Administrator>”
# 用自带的IDLE打开你编写的这个py文件，里面有个路径，对于我来说是E:\AllFilesIo\PythonIO\Python_LP2THW\ex13py2.py
# 然后我在上面这个路径下面输入：python E:\AllFilesIo\PythonIO\Python_LP2THW\ex13py2.py first 2nd 3rd  #py文件后面紧跟着的3个就是参数，这样就能调试通过了。
# 总结：直接在IDLE里面编辑的py文件，如果需要通过命令行+参数的方法运行，需要在powershell里通过ctrl+Z进入到上一级路径，在这个基础上 输入[python  路径  参数1 参数2 参数3]回车运行。
#和其他编辑器不同（ctrl+v），在powershell窗口里面，粘贴只需要右键就行可以了。（这个路径是通过Python自带的IDE运行之后，上面标注的路径，才copy出来的。）
'''

# 加分题【将 raw_input 和 argv 一起使用，让你的脚本从用户手上得到更多的输入】我没做，因为不知道如何将raw_input作为参数来使用。


```
###RESULT
```
'''
运行后显示如下：这里用了cheese apple bread共3个参数。
PS C:\Users\Administrator> python E:\AllFilesIo\PythonIO\Python_LP2THW\ex13py2.py cheese apple bread
The scipt is called: E:\AllFilesIo\PythonIO\Python_LP2THW\ex13py2.py
Your first variable is: cheese
Your second variable is: apple
Your third variable is: bread
PS C:\Users\Administrator>

'''
# 如果 多填写了一个，就会出现如下状况
'''
PS C:\Users\Administrator> python E:\AllFilesIo\PythonIO\Python_LP2THW\ex13py2.py cheese apple bread blue
Traceback (most recent call last):
  File "E:\AllFilesIo\PythonIO\Python_LP2THW\ex13py2.py", line 5, in <module>
    script,first,second,third = argv
ValueError: too many values to unpack
PS C:\Users\Administrator>
'''
```

-----

## 第14题
###CODE
```
# 第14题
# 使用argv和raw_input 一起来向用户提特别的问题。这是下一节习题读写的基础。
#说实话，后面这句话我没看懂——{我们将用户提示符设置为变量 prompt，这样我们就不需要在每次用到 raw_input 时重复输入提示用户的字符了。而且如果你要将提示符修改成别的字串，你只要改一个位置就可以了}

from sys import argv #引入了一个argv

script , user_name = argv #这个argv有2个参量：script（程序名称）user_name（用户名）

prompt='>' # 引入一个新变量prompt 用来代表＞号。

print "Hi %s, I'm the %s script." %(user_name,script)#将两个参量分别引入字符串句子中。

print "I'd like to ask you a few questions."

print "Do you like me %s?"%user_name#引入用户输入参量1

likes= raw_input(prompt)# 将prompt作为参量再次作为input输入，赋值给likes这个变量。

print "Where do you live %s?"% user_name

lives=raw_input(prompt)# 将prompt作为参量再次作为input输入，赋值给lives这个变量。

print "What kind of computer do you have?"

computer=raw_input(prompt) #将prompt这个变量赋值给变量computer

print"""
Alright,so you said %r about liking me.# 这里的占位符后面没有跟变量。

You live in %r. Not sure where that is.# 占位符后面没有跟变量，而且is被提示了，说明is是一个专业名字，但是在这里估计是没啥鸟用。

And you have a %r computer. Nice.# 这里也有一个占位符，估计也没啥用。

"""% (likes,lives,computer) #在Python自带IDE中这行被涂成绿色，意思是注释掉了，但是这行还是有用的语句。
# 我明白了，在两个{三个双引号""" }之间理论上被注释或者成段打印的多段字符串，里面的站位符，可以被最后的三引号之外的参数，集中引用。
# 注意连续的三个半角的双引号之间不可以有空格，最后的三个双引号也是如此。
```
### RESULT

```
********以下是windows下运行的结果************
'''
PS C:\Users\Administrator> python E:\AllFilesIo\PythonIO\Python_LP2THW\ex14py2.py Andy
Hi Andy, I'm the E:\AllFilesIo\PythonIO\Python_LP2THW\ex14py2.py script.
I'd like to ask you a few questions.
Do you like me Andy?
>Yes
Where do you live Andy?
>Tianjin
What kind of computer do you have?
>ThinkPad
Alright,so you said 'Yes' about liking me.# 杩欓噷鐨勫崰浣嶇鍚庨潰娌℃湁璺熷彉閲忋€?

You live in 'Tianjin'. Not sure where that is.# 鍗犱綅绗﹀悗闈㈡病鏈夎窡鍙橀噺锛岃€屼笖is琚彁绀轰簡锛岃鏄巌s鏄竴涓
笓涓氬悕瀛楋紝浣嗘槸鍦ㄨ繖閲屼及璁℃槸娌″暐楦熺敤銆?

And you have a 'ThinkPad' computer. Nice.# 杩欓噷涔熸湁涓€涓崰浣嶇锛屼及璁′篃娌″暐鐢ㄣ€?
'''
***********以下内容是在macbook中运行的结果***********
''''
itifadeMacBook-Pro:~ yyy$ python /Users/yyy/Documents/Python_LP2THW/ex14py2.py Andy
Hi Andy, I'm the /Users/yyy/Documents/Python_LP2THW/ex14py2.py script.
I'd like to ask you a few questions.
Do you like me Andy?
>No
Where do you live Andy?
>China
What kind of computer do you have?
>Macbook

Alright,so you said 'No' about liking me.# 这里的占位符后面没有跟变量。

You live in 'China'. Not sure where that is.# 占位符后面没有跟变量，而且is被提示了，说明is是一个专业名字，但是在这里估计是没啥鸟用。
And you have a 'Macbook' computer. Nice.# 这里也有一个占位符，估计也没啥用。
itifadeMacBook-Pro:~ yyy$
'''
```



---
## 第15题
###CODE
```
from sys import argv #argv参数用于获取文件名变量。

script,filename=argv #argv参数用于获取文件位置和文件名。带参数的变量。例如我可以在命令行里输入AI作为filename。

txt= open(filename)#注意open()命令类似raw_input()命令，接收一个参数，返回一个值。可以讲这个值赋予一个变量。这里，这个变量就是txt，被赋予了open（）函数的返回值。

print "Here's your file %r:"% filename

print txt.read()#我们在txt上 调用了一个函数。你从 open 获得的东西是一个file(文件)，文件本身也支持 一些命令。它接受命令的方式是使用句点.(英文称作 dot 或者 period)，紧跟 着你的命令，然后是类似 open 和 raw_input 一样的参数。不同点是:当你 说txt.read时，你的意思其实是:“嘿 txt!执行你的 read 命令，无需任何参 数!”

print "Type the filename again:"

file_again= raw_input(">")# 注意：raw_input()命令

txt_again= open(file_again)

print txt_again.read()


```
###RESULT
```
''''
运行后显示的结果：注意，提到的文件和路径必须完整才行。

itifadeMacBook-Pro:~ yyy$ python  Documents/Python_LP2THW/ex15py2.py Documents/Python_LP2THW/ex15py2_sample.txt
Here's your file 'Documents/Python_LP2THW/ex15py2_sample.txt':
This is stuff I typed into a file.
It is really cool stuff.
Lots and lots of fun to have i here.
Type the filename again:
>Documents/Python_LP2THW/ex15py2_sample.txt
This is stuff I typed into a file.
It is really cool stuff.
Lots and lots of fun to have i here.
itifadeMacBook-Pro:~ yyy$

'''
# 由于安装路径的问题，现在用python经常用到路径，还是比较别手的。有点烦躁。折腾一早上，完成1题，还不算加分部分（本章很重要，作者要求你做好加分题）




''''
现在请在命令行运行 pydoc open 来读读它的说 明。
在mac中可以清晰的看到和使用pydoc 这个命令
itifadeMacBook-Pro:~ yyy$ pydoc open

Help on built-in function open in module __builtin__:

open(...)
    open(name[, mode[, buffering]]) -> file object

    Open a file using the file() type, returns a file object.  This is the
    preferred way to open a file.  See file.__doc__ for further information.
(END)
'''
```
---
## 第16题
###CODE
```
from sys import argv

script,filename=argv

print "We're going to erase %r."%filename

print "If you don't want that,hit CTRL-C(^C)."

print "If you do want that,hit RETURN."

raw_input("?")

print "Opening the file..."
target= open(filename,'w')#为什么要多加一个参数w呢？是不是应该通过pydoc open 来查看一下呢？

print "Truncating the file.Goodbye!"
target.truncate()

print"Now I'm going to ask you for three lines."

line1= raw_input("line 1:")

line2= raw_input("line 2:")

line3= raw_input("line 3:")

print "I'm going to write these to the file."

target.write(line1)
target.write("\n")
target.write(line2)
target.write("\n")
target.write(line3)
target.write("\n")

print "And finally,we close it."
target.close()

'''
python  Documents/Python_LP2THW/ex16.py Documents/Python_LP2THW/test.txt
'''
# 20171024 心烦 加分题没做
```
###RESULT
```
20171024 上午发现ex16文件中用中文注释，不能运行。于是，将它单独摘出来，列在下面：
#从本文件开始，我们的命名中不再使用py2这个关键词，直接使用教材中提到的命名方法。
# 以下是重要的一些命令：
close- 关闭文件。同：文件》保存。。
read-读取文件内容，你可以把结果赋值给一个变量。
readline-读取文本文件中的一行
truncate-清空文件，小心使用这个命令。
write(stuff)- 将stuff写入文件。
上面这些命令，有的需要一些输入参数。
write-需要接收一个字符串作为参数，从而将该字符串写入文件。
—
'''
----运行的结果如下----
itifadeMacBook-Pro:~ yyy$ python  Documents/Python_LP2THW/ex16.py Documents/Python_LP2THW/test.txt
We're going to erase 'Documents/Python_LP2THW/test.txt'.
If you don't want that,hit CTRL-C(^C).
If you do want that,hit RETURN.
?yes
Opening the file...
Truncating the file.Goodbye!
Now I'm going to ask you for three lines.
line 1:How old are you?
line 2:How much do you earn?
line 3:Do you have children?
I'm going to write these to the file.
And finally,we close it.
itifadeMacBook-Pro:~ yyy$
----运行的结果如上---
'''
```
---
## 第17题
###CODE
```
#17
from sys import argv
from os.path import exists#filename as input

script,from_file,to_file= argv

print "Copying from %s to %s" %(from_file,to_file)

# we could do these two on one line too,how?
input= open(from_file)
indata=input.read()

print"The input file is %d bytes llong"% len(indata)

print "Does the output file exist?%r"% exists(to_file)
print"Ready,hit RETURN to cotinue,CTRL-C to abort."
raw_input()

output= open(to_file,'w')
output.write(indata)

print"Alright,all done"

output.close()
input.close()


'''

```
###RESULT
```
# The Result .....Any Chinese Character Can not be in the it ,or it will report a wrong!

itifadeMacBook-Pro:~ yyy$ python Documents/Python_LP2THW/ex17.py Documents/Python_LP2THW/test.txt Documents/Python_LP2THW/copied.txt
Copying from Documents/Python_LP2THW/test.txt to Documents/Python_LP2THW/copied.txt
The input file is 61 bytes llong
Does the output file exist?True
Ready,hit RETURN to cotinue,CTRL-C to abort.

Alright,all done
itifadeMacBook-Pro:~ yyy$
--- cat
itifadeMacBook-Pro:~ yyy$ cat Documents/Python_LP2THW/copied.txt
How old are you?
How much do you earn?
Do you have children?
itifadeMacBook-Pro:~ yyy$
'''
```
>找出为什么你需要在代码中写 output.close()? ——现在我还不知道。这个题的加分题，我也没有做。
---
## 第18题
###CODE
```
#命名-变量-代码-函数（function）
#函数可以教你做3样事情：给代码片段命名；它们可以接受函数，就跟你的脚本接受argv一样；通过使用#1和#2，它们可以让你创建微型脚本或者小命令。
#你可以用def新建立函数，你现在学建立4个函数。
# 采用Python2.7自带的编辑器，打开你用TextMate创建的文件时，他会提示时，在哪里输入个啥#*--UTF8---,这样编译的时候就不会出错了，直接在TextMate里编辑则会出错，容易报编码错误。

#this one is like your scripts with argv 这个函数和你的脚本里看到的argv带参数的变量是一个意思。
def print_two(*args):# A Function is defined。这里定义了个函数，「*args」是个什么鬼？为何要用*？
	arg1,arg2=args# 程序运行的时候需要输入两个参量arg1和arg2，这两个用户输入量会作为参量参与运行。
	print "arg1:%r,arg2:%r"%(arg1,arg2)

# ok,that *args is actually pointless,we can just do this
def print_two_again(arg1,arg2):#这里多了一种打印两个用户输入内容的函数方法。这个函数可以跳过解包过程，追饿使用（）里边的名称作为变量名。
	print "arg1:%r,arg2:%r"%(arg1,arg2)

# this just takes one argument
def print_one(arg1):#仅仅打印一种用户输入参数arg1
	print "arg1:%r"%arg1

# this one takes no arguments
def print_none():#打印出
	print "I got nothin'."

print_two("Zed","Shaw")# 程序运行直接需要的两个输入参数，均用在这里了。
print_two_again("Zed","Shaw")# 这里貌似可以接受用户输入。
print_one("First!")
print_none()

# ················
'''
下面肢解以下print_two
1.首先我们高速Python，我要创建一个函数，用了命令def，也就是定义（define）的意思。
2.名字可以随便取，当然最好是能体现这个函数的功能，例如print_two.
3.我们告诉函数，我们需要* args，这个和脚本argv相似，参数必须放在（）中才能运行。
4.接着用「：」结束本行，下一行开始缩进。
5.冒号以下，前面缩进4个空格的，都属于这个函数的内容，第一行，用于-解包-
6.解包之后的每个参数打印出来，这样会显得更加清晰。

定义函数注意：
1.函数定义以def开始。
2.函数名称以字符和下划线组成。
3.函数名称紧跟着「（」
4.括号里包含多个参数，分别以逗号隔开。
5.不能使用重复的参数名。
6.参数最后要加入「）」、「：」和「？」
7.函数定义代码后新行要缩进4个格子
8.函数结束后要取消缩进。


使用函数注意：
1.调用函数（use或call）是否使用了函数的名称？
2.函数名称是否紧跟着「（？」
3.括号后又无参数？多个参数是否以逗号隔开？
4.函数是否以「）」结尾？
另注意：run、call和use函数是同一个意思。

'''
#················




```
###RESULT
```
#以下是上述代码的运行结果#
'''
#以下是上述代码的运行结果#

Python 2.7.14 (v2.7.14:84471935ed, Sep 16 2017, 12:01:12)
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "copyright", "credits" or "license()" for more information.
>>> WARNING: The version of Tcl/Tk (8.5.9) in use may be unstable.
Visit http://www.python.org/download/mac/tcltk/ for current information.

============ RESTART: /Users/yyy/Documents/Python_LP2THW/ex18.py ============
arg1:'Zed',arg2:'Shaw'
arg1:'Zed',arg2:'Shaw'
arg1:'First!'
I got nothin'.
>>>
'''
```
---
## 第19题
###CODE
```
 # -*- coding: utf-8 -*-
# 19:函数和变量

#注意，函数里的变量和脚本里的变量是没有任何关系的。

# 下面开始编程

def cheese_and_crackers (cheese_count,boxes_of_crackers):
	print "You have %d cheeses!"% cheese_count
	print "You have %d boxes of crackers!"%boxes_of_crackers
	print "Man that's enough for a party!"
	print "Get a blanket.\n"#\n在这里起了个啥作用？

print "We can just give the function number directly:"
cheese_and_crackers(20,30)

print "OR,we can use variables from our script:"
amount_of_cheese=10
amount_of_crackers=50

cheese_and_crackers(amount_of_cheese,amount_of_crackers)

print "We can evern do math inside too:"
cheese_and_crackers(10+20,5+6)

print "And we can combine the two,variables and math:"
cheese_and_crackers(amount_of_cheese +100, amount_of_crackers +1000)


```
###RESULT
```
'''
运行后的结果：
>>>
============ RESTART: /Users/yyy/Documents/Python_LP2THW/ex19.py ============
We can just give the function number directly:
You have 20 cheeses!
You have 30 boxes of crackers!
Man that's enough for a party!
Get a blanket.

OR,we can use variables from our script:
You have 10 cheeses!
You have 50 boxes of crackers!
Man that's enough for a party!
Get a blanket.

We can evern do math inside too:
You have 30 cheeses!
You have 11 boxes of crackers!
Man that's enough for a party!
Get a blanket.

And we can combine the two,variables and math:
You have 110 cheeses!
You have 1050 boxes of crackers!
Man that's enough for a party!
Get a blanket.

>>>
'''
```
---
## 第20题
###CODE
```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第20题 函数和文件
from sys import argv# 从sys库中引入argv变量，包含2个参数

script, input_file = argv# argv变量包含2个参数，第一个是本程序名称，后一个是被引入的文件名。

def print_all(f):#定义一个函数，但是函数中的带的f是个啥。f是file的意思。
	print f.read()#f可以直接调用read()方法？这个是什么套路，忘了

def rewind(f):#定义里一个函数rewind?在这个函数里，依然使用了f参数，f参数可以直接调用seek()方法。
	f.seek(0)#f可以直接调用seek()函数

def print_a_line(line_count,f):#定义了一个新函数，函数的作用是打印一整行。函数中有2个参数，第一个参数是数数有几行，第几行？；第二个参数是f，但是f是个啥？传递一个变量。
	print line_count,f.readline()#打印一整行的这个函数中低你了打印两个东西，一个是行数，一个是数几行？

current_file=open(input_file)#这行带啊的意思是：引入一个current_file变量，通过open方法打开了input_file参数的这个文件。

print " First let's print the whole file:\n"# 打印一个字符串

print_all(current_file) #调用printall()这个函数，这里是打印所有的意思。

print "Now let's rewind,kind of like a tape."#打印一行字符串。

rewind(current_file)#调用一个rewind()函数,其实质是调用了一个叫做seek()的函数。

print "Let's print three lines:"

current_line=1#current_line变量被新赋予了一个数值1
print_a_line(current_line,current_file)

current_line=current_line+1#每运行一次，current_line变量会再+1
print_a_line(current_line,current_file)

current_line=current_line+1
print_a_line(current_line,current_file)


```
###RESULT
```

# 运行后的结果：
'''
itifadeMacBook-Pro:~ yyy$ python  Documents/Python_LP2THW/ex20.py Documents/Python_LP2THW/test.txt
 First let's print the whole file:

How old are you?
How much do you earn?
Do you have children?

Now let's rewind,kind of like a tape.
Let's print three lines:
1 How old are you?

2 How much do you earn?

3 Do you have children?

itifadeMacBook-Pro:~ yyy$
'''

```
## LOG

- 20171023 白天完成了8～14题，并于晚上上传，本文件上传11～14题。
- 20171024 早上完成第15题（承前启后），暂时没做加分题。
- 20171024 夜，里今天是程序员的节日，多么希望我能成为一个程序员，通过代码改变世界。今天白天到效率有点低，更新了16和17代码，主要是16，理解还不深入，死磕了啊，先刷一遍再说吧。
- 20171025 早上死磕18题。另# 采用Python2.7自带的编辑器，打开你用TextMate创建的文件时，他会提示时，在哪里输入个啥#--UTF8---,这样编译的时候就不会出错了，直接在TextMate里编辑则会出错，容易报编码错误。
-20171026 完成19和20题。
-20171027早上更新到简书。safari中简书对于直接粘贴图片不支持，改用chrome界面，粘贴的还算顺利，不过有时候会莫名其妙的崩溃。早上又登陆不了chrome上的简书，我竟然忘了账户的密码。
