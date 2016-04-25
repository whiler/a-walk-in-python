## WEB ##
在访问 [http://www.bing.com/](http://www.bing.com/) 的时候，计算机完成了一系列复杂的网络通信。
Python 可以通过 _urllib2_ 模块简单地模拟这个过程。

```
import urllib2

url = 'http://www.bing.com/'
connection = urllib2.urlopen(url)
content = connection.read()
connection.close()

print(content)
```

其中 ```connection = urllib2.urlopen(url)``` 通过调用 _urllib2_ 模块提供的 _urlopen_ 函数，建立了一个与 _url_ 的连接 _connection_ ；

```content = connection.read()``` 从 _connection_ 中读取内容；

```connection.close()``` 关闭连接 _connection_ ；

最后 ```print(content)``` 将从连接中读取的内容打印出来。

将这一过程封装成一个简单的下载函数：

```
import urllib2

def download(url)
    connection = urllib2.urlopen(url)
    content = connection.read()
    connection.close()
    return content
```

需要下载的网页内容的时候，将链接地址传递给 _download_ 函数即可。

如：

```
content = download('https://www.douban.com/')
```
