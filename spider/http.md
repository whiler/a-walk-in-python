## HTTP ##
HTTP ，是一种服务器和浏览器之间互相乎沟通的简单协议，如同老乡之间用方言进行沟通一样。

在访问 [http://www.bing.com/](http://www.bing.com/) 的时候，计算机完成了一系列复杂的 HTTP 网络通信。
Python 可以通过 [urllib.request](https://docs.python.org/3.5/library/urllib.request.html) 模块简单地模拟这个过程。

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
#

import urllib.request

url = 'http://www.bing.com/'
connection = urllib.request.urlopen(url)
content = connection.read()
connection.close()

print(content)
```

其中 ```connection = urllib.request.urlopen(url)``` 通过调用 urllib.request 模块提供的 [urlopen](https://docs.python.org/3.5/library/urllib.request.html#urllib.request.urlopen) 函数，建立了一个 url 的连接对象 connection ；

```content = connection.read()``` 从 connection 中读取内容；

```connection.close()``` 关闭连接 connection ；

最后 ```print(content)``` 将从连接中读取的内容打印出来。

将这一过程封装成一个简单的下载函数：

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
#

import urllib.request

def download(url):
    connection = urllib.request.urlopen(url)
    content = connection.read()
    connection.close()
    return content
```

需要下载的网页内容的时候，将链接地址传递给 download 函数即可。

如：

```
content = download('https://www.douban.com/')
print(content)
```
