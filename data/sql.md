## SQL ##
[SQL](https://en.wikipedia.org/wiki/SQL) 是为关系数据库（ RDBMS ）或者关系数据流（ RDSMS ）设计的结构化查询语言。
主要包括数据定义、管理数据和查询数据，查询数据是 SQL 中最常见的操作。

### 数据定义 ###
SQL 通过数据定义语言（ DDL ）管理表结构和索引。主要包括创建（ CREATE ）、修改（ ALTER ）、重命名（ RENAME ）、移除（ DROP ）和截断（ TRUNCATE ）操作。

创建一个名为 division 的数据表，并指定 id 字段为主键：
```
CREATE TABLE division (
    id INTEGER,
    code INTEGER,
    name VARCHAR(255),
    PRIMARY KEY (id)
);
```

在 division 表中添加一个 created 字段：

```
ALTER TABLE division ADD created INTEGER;
```

将 division 表截断（清空）：
```
TRUNCATE TABLE division;
```

移除 division 表：

```
DROP TABLE division;
```

### 管理数据 ###
SQL 通过数据操作语言（ DML ）管理数据，主要包括插入（ INSERT ）、更新（ UPDATE ）和删除（ DELETE ）。

向 division 表中插入一条数据：

```
INSERT INTO division (code, name, created) VALUES (620702104203, '敬依村委会', 1468492389);
```

将 division 表中 id 为 1 的数据中的 created 字段更新成 1468492504 ：

```
UPDATE division SET created = 1468492504 WHERE id = 1;
```

从 division 表中删除 id 为 1 的一条数据：

```
DELETE FROM division WHERE id = 1;
```

### 查询数据 ###
查询数据是 SQL 中最常见的操作。

查询某地区自 2000 年以来的犯罪事件总数：

```
SELECT
    division.name, COUNT(1)
FROM division
JOIN crime ON (crime.division = division.code)
WHERE division.code > 110000000000 AND division.code < 120000000000
    AND crime.created >= 946656000
GROUP BY division.code;
```
