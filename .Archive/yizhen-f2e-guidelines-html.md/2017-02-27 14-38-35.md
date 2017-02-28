# HTML 编码规范

* [语法](#contents-html-syntax)
* [HTML5 doctype](#contents-html-doctype)
* [语言属性（Language attribute）](#contents-html-attribute)
* [IE 兼容模式](#contents-html-ie-compatibility-mode)
* [字符编码](#contents-html-encoding)
* [引入 CSS 和 JavaScript 文件](#contents-html-link-src)
* [标签](#contents-html-markup)
* [属性顺序](#contents-html-attribute-order)
* [图片](#contents-html-img)

<h2 id="contents-html-syntax">HTML</h2>
* 用**两个空格**来代替制表符（tab），保证在所有环境下获得一致展现的方法。
* 嵌套元素应当缩进一次（即两个空格）。
* 对于属性的定义，确保全部使用双引号，绝不要使用单引号。
* 不要在自闭合（self-closing）元素的尾部添加斜线，HTML5 规范中明确说明这是可选的。
* 不要省略可选的结束标签（closing tag）（例如，`</li>` 或 `</body>`）。

```html
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

<h2 id="contents-html-doctype">HTML5 doctype</h2>
为每个 HTML 页面的第一行添加标准模式（standard mode）的声明，这样能够确保在每个浏览器中拥有一致的展现。
```html
<!DOCTYPE html>
<html>
  <head>
  </head>
</html>
```

<h2 id="contents-html-attribute">语言属性</h2>
根据 HTML5 规范：

	强烈建议为 html 根元素指定 lang 属性，从而为文档设置正确的语言。这将有助于语音合成工具确定其所应该采用的发音，有助于翻译工具确定其翻译时所应遵守的规则等等。

更多关于 `lang` 属性的知识可以从 [此规范](http://www.w3.org/html/wg/drafts/html/master/semantics.html#the-html-element) 中了解。

这里列出了[语言代码表](http://www.sitepoint.com/web-foundations/iso-2-letter-language-codes/)。
```html
<html lang="zh-CN">
  ...
</html>
```

<h2 id="contents-html-ie-compatibility-mode">IE兼容模式</h2>
IE 支持通过特定的 <meta> 标签来确定绘制当前页面所应该采用的 IE 版本。除非有强烈的特殊需求，否则最好是设置为 edge mode，从而通知 IE 采用其所支持的最新的模式。
```html
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```

<h2 id="contents-html-encoding">字符编码</h2>
通过明确声明字符编码，能够确保浏览器快速并容易的判断页面内容的渲染方式。这样做的好处是，可以避免在 HTML 中使用字符实体标记（character entity），从而全部与文档编码一致（一般采用 UTF-8 编码）。

页面必须使用精简形式，明确指定字符编码。指定字符编码的 meta 必须是 head 的第一个直接子元素。
```html
<html>
  <head>
    <meta charset="UTF-8">
    ...
  </head>
  <body>
    ...
  </body>
</html>
```

<h2 id="contents-html-link-src">引入 CSS 和 JavaScript 文件</h2>
* 根据 HTML5 规范，在引入 CSS 和 JavaScript 文件时一般不需要指定 `type` 属性，因为 `text/css` 和 `text/javascript` 分别是它们的默认值。
* CSS 文件放置在 head 中，JavaScript 放置在页面尾部

```html
<html>
  <head>
    <meta charset="UTF-8">
    <!-- External CSS -->
    <link rel="stylesheet" href="code-guide.css">
      ...
    <!-- In-document CSS -->
    <style>
      /* ... */
    </style>
  </head>
  <body>
    ...
    <!-- JavaScript -->
    <script src="code-guide.js"></script>
  </body>
</html>
```

<h2 id="contents-html-markup">标签</h2>
* 标签名必须使用小写字母。
* 对于无需自闭合的标签，不允许自闭合。
* 对 HTML5 中规定允许省略的闭合标签，不允许省略闭合标签。
* 标签使用必须符合标签嵌套规则。
* HTML 标签的使用应该遵循标签的语义。
* 尽量遵循 HTML 标准和语义，但是不要以牺牲实用性为代价。任何时候都要尽量使用最少的标签并保持最小的复杂度。
* 常见无需自闭合标签有 input、br、img、hr、link、mete 等。

```html
<input tyle="text" name="title">
```

<h2 id="contents-html-attribute-order">属性顺序</h2>
HTML 属性应当按照以下给出的顺序依次排列，确保代码的易读性。

* `class`
* `id`, `name`
* `data-*`
* `src`, `for`, `type`, `href`
* `title`, `alt`
* `aria-*`, `role`

class 用于标识高度可复用组件，因此应该排在首位。id 用于标识具体组件，应当谨慎使用（例如，页面内的书签），因此排在第二位。

```html
<a class="..." id="..." data-modal="toggle" href="#">
  Example link
</a>
<input class="form-control" type="text">
<img src="..." alt="...">
```

布尔类型的属性，建议不添加属性值。
```html
<input type="text" disabled>
<input type="checkbox" value="1" checked>
```

<h2 id="contents-html-img">图片</h2>
* 禁止 img 的 src 取值为空。延迟加载的图片也要增加默认的 src。
  src 取值为空，会导致部分浏览器重新加载一次当前页面，参考：[https://developer.yahoo.com/performance/rules.html#emptysrc](https://developer.yahoo.com/performance/rules.html#emptysrc)
* 为重要图片添加 alt 属性。
* 添加 width 和 height 属性，以避免页面抖动。
* 有下载需求的图片采用 img 标签实现，无下载需求的图片采用 CSS 背景图实现。
  * 产品 logo、用户头像、用户产生的图片等有潜在下载需求的图片，以 `<img>` 形式实现，能方便用户下载。
  * 无下载需求的图片，比如：icon、背景、代码使用的图片等，尽可能采用 CSS 背景图实现。
* 图片格式
  * 普通背景图一律使用 PNG-8;
  * 半透明效果使用 PNG-24，若要兼容 IE6 需使用兼容图，并且在中 `_bakcground` 引入；
  * 大尺寸，颜色较多的图片，使用“存储为 web 格式”并适当调整图片品质，找到文件大小于图片质量的平衡点。
* 关于 CSS Sprite 等相关自动化处理技术，将会单独整理供参考。借助自动化工具提升工作效率。

## 致谢
1. [http://codeguide.co/](http://codeguide.co/)
2. [http://zoomzhao.github.io/code-guide/](http://zoomzhao.github.io/code-guide/)
