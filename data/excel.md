## Excel 文件 ##
Microsoft Excel 是微软（ Microsoft ）办公套件（ Office ）中处理电子表格的办公软件，生成的数据文件是 Excel 文件。

Python 没有自带处理 Excel 文件的模块，需要安装第三方包 [openpyxl](https://bitbucket.org/openpyxl/openpyxl) 来处理 Excel 文件。

### 数据写入 Excel ###

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
#

from openpyxl import Workbook

title = '乌江镇'
header = ['代码', '城乡分类', '名称']  # 表头
rows = [
    [620702104001, 220, '平原堡社区居委会'],  # 一行数据，每一个单元格的数据可以是字符串或者数值
    [620702104200, 112, '谢家湾村委会'],
    [620702104201, 220, '元丰村委会'],
    [620702104202, 220, '贾家寨村委会'],
    [620702104203, 220, '敬依村委会'],
    [620702104204, 121, '乌江村委会'],
    [620702104205, 220, '管寨村委会'],
    [620702104206, 220, '东湖村委会'],
    [620702104207, 220, '平原村委会'],
    [620702104208, 220, '安镇村委会'],
    [620702104209, 220, '天乐村委会'],
    [620702104210, 220, '大湾村委会'],
    [620702104211, 220, '小湾村委会'],
    [620702104212, 220, '永丰村委会']
]

wb = Workbook()  # 新建一个空白的 Workbook

ws = wb.active  # 获得当前活跃的表格（ WorkSheet ）

ws.title = title  # 设置表格的标题
ws.append(header)  # 添加表头
for row in rows:
    ws.append(row)  # 添加每一行数据

wb.save('demo.xlsx')  # 保存为 demo.xlsx
```

### 读取 Excel ###

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
#

from openpyxl import load_workbook

wb = load_workbook('demo.xlsx')  # 从文件中加载 Workbook
ws = wb.get_sheet_by_name('乌江镇')  # 根据表格标题获得一个表格

for row in ws.rows:  # 遍历表格中的每一行
    for cell in row:  # 遍历一行中的每一个单元格
        print(cell.value)  # 单元格的内容

for row in ws['A1':'C15']:  # 遍历从 A1 到 C15 区域中的每一行
    for cell in row:
        print(cell.value)
```
