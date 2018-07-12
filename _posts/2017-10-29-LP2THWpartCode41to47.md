---
layout: post
title: 《笨办法学Python》记录-part5（习题41～47）
date: 2017-11-06
categories: blog
tags: [Python,笨办法学Python,LearPython2TheHardWay,LP2THW]
description: 立个Flag开始学Python。
---

> 题记1:本文件是“《笨办法学Python2.x》教&学记录”的第5部分，记录41-50题的教学。
>题记2:废话少说，先刷题。

---
## 第41题
### CODE
```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第41题 来自 Percal25号行星的哥顿人（Gothons）
# 上一节里你发现了dict的秘密功能了嘛，你可以解释给自己听嘛？好吧，让我来给你解释一下：
'''
cities['_find']= find_city
city_found= cities['_find'](cities,state)
#你要记住一个函数也可以作为一个变量，"def find_city"创建了一个可以在任何地方都能使用的变量。在这段代码里，我们把
'''


#原文内容
#作者其实想告诉你的是，你可以使用剥开洋葱等方法把代码读透彻。

#∂∂ƒ©åEEßß∂ƒ©˙∂´®†¥¨ˆππ“““øΩ”””˙∆˚¬…¬…¬¬¬¬………æææ  µ˜µ˜∫√ç≈Ωåœœ∑

'''
你要记住一个函数也可以作为一个变量，``def find_city`` 比如这一句创建了一 个你可以在任何地方都能使用的变量。在这段代码里，我们首先把函数 find_city 放到叫做 cities 的字典中，并将其标记为 '_find'。 这和我们将 州和市关联起来的代码做的事情一样，只不过我们在这里放了一个函数的名称。
好了，所以一旦我们知道 find_city 是在字典中 _find 的位置，这就意味着我 们可以去调用它。第二行代码可以分解成如下步骤:
1. Python 看到 city_found = 于是知道了需要创建一个变量。
2. 然后它读到cities，然后知道了它是一个字典
3. 然后看到了['_find']，于是 Python 就从索引找到了字典cities中对应的位
  置，并且获取了该位置的内容。
4. ['_find']这个位置的内容是我们的函数find_city，所以 Python 就知道了
这里表示一个函数，于是当它碰到 ( 就开始了函数调用。
5. 这两个参数将被传递到函数 中，然后这个函数就被
   cities, state
find_city
运行了。
6. find_city接着从cities中寻找states，并且返回它找到的内容，如果什么
都没找到，就返回一个信息说它什么都没找到。
7. Python find_city 接受返回的信息，最后将该信息赋值给一开始
的   这个变量。
city_found
 我再教你一个小技巧。如果你倒着阅读的话，代码可能会变得更容易理解。让我 们来试一下，一样是那行:
1. state和city是... 2. 作为参数传递给...
3. 一个函数，位置在...
132

4. '_find'然后寻找，目的地为... 5. cities这个位置...
6. 最后赋值给city_found.
还有一种方法读它，这回是“由里向外”。
1. 找到表达式的中心位置，此次为['_find'].
2. 逆时针追溯，首先看到的是一个叫cities的字典，这样就知道了 cities 中
的 _find 元素。
3. 上一步得到一个函数。继续逆时针寻找，看到的是参数。
4. 参数传递给函数后，函数会返回一个值。然后再逆时针寻找。
5. 最后，我们到了city_found=的赋值位置，并且得到了最终结果。
 数十年的编程下来，我在读代码的过程中已经用不到上面的三种方法了。我只要 瞟一眼就能知道它的意思。甚至给我一整页的代码，我也可以一眼瞄出里边的 bug 和错误。这样的技能是花了超乎常人的时间和精力才锻炼得来的。在磨练 的过程中，我学会了下面三种读代码的方法，它们是用户几乎所有的编程语言:
1. 从前向后。 2. 从后向前。 3. 逆时针方向。
 下次碰到难懂的语句时，你可以试试这三种方法。
'''
# 代码部分
from sys import exit
from random import randint

def death():
	quips = ["You died. You kinda suck at this.",
			 "NIce job, you died ...jackass.",
			 "Sunch a luser.",
			 "I have a small puppy that's better at this."]

	print quips[ randint(0,len(quips)-1)]
	exit(1)

def central_corridor():
	print "The Gothons of Planet Percal #25 have invaded your ship and destroyed "
	print "your entire crew. You are the last surviving member and your last"
	print "mission is to get thr neutron destruct bomb from the Weapons Armory,"
	print "put it in the bridge,and blow the ship up after getting into an "
	print "escape pod."
	print "\n"
	print "You're running down the central corridor to the Weapons Armory when"
	print "a Gothon jumps out ,red scaly skin,dark grimy teeth,and evil clown costume"
	print "flowing around his hate filled body.He's blocking the door to the"
	print "Armory and about to pull aweapon to blast you."

	action = raw_input(">")

	if action =="shoot!":
		print "Quick on the draw you yank out your blaster and fire it at the Gothon."
		print "His clown costume is flowing and moving around his body,which throws"
		print "off your aim.Your laser hits his costume but misses him entirely. This"
		print "completely  ruins his brand new costume his mother bought him,which"
		print "makes him fly into an insane rage and blast you repeatly in the face until"
		print "you are dead.Then he eats you."
		return 'death'

	elif action == "dodge!":
		print "Like a world class boxer you dodge, weave,slip and slider right"
		print " as the Gothon's blaster cranks a laser past your head."
		print " In the middle of your artful dodge your foot slips an you"
		print " bang  your head on the metal wall and pass out."
		print "You wake up shortly after only to die as the Gothon stomps on"
		print "your head and eats you."
		return 'death'

	elif action == "tell a joke":
		print "Lucky for you they made you learn Gothon insults in the academy."
		print "You tell the one Gothon joke you know:"
		print "Lbhe zbgure vf fb sng , jura fur fvgf nebhaq qurbuhfr ,fur fvgf nebhaq qur ubhfr."
		print "The Gothin stops,tries not to laugh,then busts out lauging and can't move."
		print "While he's laughing you run up and shoot him square in the head"
		print "putting him down,then jump through the Weapen Armory door."
		return 'laser_weapon_armory'

	else:
		print "DOES NOT COMPUTR!"
		return 'central_corridor'

def laser_weapon_armory():
	print "You do a dive roll into the Weapon Armory,crouch and scan the room"
	print "for more Gothons that might be hiding.It's dead quiet,too quiet."
	print "You stand up and run to the far side of the rom and find the "
	print "neutron bomb in its container.There's a keypad lock on the box"
	print "and you need the code to get the bomb out.If you get the code"
	print "wrong 10 times then the lock closes forever and you can't"
	print "get the bomb.The code is 3 digits."
	code ="%d%d%d"%(randint(1,9),randint(1,9),randint(1,9))
	guess= raw_input("[keypad]>")
	guesses = 0 #guess后面加复数es
	print "the guess is "+ guess
	print "the code is "+code
	while guess != code and guesses < 10:
		print "BZZZZEDDD!"
		guesses += 1
		guess =  raw_input("[keypad]>")

	if guess == code:
		print "The container clicks open and the seal breaks,letting gas out."
		print "You grab the neutron bomb and run as fast as you can to the"
		print "bridge where you must place it in the right spot."
		return 'the_bridge'
	else:
		print "The lock buzzes one last time and then you hear a sickening"
		print "melting sound as the mechanism is fused together."
		print "You decide to sit there,and finally the Gothons blow up the"
		print "ship from their ship and you die."
		return 'death'

def the_bridge():
	print "You burst onto the Bridge with the neutron destruct bomb"
	print "under your arm and surprise 5 Gothons who are trying to "
	print "take control of the ship.Each of them has an even uglier"
	print "clown costume than the last.The have't pulled their"
	print "weapons out yet,as they see the active bomb under your"
	print "arm and don't want to set it off."

	action =raw_input("> ")

	if action == "throw the bomb":
		print "In a panic you throw the bomb at the group of Gothons"
		print "and make aleap for the door.Right as you drop it a"
		print "Gothon shoots you right in the back killing you."
		print "As you die as you see another Gothon frantically try to disarm"
		print "the bomb.You die knowing they will pribably blow up when"
		print "it goes off."
		return 'death'

	elif action == "slowly place the bomb":
		print "You point your blaster at the bomb under your arm"
		print "and the Gothons put their hands up and start to sweat."
		print "You inch backward to the door,open it,and then carefully"
		print "place the bomb on the floor,pointing your blaster ast it."
		print "You then jump back through the door,punch the close button"
		print "and blast the lock so the Gothons can't get our."
		print "Now that the bomb is placed you run to the escape pod to "
		print " get off this tin can."
		return 'escape_pod'
	else:
		print "DOES NOT COMPUTE!"
		return "the_bridge"

def escape_pod():
	print "You rush through the ship desperately trying to make it to "
	print "the escape pod before the whole ship explodes. It seems like "
	print "hardly any Gothons are on the ship, so your run is clear of "
	print "interference.You get to the chamber with the escape pods, and"
	print "now need to pick one to take. Some of them could be damaged"
	print "but you don't have time to look.There's 5 pods,which one"
	print "do you take ?"

	good_pod =randint(1,5)
	guess = raw_input("[pod #]>")


	if int(guess) != good_pod:
		print "You jump into pod %s and hit the eject button."%guess
		print "The pod escapes out into the void of space,then"
		print "implodes as the hull ruptures, crushing your body"
		print "into jam jelly."
		return 'death'
	else:
		print "You jump into pod %s and hit the eject button."%guess
		print "The pod easily slides out into space heading to"
		print "the planet below. As it flies to the planet,you look"
		print " back and see your ship implode then explode like a "
		print "bright star,taking out the Gothon ship at the same"
		print "time.You won!"
		exit(0)


ROOMS = {
	'death':death,
	'central_corridor':central_corridor,
	'laser_weapon_armory':laser_weapon_armory,
	'the_bridge':the_bridge,
	'escape_pod':escape_pod
	}


def runner(map, start):
	next = start

	while True:
		room = map[next]
		print "\n---------"
		next = room()

runner(ROOMS, 'central_corridor')#没看出来哪里又问题，增加个空格看看行不行。

```
### RESULT
```
# 运行后的结果：
'''
---------第3次运行结果-----------

Python 2.7.14 (v2.7.14:84471935ed, Sep 16 2017, 12:01:12)
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "copyright", "credits" or "license()" for more information.
>>> WARNING: The version of Tcl/Tk (8.5.9) in use may be unstable.
Visit http://www.python.org/download/mac/tcltk/ for current information.

============ RESTART: /Users/yyy/Documents/Python_LP2THW/ex41.py ============

---------
The Gothons of Planet Percal #25 have invaded your ship and destroyed
your entire crew. You are the last surviving member and your last
mission is to get thr neutron destruct bomb from the Weapons Armory,
put it in the bridge,and blow the ship up after getting into an
escape pod.


You're running down the central corridor to the Weapons Armory when
a Gothon jumps out ,red scaly skin,dark grimy teeth,and evil clown costume
flowing around his hate filled body.He's blocking the door to the
Armory and about to pull aweapon to blast you.
>tell a joke
Lucky for you they made you learn Gothon insults in the academy.
You tell the one Gothon joke you know:
Lbhe zbgure vf fb sng , jura fur fvgf nebhaq qurbuhfr ,fur fvgf nebhaq qur ubhfr.
The Gothin stops,tries not to laugh,then busts out lauging and can't move.
While he's laughing you run up and shoot him square in the head
putting him down,then jump through the Weapen Armory door.

---------
You do a dive roll into the Weapon Armory,crouch and scan the room
for more Gothons that might be hiding.It's dead quiet,too quiet.
You stand up and run to the far side of the rom and find the
neutron bomb in its container.There's a keypad lock on the box
and you need the code to get the bomb out.If you get the code
wrong 10 times then the lock closes forever and you can't
get the bomb.The code is 3 digits.
[keypad]>test
the guess is test
the code is 823
BZZZZEDDD!
[keypad]>456
BZZZZEDDD!
[keypad]>823
The container clicks open and the seal breaks,letting gas out.
You grab the neutron bomb and run as fast as you can to the
bridge where you must place it in the right spot.

---------
You burst onto the Bridge with the neutron destruct bomb
under your arm and surprise 5 Gothons who are trying to
take control of the ship.Each of them has an even uglier
clown costume than the last.The have't pulled their
weapons out yet,as they see the active bomb under your
arm and don't want to set it off.
>


--------------第3次完成--------------
'''
# 加分习题[暂时没做]
'''
1. 解释一下返回至下一个房间的工作原理。
2. 创建更多的房间，让游戏规模变大。
3. 除了让每个函数打印自己以外，再学习一下“文档字符串(docstrings)”式的注解。看
看你能不能将房间 述写成文档注解，然后修改运行它的代码，让它把文档注解打
印出来。
4. 一旦你用了文档注解作为房间 述，你还需要让这个函数打印出用户 示吗?试着
让运行函数的代码打出用户 示来，然后将用户输入传递到各个函数。你的函数应
该只是一些 if 语句组合，将结果打印出来，并且返回下一个房间。
5. 这其实是一个小版本的“有限状态机(finitestatemachine)”，找资料阅读了解一下，
  虽然你可能看不懂，但还是找来看看吧。
'''

```
---
## 第42题
### CODE
```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第42题 物以类聚--CLASS 类
'''
你可以使用class这个关键字创建更棒的“函数字典”。
用到class的编程语言被称作Obje:ct Oriented Programming(OOP)（面向对象编程）
空客A330飞欧洲的。

stuff = ['Test','This','Out']#stuff 是一个「列表」“类”list class
print ' '.join(stuff)#' '（空格）是一个「字符串」类string class

还有一个概念，叫做 boject(物件)，创建几个 class后就会素娥到。怎么创建class呢？和创建ROOMS的方法差不多，但是其实跟家的简单：
'''
## 编程开始：下面的编程代码术语「升级版」
class TheThing(object):
# 报错：AttributeError: 'TheThing' object has no attribute 'number'

	def _init_(self):
		self.number = 0
	def some_function(self):
		print "I got called."
	def add_me_up(self,more):#Debug1,在more前面增加一个空格ok。
		self.number += more#报错debug，这个number没有attribute。检查未见异常。
		return self.number

		print self # 临时
		print more# 临时
		print self.number# 临时

# two different things
a = TheThing()#没有找到问题。
b = TheThing()

a.some_function()
b.some_function()

print a.add_me_up(20)#报错debug，但是没有找到问题所在。
'''Traceback (most recent call last):
  File "/Users/yyy/Documents/Python_LP2THW/ex42.py", line 37, in <module>
    print a.add_me_up(20)#报错debug，但是没有找到问题所在。
  File "/Users/yyy/Documents/Python_LP2THW/ex42.py", line 23, in add_me_up
    self.number += more#报错debug，这个number没有attribute。检查未见异常。
AttributeError: 'TheThing' object has no attribute 'number'
'''
print a.add_me_up(20)
print b.add_me_up(30)
print b.add_me_up(30)

print a.number
print b.number

# 作者的吐槽
'''
Python是个旧语言，包含很多丑陋的设计决定，为了掩盖，它们就做了新的丑陋设计，然后告诉人们让他们习惯这些新的坏设计。class TheTHing(object)就是其中一个例子。你也不用担心你为什么要在class后面添加一个（object），好吧，跟着做就是了。
你看到参数里的self么怼了，它就是Python
穿件的格外的参数，有了它你才能实现a.some_function()'这种用法，这时候他就会把\前者翻译成''some_function(a)执行下去。为什么用self呢？因为你的函数并不知道你的这个“实例”是来自一个叫做TheThing或者别的名字的class。所以你只要一用一个通用的名字self,这样你写出来的函数在任何情况下都能正常哦给你做了。
其实，你可以使用self意外的别的字眼，不过这样做的话，你就会成为其他程序员的众矢之的。只有变态才会在这里乱改。。对以后会读到你的代码的人好点，因为你现在的代码10年以后，所有的代码都会是一团糟。
接下来看到_init_函数了嘛？这就是你微Python class 设置内部变量的方式。你可以使用.将它们设置到self上面。另外看到我们使用了add_me_up()为你创建的self.number加值。后面你可以看到我们如何为数字加数值。

Class是很强大的东西，你应该好好读读相关的东西。金科鞥多找些东西读读，多多实验。你其实知道它们应该怎么用，只要试试就知道了，好吧下面使用class写一个练习。

好吧，下面我们将41题重写一遍。

'''
from sys import exit
from random import randint

class Game(object):

	def _init_(self,start):
		self.quips=[
			"You died. You kinda suck at this.",
			"Your mom would be pround.If she were smarter.",
			"Such a luser.",
			"I have a small puppy that's etter at this."]
		self.start = start
	def play(self):
		next = self.stat

		while True:
			print "\n------------"
			room =getattr(self,next)
			next = room()
# 我发现下面连续的定义的5个函数和ex41中至少是在名称和顺序上是一样的。
#在新的death()函数里，比上一个版本简洁的多。
# 在上一个版本里用到的是ROOMS = {  }这样的东西。多定义了一个函数def runner(），多了一个函数runner(参数ROOMS)
#在这个版本里声明了一个类：class Game(object)
#在这个版本里多了一个参数a_game，而且这个a_game还可以执行play()方法。
	def death(self):
		print self.quips[randint(0,len(self.quips)-1)]
		exit(1)

	def central_corridor(self):
		print "The Gothons of Planet Percal #25 have invaded your ship and destroyed"
		print "your entire crew. You are the last surviving member and your last"
		print "mission is to get the neutron destruct bomb from the Weapons Armory,"
		print "put it in the bridge, and blow the ship up after getting into an "
		print "escape pod."
		print "\n"
		print "You're running down the central corridor to the Weapons Armory when"
		print "a Gothon jumps out, red scaly skin, dark grimy teeth, and evil clown costume"
		print "flowing around his hate filled body. He's blocking the door to the"
		print "Armory and about to pull a weapon to blast you."

		action =  raw_input("> ")


		if action == "shoot!":
			print "Quick n the draw you yank out your blaster and fire it at the Gothon."

			print "His clown costume is flowing and moivng around his body,which throws"

			print "off your aim.Your laser hits his costume but misses him entirely. This"

			print "completely ruins his brand new costume his mother bought him, which"

			print " makes him fly into an insane rage and blast you repeatedly in the face until"

			print "you are dead. Then he eats you."

			return 'death'

		elif action == "dodge!":
			print "Like a world class boxer you dodge,weave,slip and slide right"
			print "as the Gothon's blaser cranks a laser past your head."
			print "In the middle of your artful dodge your foot slips and you"
			print "bang your head on the metal wall and pass out."
			print "You wake up shortly after only to die as the Gothon stomps on"
			print "your head and eats you."
			return 'death'
		elif action == "tell a joke":
			print "Lucky for you they made you learn Gothon insults in the academy."
			print "You tell the one Gothon joke you know:"
			print "Lbhe zbgure vf fb sng, jura fur fvgf nebhaq gur ubhfr, fur fvgf nebhaq gur ubhfr."
			print "The Gothon stops, tries not to laugh, then busts out laughing and can't move."
			print "While he's laughing you run up and shoot him square in the head"
			print "putting him down, then jump through the Weapon Armory door."
			return 'laser_weapon_armory'

		else:
			print "DOES NOT COMPUTE!"
			return 'central_corridor'

	def laser_weapon_armory(self):
		print "You do a dive roll into the Weapon Armory, crouch and scan the room"
		print "for more Gothons that might be hiding. It's dead quiet, too quiet."
		print "You stand up and run to the far side of the room and find the"
		print "neutron bomb in its container. There's a keypad lock on the box"
		print "andyouneedthecodetogetthebombout. If you get the code"
		print "wrong 10 times then the lock closes forever and you can't"
		print "get the bomb. The code is 3 digits."
		code = "%d%d%d" % (randint(1,9), randint(1,9),randint(1,9))
		guess = raw_input("[keypad]> ")
		guesses = 0

		while guess !=code and guesses < 10:
			print "BZZZZZEDDDD!"
			guesses += 1
			guess = raw_input("[keypad]>")

		if guess == code:
			print "The container clicks open and the seal breaks, letting gas out."
			print "You grab the neutron bomb and run as fast as you can to the "
			print "bridge where you must place it in the right spot."
			return 'the_bridge'
		else:
			print "The lock buzzes one last time and then you hear a sickening"
			print "melting sound as the mechanism is fused together."
			print "You decide to sit there, and finally the Gothons blow up the"
			print "ship from their ship and you die."
			return 'death'

	def the_bridge(self):
		print "You burst onto the Bridge with the netron destruct bomb"
		print "under your arm and surprise 5 Gothons who are trying to"
		print "takecontroloftheship. Eachofthemhasan even uglier"
		print "clown costume than the last. They haven't pulled their"
		print "weapons out yet, as they see the active bomb under your"
		print "arm and don't want to set it off."

		action = raw_input("> ")

		if action == "throw the bomb":
			print "In a pannic you throw the bomb at the group of Gothons"
			print "and make a leap for the door. Right as you drop it a "
			print "Gothon shoots you right in the back killing you."
			print "As you die you see another Gothon frantically try to disarm"
			print "the bomb. You die knowing they will probably blow up when"
			print "it goes off."
			return 'death'

		elif action == "slowly place the bomb":
			print "You point your blaster at the bomb under your arm"
			print "and the Gothons put their hands up and start to sweat."
			print "You inch backward to the door, open it, and then carefully"
			print "place the bomb on the floor, pointing your blaster at it."
			print "You then jump back through the door, punch the close button"
			print "and blast the lock so the Gothons can't get out."
			print "Now that the bomb is placed you run to the escape pod to"
			print "get off this tin can."
			return 'escape_pod'
		else:
			print "SOES NOT COMPUTE!"
			return "the_bridge"

	def escape_pod(self):
		print "You rush through the ship desperately trying to make it to"
		print "the escape pod before the whole ship explodes. It seems like"
		print "hardly any Gothons are on the ship, so your run is clear of"
		print "interference. Yougettothechamberwiththe escape pods, and"
		print "now need to pick one to take. Some of them could be damaged"
		print "but you don't have time to look. There's 5 pods, which one"
		print "do you take?"

		good_pod = randint(1,5)
		guess = raw_input("[pod #]> ")

		if int(guess) != good_pod:
			print "You jump into pod %s and hit the eject button."% guess
			print "The pod escapes out into the void of space,then"
			print "implodes as the hull ruptures,crushing your body"
			print "into jam jelly."
			return 'death'
		else:
			print "You jump into pod %s and hit the eject button." % guess
			print "The pod easily slides out into space heading to"
			print "the planet below. As it flies to the planet,you look"
			print "back and see your ship implode then explode like a"
			print "bright star, taking out the Gothon ship at the same"
			print "time. You won!"
			exit(0)

a_game =Game("central_corridor")
a_game.play()

'''

# 加分题
'''
1. 研究一下__dict__是什么东西，应该怎样使用。

2. 再为游戏添加一些房间，确认自己已经学会使用 class 。

3. 创建一个新版本，里边使用两个 class，其中一个是Map，另一个是Engine。
示:把play放到Engine里面。

'''

```
### RESULT
```

# 运行后的结果：
# 20171104注意，本文件的py代码并没有很好的通过“debug”，所以日后需要进一步调试，为了不行动瘫痪，我们将进入下一章ex43。

'''
这个版本的游戏和你的上一版效果应该是一样的，其实有些代码都几乎一样。比较一下两版代码，弄懂其中不同的地方，重点需要理解这些东西:

1. 怎样创建一个classGame(object)并且放函数到里边去。

2. __init__是一个特殊的初始方法，可以预设重要的变量在里边。

3. 为 class 添加函数的方法是将函数在 class 下再缩进一阶，class 的架构就是通过缩进实现的，这点很重要。

4. 你在函数里的内容又缩进了一阶。

5. 注意冒号的用法。

6. 理解self的概念，以及它在__init__、play、death里是怎样使用的。

7. 研究play里的getattr的功能，这样你就能明白play所做的事情。其实你可以手动在 Python命令行实验一下，从而弄懂它。

8. 最后我们怎样创建了一个Game，然后通过play()让所有的东西运行起来。

```
---
## 第43题
### CODE
```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第43题 你来制作一个游戏
##作者要求：
'''
你要开始学会自食其力了，那就是你需要的所有的信息网上都有，你只要去搜索就能找到。
以下是你的要求：
1.制作一个截然不同的游戏。
2.使用多个文件，并使用import调用这些文件。
3.对每个房间使用一个class,class的明明要能体现出它的用处。例如GlodRoom,KoiPondRoom.
4.你的执行器代码应该了解这些房间，所以创建一个class来调用并记录这些房间，这里有许多的方法，考虑返回一个房间，或者使用变量来指定下一个房间。

 其他的事情就全靠你了。花一个星期完成这件任务，做一个你能做出来的最好的游戏。使用你学过的任何东西(类，函数，字典，列表......)来改进你的程序。 这节课的目的是教你如何构建 class 出来，而这些class 又能调用到其它 Python 文件中的 class。
我不会详细地告诉你告诉你怎样做，你需要自己完成。试着下手吧，编程就是解决问题的过程，这就意味着你要尝试各种可能性，进行实验，经历失败，然后丢掉你做出来的东西重头开始。当你被某个问题卡住的时候，你可以向别人寻求帮助，并把你的代码贴出来给他们看。如果有人刻薄你，别理他们，你只要集中精力在帮你的人身上就可以了。持续修改和清理你的代码，直到它完整可执行为止， 然后再研究一下看它还能不能被改进。
祝你好运，下个星期你做出游戏后我们再见。

'''

```
###RESULT
```
# 运行后的结果：
'''
这里我没有单独完成或者写出什么来，下面请继续。

'''
```
---
## 第44题
### CODE
```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第44题 给你的游戏打分
这节练习的目的是检查评估你的游戏。也许你只完成一半，卡在那里没有进行下去，也许你勉强做出来了。不管怎样，我们将串一下你应该弄懂的一些东西，并确认你的游戏里有使用到它们。我们将学习如何用正确的格式构建 class，使用 class的一些通用习惯，另外还有很多的“书本知识”让你学习。

为什么我会让你先行尝试，然后才告诉你正确的做法呢?因为从现在开始你要学会“自给自足”，以前是我牵着你前行，以后就得靠你自己了。后面的习题我只会告诉你你的任务，你需要自己去完成，在你完成后我再告诉你如何可以改进你的 作业。

一开始你会觉得很困难并且很不习惯，但只要坚持下去，你就会培养出自己解决问题的能力。你还会找出创新的方法解决问题，这比从课本中拷贝解决方案强多 了。

函数的风格

以前我教过的怎样写好函数的方法一样是适用的，不过这里要添加几条:

  由于各种各样的原因，程序员将 class(类)里边的函数称作 method (方法)。很大 程度上这只是个市场策略(用来推销OOP)，不过如果你把它们称作“函数”的话，是会有啰嗦的人跳出来纠正你的。如果你觉得他们太烦了，你可以告诉他们从数学方面演示一下“函数”和“方法”究竟有什么不同，这样他们会很快闭嘴的。

「这里作者的意思是说，其实面向对象程序设计OOP里的“method方法”在数学上就是“函数”」  

  在你使用 class的过程中，很大一部分时间是告诉你的 class 如何“做事情”。给这些函数命名的时候，与其命名成一个名词，不如命名为一个动词，作为给 class 的 一个命令。就和 list 的 pop (抛出)函数一样，它相当于说:“嘿，列表，把这东西给 我pop出去。”它的名字不是remove_from_end_of_list，因为即使它的功能的确是这样，这一串字符也不是一个命令。
  让你的函数保持简单小巧。由于某些原因，有些人开始学习 class 后就会忘了这一 条。
  「作者的意思是：要保持函数的简洁小巧，要把函数ing名为动词而不是名词。」



  类的风格

    - 你的 class 应该使用 “camel case(驼峰式大小写)”，例如你应该使 用 SuperGoldFactory 而不是 super_gold_factory。
    - 你的__init__不应该做太多的事情，这会让 class 变得难以使用。「这话啥意思」
    - 你的其它函数应该使用 “underscore format(下划线隔词)”，所以你可以写my_awesome_hair而不是myawesomehair或者MyAwesomeHair。
    用一致的方式组织函数的参数。如果你的 class 需要处理 users、dogs、 和 cats，就保持这个次序(特别情况除外)。如果一个函数的参数是 (dog, cat, user) ，另一个的是 (user, cat, dog) ，这会让函数使用 起来很困难。
    不要对全局变量或者来自模组的变量进行重定义或者赋值，让这些东西自 顾自就行了。
    不要一根筋式地维持风格一致性，这是思维力底下的妖怪喽啰做的事情。 一致性是好事情，不过愚蠢地跟着别人遵从一些白痴口号是错误的行为 ——这本身就是一种坏的风格。好好为自己照想把。
    永远永远都使用 class Name(object) 的方式定义 class，否则你会碰到 大麻烦。


  代码风格
    为了以方便他人阅读，为自己的代码字符之间留下一些空白。你将会看到一些很差 的程序员，他们写的代码还算通顺，但字符之间没有任何空间。这种风格在任何编 程语言中都是坏习惯，人的眼睛和大脑会通过空白和垂直对齐的位置来扫 和区隔 视觉元素，如果你的代码里没有任何空白，这相当于为你的代码上了迷彩装。如果 一段代码你无法朗读出来，那么这段代码的可读性可能就有问题。如你找不到让某 个东西易用的方法，试着也朗读出来。这样不仅会逼迫你慢速而且真正仔细阅读过 去，还会帮你找到难读的段落，从而知道那些代码的易读性需要作出改进。
    学着模仿别人的风格写 Python 程序，直到哪天你找到你自己的风格为止。
    一旦你有了自己的风格，也别把它太当回事。程序员工作的一部分就是和别人的代 码打交道，有的人审美就是很差。相信我，你的审美某一方面一定也很差，只是你从未意识到而已。
    如果你发现有人写的代码风格你很喜欢，那就模仿他们的风格。

好的注释
  有程序员会告诉你，说你的代码需要有足够的可读性，这样你就无需写注释了。他们会以自己接近官腔的声音说“所以你永远都不应该写代码注释。”这些人要么是一 些顾问型的人物，如果别人无法使用他们的代码，就会付更多钱给他们让他们解决 问题。要么他们能力不足，从来没有跟别人合作过。别理会这些人，好好写你的注 解。
  写注解的时候，述清楚为什么你要这样做。代码只会告诉你“这样实现”，而不会告诉你“为什么要这样实现”，而后者比前者更重要。
  当你为函数写文档注解的时候，记得为别的代码使用者也写些东西。你不需要狂写一大堆，但一两句话谢谢这个函数的用法还是很有用的。
  最后要说的是，虽然注解是好东西，太多的注解就不见得是了。而且注解也是需要维护的，你要尽量让注解短小精悍一语中的，如果你对代码做了更改，记得检查并 更新相关的注解，确认它们还是正确的。  


  为你的游戏评分
  现在我要求你假装成是我，板起脸来，把你的代码打印出来，然后拿一支红笔，把代码中所有的错误都标出来。你要充分利用你在本章以及前面学到的知识。等 你批改完了，我要求你把所有的错误改对。这个过程我需要你多重复几次，争取 找到更多的可以改进的地方。使用我前面教过的方法，把代码分解成最细小的单 元一一进行分析。
  这节练习的目的是训练你对于细节的关注程度。等你检查完自己的代码，再找一段别人的代码用这种方法检查一遍。把代码打印出来，检查出所有代码和风格方面的错误，然后试着在不改坏别人代码的前 下把它们修改正确、
  这周我要求你的事情就是批改和纠错，包含你自己的代码和别人的代码，再没有别的了。这节习题难度还是挺大，不过一旦你完成了任务，你学过的东西就会牢 牢记在脑中。

```
### RESULT
```
本章无代码。
```
---
## 第45题
### CODE
```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第45题 对象、类、以及从属关系
# 以下是代码部分
## Animal is-a object(yes,sort of confusing) look at the extra credit
## Animal 是一个「对象」

class Animal(object):#
	pass
## 上面：这就用到了“类即是对象”的概念。他们决定用小写的“object”这个词作为一个类， 让你在创建新类时从它继承下来。有点晕了吧?一个类从另一个类继承，而后者 虽然是个类，但名字却叫“object”......不过在定义类的时候，别忘记要从 object 继承就好了。

##??
class Dog(Animal):
	def _init_(self,name):
		## ??
		self.name= name

## ??
class Cat(Animal):

	def _init_(self,name):
		##??
		self.name =name

## ??
class Person(object):

	def _init_(self,name):
		## ??
		self.name = name

		## Person has-a pet of some kind
		self.pet = None

## ??
class Employee(Person):

	def _init_(self,name,salary):
		## ?? hmm what is this trange magic?
		super(Employee,self)._init_(name)
		## ??
		self.salary =salary

## ??
class Fish(object):
	pass

## ??
class Salmon(Fish):
	pass

## rover is-a Dog
rover = Dog("Rover")

## ??
satan = Cat("Satan")

##??
mary =Person("Mary")

## ??
mary.pet = satan

## ??
frank = Employee("Frank",120000)

## ??
frank.pet =rover

## ??
flipper = Fish()

## ??
crouse = Salmon()

##??
harry = Halibut()

## 虽然说了一大堆关于“类class”和“对象object”的概念——object是class的一种是一种新的class
```
### RESULT
```
# 运行后的结果：
'''
习题 45: 对象、类、以及从属关系

有一个重要的概念你需要弄明白，那就是“类(class)”和“对象(object)”的区别。问
题在于，class 和object并没有真正的不同。它们其实是同样的东西，只是在不同的时间名字不同罢了。我用禅语来解释一下吧:
鱼和泥鳅有什么区别?
这个问题有没有让你有点晕呢?说真的，坐下来想一分钟。我的意思是说，鱼和泥鳅是不一样，不过它们其实也是一样的是不是?泥鳅是鱼的一种，所以说没什 么不同，不过泥鳅又有些特别，它和别的种类的鱼的确不一样，比如泥鳅和黄鳝 就不一样。所以泥鳅和鱼既相同又不同。怪了。这个问题让人晕的原因是大部分人不会这样去思考问题，其实每个人都懂这一点， 你无须去思考鱼和泥鳅的区别，因为你知道它们之间的关系。你知道泥鳅是鱼的一种，而且鱼还有别的种类，根本就没必要去思考这类问题。
让我们更进一步，假设你有一只水桶，里边有三条泥鳅。假设你的好人卡多到没地方用，于是你给它们分别取名叫小方，小斌，小星。现在想想这个问题:
小方和泥鳅有什么区别? 这个问题一样的奇怪，但比起鱼和泥鳅的问题来还好点。你知道小方是一条泥鳅，所以他并没什么不同，他只是泥鳅的一个“实例(instance)”。小斌和小星一样也是泥鳅的实例。我的意思是说，它们是由泥鳅创建出来的，而且代表着和泥鳅一样 的属性。所以我们的思维方式是(你可能会有点不习惯):鱼是一个“类(class)”，泥鳅是一个“类(class)”，而小方是一个“对象(object)”。仔细想想，然后我再一点一点慢 慢解释给你。鱼是一个“类”，表示它不是一个真正的东西，而是一个用来 述具有同类属性的 实例的概括性词汇。
你有鳍?你有鳔?你住在水里?好吧那你就是一条鱼。后来河蟹养殖专家路过，看到你的水桶，于是告诉你:“小伙子，你这些鱼是泥 鳅。” 专家一出，真相即现。并且专家还定义了一个新的叫做“泥鳅”的“类”，而这个“类”又有它特定的属性。细长条?有胡须?爱钻泥巴?吃起来味道还可以? 那你就是一条泥鳅。
最后家庭煮父过来了，他跟河蟹专家说:“非也非也，你看到的是泥鳅，我看到的是小方，而且我要把小方和剁椒配一起做一道小菜。”于是你就有了一只叫做 小方的泥鳅的“实例(instance)”(泥鳅也是鱼的一个“实例”)，并且你使用了它(把 它塞到你的胃里了)，这样它就是一个“对象(object)”。
这会你应该了解了:小方是泥鳅的成员，而泥鳅又是鱼的成员。这里的关系式:
对象属于某个类，而某个类又属于另一个类。

写成代码是什么样子？

这个概念有点绕人，不过实话说，你只要在创建和使用 class 的时候操心一下 就可以了。我来给你两个区分 Class 和 Object 的小技巧。
首先针对类和对象，你需要学会两个说法，“is-a(是啥)”和“has-a(有啥)”。“是啥”要用在谈论“两者以类的关系互相关联”的时候，而“有啥”要用在“两者无共同点， 仅是互为参照”的时候。
接下来，通读这段代码，将每一个注解为 ##?? 的位置标明他是“is-a”还是“has-a”的关系，并讲明白这个关系是什么。在代码的开始我还举了几个例子，所以你只 要写剩下的就可以了。
记住，“是啥”指的是鱼和泥鳅的关系，而“有啥”指的是泥鳅和鳃的关系。(译注:为了解释方便，译文使用了中文鱼名。原文使用的是“三文鱼(salmon)”和“大比目鱼(halibut)”，名字也是英文常用人名。)


关于 class Name(object)
记得我曾经强迫让你使用 class Name(object) 却没告诉你为什么吧，现在你 已经知道了“类”和“对象”的区别，我就可以告诉你原因了。如果我早告诉你的话， 你可能会晕掉，也学不会这门技术了。
真正的原因是在 Python 早期，它对于class的定义在很多方面都是严重有问 题的。当他们承认这一点的时候已经太迟了，所以逼不得已，他们需要支持这种有问题的 class。为了解决已有的问题，他们需要引入一种“新类”，这样的话“旧 类”还能继续使用，而你也有一个新的正确的类可以使用了。
这就用到了“类即是对象”的概念。他们决定用小写的“object”这个词作为一个类， 让你在创建新类时从它继承下来。有点晕了吧?一个类从另一个类继承，而后者 虽然是个类，但名字却叫“object”......不过在定义类的时候，别忘记要从 object 继承就好了。
的确如此。一个词的不同就让这个概念变得更难理解，让我不得不现在才讲给你。
现在你可以试着去理解“一个是对象的类”这个概念了，如果你感兴趣的话。
不过我还是建议你别去理解了，干脆完全忘记旧格式和新格式类的区别吧，就假 设 Python 的 class 永远都要求你加上 (object) 好了，你的脑力要留着思考更 重要的问题。


加分习题
1. 研究一下为什么 Python 添加了这个奇怪的叫做object的 class，它究竟有什么 含义呢?
2. 有没有办法把Class当作Object使用呢?
3. 在习题中为 animals、fish、还有 people 添加一些函数，让它们做一些事情。看看
当函数在 Animal 这样的“基类(base class)”里和在 Dog 里有什么区别。
4. 找些别人的代码，理清里边的“是啥”和“有啥”的关系。
5. 使用列表和字典创建一些新的一对应多的“has-many”的关系。
6. 你认为会有一种“has-many”的关系吗?阅读一下关于“多重继承(multiple
inheritance)”的资料，然后尽量避免这种用法。
'''
```
---
## 第46题
### CODE
```
#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第46题 一个项目骨架
# 以下是代码部分
'''
这里你将学会如何建立一个项目“骨架”目录。这个骨架目录具备让项目跑起来的所有基本内容。它里边会包含你的项目文件布局、自动化测试代码，模组，以及安装脚本。当你建立一个新项目的时候，只要把这个目录复制过去，改改目录的名字，再编辑里边的文件就行了。
'''
## 骨架内容
### 首先使用下述命令创建你的骨架目录：
'''
~ $ mkdir -p projects
~ $ cd projects/
~/projects $ mkdir skleton
~/projects $ cd skeleton
~/projects/skeleton $ mkdir in NAME tests docs
'''
### 我使用了一个叫做projects 的目录来存放我自己的各个项目。然后我在李彬啊建立了一个叫做 skeleton 的文件夹，这就是我们新项目的基础目录。其中叫做NAME的文件夹是你的项目等主要文件夹，你剋一将它任意明明。

##接下来我们要配置一些初始文件：

'''
~/projects/skeleton $ touch NAME/_init_.py
~/projects/skeleton $ touch tests/_init_.py


'''
## 以上命令为你创建了空的模组目录，以供你后面为其添加代码。然后我们需要建立一个setup.py文件，这个文件在安装项目的时候我们会用到它。

## 文件名  setup.py
try:
	from setuptools import setup
except ImportError:
	from distutils.core import setup

config ={
	'description':'My Project',
	'author':'My Name',
	'url':'URL to ger it at.',
	'download_url':'Where to download it.',
	'author_email':'My email.',
	'version':'0.1',
	'install_requires':['nose'],
	'packeage':['NAME'],
	'scripts':[],
	'name':'projectname'
}

setup(**config)

#编辑这个文件，把自己的练习方式写进去，然后放到那里就行了。最后你需要一个简单的测试专用的骨架文件叫tests/NAME_tests.py



## 文件名NAME_tests.py
from nose.tools import *
import NAME

def setup():
	print "SETUP!"

def teardown():
	print "TEAR DOWN!"

def test_basic():
	print "I RAN!"

## Python 软件包的安装
''''
接下来你需要安装下面的软件包:
1. pip – http://pypi.python.org/pypi/pip
2. distribute – http://pypi.python.org/pypi/distribute
3. nose – http://pypi.python.org/pypi/nose/
4. virtualenv – http://pypi.python.org/pypi/virtualenv



我要预先警告你，这个过程会是相当无趣。在业内我们将这种事情叫做 “yak shaving(剃牦牛)”。它指的是在你做一件有意义的事情之前的一些准备工作，而这些准备工作又是及其无聊冗繁的。你要做一个很酷的 Python 项目，但是创建骨架目录需要你安装一些软件包，而安装软件包之前你还要安装 package installer(软件包安装工具)，而要安装这个工具你还得先学会如何在你的操作系统下安装软件，真是烦不胜烦呀。无论如何，还是克服困难把。你就把它当做进入编程俱乐部的一个考验。每个程序员都会经历这条道路，在每一段“酷”的背后总会有一段“烦”的。
'''
##测试你的配置
'''
安装了所有上面的软件包以后，你就可以做下面的事情了:
~/projects/skeleton $ nosetests .
-------------------------------------------------------- --------------
Ran 1 test in 0.007s
OK

下一节练习中我会告诉你 nosetests 的功能，不过如果你没有看到上面的画面， 那就说明你哪里出错了。确认一下你的NAME和tests目录下存在__init__.py， 并且你没有把 tests/NAME_tests.py 命名错。

'''
##使用这个骨架
'''
剃牦牛的事情已经做的差不多了，以后每次你要新建一个项目时，只要做下面的 事情就可以了:
1. 拷贝这份骨架目录，把名字改成你新项目的名字。
2. 再将 NAME 模组更名为你需要的名字，它可以是你项目的名字，当然别的名字也
行。
3. 编辑 setup.py 让它包含你新项目的相关信息。
4. 重命名tests/NAME_tests.py，让它的名字匹配到你模组的名字。
5. 使用nosetests检查有无错误。
6. 开始写代码吧。

'''
## 小测验
'''
小测验
这节练习没有加分习题，不过需要你做一个小测验:
1. 找文档阅读，学会使用你前面安装了的软件包。
2. 阅读关于setup.py的文档，看它里边可以做多少配置。Python 的安装器并不是一个好软件，所以使用起来也非常奇怪。
3.创建一个项目，在模组目录里写一些代码，并让这个模组可以运行。
4.在目录下放一个可以运行的脚本，找材料学习一下怎样创建可以在系统下运行bin的 Python 脚本。
5.在你的setup.py中加入bin这个目录，这样你安装时就可以连它安装进去。
6.使用setup.py安装你的模组，并确定安装的模组可以正常使用，最后使用pip将其卸载。
'''


# 运行后的结果：
'''
本章学的云里雾里。大概是说要在网上有这种模块可以自动安装一些“包”和“模块”
'''

```
### RESULT
```
Nothing
```
---
## 第47题
### CODE
```

#!/usr/bin/python
# -*- coding: utf-8 -*-
# 第47题 自动化测试
'''
为了确认游戏的功能是否正常，你需要一遍一遍地在你的游戏中输入命令。这个过程是很枯燥无味的。如果能写一小段代码用来测试你的代码岂不是更好?然后只要你对程序做了任何修改，或者添加了什么新东西，你只要“跑一下你的测试”，而这些测试能确认程序依然能正确运行。这些自动测试不会抓到所有的 bug， 但可以让你无需重复输入命令运行你的代码，从而为你节约很多时间。

从这一章开始，以后的练习将不会有“你应该看到的结果”这一节，取而代之的是一个“你应该测试的东西”一节。从现在开始，你需要为自己写的所有代码写自动化测试，而这将让你成为一个更好的程序员。

我不会试图解释为什么你需要写自动化测试。我要告诉你的是，你想要成为一个程序员，而程序的作用是让无聊冗繁的工作自动化，测试软件毫无疑问是无聊冗繁的，所以你还是写点代码让它为你测试的更好。

这应该是你需要的所有的解释了。因为你写单元测试的原因是让你的大脑更加强健。你读了这本书，写了很多代码让它们实现一些事情。现在你将更进一步，写出懂得你写的其他代码的代码。这个写代码测试你写的其他代码的过程将强迫你清楚的理解你之前写的代码。这会让你更清晰地了解你写的代码实现的功能及其 原理，而且让你对细节的注意更上一个台阶。

'''
## 撰写测试用例
'''
我们将拿一段非常简单的代码为例，写一个简单的测试，这个测试将建立在上节 我们创建的项目骨架上面。
首先从你的项目骨架创建一个叫做ex47的项目。确认该改名称的地方都有改过， 尤其是test/ex47_tests.py这处不要写错，另外运行 nosetest 确认一下没有错误信息。检查一下tests/skel_tests.pyc这个文件，有的话就把它删掉， 这一点需要尤其注意。
接下来创建一个简单的 ex47/game.py文件，里边放一些用来被测试的代码。我们现在放一个傻乎乎的小 class 进去，用来作为我们的测试对象:
'''
#代码开始

class Room(object):

	def _init_(self,name,description):
		self.name = name
		self.description = description
		self.paths = {}

	def go(self,direction):
		return self.paths.get(direction,None)

	def ass_paths(self,paths):
		self.paths.update(paths)

# 准备好这个文件，接下来把测试骨架改为这个样子：

from nose.tools import *
from ex47.game import Room

def test_room():
	gold = Room("GoldRoom",
	"""This room has gold in it you can grab.There's a
	door to te north.""")
	assert_equal(gold.name,"GoldRoom")
	assert_equal(gold.paths,{})

def test_room_paths():
	center = Room("Center","Test room in the center.")
	north = Room("North","Test room in the north.")
	south = Room("South","Test room in the south.")

	center.add_paths({'north':north,'south':south})
	assert_equal(center.go('north'),north)
	assert_equal(center.go('south'),south)

def test_map():
	start = Room("Start","You can go west and down a hole.")
	west =Room("Trees","There are trees here,you can go east")
	down =Room("Dungeon","It's dark down here,you can go up.")

	start.add_paths({'west'.west,'down':down})
	west.add_paths({'east':start})
	down.add_paths({'up':start})

	assert_equal(start.go('west'),west)
	assert_equal(start.go('west').go('east'),start)
	assert_equal(start.go('down').go('up'),start)

## 文字：
''''
这个文件 import了你在ex47.game创建的Room这个类，接下来我们要做的就 是测试它。于是我们看到一系列的以 test_ 开头的测试函数，它们就是所谓的“测 试用例(test case)”，每一个测试用例里面都有一小段代码，它们会创建一个或者一些房间，然后去确认房间的功能和你期望的是否一样。它测试了基本的房间功能，然后测试了路径，最后测试了整个地图。
这里最重要的函数时assert_equal，它保证了你设置的变量，以及你在Room里设置的路径和你的期望相符。如果你得到错误的结果的话，nosetests将会打印出一个错误信息，这样你就可以找到出错的地方并且修正过来。
'''
#测试指南
'''
在写测试代码时，你可以照着下面这些不是很严格的指南来做:
1. 测试脚本要放到tests/目录下，并且命名为BLAH_tests.py，否
则 nosetests 就不会执行你的测试脚本了。这样做还有一个好处就是防止测试代 码和别的代码互相混掉。
2. 为你的每一个模组写一个测试。
3. 测试用例(函数)保持简短，但如果看上去不怎么整洁也没关系，测试用例一般都
有点乱。
4. 就算测试用例有些乱，也要试着让他们保持整洁，把里边重复的代码删掉。创建一
些辅助函数来避免重复的代码。当你下次在改完代码需要改测试的时候，你会感谢
  我这一条建议的。重复的代码会让修改测试变得很难操作。
5. 最后一条是别太把测试当做一回事。有时候，更好的方法是把代码和测试全部删掉，
然后重新设计代码。

# 你应该看到的结果


~/projects/simplegame $ nosetests ...
-------------------------------------------------------- --------------
Ran 3 tests in 0.007s
OK
177
 如果一切工作正常的话，你看到的结果应该就是这

加分习题
1. 仔细读读 nosetest 相关的文档，再去了解一下其他的替代方案。
2. 了解一下 Python 的 “doc tests” ，看看你是不是更喜欢这种测试方式。
3. 改进你游戏里的 Room，然后用它重建你的游戏，这次重写，你需要一边写代码，
一边把单元测试写出来。


'''


```
### RESULT
```
# 运行后的结果：
'''
习题 45: 对象、类、以及从属关系

有一个重要的概念你需要弄明白，那就是“类(class)”和“对象(object)”的区别。问
题在于，class 和object并没有真正的不同。它们其实是同样的东西，只是在不同的时间名字不同罢了。我用禅语来解释一下吧:
鱼和泥鳅有什么区别?
这个问题有没有让你有点晕呢?说真的，坐下来想一分钟。我的意思是说，鱼和泥鳅是不一样，不过它们其实也是一样的是不是?泥鳅是鱼的一种，所以说没什 么不同，不过泥鳅又有些特别，它和别的种类的鱼的确不一样，比如泥鳅和黄鳝 就不一样。所以泥鳅和鱼既相同又不同。怪了。这个问题让人晕的原因是大部分人不会这样去思考问题，其实每个人都懂这一点， 你无须去思考鱼和泥鳅的区别，因为你知道它们之间的关系。你知道泥鳅是鱼的一种，而且鱼还有别的种类，根本就没必要去思考这类问题。
让我们更进一步，假设你有一只水桶，里边有三条泥鳅。假设你的好人卡多到没地方用，于是你给它们分别取名叫小方，小斌，小星。现在想想这个问题:
小方和泥鳅有什么区别? 这个问题一样的奇怪，但比起鱼和泥鳅的问题来还好点。你知道小方是一条泥鳅，所以他并没什么不同，他只是泥鳅的一个“实例(instance)”。小斌和小星一样也是泥鳅的实例。我的意思是说，它们是由泥鳅创建出来的，而且代表着和泥鳅一样 的属性。所以我们的思维方式是(你可能会有点不习惯):鱼是一个“类(class)”，泥鳅是一个“类(class)”，而小方是一个“对象(object)”。仔细想想，然后我再一点一点慢 慢解释给你。鱼是一个“类”，表示它不是一个真正的东西，而是一个用来 述具有同类属性的 实例的概括性词汇。
你有鳍?你有鳔?你住在水里?好吧那你就是一条鱼。后来河蟹养殖专家路过，看到你的水桶，于是告诉你:“小伙子，你这些鱼是泥 鳅。” 专家一出，真相即现。并且专家还定义了一个新的叫做“泥鳅”的“类”，而这个“类”又有它特定的属性。细长条?有胡须?爱钻泥巴?吃起来味道还可以? 那你就是一条泥鳅。
最后家庭煮父过来了，他跟河蟹专家说:“非也非也，你看到的是泥鳅，我看到的是小方，而且我要把小方和剁椒配一起做一道小菜。”于是你就有了一只叫做 小方的泥鳅的“实例(instance)”(泥鳅也是鱼的一个“实例”)，并且你使用了它(把 它塞到你的胃里了)，这样它就是一个“对象(object)”。
这会你应该了解了:小方是泥鳅的成员，而泥鳅又是鱼的成员。这里的关系式:
对象属于某个类，而某个类又属于另一个类。

写成代码是什么样子？

这个概念有点绕人，不过实话说，你只要在创建和使用 class 的时候操心一下 就可以了。我来给你两个区分 Class 和 Object 的小技巧。
首先针对类和对象，你需要学会两个说法，“is-a(是啥)”和“has-a(有啥)”。“是啥”要用在谈论“两者以类的关系互相关联”的时候，而“有啥”要用在“两者无共同点， 仅是互为参照”的时候。
接下来，通读这段代码，将每一个注解为 ##?? 的位置标明他是“is-a”还是“has-a”的关系，并讲明白这个关系是什么。在代码的开始我还举了几个例子，所以你只 要写剩下的就可以了。
记住，“是啥”指的是鱼和泥鳅的关系，而“有啥”指的是泥鳅和鳃的关系。(译注:为了解释方便，译文使用了中文鱼名。原文使用的是“三文鱼(salmon)”和“大比目鱼(halibut)”，名字也是英文常用人名。)


关于 class Name(object)
记得我曾经强迫让你使用 class Name(object) 却没告诉你为什么吧，现在你 已经知道了“类”和“对象”的区别，我就可以告诉你原因了。如果我早告诉你的话， 你可能会晕掉，也学不会这门技术了。
真正的原因是在 Python 早期，它对于class的定义在很多方面都是严重有问 题的。当他们承认这一点的时候已经太迟了，所以逼不得已，他们需要支持这种有问题的 class。为了解决已有的问题，他们需要引入一种“新类”，这样的话“旧 类”还能继续使用，而你也有一个新的正确的类可以使用了。
这就用到了“类即是对象”的概念。他们决定用小写的“object”这个词作为一个类， 让你在创建新类时从它继承下来。有点晕了吧?一个类从另一个类继承，而后者 虽然是个类，但名字却叫“object”......不过在定义类的时候，别忘记要从 object 继承就好了。
的确如此。一个词的不同就让这个概念变得更难理解，让我不得不现在才讲给你。
现在你可以试着去理解“一个是对象的类”这个概念了，如果你感兴趣的话。
不过我还是建议你别去理解了，干脆完全忘记旧格式和新格式类的区别吧，就假 设 Python 的 class 永远都要求你加上 (object) 好了，你的脑力要留着思考更 重要的问题。


加分习题
1. 研究一下为什么 Python 添加了这个奇怪的叫做object的 class，它究竟有什么 含义呢?
2. 有没有办法把Class当作Object使用呢?
3. 在习题中为 animals、fish、还有 people 添加一些函数，让它们做一些事情。看看
当函数在 Animal 这样的“基类(base class)”里和在 Dog 里有什么区别。
4. 找些别人的代码，理清里边的“是啥”和“有啥”的关系。
5. 使用列表和字典创建一些新的一对应多的“has-many”的关系。
6. 你认为会有一种“has-many”的关系吗?阅读一下关于“多重继承(multiple
inheritance)”的资料，然后尽量避免这种用法。
'''
```
---

## LOG
- 20171106 早上创建本文件，将11月初完成了4题贴上来，目前更新到43题。从40题左右开始又些难度了，有点难以理解了，不过还是废话少说先刷题。
- 20171109中午 刷完了所有题，但是真心讲后面这些就是类似于抄写代码，本着先刷完第一遍再说的态度先刷下来再说，后面这些题还是有些理解难度的，当你投入的时间不够的话，还是比较难以理解的。继续进步吧，死磕总是能磕下来的，等刷完 LP3THW了再来扣这些问题吧。由于 jianshu.com页面是有限制的，所有本文档只写了41-47，剩下的48-52题新启一个页面来填写。
