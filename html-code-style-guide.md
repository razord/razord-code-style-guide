# HTML 代码规范

## 黄金法则

始终同意并遵循规范的每一条内容

> 不管有多少参与者，代码都应该像同一个人所写。 

## 语法

 - 使用 **4个空格** 的 `soft tabs` — 这是保证代码在各种环境下显示一致的唯一方式。
 - 嵌套的节点应该缩进（两个空格）。
 - 在属性上，使用双引号，不要使用单引号。
 - 不好在自动闭合标签结尾处使用斜线 - [HTML5](http://dev.w3.org/html5/spec-author-view/syntax.html#syntax-start-tag) 规范 指出他们是可选的。
 - 不要忽略可选的关闭标签（例如，`</li>` 和 `</body>`）。
 
#### Example

```HTML
<!DOCTYPE html>
<html>
    <head>
        <title>Page title</title>
    </head>
    <body>
        <img src="images/company-logo.png" alt="Company">
        <h1 class="hello-world">Hello, world!</h1>
    </body>
</html>
```
 
## HTML5 DOCTYPE

在每个 HTML 页面开头使用这个简单地 doctype 来启用标准模式，使其每个浏览器中尽可能一致的展现。

#### Example

```HTML
<!DOCTYPE html>
<html>
    <head>
    </head>
</html>
```

## Language 属性

根据 HTML5 规范：

> 鼓励网站作者在 html 元素上指定 lang 属性，来指出页面的语言。这样做有助于语言合成工具来确定发音方式，以及帮助翻译工具决定使用的规则，等等。

通过[规范](http://www.w3.org/html/wg/drafts/html/master/semantics.html#the-html-element)中的 `lang` 属性了解更多相关内容。

前往 Sitepoint 查看 [language codes](http://reference.sitepoint.com/html/lang-codes) 列表。

#### Example

```HTML
<html lang="en-us">
    <!-- ... -->
</html>

<html lang="zh-cmn-Hans">
    <!-- ... -->
</html>
```

## 字符编码

通过声明一个明确的字符编码，让浏览器轻松、快速的确定适合网页内容的渲染方式。这样做之后，需要避免在 HTML 中出现字符实体，直接提供字符与文档一致的编码（通常是 UTF-8）。

#### Example

```HTML
<head>
    <meta charset="UTF-8">
</head>
```

## IE 兼容模式

Internet Explorer 支持使用兼容性 `<meta>` 标签来指定使用什么版本的 IE 来渲染页面。如果不是特殊需要，通常通过 **edge mode** 来通知 IE 使用最新的兼容模式。

For more information, [read this awesome Stack Overflow article](http://stackoverflow.com/questions/6771258/what-does-meta-http-equiv-x-ua-compatible-content-ie-edge-do).

#### Example

```HTML
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```

## 引入 CSS 和 JavaScript

根据 HTML5 规范, 通常在引入 CSS 和 JavaScript 时不需要指明 `type`，因为 `text/css` 和 `text/javascript` 分别是他们的默认值。

HTML5 规范链接:

 - [使用 link](http://www.w3.org/TR/2011/WD-html5-20110525/semantics.html#the-link-element)
 - [使用 style](http://www.w3.org/TR/2011/WD-html5-20110525/semantics.html#the-style-element)
 - [使用 script](http://www.w3.org/TR/2011/WD-html5-20110525/scripting-1.html#the-script-element)

#### Example

```HTML
<!-- External CSS -->
<link rel="stylesheet" href="code-guide.css">

<!-- In-document CSS -->
<style>
    /* ... */
</style>

<!-- JavaScript -->
<script src="code-guide.js"></script>
```

## 实用高于完美

尽量遵循 HTML 标准和语义，但是不应该以浪费实用性作为代价。任何时候都要用尽量小的复杂度和尽量少的标签来解决问题。

## 属性顺序

HTML 属性应该按照特定的顺序出现以保证易读性。

 - `class`
 - `id`, `name`
 - `data-*`
 - `src`, `for`, `type`, `href`, `value`
 - `title`, `alt`
 - `role`, `aria-*`

Classes 是为高可复用组件设计的，所以他们处在第一位。Ids 更加具体而且应该尽量少使用（例如, 页内书签），所以他们处在第二位。

#### Example

```HTML
<a class="..." id="..." data-toggle="modal" href="#">
    Example link
</a>

<input class="form-control" type="text">

<img src="..." alt="...">
```

## Boolean 属性

Boolean 属性指不需要声明取值的属性。XHTML 需要每个属性声明取值，但是 HTML5 并不需要。

了解更多内容，参考 [WhatWG section on boolean attributes](http://www.whatwg.org/specs/web-apps/current-work/multipage/common-microsyntaxes.html#boolean-attributes):

> 一个元素中 Boolean 属性的存在表示取值 true，不存在则表示取值 false。

如果你必须为属性添加并不需要的取值，参照 WhatWG 的指引:

> 如果属性存在，他的取值必须是空字符串或者 [...] 属性的规范名称，不要在首尾包含空白字符。

**简而言之，不要为 Boolean 属性添加取值。**

#### Example

```HTML
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
    <option value="1" selected>1</option>
</select>
```

## 减少标签数量

在编写 HTML 代码时，需要尽量避免多余的父节点。很多时候，需要通过迭代和重构来使 HTML 变得更少。 参考下面的示例:

#### Example

```HTML
<!-- Not so great -->
<span class="avatar">
    <img src="...">
</span>

<!-- Better -->
<img class="avatar" src="...">
```

## JavaScript 生成标签

在 JavaScript 文件中生成标签让内容变得更难查找，更难编辑，性能更差。应该尽量避免这种情况的出现。
