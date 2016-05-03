## HTML 文本处理 ##
我们通过浏览器看到的网页内容，基本都是 _HTML_ 文档。
_HTML_ 文档是普通的文本文档，文件内容就是 _HTML_ 源代码。
为了方便计算机处理， _HTML_ 文档有固定的结构。
_HTML_ 文档中内容繁多，我们要做的是从 _HTML_ 中找到链接地址。

### 从 _HTML_ 中找到链接地址 ###
在 _HTML_ 中，链接有特殊的表示方法。

如 _[豆瓣](https://www.douban.com/)_ ，它的 _HTML_ 源代码是

```
<a href="https://www.douban.com/">豆瓣</a>
```

前后闭合的 _a_ 标签在 _HTML_ 中表示一个链接，如： ```<a>豆瓣</a>``` 。
一个有效的链接必须有一个链接地址，链接地址保存在 _a_ 标签的 _href_ 属性中。如例子中的 _https://www.douban.com/_ 。

了解 _HTML_ 中的链接地址的保存方式后，从 _HTML_ 中找到链接地址的过程就简化为：

1. 解析 _HTML_ 源文件；
2. 找所有的 _a_ 标签；
3. 从 _a_ 标签中得到 _href_ 属性。

解析 _HTML_ 源文件，可以通过第三方 _lxml_ 包的 _html_ 模块完成。
_html_ 模块的 _fromstring_ 函数可以将 _HTML_ 解析成一个节点树。
每一对闭合的标签构成一个节点，各个节点按照 _HTML_ 源码中的层级关系组成一棵节点树。
通过 _html_ 模块构建的节点对象有一个 _cssselect_ 方法，可以通过 _CSS Selector_ 搜索满足条件的所有子节点。

安装 _lxml_ 第三方包：

```
pip install lxml
```

网页内容中解析链接地址：

```
from lxml import html

def extract_urls(content):
    urls = list()
    selector = 'a'
    root = html.fromstring(content)
    nodes = root.cssselect(selector)
    for node in nodes:
        url = node.attrib.get('href')
        if url:
            urls.append(url)
    return urls
```

```urls = list()``` 初始化一个空的列表，用于保存找到的链接地址；

```selector = 'a'``` _CSS Selector_ 是 ```a``` ；

```root = html.fromstring(content)``` 用 _html_ 模块的 _fromstring_ 函数，解析 _HTML_ 源码，找到 _HTML_ 根节点；

```nodes = root.cssselect(selector)``` 用根节点的 _cssselect_ 方法，找到所有的 _a_ 标签节点；

```url = node.attrib.get('href')``` 从节点的属性中获得 _href_ 属性值；

调用示例：

```
content = '<a href="https://www.douban.com/">豆瓣</a>'
urls = extract_urls(content)
for url in urls:
    print(url)
```

通过类似的方法，可以从 _HTML_ 中抽取其他感兴趣的内容，比如：电影排期、房屋售价、演出时间……
