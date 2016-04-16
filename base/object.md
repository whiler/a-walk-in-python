## 面向对象 ##
为了能面向「对象」编程，得先学会面向兴趣编程、面向人民币编程和面向对象编程。
已经看到这儿了，面向兴趣编程算是学会了。
面向人民币编程这么实际的事还用想吗？
剩下需要学的就是面向对象了。

面向对象是真实世界在计算机编程中的抽象表现，真实世界中的任何事物都可以看作一个对象，抽象世界也可以。
真实世界中的事物都可以分门别类（生物分类，界门纲目科属种），任何事物都是一个类别的实例，都有属性和行为。
例如我自己作为一个普通的人类，有年龄、性别、籍贯等属性，有吃、喝、拉、撒等行为。
面向对象编程将真实世界的对象抽象为类后，添加了封装、多态和继承三个特性，同时将对象的行为定义成类的方法。

### Python 中的面向对象 ###
Python 从设计之初就是一门面向对象的语言，在 Python 中任何东西都是对象。从一个“人”的抽象开始：
```
class Person:
	def __init__(self, name, age, gender):
		self.name = name
		self.age = age
		self.gender = gender
	
	def eat(self, food):
		pass
	
	def drink(self, water):
		pass
````

Python 中，通过 class 关键字来定义一个类， Person 是类的名字；
def __init__(self, name, age, gender) 这个函数是定义了这个 Person 类的封装（构建）方法，通过 name ， age ， gender 来封装一个 Person 类；
def eat(self, food) 和 def drink(self, water) 分别定义了这个 Person 类的 eat 方法和 drink 方法。
