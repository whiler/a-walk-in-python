## 文本处理 ##
通过对字符串进行匹配、拼接、替换、拆分等简单的操作完成文本处理。
文本处理可以完成分词、语义分析、翻译等复杂而且有意思的工作。
但是，我们要做的是： **从网页源文件中找到链接地址** 。

### 从网页源文件中找到链接地址 ###
网页源文件是普通的文本文件，文件内容是 _HTML_ 源代码。
在 _HTML_ 中，链接有特殊的表示方法。

如 _[豆瓣](https://www.douban.com/)_ ，它的 _HTML_ 源代码是

```
<a href="https://www.douban.com/">豆瓣</a>
```

前后闭合的 _a_ 标签在 _HTML_ 中表示一个链接，如： ```<a>豆瓣</a>``` 。
一个有效的链接必须有一个有效的链接地址，链接地址保存在 _a_ 标签的 _href_ 属性中。如例子中的 _https://www.douban.com/_ 。

了解网页源文件中的链接地址的保存方式后，从网页源文件中找到链接地址的过程就简化为：

1. 解析 _HTML_ 源文件；
2. 找所有的 _a_ 标签；
3. 从 _a_ 标签中得到 _href_ 属性。

解析 _HTML_ 源文件，可以通过 _html.parser_ 模块提供的 _HTMLParser_ 类完成。
因为只需要知道 _a_ 标签的 _href_ 属性，所以定义的解析类，继承 _HTMLParser_ 后，仅仅实现 _handle_starttag_ 方法即可。

```
from html.parser import HTMLParser

class URLParser(HTMLParser):
    def __init__(self):
        super(URLParser, self).__init__()
        self.urls = list()

    def reset(self):
        super(URLParser, self).reset()
        del self.urls[:]

    def handle_starttag(self, tag, attrs):
        if tag == 'a':
            url = attrs['href']
            if url:
                self.urls.append(url)
```

调用示例：

```
content = '<a href="https://www.douban.com/">豆瓣</a>'
parser = URLParser()
parser.reset()
parser.feed(content)
for url in parser.urls:
    print(url)
```

通过类似的方法，可以从网页源文件中抽取其他感兴趣的内容，比如：电影排期、房屋售价、演出时间……
