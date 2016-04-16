## 错误和异常 ##
> 人非圣贤，孰能无过！过而能改，善莫大焉。

人都会犯错，工程师也不例外，工程师编写的程序也会出现异常、错误和 BUG 。
可以预知的异常和错误在 Python 中可以捕获，逻辑实现上的错误无能为力，这是工程师的逻辑问题，不能迁怒编程语言和工具。

在 Python 中，通过 ```try ... except ... else ... finally ...``` 来捕获可以预知的异常和错误。例如：
```
try:
    4 / 0
except ZeroDivisionError:
    print('ZeroDivisionError')
except:
    print('OtherError')
else:
    print('OK')
finally:
    print('finish')
```

其中 try 和 except 将需要捕获异常的代码段包裹起来，通过多个 except 依次捕获可能的异常和错误，捕获到错误后执行对应的代码段，最后，不论是否捕获到异常都执行 finally 中的代码。
