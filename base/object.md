## 面向对象 ##
面向对象是真实世界在计算机编程中的抽象表现，真实世界中的任何事物都可以看作一个对象，抽象世界也可以。
真实世界中的事物都可以分门别类（生物分类，界门纲目科属种），任何事物都是一个类别的实例，都有属性和行为。
例如我自己作为一个普通的人类，有年龄、性别、籍贯等属性，有吃、喝、拉、撒等行为。
面向对象编程将真实世界的对象抽象为类后，添加了封装、多态和继承三个特性，同时将对象的行为定义成类的方法（method）。

### Python 中的面向对象 ###
Python 从设计之初就是一门面向对象的语言，在 Python 中任何东西都是对象。

#### 封装 ####
从一个“人”的抽象类 _Person_ 开始：

```
class Person:
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

Python 中，通过 _class_ 关键字来定义一个类， _Person_ 是类的名字；

```def __init__(self, name, age, gender)``` 这个函数定义了 _Person_ 类的封装（构建）方法，通过 _name_ ， _age_ ， _gender_ 来构建一个 _Person_ 类的对象；

```def eat(self, food)``` 和 ```def drink(self, water)``` 分别定义了 _Person_ 类的 _eat_ 方法和 _drink_ 方法；

```zhang = Person('张三', 24, '男')``` 创建了一个 _Person_ 类的实例对象。
创建一个对象时，将自动调用类的构建方法 _\_\_init\_\__ ，按照构建方法中定义的参数将 _'张三'_ 、_24_ 、_'男'_ 传递给构建方法，完成创建过程；

```zhang.eat('芝士汉堡')``` 调用了这个对象的 _eat_ 方法。

定义类的方法（method）和定义一个函数类似，仅仅是第一个参数是固定的 _self_ 而已。
在方法中，_self_ 表示当前对象。
调用对象的方法时，不用传 _self_ 参数。

#### 继承 ####
面向对象的继承指一个子类继承父类的方法。
如同世袭制一样，太子继承皇帝的权利。

继承“人”类，创建一个职员类 _Staff_：

```
class Staff(Person):
    def work(self):
        print('work hard')

zhang = Staff('张三', 24, '男')
zhang.drink('白酒')
zhang.wrok()
```

```class Staff(Person):``` 定义一个 _Staff_ 类，继承自 _Person_ 类；

```def work(self):``` 定义了一个 _work_ 方法；

```zhang = Staff('张三', 24, '男')``` 创建了一个 _Staff_ 类的实例对象。
因为没有重写构建方法 _\_\_init\_\__ ，所以直接调用父类 _Person_ 的构建方法完成创建过程。

```zhang.drink('白酒')``` 调用对象的 _drink_ 方法，这个方法继承自父类 _Person_ ；

```zhang.wrok()``` 调用对象的 _work_ 方法，将输出 _work hard_ 。

#### 多态 ####
面向对象中的多态指子类覆盖父类的方法，有自己的定义。
比如太子虽然继承皇帝的权利，但嗜好不一定跟皇帝一样。

继承职员类，创建一个工程师类 _Engineer_ ：

```
class Engineer(Staff):
    def work(self):
        print('create new BUG')

zhang = Engineer('张三', 24, '男')
zhang.wrok()
```

```class Engineer(Staff):``` 定义了一个 _Engineer_ 类，继承自 _Staff_ 类；

```def work(self):``` 定义一个 _work_ 方法，它覆盖了父类 _Staff_ 的 _work_ 方法；

```zhang.wrok()``` 调用了对象的 _work_ 方法，将输出 _create new BUG_ 。
