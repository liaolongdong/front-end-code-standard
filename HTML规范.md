@(开发规范)

# HTML规范

### 基本结构
- 文件应以<!DOCTYPE html>首行顶格开始，该标签告知浏览器文档所使用的是 HTML 规范。
- 必须在head元素内部的meta标签内声明文档的字符编码charset, 如：<meta charset="UTF-8">，这句代码告诉浏览器应该此HTML文件使用的字符集是什么，如果不加此行代码，那么在浏览器中可能显示为乱码。
- 在visual studio code编辑器中输入 `!` 然后按下 `tab` 键就会生成如下 `html` 代码
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```

### 布尔型属性

元素的布尔型属性如果有值，就是 `true`，如果没有值，就是 `false`。

### 属性顺序

HTML 属性应当按照以下给出的顺序依次排列，确保代码的易读性。

- `class`
- `id, name`
- `data-*`
- `src, for, type, href, value`
- `title, alt`
- `role, aria-*`

`class`用于标识高度可复用组件，因此应该排在首位。`id` 用于标识具体组件，应当谨慎使用（例如，页面内的书签），因此排在第二位。

对于属性的定义，确保全部使用双引号，绝不要使用单引号。

### 减少标签数量

尽量不要套无用的标签，增加标签的数量，比如：
```html
/* bad */
<span class='avatar'>
	<img src='./123.png'>
</span>

/* better */
<img class='avatar' src='./123.png'>
```

### 标签语义化

什么是标签语义化，简单来说。就是让正确的标签干正确的事儿。比如只有一行文本，就应该使用`P`标签，而列表就应该使用`ul`或者`ol`，视具体的场景而定。

#### img 标签

- `img` 标签， 应该使用`alt`,用于图片不显示或者图片发生错误时的`文字提示`。

#### H1~H6标签

> 
 - `H1` 每个页面只能有一个，有利于网络爬虫`SEO`。
 - 不要为了减小标题的字体而使用低级别的标题， 而是使用 CSS `font-size` 属性。
 - 避免跳过某级标题：始终要从` <h1>` 开始，接下来使用 `<h2>` 等等
 - 使用 `section` 的时候，应当每个 `section` 都使用一个 `<h2>`

#### footer标签

- `<footer>`元素内的作者信息应包含在`<address>` 元素中。

#### div标签

>` <div>` 元素是一个通用型的流内容容器，它在语义上不代表任何特定类型的内容，它可以被用来对其它元素进行分组，一般用于样式化相关的需求（使用 class 或 id 特性) 或者对具有相同特性的一组元素进行分组 (比如 lang)，它应该在没有任何其它语义元素可用时才使用 (比如 `<article>` 或 `<nav>`) 。

所以不能再这里面直接包含文字，如果需要包含一段文本，应该需要使用`P`标签来包裹。

#### dl 自定义列表

> `<dl>` 元素 是一个包含术语定义以及描述的列表，通常用于展示词汇表或者元数据 (键-值对列表)。

#### 斜体标签的一些区别

- `<em>` 表示强调或重读。
- `<strong>` 表示重要性。
- `<mark>` 表示相关性。
- `<cite>` 标记著作名，如一本书、剧本或是一首歌。
- `<dfn>` 标记术语的定义实例。
- `<i>` 用于表现因某些原因需要区分普通文本的一系列文本

#### （ol）有序列表和（ul）无序列表

很多时候，有序列表有很多自带的序列样式可设置，但是经常在开发中看见自己去定义序列号, 而`ul`代表多项的`无序列表`，即无数值排序项的集合，且它们在列表中的顺序是没有意义的。比如：
```js
/* bad */
<ul>
	<li>1. 第一段文本！！！</li>
	<li>2. 第二段文本！！！</li>
	<li>3. 第三段文本！！！</li>
	<li>4. 第四段文本！！！</li>
</ul>

/* better */
<ol class='txt-list' type='1'>
	<li>第一段文本！！！</li>
	<li>第二段文本！！！</li>
	<li>第三段文本！！！</li>
	<li>第四段文本！！！</li>
</ol>

/* css样式写法 */
.txt-list {
	list-style-type: decimal
}
```

### 避免使用table布局

不要使用table布局，现在基本上被淘汰了，而应该代之以div来布局，方便控制。

更多的样式属性去MDN查看或者[w3school](http://www.w3school.com.cn/cssref/pr_list-style-type.asp)