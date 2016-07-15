## CSS Selector ##
CSS Selector 被称为 CSS 选择器。
用于快速检索 HTML 中匹配 CSS Selector 的节点。
常见的 CSS Selector 有三种：

- ID 选择器
- 类选择器
- 标签选择器

### ID 选择器 ###
ID 选择器用于精确检索标签 ID 等于指定值的节点。
用 # 和 ID 值拼接表示。

例如，可以通过 ID 选择器 ```#contents``` 检索出 ```<ol id="contents" class="catalogue">...</ol>``` 这个节点：

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
类选择器用于检索标签中带有 CSS 类属性的节点。
用 . 和类名拼接表示。

一个节点可以有多个 CSS 样式类。

例如，可以通过 类选择器 ```.bold``` 检索所有 CSS 样式中含有 bold 类的节点。

### 标签选择器 ###
标签选择器用于检索指定标签的节点。
直接使用标签名表示。

例如，可以用 标签选择器 ```li``` 检索所有的 li 节点。

CSS 选择器可以分层级检索。

例如： ```#contents .active``` 表示，从 ```#contents``` 检索结果的子节点中检索匹配 ```.active``` 的节点。
最后得到 ```<li class="link bold active">Crime</li>``` 节点。
