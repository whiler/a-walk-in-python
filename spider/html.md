## HTML 文本处理 ##
通过网页浏览器看到的网页内容，基本都是 HTML 文档。
HTML 文档是普通的文本文档，内容就是 HTML 源代码。
为了方便计算机处理， HTML 文档有固定的结构。
HTML 文档中内容繁多，我们要做的是从 HTML 中找到链接地址。

### 从 HTML 中找到链接地址 ###
在 HTML 中，链接有特殊的表示方法。

如 [豆瓣](https://www.douban.com/) ，它的 HTML 源代码是

```
<a href="https://www.douban.com/">豆瓣</a>
```

前后闭合的 a 标签在 HTML 中表示一个链接，如： ```<a>豆瓣</a>``` 。
一个有效的链接必须有一个链接地址，链接地址保存在 a 标签的 href 属性中。
如例子中的 _https://www.douban.com/_ 。

了解 HTML 中的链接地址的保存方式后，从 HTML 中找到链接地址的过程就简化为：

1. 解析 HTML 源文件；
2. 找所有的 a 标签；
3. 从 a 标签中得到 href 属性。

解析 HTML 源文件，可以通过第三方 lxml 包的 html 模块完成。
html 模块的 fromstring 函数可以将 HTML 解析成一个节点树。
每一对闭合的标签构成一个节点，各个节点按照 HTML 源码中的层级关系组成一棵节点树。
通过 html 模块构建的节点对象有 cssselect 方法，可以通过 CSS Selector 搜索满足条件的所有子节点。

```
<html>
    <head>
        <title>Demo</title>
    </head>
    <body>
        <article>
            <section></section>
            <section>
                <p></p>
                <p></p>
                <p>
                    <a href="https://www.google.com/">google</a>
                </p>
                <p>
                    <a href="https://www.douban.com/">douban</a>
                </p>
            </section>
            <section></section>
        </article>
    </body>
</html>
```

```
               +------+
               | html |
               +------+
                   |
            +------+--+
            |         |
        +------+  +------+
        | head |  | body |
        +------+  +------+
           |          |
       +-------+  +---------+
       | title |  | article |
       +-------+  +---------+
                      |
         +------------+------------+
         |            |            |
    +---------+  +---------+  +---------+
    | section |  | section |  | section |
    +---------+  +---------+  +---------+
                      |
          +------+----+-+------+
          |      |      |      |
        +---+  +---+  +---+  +---+
        | p |  | p |  | p |  | p |
        +---+  +---+  +---+  +---+
                        |      |
                      +---+  +---+
                      | a |  | a |
                      +---+  +---+
```

安装 lxml 第三方包：

```
pip install lxml
```

网页内容中解析链接地址：

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
#

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

```selector = 'a'``` CSS Selector 是 ```a``` ；

```root = html.fromstring(content)``` 用 html 模块的 fromstring 函数，解析 HTML 源码，找到 HTML 根节点；

```nodes = root.cssselect(selector)``` 用根节点的 cssselect 方法，找到所有的 a 标签节点；

```url = node.attrib.get('href')``` 从节点的属性中获得 href 属性值；

调用示例：

```
content = '<a href="https://www.douban.com/">豆瓣</a>'
urls = extract_urls(content)
for url in urls:
    print(url)
```

通过类似的方法，可以从 HTML 中抽取其他感兴趣的内容，比如：电影排期、房屋售价、演出时间……
