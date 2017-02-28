# CSS 编码规范

* [语法](#css-syntax)
* [声明顺序](#css-declaration-order)
* [不要使用`@import`](#css-improt)
* [媒体查询的位置](#css-media-queries)
* [带前缀的属性](#css-prefixed-properties)
* [单行规则声明](#css-single-declarations)
* [简写形式的属性声明](#css-shorthand)
* [SASS 中的嵌套](#css-nesting)
* [SASS 中的运算符](#css-operators)
* [代码注释](#css-comments)
* [class 命名](#css-classes)
* [选择器](#css-selectors)
* [代码组织](#css-organization)

<h2 id="css-syntax">语法</h2>
* 用**两个空格**来代替制表符（tab），这是唯一能保证在所有环境下获得一致展现的方法。
* 为选择器分组时，将单独的选择器单独放在一行。
* 为了代码的易读性，在每个声明块的左花括号前添加一个空格。
* 声明块的右花括号应当单独成行。
* 每条声明语句的 `:` 后应该插入一个空格。
* 为了获得更准确的错误报告，每条声明都应该独占一行。
* 所有声明语句都应当以分号结尾。最后一条声明语句后面的分号是可选的，但是，如果省略这个分号，你的代码可能更易出错。
* 对于以逗号分隔的属性值，每个逗号后面都应该插入一个空格（例如，`box-shadow`）。
* 颜色取值 `rgb()`、`rgba()`、`hsl()`、`hsla()` 或 `rect()` ，不要在取值中插入空格。
* 对于属性值或颜色参数，省略小数前面的 0 （例如，`.5` 代替 `0.5`；`-.5px` 代替 `-0.5px`）。
* 十六进制值应该全部小写，例如，`#fff`。在浏览文档时，小写字符易于分辨，因为他们的形式更易于区分。
* 尽量使用简写形式的十六进制值，例如，用 `#fff` 代替 `#ffffff`。
* 为选择器中的属性添加双引号，例如，`input[type="text"]`。只有在[某些情况](http://mathiasbynens.be/notes/unquoted-attribute-values#css)下是可选的，但是，为了代码的一致性，建议都加上双引号。
* 避免为 0 值指定单位，例如，用 `margin: 0;` 代替 `margin: 0px;`。
* `url()` 函数中的路径不加引号。
* `url()` 函数中的绝对路径可省去协议名。

```css
/* Bad CSS */
.selector, .selector-secondary, .selector[type=text] {
  padding:15px;
  margin:0px 0px 15px;
  background-color:rgba(0, 0, 0, 0.5);
  box-shadow:0 1px 2px #CCC,inset 0 1px 0 #FFFFFF
}

/* Good CSS */
.selector,
.selector-secondary,
.selector[type="text"] {
  padding: 15px;
  margin-bottom: 15px;
  background-color: rgba(0,0,0,.5);
  box-shadow: 0px 1px 2px #ccc, inset 0 1px 0 #fff;
}
```

<h2 id="css-declaration-order">声明顺序</h2>
相关的属性声明应当归为一组，并按照下面的顺序排列：

* Formatting Model `position` / `top` / `right` / `bottom` / `left` / `float` / `display` / `overflow` 等
* Box Model `border` / `margin` / `padding` / `width` / `height` 等
* Typographic `font` / `line-height` / `text-align` / `word-wrap` 等
* Visual `background` / `color` / `transition` / `list-style` 等

由于定位（positioning）可以从正常的文档流中移除元素，并且还能覆盖盒模型（box model）相关的样式，因此排在首位。盒模型排在第二位，因为它决定了组件的尺寸和位置。

其他属性只是影响组件的内部（inside）或者是不影响前两组属性，因此排在后面。

```css
.sidebar {
  /* formatting model: positioning schemes / offsets / z-indexes / display / ...  */
  position: absolute;
  top: 50px;
  left: 0;
  overflow-x: hidden;

  /* box model: sizes / margins / paddings / borders / ...  */
  width: 200px;
  padding: 5px;
  border: 1px solid #ddd;

  /* typographic: font / aligns / text styles / ... */
  font-size: 14px;
  line-height: 20px;

  /* visual: colors / shadows / gradients / ... */
  background: #f5f5f5;
  color: #333;
  -webkit-transition: color 1s;
     -moz-transition: color 1s;
          transition: color 1s;

  /* misc */
  opacity: 1;
}
```

<h2 id="css-improt">不要使用 `@import`</h2>
与 `<link>` 标签相比，`@import` 指令要慢很多，不光增加了额外的页面请求，还会导致不可预料的问题。替代办法有以下几种：

* 使用多个 <link> 元素
* 通过 Sass 或 Less 类似的 CSS 预处理器将多个 CSS 文件编译为一个文件

```html
<!-- Use link elements -->
<link rel="stylesheet" href="core.css">

<!-- Avoid @imports -->
<style>
  @import url("more.css");
</style>
```

<h2 id="css-media-queries">媒体查询（Media query）的位置</h2>
将媒体查询放在尽可能相关规则的附近。不要将他们打包放在一个单一样式文件中或者放在文档底部。如果你把他们分开了，将来只会被大家遗忘。下面给出一个典型的实例。

```css
.element { ... }
.element-avatar { ... }
.element-selected { ... }

@media (min-width: 480px) {
  .element { ...}
  .element-avatar { ... }
  .element-selected { ... }
}
```

<h2 id="css-prefixed-properties">带前缀的属性</h2>
当使用特定厂商的带有前缀的属性时，通过缩进的方式，让每个属性的值在垂直方向对齐，这样便于多行编辑。

```css
/* Prefixed properties */
.selector {
  -webkit-box-shadow: 0 1px 2px rgba(0,0,0,.15);
          box-shadow: 0 1px 2px rgba(0,0,0,.15);
}
```

<h2 id="css-single-declarations">单行规则声明</h2>
对于**只包含一条声明**的样式，为了易读性和便于快速编辑，建议将语句放在同一行。对于带有多条声明的样式，还是应当将声明分为多行。

这样做的关键因素是为了错误检测 - 例如，CSS 校验器指出在 20 行有语法错误。如果是单行单条声明，你就不会忽略这个错误；如果是单行多条声明的话，你就要仔细分析避免漏掉错误了。

```css
/* Single declarations on one line */
.span1 { width: 60px; }
.span2 { width: 140px; }
.span3 { width: 220px; }

/* Multiple declarations, one per line */
.sprite {
  display: inline-block;
  width: 16px;
  height: 15px;
  background-image: url(../img/sprite.png);
}
.icon { background-position: 0 0; }
.icon-home { background-position: 0 -20px; }
.icon-account { background-position: 0 -40px; }
```

<h2 id="css-shorthand">简写形式的属性声明</h2>
在需要显示地设置所有值的情况下（属性简写需要你必须显式设置所有取值），应当尽量限制使用简写形式的属性声明。常见的滥用简写属性声明的情况如下：

* `padding`
* `margin`
* `font`
* `background`
* `border`
* `border-radius`

大部分情况下，我们不需要为简写形式的属性声明指定所有值。例如，HTML 的 heading 元素只需要设置上、下边距（margin）的值，因此，在必要的时候，只需覆盖这两个值就可以。过度使用简写形式的属性声明会导致代码混乱，并且会对属性值带来不必要的覆盖从而引起意外的副作用。

MDN（Mozilla Developer Network）上一片非常好的关于 [shorthand properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties) 的文章，对于不太熟悉简写属性声明及其行为的用户很有用。

```css
/* Bad example */
.element {
  margin: 0 0 10px;
  background: red;
  background: url("image.jpg");
  border-radius: 3px 3px 0 0;
}

/* Good example */
.element {
  margin-bottom: 10px;
  background-color: red;
  background-image: url("image.jpg");
  border-top-left-radius: 3px;
  border-top-right-radius: 3px;
}
```

<h2 id="css-nesting">LESS 和 SASS 中的嵌套</h2>
避免非必要的嵌套。这是因为虽然你可以使用嵌套，但是并不意味着应该使用嵌套。只有在必须将样式限制在父元素内（也就是后代选择器），并且存在多个需要嵌套的元素时才使用嵌套。
```css
// Without nesting
.table > thead > tr > th { … }
.table > thead > tr > td { … }

// With nesting
.table > thead > tr {
  > th { … }
  > td { … }
}
```

<h2 id="css-operators">LESS 和 SASS 中的运算符</h2>
避免非必要的嵌套。这是因为虽然你可以使用嵌套，但是并不意味着应该使用嵌套。只有在必须将样式限制在父元素内（也就是后代选择器），并且存在多个需要嵌套的元素时才使用嵌套。
```css
// Bad example
.element {
  margin: 10px 0 @variable*2 10px;
}

// Good example
.element {
  margin: 10px 0 (@variable * 2) 10px;
}
```

<h2 id="css-comments">注释</h2>
代码是由人编写并维护的。请确保你的代码能够自描述、注释良好并且易于他人理解。好的代码注释能够传达上下文关系和代码目的。不要简单地重申组件或 class 名称。

对于较长的注释，务必书写完整的句子；对于一般性注解，可以书写简洁的短语。
```css
/* Bad example */
/* Modal header */
.modal-header {
  ...
}

/* Good example */
/* Wrapping element for .modal-title and .modal-close */
.modal-header {
  ...
}
```

<h2 id="css-classes">class 命名</h2>
* class 名称中只能出现小写字符和破折号（dashe）（不是下划线，也不是驼峰命名法）。破折号应当用于相关 class 的命名（类似于命名空间）（例如，.btn 和 .btn-danger）。
* 避免过度任意的简写。.btn 代表 button，但是 .a 不能表达任何意思。
* class 名称应当尽可能短，并且意义明确。
* 使用有意义的名称。使用有组织的或目的明确的名称，而不是抽象的名称。
* 基于最近的父 class 或基本（base） class 作为新 class 的前缀。
* 使用 .js-* class 来标识行为（与样式相对），并且不要将这些 class 包含到 CSS 文件中。
这些规则在创建 Sass 和 Less 变量名时同样有用。
```css
/* Bad example */
.t { ... }
.red { ... }
.header { ... }

/* Good example */
.tweet { ... }
.important { ... }
.tweet-header { ... }
```

<h2 id="css-selectors">选择器</h2>
* 对于通用元素使用 classes ，这样利于渲染性能的优化。
* 对于经常出现的组件，避免使用属性选择器（例如，[class^="..."]）。浏览器的性能会受到这些因素的影响。
* 选择器要尽可能短，并且尽量限制组成选择器的元素个数，建议不要超过 **3** 。
* **只有**在必要的时候才将 class 限制在最近的父元素内（也就是使用后代选择器）（例如，不使用带前缀的 classes 时）。

```css
/* Bad example */
span { ... }
.page-container #stream .stream-item .tweet .tweet-header .username { ... }
.avatar { ... }

/* Good example */
.avatar { ... }
.tweet-header .username { ... }
.tweet .avatar { ... }
```

<h2 id="css-organization">代码组织</h2>
* 以组件为单位组织代码段。
* 制定一致的注释规范。
* 使用一致的空白符将代码分隔成块，这样利于文档的阅读。
* 如果使用了多个 CSS 文件，将其按照组件而非页面的形式分拆，因为页面会被重组，而组件只会被移动。

```css
/*
 * Component section heading
 */

.element { ... }


/*
 * Component section heading
 *
 * Sometimes you need to include optional context for the entire component.
  * Do that up here if it's important enough.
 */

.element { ... }

/* Contextual sub-component or modifer */
.element-heading { ... }
```