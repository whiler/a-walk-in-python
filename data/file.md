## 文件 ##
_XXX.doc_ 、 _XXX.jpg_ 、 _XXX.txt_ 、 _XXX.exe_ 这些是都是文件。
文件的本质是数据保存到存储介质的产物。
Python 提供了 [open](https://docs.python.org/3.5/library/functions.html#open) 函数用于打开文件。
open 函数打开一个文件，返回一个文件对象，文件对象提供基本的 read 、 write 、 close 方法来操作文件。

- read ，从文件中读取内容
- write ，将数据写入文件
- close ，关闭文件


### 文本文件 ###
默认情况下， open 函数将文件视为普通文本文件以只读方式打开。
文本文件的特点是文件内容全是字符，字符的顺序和数据的顺序一一对应。

```
poem = [
    "Love",
    "by Roy Croft",
    "",
    "I love you",
    "Not only for what you are,",
    "But for what I am",
    "When I am with you.",
    "",
    "I love you,",
    "Not only for what",
    "You have made of yourself,",
    "But for what",
    "You are making of me.",
    "",
    "I love you",
    "For the part of me",
    "That you bring out;",
    "",
    "I love you",
    "For putting your hand",
    "Into my heaped-up heart",
    "And passing over",
    "All the foolish, weak things",
    "That you can't help",
    "Dimly seeing there,",
    "",
    "And for drawing out",
    "Into the light",
    "All the beautiful belongings",
    "That no one else had looked",
    "Quite far enough to find",
    "",
    "I love you because you",
    "Are helping me to make",
    "Of the lumber of my life",
    "Not a tavern",
    "But a temple.",
    "",
    "Out of the works",
    "Of my every day",
    "Not a reproach",
    "But a song.",
    "",
    "I love you",
    "Because you have done",
    "More than any creed",
    "Could have done",
    "To make me good.",
    "And more than any fate",
    "Could have done",
    "To make me happy.",
    "",
    "You have done it",
    "Without a touch,",
    "Without a word,",
    "Without a sign.",
    "",
    "You have done it",
    "By being yourself.",
    "Perhaps that is what",
    "Being a friend means,",
    "After all."
]

# 打开一个文本文件 poem.txt 。
# 如果文件不存在，则新建一个空白文件。
# 如果文件已经存在，则将文件清空成一个空白文件。
fp = open('poem.txt', 'w')

for line in poem:
    fp.write(line)  # 将每一段诗句写入文件
    fp.write('\n')  # 写入换行符
fp.close()  # 关闭文件

fp = open('poem.txt', 'r')  # 打开一个文本文件 poem.txt 。
content = fp.read()  # 读取全部文件内容
fp.close()
print(content)

fp = open('poem.txt', 'r')  # 打开一个文本文件 poem.txt 。
for line in fp:  # 逐行读取文件内容，得到每一行诗句
    print(line)
fp.close()
```

**换行符** '\n' 是换行符，也是一个字符，显示文本内容时换行。
