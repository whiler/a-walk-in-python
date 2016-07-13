## 文件 ##
`XXX.doc` 、 `XXX.jpg` 、 `XXX.txt` 、 `XXX.exe` 这些是都是文件。
文件的本质是数据保存到存储介质的产物。
Python 提供了 [open](https://docs.python.org/3.5/library/functions.html#open) 函数用于打开文件。

### 文本文件 ###
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

fp = open('love.txt', 'w')
for line in poem:
	fp.write(line)
	fp.write('\n')
fp.close()

fp = open('love.txt', 'r')
content = fp.read()
fp.close()
print(content)
```

**换行符** '\n' 是换行符，也是一个字符，显示文本内容时换行。
