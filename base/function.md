## 函数 ##
函数比较抽象，和数学中的函数比较学习会容易理解些。

### 数学中的函数 ###
函数指一个量随着另一个量的变化而变化，在变化过程中，假设有两个变量 x 、 y ，如果对于任意一个 x 都有唯一确定的一个 y 和它对应，那么就称 y 是 x 的函数 $ y = f(x) $ ，x 的取值范围叫做定义域，y 对应的值的范围叫做值域。
如：正弦函数 sin 。

### 编程中的函数 ###
编程中的函数基本和数学中的概念一致，仅仅是定义域和值域的取值变成了编程中的数据类型，不再单纯地只有数，函数将数据和逻辑按需要组成一个独立的执行单元。
如：正弦函数 sin ，计算字符串长度的函数 strlen 。

数学中的 sin ，定义域是实数，值域是 -1.0 到 1.0 的实数；
编程中的 sin ，输入（参数）是实数，输出（返回值）也 -1.0 到 1.0 的实数；
编程中的 strlen ，输入（参数）是字符串，输出（返回值）是整数。

### Python 中的函数 ###
在数学中定义一个一元一次函数。

$$
    y = f(x) = 5 * x + 1
$$

在数学中使用这个函数 $ y = f(5) = 26 $ 。

在 Python 中定义一个一元一次函数：

```
def f(x):
    return 5 * x + 1
```

在 Python 中使用这个函数：

```
y = f(5)
```

在 Python 中定义用 def 关键字和函数名定义一个函数，接着是前后括号括起来的参数列表。
函数的逻辑实现代码相对定义函数的那一行进行缩进。

例如，按照北京市出租车自 2013 年 6 月 10 日起执行的计费标准，计算出租车费用的函数：

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
#

def taxi(distance):
    extra ＝ 1.0
    starting = 13.0
    price = 2.3
    threshold = 3000.0
    fare = starting + extra
    if distance > threshold:
        delta = (distance - threshold) / 1000.0
        delta = round(delta)
        fare = fare + delta * price
    return round(fare)
```

```def taxi(distance)``` 开始定义了一个函数名为 taxi 输入参数为 distance 的函数；

```extra ＝ 1.0``` 定义了燃油附加费；

```starting = 13.0``` 定义了起步价；

```price = 2.3``` 定义了每公里 2.3 元人民币；

```threshold = 3000.0``` 定义了起步价可以坐的距离， 3 公里；

```fare = starting + extra``` 表示了坐上出租车后便产生的 起步价 和 油附加费 的费用；

```if distance > 3000.0``` 判断行驶距离是否超过3公里；

```delta = (distance - 3000.0) / 1000.0``` 计算超出3公里后的距离；

```delta = round(delta)``` 表示对距离四舍五入；

```fare = fare + delta * price``` 表示除了之前已经产生的费用，还需要加上超出3公里后每公里 2.3 元的费用；

```return round(fare)``` 表示，最后的结算以元为单位，元以下四舍五入。


其中 [round](https://docs.python.org/3.5/library/functions.html#round) 是由 Python 提供的四舍五入计算函数，Python 还提供了很多其他的函数，比如 [print](https://docs.python.org/3.5/library/functions.html#print) 函数可以输出任何数据。
