# HTML

---


# 语法

- 缩进使用soft tab（4个空格）；
- 嵌套的节点应该缩进；
- 在属性上，使用双引号，不要使用单引号；
- 属性名全小写，用中划线做分隔符；
- 不要在自动闭合标签结尾处使用斜线（HTML5 规范 指出他们是可选的）；
- 不要忽略可选的关闭标签，例：&lt;li\&gt; 和 &lt;body\&gt;。

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Page title</title>
    </head>
    <body>
        <img src="images/company_logo.png" alt="Company">

        <h1 class="hello-world">Hello, world!</h1>
    </body>
</html>
```

# HTML5 doctype

在页面开头使用这个简单地doctype来启用标准模式，使其在每个浏览器中尽可能一致的展现；

虽然doctype不区分大小写，但是按照惯例，doctype大写 [（关于html属性，大写还是小写）](https://stackoverflow.com/questions/15594877/is-there-any-benefits-to-use-uppercase-or-lowercase-letters-with-html5-tagname)。

```html
<!DOCTYPE html>
<html>
	...
</html>
```

# lang属性

根据HTML5规范：

*应在html标签上加上lang属性。这会给语音工具和翻译工具帮助，告诉它们应当怎么去发音和翻译。*

更多关于 `lang` 属性的说明在[这里](http://w3c.github.io/html/semantics.html#the-html-element)；

在sitepoint上可以查到[语言列表](https://www.sitepoint.com/iso-2-letter-language-codes/)；

但sitepoint只是给出了语言的大类，例如中文只给出了zh，但是没有区分香港，台湾，大陆。而微软给出了一份更加详细的语言列表，其中细分了zh-cn, zh-hk, zh-tw。

```html
<!DOCTYPE html>
<html lang="en-us">
    ...
</html>
```

# 字符编码

通过声明一个明确的字符编码，让浏览器轻松、快速的确定适合网页内容的渲染方式，通常指定为'`UTF-8`'。


```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
    </head>
    ...
</html>
```

# IE兼容模式

用 `&lt;meta&gt;` 标签可以指定页面应该用什么版本的IE来渲染；

如果你想要了解更多，请点击 [这里](http://stackoverflow.com/questions/6771258/whats-the-difference-if-meta-http-equiv-x-ua-compatible-content-ie-edge-e)

不同doctype在不同浏览器下会触发不同的渲染模式 ([这篇文章](https://hsivonen.fi/doctype/) 总结的很到位。)

``` html
<!DOCTYPE html>
<html>
    <head>
        <meta http-equiv="X-UA-Compatible" content="IE=Edge">
    </head>
    ...
</html>
```

# 引入CSS, JS

根据HTML5规范, 通常在引入CSS和JS时不需要指明 `type` `text/css` `text/javascript` 分别是他们的默认值。

HTML5 规范链接

[使用link](http://www.w3.org/TR/2011/WD-html5-20110525/semantics.html#the-link-element)
[使用style](http://www.w3.org/TR/2011/WD-html5-20110525/semantics.html#the-style-element)
[使用script](http://www.w3.org/TR/2011/WD-html5-20110525/scripting-1.html#the-script-element)


```html
<!-- External CSS -->
<link rel="stylesheet" href="code_guide.css">

<!-- In-document CSS -->
<style>
    ...
</style>
<!-- External JS -->
<script src="code_guide.js"></script>
<!-- In-document JS -->
<script>
    ...
</script>
```


# 属性顺序

属性应该按照特定的顺序出现以保证易读性；

`class`

`id`

`name`

`data-*`

`src` `for` `type` `href` `value` `max-length` `max` `min`  `pattern`

`placeholder` `title` `alt`

`aria-*` `role`

`required` `readonly` `disabled`

class是为高可复用组件设计的，所以应处在第一位；

id更加具体且应该尽量少使用，所以将它放在第二位。

``` html
<a class="..." id="..." data-modal="toggle" href="#">Example link</a>

<input class="form-control" type="text">

<img src="..." alt="...">
```

# 减少标签数量

在编写HTML代码时，需要尽量避免多余的父节点；

很多时候，需要通过迭代和重构来使HTML变得更少。

```html
<span class="avatar">
    <img src="...">
</span>

<!-- Better -->
<img class="avatar" src="...">

```


# 实用高于完美

尽量遵循HTML标准和语义，但是不应该以浪费实用性作为代价；

任何时候都要用尽量小的复杂度和尽量少的标签来解决问题。