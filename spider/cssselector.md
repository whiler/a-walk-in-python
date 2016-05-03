## CSS Selector ##
_CSS Selector_ 被成为 _CSS 选择器_ 。
用于快速检索 _HTML_ 中匹配 _CSS Selector_ 的节点。
常见的 _CSS Selector_ 有三种：

- ID 选择器
- 类选择器
- 标签选择器

### ID 选择器 ###
_ID 选择器_ 用于精确检索标签 _ID_ 等于指定值的节点。

例如，可以通过 _ID 选择器_ ```#contents``` 检索出 ```ol#contents``` 这个节点：

```
<article>
    <h3>CONTENTS</h3>
    <ol id="contents" class="catalogue">
        <li class="link bold">Technician</li>
        <li class="link bold">Observer</li>
        <li class="link bold">Cub</li>
        <li class="link bold">Computer</li>
        <li class="link bold">Timer</li>
        <li class="link bold">Life-Plotter</li>
        <li class="link bold">Prelude to Crime</li>
        <li class="link bold active">Crime</li>
        <li class="link bold">Interlude</li>
    </ol>
</article>
```

### 类选择器 ###
_类选择器_ 用于检索标签中带有 _CSS_ 类属性的节点。

例如，可以通过 _类选择器_ ```.bold``` 检索所有 _CSS_ 样式中含有 _bold_ 类的节点。

### 标签选择器 ###
_标签选择器_ 用于检索指定标签的节点。

例如，可以用 _标签选择器_ ```li``` 检索所有的 _li_ 节点。

_CSS 选择器_ 可以分层级检索。

例如： ```#contents .active``` 表示，从 ```#contents``` 检索结果的子节点中检索匹配 ```.active``` 的节点。
最后得到 ```<li class="link bold active">Crime</li>``` 节点。
