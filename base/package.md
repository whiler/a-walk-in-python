## 模块和包 ##
模块（ module ）和包（ package ）是用来组织管理函数的，在 Python 中，把多个函数写到一个文件中，这个文件就是一个模块了，就是这么简单。
把多个模块文件组织到文件夹中，这个文件夹就是包了，不难理解。
当然，把各个函数写到一个文件中构成模块，以及将各个模块组成包都需要按照一定的逻辑需要。
比如：将和时间相关的函数组织起来构成 [time](https://docs.python.org/3.5/library/time.html) 模块，将日期相关的函数组织起来形成 [datetime](https://docs.python.org/3.5/library/datetime.html) 模块，将字符串正则表达式匹配相关的函数组织起来的 [re](https://docs.python.org/3.5/library/re.html) 模块等。

为了使用特定模块／包提供的函数和类，需要引入这些模块／包。
引入这些模块／包后，可以通过模块／包调用里面提供的函数，也可以直接从模块／包中引入具体的函数，直接调用。

引入 time 模块并使用 time 模块中的 [time](https://docs.python.org/3.5/library/time.html#time.time) 函数，得到当前时刻的时间戳。

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
#

import time

timestamp = time.time()
print(timestamp)
```

直接从 time 模块中引入 time 函数，得到当前的时间戳。

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
#

from time import time

timestamp = time()
print(timestamp)
```


关于时间，准确地说是时刻，在编程中一般用时间戳（ timestamp ）表示。
时间戳是从格林威治时间公元 1970 年 01 月 01 日 00 时 00 分 00 秒起到一个时刻的总秒数，最开始的时刻记为 0.0 。

### 第三方包 ###
Python 自带了很多常用的基础模块，比如提到过的 time 、 datetime 、 re 。
当然，Python 也允许安装第三方包来扩展 Python 的处理能力，如同智能手机允许安装其他应用一样。

Python 通过 [PyPI (the Python Package Index)](https://pypi.python.org/pypi) 提供第三方包检索服务，用 [pip](https://pip.pypa.io/) 命令安装第三方包。

#### 安装 pip ####
从 Python 3.4 起，Python 已经自带 pip 了。
若没有安装，可以先下载 [get-pip.py](https://bootstrap.pypa.io/get-pip.py) ，然后用下面的命令安装：

```
python3 get-pip.py
```

#### 管理第三方包 ####
安装好 pip 后，可以通过 pip 管理第三方包：搜索、安装、更新、卸载。

搜索名字中包含 xml 的第三方包：

````
pip3 search xml
````

安装 [lxml](http://lxml.de/) 和 [requests](https://github.com/kennethreitz/requests) 这两个第三方包：

```
pip3 install lxml requests
```

更新 requests 包：

```
pip3 install --upgrade requests
```

卸载 requests 包：

```
pip3 uninstall requests
```
