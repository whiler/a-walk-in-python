## 错误和异常 ##
人都会犯错，工程师也不例外，工程师编写的程序也会出现异常、错误和 BUG 。
可以预知的异常和错误在 Python 中可以捕获，逻辑实现上的错误无能为力，这是工程师的逻辑问题，不能迁怒编程语言和工具。

在 Python 中，通过 ```try ... except ... else ... finally ...``` 来捕获可以预知的异常和错误。

例如直接执行
```
4 / 0
```
会看到错误信息 _ZeroDivisionError: integer division or modulo by zero_ ，这是一个除零错误，数学计算中，除数不能为零。

为了捕获这个除零错误我们可以这样做：
```
try:
	4 / 0
except ZeroDivisionError:
	print('发现除零错误')
except:
	print('发现其他未知错误')
else:
	print('一切正常，什么错误都没有发生')
finally:
	print('代码执行结束')
```

其中 _try_ 和 _except_ 将需要捕获异常的代码段包裹起来，通过多个 _except_ 依次捕获可能的异常和错误，捕获到错误后执行对应的代码段，最后，不论是否捕获到异常都执行 _finally_ 中的代码。

```try:``` 表示捕获接下来的代码中的错误；

```4 / 0``` 是一段会引起错误的代码；

```except ZeroDivisionError:``` 表示仅仅捕获除零错误 (ZeroDivisionError)；

```except:``` 表示捕获所有的错误；

```else:``` 表示没有错误时执行的代码段；

```finally:``` 表示，无论是发生错误，都要执行的代码段。
