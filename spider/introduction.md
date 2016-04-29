## 简介 ##
网络爬虫通过下载种子地址中的网页内容，解析里面的链接地址，然后下载对应的内容，再解析，再下载……如此反复爬取互联网上的数据。
这是一个“鸡生蛋，蛋生鸡”的过程，会无限制的爬取下去。
为了避免这样的结果，需要过滤处理解析得到的地址，防止过度爬取。

最后的流程：

```
          +--------+
          | start  |
          +--------+
              |
              v
       +--------------+
       |     url      |
       +--------------+
              | <----------------------------+
              v                              |
       +--------------+                      |
       |   download   |                      |
       +--------------+                      |
              |                              |
              v                              |
         +---------+                         |
         | content |                         |
         +---------+                         |
          |       |                          |
          |       +---------------+          |
          |                       |          |
          v                       v          |
    +---------------------+ +---------------+|
    | extract_interesting | | extract_urls  ||
    +---------------------+ +---------------+|
                                    |        |
                                    v        |
                                +--------+   |
                                | filter |   |
                                +--------+   |
                                    |        |
                                 N  |  Y     |
                  +-----------------+--------+
                  |
                  v
              +------+
              | stop |
              +------+
```

大致的代码逻辑：

```
def crawler(url):
    content = download(url)
    urls = extract_urls(content)
    something = extract_something(content)
    follow_urls = url_filter(urls)
    for url in follow_urls:
        crawler(url)
```

其中 _download_ 函数通过链接地址下载网页内容， _extract_urls_ 从网页内容中解析链接地址， _extract_something_ 从网页中解析感兴趣的内容， _url_filter_ 过滤解析得到的链接地址，控制爬取范围。
实现这些函数就可以实现一个简单的网络爬虫了。

_download_ 函数将涉及 _HTTP_ 网络通信，_extract_urls_ 和 _extract_something_ 涉及简单的 _HTML_ 文本处理，这些都会在接下来的内容中慢慢的讲。
