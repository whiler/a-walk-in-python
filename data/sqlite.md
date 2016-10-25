## SQLite ##
[SQLite](https://www.sqlite.org/) 是遵守 [ACID](https://en.wikipedia.org/wiki/ACID) 的关系数据库管理系统，实现了大多数 [SQL](https://en.wikipedia.org/wiki/SQL) 标准。
将数据导入 SQLite 后，使用 SQL 处理数据极其方便。

Python 提供了 [sqlite3](https://docs.python.org/3.5/library/sqlite3.html) 模块操作 SQLite 数据库。

### SQLite 建表 ###

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
#

import sqlite3

conn = sqlite3.connect('demo.db')  # 创建连接
cur = conn.cursor()  # 获得连接游标
# 建表 SQL 语句
sql = """
CREATE TABLE division (
    code int,
    name text
)
"""
cur.execute(sql)  # 执行 SQL 语句
conn.commit()  # 提交，对数据的改动会写入数据文件
conn.close()  # 关闭连接
```

### 数据导入 SQLite ###

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
#

import sqlite3

rows = [
    (620702104001, '平原堡社区居委会'),  # 一行数据，根据表结构以及 SQL 语句确定每一列的数据类型
    (620702104200, '谢家湾村委会'),
    (620702104201, '元丰村委会'),
    (620702104202, '贾家寨村委会'),
    (620702104203, '敬依村委会'),
    (620702104204, '乌江村委会'),
    (620702104205, '管寨村委会'),
    (620702104206, '东湖村委会'),
    (620702104207, '平原村委会'),
    (620702104208, '安镇村委会'),
    (620702104209, '天乐村委会'),
    (620702104210, '大湾村委会'),
    (620702104211, '小湾村委会'),
    (620702104212, '永丰村委会')
]

conn = sqlite3.connect('demo.db')
cur = conn.cursor()
sql = 'INSERT INTO division (code, name) VALUES (?, ?)'
for row in rows:
    cur.execute(sql, row)  # 逐行插入数据
conn.commit()
conn.close()
```

### 从 SQLite 中读取数据 ###

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
#

import sqlite3

conn = sqlite3.connect('demo.db')
cur = conn.cursor()
sql = 'SELECT code, name FROM division'
cur.execute(sql)
for row in cur:  # 遍历查询结果
    print(row)
conn.close()
```
