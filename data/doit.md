## 牛刀小试 ##

1. 为 [区划代码的爬虫](../spider/doit.md) 增加本地文件缓存功能，若链接地址被访问过，直接采用缓存的内容，不再通过 HTTP 获得内容；
2. 将 [区划代码的爬虫](../spider/doit.md) 抓取的数据保存为 csv 文件；
3. 将上一步获得的 csv 文件数据导入 sqlite 数据库；
4. 从 sqlite 数据库中找出区县数目最多的城市。