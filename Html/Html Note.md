# Html Note

## 概述

- html主要包含标签、属性
- 标签有单标签和双标签
  - 双标签通常可以用来给标签之间的内容设置属性
  - 单标签常用的有`br`,`hr`,`link`,可以用 **/** 结尾，如`<hr/>`
- 有些属性是布尔属性，不需要给定值，如`ol`中的`reversed`
- 代码不区分大小写

语义化标记：通过选用恰当的标签，向用户、浏览器和搜索引擎以及其他处理系统描述内容，提高了无障碍性。

## 注释

```html
<!-- -->
```

## 特殊字符(HTML实体)

- [HTML](https://developer.mozilla.org/zh-CN/docs/Glossary/HTML) 实体是一段以连字号（`&`）开头、以分号（`;`）结尾的文本（字符串）
- HTML 实体常用于显示保留字符（这些字符会被解析为 HTML 代码）和不可见的字符（如“不换行空格”）

|符号代码|显示结果|说明|
|---|---|---|
|`&nbsp;`|&nbsp;|不断行空格|
|`&ensp;`|&ensp;|半角空格|
|`&emsp;`|&emsp;|全角空格|
|`&lt;`|<|小于|
|`&gt;`|>|大于|
|`&amp;`|&|&符|
|`&times;`|×|乘|
|`&divide;`|÷|除|
|`&quot;`|"|双引号|
|`&copy;`|©|版权|
|`&reg;`|®|注册商标|
|`&trade;`|™|商标|

> 其他特殊字符可参阅文档

## 全局属性

HTML具有一些全局属性，全局属性是通用的，所有HTML元素都可以指定。

### lang属性

- 指定了该元素内容， 以及该元素包含文本的属性的主要语言
- 如果元素省略了这些属性，该元素的语言就是其父元素的语言（如果有的话）
- 鼓励作者在根 html 元素上指定`lang`属性，给出文档的语言。这可以帮助语音合成工具确定要使用的发音，帮助翻译工具确定要使用的规则，等等

### title属性

- 表示元素的建议信息
  - 在链接上，这可能是目标资源的标题或描述；在图片上，它可以是图片来源或图片的描述；在段落上，它可能是文本的脚注或评论；在引用上，可以是来源的进一步信息； 在交互式内容上，它可能是元素的标签或使用说明；等等
- 有些元素比如`link`，`abbr`，和`input`为`title`属性定义了额外的语义

### id属性

- 定义唯一标识符（ID）
- 用于在链接（使用片段）、脚本和样式（通过 CSS）中辨识元素

### class属性

- 一个以空格分隔的元素的类名列表，它允许CSS和Javascript通过类选择器或DOM方法来选择和访问特定的元素

> 其他全局可参阅[文档](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes)

## html结构

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
    </head>
    <body>
        Hello
    </body>
</html>
```

`<!DOCTYPE html>`是html文档声明，页面需要处于第一行的文档声明

html可以有属性`lang`，如`lang="en"`

## Head

- `head`中主要包含元数据内容
  - 元数据内容是设置其余内容的呈现或行为，包括样式、脚本及数据，能帮助一些软件（例如[搜索引擎](https://developer.mozilla.org/zh-CN/docs/Glossary/Search_engine)、[浏览器](https://developer.mozilla.org/zh-CN/docs/Glossary/Browser) 等等）更好地运用和渲染页面。对于样式和脚本的元数据，可以直接在网页里定义，也可以链接到包含相关信息的外部文件
  - `base`, `link`, `meta`, `script`, `style`, `title`等

|标签名|描述|
|:---:|---|
|`head`|文档信息|
|`title`|标题|
|`base`|链接的默认地址或默认目标|
|`link`|文档与外部资源之间的关系|
|`meta`|元信息|
|`script`|客户端脚本|
|`style`|文档样式|

### \<title\>

- 表示文档的标题或名称
- 必须要有的

```html
<head>
    <title>Title of the document</title>
</head>
```

### \<base\>

- 为页面上的所有链接规定默认根地址
- 只能有一个

属性有`href`和`target`

```html
<!-- 引用自w3c -->
<head>
    <title>This is an example for the &lt;base&gt; element</title>
    <base href="https://www.example.com/news/index.html">
</head>
<body>
    <!-- https://www.example.com/news/archives.html -->
    <p>Visit the <a href="archives.html">archives</a>.</p>
</body>
```

### \<link\>

- 链接一个与当前文档存在关系的外部资源
- `rel`属性常用的值由`stylesheet`和`icon`，用于链接外部样式表和链接外部图标

```html
<!-- 加载图标 -->
<link rel="icon" href="img/icon.jpg">
```

### \<meta\>

- 不会显示在页面上，但是对于机器是可读的
- 可以有多个

`<meta>`常用属性有`charset`, `http-equiv`, `name`, `content`, `name`/`http-equiv`与`content`组成键值对

|属性|值|说明|
|---|---|---|
|`charset`||字符集编码，如果存在该属性，则其值必须是字符串 `"utf-8"` 的不区分 ASCII 大小写的匹配，因为 UTF-8 是 HTML5 文档的唯一有效编码。声明字符编码的 `<meta>` 元素必须完全位于文档的前 1024 个字节内。|
|`name`|`author`\|`description`\|`keywords`\|`generator`|作者\|描述\|关键字，使用逗号分隔\|编辑器|
|`name`|[`viewport`](#viewport)|设置视口，改善网站在各种设备上的外观|
|`name`|`color-scheme`|颜色模式|
|`name`|`robots`|爬虫、协作搜寻器|
|`name`|`application-name`|Web应用程序的名称(如果不是，不得使用)|
|`http-equiv`|`refresh`|文档的刷新时间（和刷新后的地址）|
|`http-equiv`|`set-cookie`|设置cookie|
|`http-equiv`|`content-security-policy`|内容安全策略|
|`http-equiv`|`default-style`|预定义样式表,`content`须匹配同一文档中的一个`link`或`style`元素上`title`|
|`content`|`<context>`|`name`或`http-equiv`属性关联的值|

#### viewport

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

## Body

### 段落与换行

#### 段落

```html
<p>段落</p>
```

#### 换行

```html
<br>
```

### 分隔线

```html
<hr>
```

### 文本修饰

|标签名|效果预览|说明|
|:---:|---|---|
|`strong`|<strong>你好</strong>|表示重要，默认加粗|
|`b`|<b>你好</b>|表示引起注意，默认加粗|
|`em`|<em>你好</em>|表示强调，默认斜体，`i`|
|`u`|<u>你好</u>|下划线|
|`ins`|<ins>你好</ins>|表示插入，默认下划线|
|`s`|<s>你好</s>|表示错误|
|`del`|<del>你好</del>|表示删除|
|`mark`|<mark>你好</mark>|突出显示|
|`sup`|<sup>你好</sup>|定义上标|
|`sub`|<sub>你好</sub>|定义下标|
|`small`|<small>你好</small>|变小|
|`time`|<time datetime="18:00">你好</time>|与`datetime`属性结合使用，机器可读|
|`abbr`|<abbr title="s">你好</abbr>|与title属性结合使用，当鼠标指针悬停在缩写上会显示完整名称|

#### 注音 \<ruby\>

```html
<ruby>
    中<rt>zhong</rt>
</ruby>
```

效果:
<ruby>
    中<rp>(</rp><rt>zhong</rt><rp>(</rp>
</ruby>

### 标题

- 6级

```html
<h1></h1>...<h6></h6>
```

### 列表

- 有序列表
- 无序列表
- 定义列表
- 菜单列表
- 目录列表

```html
<li>列表项</li>
```

#### 无序列表

|属性|值|说明|
|---|---|---|
|`type`|`disc`|实心圆形|
|`type`|`circle`|空心圆形|
|`type`|`square`|实心正方形|

```html
<ul>
    <li>stdin</li>
    <li>stdout</li>
    <li>stderr</li>
</ul>
```

#### 有序列表

|属性|值|说明|
|---|---|---|
|`reversed`||降序，布尔类型|
|`type`|`a`\|`A`|小写\|大写英文|
|`type`|`i`\|`l`|小写\|大写罗马|
|`type`|`1`|数字(默认)|
|`start`|`"数字"`|开始|
|`value`|`"数字"`|对于**li**,改变当前列表项的值，并影响其后|

```html
<ol>
    <li>stdin</li>
    <li>stdout</li>
    <li>stderr</li>
</ol>
```

#### 定义列表

```html
<dl>
    <dt>项目1</dt>
        <dd>描述1</dd>
        <dd>描述2</dd>
    <dt>项目2</dt>
        <dd>描述1</dd>
        <dd>描述2</dd>
</dl>
```

### 预格式化

等宽字体，显示与输入相同

```html
<pre>预格式化文本</pre>
```

### 代码

等宽字体

```html
<code>print(x)</code>
```

### 引用

| 标签名 | 说明                                              |
| :----: | ------------------------------------------------- |
|  `cite`  | 表示一个作品的引用，默认斜体，可以与`<a>`结合使用 |

```html
<figure>
    <blockquote>
        <p>It was a bright cold day in April, and the clocks were striking thirteen.</p>
    </blockquote>
    <figcaption>
        First sentence in <cite><a href="http://www.george-orwell.org/1984/0.html">Nineteen Eighty-Four</a></cite> by George
        Orwell (Part 1, Chapter 1).
    </figcaption>
</figure>

<blockquote>
    <p>It was a bright cold day in April, and the clocks were striking thirteen.</p>
    <cite><a href="http://www.george-orwell.org/1984/0.html">Nineteen Eighty-Four</a></cite>
</blockquote>
```

|属性|值|说明|
|:---:|---|---|
|`cite`|`<url>`|是一个标注引用的信息的来源文档或者相关信息的 URL。通常用来描述能够解释引文的上下文或者引用的信息。|

#### 行引用

- 用来引用短的文本

```html
<q>行引用</q>
```

#### 块引用

- 会将标签内的文字缩进

```html
<blockquote>块引用<blockquote>
```

### 链接

#### target属性

|属性|值|说明|
|:---:|:---:|---|
|`target`|`_self`|在当前页面打开被链接文档（默认值）|
||`_blank`|通常在新标签页打开，但用户可以通过配置选择在新窗口打开|
||`_parent`|在父框架中打开被链接文档。如果没有父级框架，行为与 `_self` 相同|
||`_top`|在最顶级打开(用于`<iframe>`元素)|

> `<iframe>`元素是一种将页面内容嵌入另一页面之中的方法。

#### \<a\>

anchor

|属性|值|说明|
|:---:|---|---|
|`href`|`<url>#<id>`\|`tel:电话`\|`mailto:邮箱`|链接对象，url，相对链接或绝对链接|
|`target`|`_self`\|`_blank`\|`_parent`\|`_top`|打开方式|

```html
<a href="minecraft.jpg" title="minecraft">链接</a>
<a href="#书签id">书签标题</a> <!-- 同一页面 -->
<a href="url#书签id">书签标题</a> <!-- 不同页面 -->
```

### 题注

```html
<!-- 有标题的图像 -->
<figure>
    <img
        src="/zh-CN/docs/Web/HTML/Element/figure/favicon-192x192.png"
        alt="The beautiful MDN logo.">
    <figcaption>MDN Logo</figcaption>
</figure>
```

### 图片

- `src`必须，其他可选
- 可套超链接

|属性|值|说明|
|:---:|:---:|---|
|`src`|`<url>`|路径地址|
|`alt`||替换文本|
|`width`\|`height`|`"整数"`(px)|宽度\|高度|
|`srcset`||以逗号分隔的一个或多个字符串列表|

```html
<img alt="替换文本" src="minecraft.jpg" title="图片">
```

> 同时包括 `height` 和 [`width`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img#attr-width) 使浏览器在加载图像之前计算图像的长宽比。此长宽比用于保留显示图像所需的空间，减少甚至防止在下载图像并将其绘制到屏幕上时布局的偏移。

#### 矢量图片

svg

可通过`<img>` 元素嵌入 SVG

[SVG：可缩放矢量图形 | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Web/SVG)

#### 响应式图片

##### srcset属性

每一个字符串由以下组成：

1. 指向图像的 [URL](https://developer.mozilla.org/zh-CN/docs/Glossary/URL)
2. 可选地，再加一个空格之后，附加以下的其一：
   - 一个宽度描述符（一个正整数，后面紧跟 `w` 符号）
   - 一个像素密度描述符（一个正浮点数，后面紧跟 `x` 符号）

```html
<img srcset="
	space-original.jpg 4x,
	space-large.jpg 3x,
	space-medium.jpg 2x,
	space-small.jpg 1x"
src="space-medium.jpg">

<img srcset="
	space-original.jpg 6200w,
	space-1024.jpg 1024w,
	space-800.jpg 800w,
	space-600.jpg 600w"
src="space-1024.jpg">
```

> `src`属性为尚不支持`srcset`的浏览器准备，属于一种回退机制。

##### \<picture\>

```html
<picture>
    <source media="(min-width: 1025px)" srcset="space-original.jpg">
    <source media="(min-width: 801px)" srcset="space-1024.jpg">
    <source media="(min-width: 601px)" srcset="space-800.jpg">
    <img src="space-600.jpg">
</picture>
```

#### 热区链接

|标签名|说明|
|:---:|---|
|`map`|图像映射元素|
|`area`|热点区域|

#### \<map\>

|属性|值|说明|
|:---:|:---:|---|
|`name`||必须存在，值不得为空并且不能带空格;如果还指定了`id`属性，则两个属性的值必须相同|

##### \<area\>

|属性|值|说明|
|:---:|:---:|---|
|`href`|||
|`alt`||在`href`使用时是必须的|
|`target`|||
|`shape`|`default`(默认)\|`rect`\|`circle`\|`poly`|整个\|矩形\|圆形\|多边形|
|`coords`|`"整数"`(px)|[坐标值](#坐标)|

```html
<!-- 引用自https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/map -->
<map name="primary">
    <area
        shape="circle"
        coords="75,75,75"
        href="https://developer.mozilla.org/docs/Web/JavaScript"
        target="_blank"
        alt="JavaScript">
    <area
        shape="circle"
        coords="275,75,75"
        href="https://developer.mozilla.org/docs/Web/CSS"
        target="_blank"
        alt="CSS">
</map>
<img
    usemap="#primary"
    src="parrots.jpg"
    alt="两只鹦鹉的照片，大小为 350 x 150">
```

###### 坐标

> 对于矩形或长方形，这个`coords`值为两个 x,y 对：左上、右下。对于圆形，这个值是 x,y,r，这里的 x,y 是一对确定圆的中心的坐标而 r 则表示的是半径值。对于多边和多边形，这个值是用 x,y 对表示的多边形的每一个点：x1,y1,x2,y2,x3,y3 等等。

### 其他媒体

#### 视频和音频

|       属性        |      值      | 说明                            |
| :---------------: | :----------: | ------------------------------- |
|       `src`       |   `<url>`    | 路径地址                        |
| `width`\|`height` | `"整数"`(px) | 宽度\|高度，`<audio>`元素不支持 |
|    `controls`     |              | 浏览器自带的控制界面            |

```html
<video controls>
    <source src="rabbit320.mp4" type="video/mp4">
    <source src="rabbit320.webm" type="video/webm">
    <p>你的浏览器不支持此视频。可点击<a href="rabbit320.mp4">此链接</a>观看</p>
</video>

<audio controls>
    <source src="small-step.wav" type="audio/wav">
    <source src="small-step.mp3" type="audio/mp3">
</audio>
```

> `type`非必须，但仍可写上，尤其是多源情况下。

### 行级和块级

- 块级自动换行，宽度默认100%
- 行级不会自动换行，宽度由内容决定

#### 行级 \<span\>

- 短语内容通用行容器
- 使用`class`或是`id`属性定义内容的格式

#### 块级 \<div\>

- 流内容通用块容器
- 使用`class`或是`id`属性定义内容的格式

### 表格

|标签名|说明|
|:---:|---|
|`table`|表格|
|`tr`|行|
|`th`|标题，对于`<thead>`里的元素使用`th`代替`td`，默认粗体|
|`td`|数据|

#### 合并单元格

|属性|值|说明|
|:---:|---|---|
|`rowspan`|`"整数"`|跨行|
|`colspan`|`"整数"`|跨列|

#### 结构化

- 按行分组

|标签名|说明|
|:---:|---|
|`caption`|表格|
|`thead`|头|
|`tbody`|主体|
|`tfoot`|尾|

#### 直列化

- 按列分组

|标签名|说明|
|:---:|---|
|`colgroup`|列组|
|`col`|父元素`colgroup`中一列或多列，只有在没有`span`属性的父元素中才有效|

|属性|值|说明|
|:---:|---|---|
|`span`|`"整数"`|跨越的连续列数。该值必须是正整数。如果不存在，其默认值为 `1`|

```html
<colgroup span="5" class="weekdays"></colgroup>
<colgroup span="2" class="weekend"></colgroup>
```

```html
<colgroup>
    <col>
    <col span="2" class="batman">
    <col span="2" class="flash">
</colgroup>
```

### 结构标签

`<header>`, `<footer>`, `<nav>`, `<section>`, `<article>`, `<aside>`, `<main>`

### 表单

- 由表单控件组成，主要包括输入信息和表单提交

#### \<form\>

表单组件可以在`<form>`标签外使用，但与表单无关，需要JS定义行为

> 表单嵌套是未定义行为

|属性|值|说明|
|:---:|:---:|---|
|**`action`**||服务器地址|
|**`method`**|`get`(默认)\|`post`|提交数据的方法|
|**`name`**||为表单赋予唯一标识，易于在CSS和JS中引用该表单|
|`enctype`||发送编码的方式，当`method="post"`|
|`novalidate`||表示不需要验证表单，布尔类型|
|`target`||提交表单后，显示响应信息位置|

`enctype`属性

- `application/x-www-form-urlencoded`(默认)
- `multipart/form-data`: 不对字符编码，用于上传文件时使用
- `text/plain`: 出现于 HTML5，用于调试

#### 表单分组 \<fieldset\>&\<legend\>

```html
<form>
  <fieldset>
    <legend>Fruit juice size</legend>
    <p>
      <input type="radio" name="size" id="size_1" value="small" />
      <label for="size_1">Small</label>
    </p>
    <p>
      <input type="radio" name="size" id="size_2" value="medium" />
      <label for="size_2">Medium</label>
    </p>
    <p>
      <input type="radio" name="size" id="size_3" value="large" />
      <label for="size_3">Large</label>
    </p>
  </fieldset>
</form>
```

#### 标签 \<label\>

- 用户界面中某个元素的说明
- 程序上与元素关联，扩展可点击区域

|属性|值|说明|
|:---:|:---:|---|
|`for`|`<元素的id>`|与元素建立关联|

#### \<input\>

|属性|值|说明|
|:---:|:---:|---|
|`type`||类型|
|`name`||提交数据中的键|
|`placeholder`||提示信息，对于输入框而言|
|`value`||默认值，提交数据中的值|
|`disabled`||禁用，布尔|
|`readonly`||只读，布尔，除了 `hidden`、`range`、`color`、`checkbox`、`radio` 和按钮以外|

##### type属性

- `text`: 单行文本输入框
- `password`: 密码输入框
- `radio`: 单选按钮
- `checkbox`: 复选框
- `file`: 文件上传按钮
- `submit`: 表单提交按钮
- `image`: 图形提交按钮，属性和`<img>`大致相同
- `reset`: 重置按钮
- `button`: 可单击按钮
- `hidden`: 隐藏，用来收集额外信息或抵御垃圾信息

#### 文本输入框和其他输入控件

`<input>`

`text`用于单行文本输入

`password`用于密码输入

`search`是搜索表单，包含提交

`url`、`tel`、`email`和`number`具有校验能力

`number`和`range`有`min`、`max`和`step`属性

`datetime-local`, `date`, `time`, `month`, `week`与日期和时间相关，有`min`、`max`和`step`属性

`color`用于输入颜色

#### 按钮

`<input>`或`<button>`

```html
<input type="submit/reset/image/button">
<button type="submit/reset"></button>
```

`submit`(默认)/`reset`/`button`

#### 单选按钮和复选框

单选按钮通过设置相同的`name`实现互斥

```html
<input type="radio" id="soup" name="meal" checked>
```

```html
<input type="checkbox" id="questionOne" name="subscribe" value="yes" checked>
```

#### 多行文本输入 \<textarea\>

|  属性  |    值    | 说明         |
| :----: | :------: | ------------ |
| `rows` | `"整数"` | 行数，默认2  |
| `cols` | `"整数"` | 列数，默认20 |

`<textarea>` 的缩放能力由 CSS `resize` 属性控制，其可能的值如下：

- `both`：默认值——允许横向和纵向缩放行为。
- `horizontal`：只允许横向水平缩放行为。
- `vertical`：只允许纵向竖直缩放行为。
- `none`：不允许缩放行为。
- `block` 和 `inline`：实验性的值，仅允许以 `block` 或 `inline` 方向缩放，如何变化取决于文字的方向，请参阅[处理不同文字方向](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/Handling_different_text_directions)以了解更多内容。

#### 选择框 \<select\>

```html
<select name="num">
    <option>1</option>
    <option>2</option>
    <option>3</option>
</select>
```

可设置`value`属性，代替`<option>`元素中的内容提交

```html
<select name="num">
    <option value="one">1</option>
    <option value="two">2</option>
    <option value="three">3</option>
</select>
```

可通过设置`<select>`的`mutiple`属性创建多选框

```html
<select name="num" multiple>
    <option>1</option>
    <option>2</option>
    <option>3</option>
</select>
```

可以由要指定默认值的`<option>`中的`selected`属性设置选择框的默认值，这样在页面加载后，该选项可以预先选中

```html
<select name="num">
    <option>1</option>
    <option>2</option>
    <option selected>3</option>
</select>
```

### 文件

被接受的文件类型可以使用 [`accept`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#accept) 属性来约束。此外，如果你想让用户选择多个文件，那么可以通过添加 [`multiple`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#multiple) 属性来实现。

`accept`属性是一个以逗号为分隔的[**唯一文件类型说明符**](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input/file#唯一文件类型说明符)列表字符串。

```html
<input type="file" name="file" id="file" accept="image/*" multiple>
```

文件选择器可以访问由设备相机和麦克风直接获取的图片、视频、音频。我们只需要这样设置 `accept` 属性即可（分别对应相机捕获的图片、视频和麦克风获取的音频）：

```html
<input type="file" accept="image/*;capture=camera">
<input type="file" accept="video/*;capture=camcorder">
<input type="file" accept="audio/*;capture=microphone">
```

### 进度条和计量条

#### 进度条 \<progress\>

具有`max`和`value`属性

```
<progress max="100" value="75">75/100</progress>
```

[`progress`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/progress) 元素中的内容是供不支持此元素浏览器进行回退，以及给屏幕阅读器提供发音材料的机制。

#### 计量条 \<meter\>

属性`min`和`max`是可选的，默认值分别是0和1

```html
<meter value="0.2">20%</meter>
```
