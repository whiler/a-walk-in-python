## 面向对象 ##
面向对象是真实世界在计算机编程中的抽象表现，真实世界中的任何事物都可以看作一个对象，抽象世界也可以。
真实世界中的事物都可以分门别类（生物分类，界门纲目科属种），任何事物都是一个类别的实例，都有属性和行为。
例如我自己作为一个普通的人类，有年龄、性别、籍贯等属性，有吃、喝、拉、撒等行为。
面向对象编程将真实世界的对象抽象为类后，添加了封装、多态和继承三个特性，同时将对象的行为定义成类的方法（ method ）。

### Python 中的面向对象 ###
Python 从设计之初就是一门面向对象的语言，在 Python 中任何东西都是对象。

#### 封装 ####
从一个“人”的抽象类 Person 开始：

```
class Person(object):
    def __init__(self, name, age, gender):
        self.name = name
        self.age = age
        self.gender = gender
    
    def eat(self, food):
        print(self.name + '正在吃' + food)
    
    def drink(self, water):
        print(self.name + '正在喝' + water)

zhang = Person('张三', 24, '男')
zhang.eat('芝士汉堡')

li = Person('李四', 26, '男')
li.drink('白酒')
````

Python 中，通过 class 关键字来定义一个类， Person 是类的名字；

```class Person(object)``` 定义一个 Person 类，继承自 object 类。 object 类是所有简单类的根源，如同

> 太极生两仪，两仪生四象。

中“太极”一般的存在。

```def init(self, name, age, gender)``` 这个函数定义了 Person 类的封装（构建）方法，通过 name ， age ， gender 来构建一个 Person 类的对象；

```def eat(self, food)``` 和 ```def drink(self, water)``` 分别定义了 Person 类的 eat 方法和 drink 方法；

```zhang = Person('张三', 24, '男')``` 创建了一个 Person 类的实例对象。
创建一个对象时，将自动调用类的构建方法 \_\_init\_\_ ，按照构建方法中定义的参数将 '张三' 、 24 、'男' 传递给构建方法，完成创建过程；

```zhang.eat('芝士汉堡')``` 调用了这个对象的 eat 方法。

定义类的方法（method）和定义一个函数类似，仅仅是第一个参数是固定的 self 而已。
在方法中，self 表示当前对象。
调用对象的方法时，不用传 self 参数。

#### 继承 ####
面向对象的继承指一个子类继承父类的方法。
如同世袭制一样，太子继承皇帝的权利。

继承“人”类，创建一个职员类 Staff ：

```
class Staff(Person):
    def work(self):
        print('work hard')

zhang = Staff('张三', 24, '男')
zhang.drink('白酒')
zhang.wrok()
```

```class Staff(Person)``` 定义一个 Staff 类，继承自 Person 类；

```def work(self)``` 定义了一个 work 方法；

```zhang = Staff('张三', 24, '男')``` 创建了一个 Staff 类的实例对象。
因为没有重写构建方法 \_\_init\_\_ ，所以直接调用父类 Person 的构建方法完成创建过程。

```zhang.drink('白酒')``` 调用对象的 drink 方法，这个方法继承自父类 Person ；

```zhang.wrok()``` 调用对象的 work 方法，将输出 work hard 。

#### 多态 ####
面向对象中的多态指子类覆盖父类的方法，有自己的定义。
比如太子虽然继承皇帝的权利，但嗜好不一定跟皇帝一样。

继承职员类，创建一个工程师类 Engineer ：

```
class Engineer(Staff):
    def work(self):
        print('create new BUG')

zhang = Engineer('张三', 24, '男')
zhang.wrok()
```

```class Engineer(Staff)``` 定义了一个 Engineer 类，继承自 Staff 类；

```def work(self)``` 定义一个 work 方法，它覆盖了父类 Staff 的 work 方法；

```zhang.wrok()``` 调用了对象的 work 方法，将输出 _create new BUG_ 。
