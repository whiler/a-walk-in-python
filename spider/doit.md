## 小试牛刀 ##

从[中华人民共和国国家统计局](http://www.stats.gov.cn/)抓取区划代码。

这是一个抓取全中国每一个村、社区以上行政区域区划代码的爬虫。
总共抓取 43,348 个网页，会执行很长时间。

可以尝试修改部分代码，看看执行的结果。

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
#
# file: doit.py
# author: whiler
# license: BSD

# 引入 http.cookiejar 模块，提供 Cookie 支持
import http.cookiejar

# 引入模块 logging 模块，记录运行日志
import logging

# 引入 socket 模块，用于捕获 HTTP 超时错误
import socket

# 引入 urllib.request 模块，处理 HTTP 连接，创建 HTTP 请求
import urllib.request

# 引入 urllib.error ，用于捕获 HTTPError 错误
import urllib.error

# 引入 urllib.parse 模块，处理链接地址
import urllib.parse

# 引入 lxml.html 第三方包，解析 HTML
import lxml.html

# 配置基本的日志记录格式
logging.basicConfig(level=logging.NOTSET,
                    format='[%(levelname)s]\t%(asctime)s\t%(message)s',
                    datefmt='%Y-%m-%d %H:%M:%S %Z')


class Spider(object):
    """
        定义一个 Spider 类，实现简单的网络爬虫
    """

    def __init__(self, seeds):
        """
            :seeds: 接受一个种子地址列表完成初始化
        """
        self.seeds = seeds

        # 伪装成一个正常的浏览器，需要的请求头信息
        self.headers = {
            # 伪装成 Firefox 浏览器
            'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10.11; rv:46.0) Gecko/20100101 Firefox/46.0',

            # 假装通过 http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2014/index.html 访问到这些被抓取的网页
            'Referer': 'http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2014/index.html'
        }

        # 使用一个集合来记录已经访问过的链接地址
        self.visited = set()

        # 支持 Cookie
        self.cookie = http.cookiejar.CookieJar()
        self.processor = urllib.request.HTTPCookieProcessor(self.cookie)
        self.opener = urllib.request.build_opener(self.processor)

    def download(self, url):
        """
            下载一个链接地址的内容
            :url: 链接地址
        """
        # 记录正在下载的地址
        logging.debug('downloading ' + url)

        # 构建一个 HTTP 请求
        request = urllib.request.Request(url, headers=self.headers)

        # 默认读取到的内容为空
        raw = ''

        # 开始捕获异常
        try:
            # 创建一个 HTTP 连接，并设置 10 秒超时
            connection = self.opener.open(request, timeout=10.0)

            # 从连接读取内容
            raw = connection.read()
        except urllib.error.HTTPError:
            # 若发生 HTTPError 错误，记下连接地址
            msg = 'download [' + url + '] raised urllib2.HTTPError, skiped'
            logging.exception(msg)
        except socket.timeout:
            # 若发生超时异常，记下连接地址
            msg = 'download [' + url + '] raised socket.timeout, skiped'
            logging.exception(msg)
        except Exception:
            # 若发生其他异常错误，记下连接地址
            msg = 'download [' + url + '] failed, skiped'
            logging.exception(msg)
        else:
            # 没有发生异常错误，关闭连接
            connection.close()

        # 将读取到的内容按照 GB18030 字符集编码方式进行解码
        content = raw.decode('gb18030')

        return content

    def extract_urls(self, url, content):
        """
            从内容中抽取链接地址
            :url: 内容的来源地址
            :content: 内容
        """
        # 使用一个列表来保存链接地址
        urls = list()

        # 在 HTML 文件中，链接的 CSS 选择器是 a
        selector = 'a'

        # 使用 lxml.html.fromstring 解析 HTML 内容，构建节点树
        root = lxml.html.fromstring(content)

        # 遍历节点树中的每一个链接节点
        for node in root.cssselect(selector):

            # 获得链接节点的 href 属性值
            relative = node.attrib.get('href', '')
            if relative:
                # 使用 urllib.parse 的 urljoin 函数，将相对地址转换为实际地址
                real = urllib.parse.urljoin(url, relative)

                # 将实际的地址添加到地址列表中
                urls.append(real)
        return urls

    def extract_something(self, url, content):
        """
            从内容中抽取感兴趣的信息
            :url: 内容的来源地址
            :content: 内容
        """
        # 使用 lxml.html.fromstring 解析 HTML 内容，构建节点树
        root = lxml.html.fromstring(content)

        # 使用字典来保存每一个地区名称和区划代码
        locations = dict()

        # 使用 http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2014/ 的长度作为计算当前链接地址相对地址的偏移量
        offset = len('http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2014/')

        # 截取当前链接地址偏移量以后的字符串作为相对地址
        relative = url[offset:]

        # 相对地址中 / 的数目为行政层级
        depth = relative.count('/')

        if 'index.html' == relative:
            # 省、自治区、直辖市和特别行政区
            # 表格中链接的文字就是区域的名称，链接地址中的数字就是区划代码

            # 表格的单元格中的链接的 CSS 选择器
            selector = '.provincetr td a'

            # 遍历每一个链接节点
            for node in root.cssselect(selector):
                # 获得链接节点的链接地址，这是一个相对地址
                href = node.attrib.get('href', '')

                # 在链接地址中找到 . 的偏移量
                offset = href.find('.')

                # 截取链接地址中 . 以前的字符串作为区划代码
                code = href[:offset]

                # 追加 0 ，补齐12位
                code = code.ljust(12, '0')

                # 链接的文字内容就是区域名称
                name = node.text_content()

                # 将区划代码和名称关联起来
                locations[code] = name

        elif depth < 4:
            # 市、区县、乡镇、村社区
            # 每一行第一个单元格的内容是区划代码，最后一个单元格的内容是区域名称

            if 0 == depth:
                # 第一层级是市
                selector = '.citytr'
            elif 1 == depth:
                # 第二层级是区县
                selector = '.countytr'
            elif 2 == depth:
                # 第三层级是乡镇
                selector = '.towntr'
            else:
                # 第四层级是村、社区
                selector = '.villagetr'

            # 遍历每一个节点，逐行处理表格中的每一行
            for node in root.cssselect(selector):
                # 获得这一行的所有单元格
                cells = node.cssselect('td')

                # 第一个单元格的内容是区划代码
                code = cells[0].text_content()

                # 最后一个单元格的内容是名称
                name = cells[-1].text_content()

                if code.isdigit():
                    # 全是是数字的才是合法的区划代码
                    locations[code] = name
        else:
            # 行政村村民小组和社区居民小组没有区划代码
            logging.warn(url)

        return locations

    def dump(self, locations):
        """
            保存抓取得到的数据
            :locations: 从每一个网页抓取得到的区域字典
        """
        # 遍历区域字典中每一对关联的区划代码和名称
        for code, name in list(locations.items()):
            msg = '[' + code + ']' + name

            # 仅仅记录日志，并没有保存起来
            logging.info(msg)
        return 0

    def filter(self, urls):
        """
            过滤链接地址
            :urls: 链接地址列表
        """
        # 使用列表保存允许抓取的链接地址
        allowed = list()

        # 遍历地址列表中的每一个地址
        for url in urls:
            if url in self.visited:
                # 已经访问过的地址，不允许再抓取
                continue
            elif not url.startswith('http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2014/'):
                # 不抓取不是以 http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2014/ 开始的链接地址
                continue
            else:
                # 将以 http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2014/ 开始，又没有访问过的地址，添加到允许访问的列表中
                allowed.append(url)
        return allowed

    def work(self):
        """
            开始干活
        """
        # 遍历种子地址中的每一个地址
        for url in self.seeds:
            # 抓取一个地址
            self.crawl(url)
        return 0

    def crawl(self, url):
        """
            抓取一个地址
            :url: 链接地址
        """
        # 下载链接地址对应的内容
        content = self.download(url)
        if not content:
            # 没有内容，退出抓取
            return

        # 将链接地址添加到访问过的地址集合中
        self.visited.add(url)

        # 从内容中抽取感兴趣的内容
        data = self.extract_something(url, content)

        # 保存抓取得到的数据
        self.dump(data)

        # 从内容中抽取链接地址
        urls = self.extract_urls(url, content)

        # 过滤抽取得到的链接地址
        allowed = self.filter(urls)

        # 遍历这些地址
        for url in allowed:
            # 抓取一个地址
            self.crawl(url)


logging.info('begin')

# 种子地址列表
seeds = ['http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2014/index.html']

# 创建一个 Spider 对象
spider = Spider(seeds)

# 调用 spider 的 work 方法，开始抓取
spider.work()

logging.info('finish')
```

[源代码下载](doit.py)
