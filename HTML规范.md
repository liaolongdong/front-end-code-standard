@(开发规范)

# HTML规范

### 文件名命名规则

- 使用小驼峰命名规则，如，`index.html、orderDetail.html`，命名尽量保持语义化，但是文件名不宜过长。

### 图片命名

- 图片名称必须小写，禁止使用特殊字符、中文。
- 使用英文或拼音缩写。
- 名称间隔使用_符号。
- 命名需要能体现图片的大概用途, 禁止文件名和实际图片内容不符。


> 常用示例：

	bg.jpg          //背景图片
	module_bg.jpg      //模块背景
	sprites.png     //精灵图
	btn_start.png   //开始按钮
	icon_play.png    //修饰性图片

> 反面例子：图片名为'weixin_qrcode'，图片内容却是头像。

### 基本结构
- 文件应以`<!DOCTYPE html>`首行顶格开始，该标签告知浏览器文档所使用的是 HTML 规范。
- 必须在head元素内部的meta标签内声明文档的字符编码charset, 如：`<meta charset="UTF-8">`，这句代码告诉浏览器应该此HTML文件使用的字符集是什么，如果不加此行代码，那么在浏览器中可能显示为乱码。
- 强烈建议为 `html` 根元素指定 `lang` 属性，从而为文档设置正确的语言。这将有助于语音合成工具确定其所应该采用的发音，有助于翻译工具确定其翻译时所应遵守的规则等等。
- 在visual studio code编辑器中输入 `!` 然后按下 `tab` 键就会生成如下 `html` 代码
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
	<!-- 页面名称-产品中文全称-官方网站-产品名称-产品slogan，28个汉字以内 -->
    <title>Document</title>
	<!-- 页面关键字(keywords) keywords为产品名、专题名、专题相关名词，之间用英文半角逗号隔开 -->
	<meta name="keywords" content="家具拆装,家具配送,家具安装,家具维修"/>
	<!-- 页面描述(description) 不超过150个字符，描述内容要和页面内容相关 -->
	<meta name="description" content="万师傅是全国专业家居售后服务网站,提供【家具】【晾衣架】【灯具】【卫浴】【墙纸地毯】的拆装,搬运等服务担保交易;师傅覆盖全国600多个城市,快速,便捷,省钱,有保障！"/>
</head>
<body>
    
</body>
</html>
```

### 页面meta

**PC端meta**

```html
<!-- 字符编码 -->
<meta charset="utf-8" />
<!-- 优先使用 IE 最新版本和 Chrome -->
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
<!-- 这个网页可以被搜索引擎搜索到 -->
<meta name="robots" content="index,follow" />
<!-- 文档作者名称 -->
<meta name="author" content="xiaoyi-better" />
<!-- 版权信息 -->
<meta name="copyright" content="xiaoyi" />
<!-- 包含页面内容的简短和精确的描述 -->
<meta name="description" content="页面的描述内容" />
<!-- 包含与逗号分隔的页面内容相关的关键字 -->
<meta name="keywords" content="页面关键字" />
```

**移动端meta**

```html
<!-- 字符编码 -->
<meta charset="utf-8" />
<!-- width - viewport的宽度；initial-scale - 初始的缩放比例；minimum-scale - 允许用户缩放到的最小比例；maximum-scale - 允许用户缩放到的最大比例；user-scalable - 用户是否可以手动缩放；viewport-fit=cover - iphonex适配刘海问题兼容处理 -->
<meta name="viewport" content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no,viewport-fit=cover" />
<!-- 为了防止页面数字被识别为电话号码，可根据实际需要添加： -->
<meta name="format-detection" content="telephone=no" /> 
<!-- 让添加到主屏幕的网页再次打开时全屏展示，可添加：   -->
<meta name="mobile-web-app-capable" content="yes" />
<!-- 是否启用 WebApp 全屏模式，删除苹果默认的工具栏和菜单栏 -->
<meta name="apple-mobile-web-app-capable" content="yes" />
<!-- 设置苹果工具栏颜色 -->
<meta name="apple-mobile-web-app-status-bar-style" content="black" />
<!-- 添加到主屏后的标题（iOS 6 新增） -->
<meta name="apple-mobile-web-app-title" content="标题" />
<!-- 这个网页可以被搜索引擎搜索到 -->
<meta name="robots" content="index,follow" />
<!-- 文档作者名称 -->
<meta name="author" content="xiaoyi-better" />
<!-- 版权信息 -->
<meta name="copyright" content="xiaoyi" />
<!-- 包含页面内容的简短和精确的描述 -->
<meta name="description" content="页面的描述内容" />
<!-- 包含与逗号分隔的页面内容相关的关键字 -->
<meta name="keywords" content="页面关键字" />
```
更多meta标签详情可查看：[meta MDN](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meta)或者[HTML meta标签总结与属性使用介绍](https://www.cnblogs.com/wangyang108/p/5995379.html)

### 引入 CSS 和 JavaScript 文件

- 根据 `HTML5` 规范，在引入 `CSS` 和 `JavaScript` 文件时一般不需要指定 `type` 属性，因为 `text/css` 和 `text/javascript` 分别是它们的默认值。
- `CSS` 文件引入放在 `</head>` 标签前
- `JavaScript` 文件引入放在 `</body>` 标签前


### 属性

- 属性和值全部小写，每个属性都必须有一个值，每个值必须加双引号。
- 元素的布尔型属性如果有值，就是 `true`，如果没有值，就是 `false`。
- HTML 属性应当按照以下给出的顺序依次排列，确保代码的易读性。
	- `class`
	- `id, name`
	- `data-*`
	- `src, for, type, href, value`
	- `title, alt, placeholder`
	- `required, readonly, disable`
	- `role, aria-*`

- `class`用于标识高度可复用组件，因此应该排在首位。`id` 用于标识具体组件，应当谨慎使用（例如，页面内的书签），因此排在第二位。
- 一个标签上引用的className不要过多，越少越好。

### 标签标准

- 正确闭合标签且必须闭合。
- 应当以最严格的xhtml strict标准来嵌套，比如：内联元素不能包含块级元素等等。
- 标签的自定义属性以data-开头，如：`<a href="#" data-num='18'></a>`。

```HTML
<!-- 正确闭合标签 -->
<!-- bad -->
<p>段落文本
<img src="imgUrl" alt="图片" >
<input type="text" placeholder="占位符" >

<!-- better -->
<p>段落文本</p>
<img src="imgUrl" alt="图片" />
<input type="text" placeholder="占位符" />

<!-- 避免内联元素中包含块级元素 -->
<!-- bad -->
<span>
	<div>内容</div>
</span>

<!-- better -->
<div>
	<span>内容</span>
</div>
```

### 标签语义化

语义化HTML：用最恰当的HTML元素标记的内容。

优点：
1. 提升可访问性；
2. SEO；
3. 结构清晰，利于维护；

通用类HTML标签：`div` —— 块级通用容器；`span` —— 行内内容无语义容器。如果语义不合适，就直接用通用类标签。

常用的语义化HTML标签：
- `H1~H6`标签
	> 
	- `H1` 每个页面只能有一个，有利于网络爬虫`SEO`。
	- 不要为了减小标题的字体而使用低级别的标题， 而是使用 CSS `font-size` 属性。
	- 避免跳过某级标题：始终要从` <h1>` 开始，接下来使用 `<h2>` 等等。
	- 使用 `section` 的时候，应当每个 `section` 都使用一个 `<h2>`。
- `<header></header>`标签：页眉通常包括网站标志、主导航、全站链接以及搜索框。
- `<nav></nav>`标签：标记导航，仅对文档中重要的链接群使用。
- `<p></p>`标签：包含一段文本段落。
- `<main></main>`标签：页面主要内容，一个页面只能使用一次。如果是web应用，则包围其主要功能。
- `<article></article>`标签：包含类似于文章类型的片段，表示文档、页面、应用或一个独立的容器， 可相互嵌套使用。
- `<section></section>`标签：具有相似主题的一组内容，比如网站的主页可以分成介绍、新闻条目、联系信息等条块。
- `<aside></aside>`标签：指定附注栏，包括引述、侧栏、指向文章的一组链接、广告、友情链接、相关产品列表等。
- `<footer></footer>`标签：页脚，只有当父级是body时，才是整个页面的页脚。
- `<address></address>`标签：作者、相关人士或组织的联系信息（电子邮件地址、指向联系信息页的链接）。
- `<code></code>`标签：标记代码。包含示例代码或者文件名 （< `&lt`;  > `&gt;`）。
- `<pre></pre>`标签：预格式化文本。保留文本固有的换行和空格。
- `<progress></progress>`：完成进度。可通过js动态更新value。
- `<dl>`标签，是一个包含术语定义以及描述的列表，通常用于展示词汇表或者元数据 (键-值对列表)。
- `<em>` 表示强调或重读。
- `<strong>` 表示重要性。
- `<mark>` 表示相关性。
- `<cite>` 标记著作名，如一本书、剧本或是一首歌。
- `<dfn>` 标记术语的定义实例。
- `<i>` 用于表现因某些原因需要区分普通文本的一系列文本

#### （ol）有序列表和（ul）无序列表

- 很多时候，有序列表有很多自带的序列样式可设置，但是经常在开发中看见自己去定义序列号, 而`ul`代表多项的`无序列表`，即无数值排序项的集合，且它们在列表中的顺序是没有意义的。比如：
```js
/* bad */
<ul>
	<li>1. 第一段文本！！！</li>
	<li>2. 第二段文本！！！</li>
	<li>3. 第三段文本！！！</li>
	<li>4. 第四段文本！！！</li>
</ul>

/* better */
<ol class='list' type='1'>
	<li>第一段文本！！！</li>
	<li>第二段文本！！！</li>
	<li>第三段文本！！！</li>
	<li>第四段文本！！！</li>
</ol>

/* css样式写法 */
.list {
	list-style-type: decimal
}
```
更多的样式属性去MDN查看或者[w3school](http://www.w3school.com.cn/cssref/pr_list-style-type.asp)

### 减少标签数量

- 尽量不要套无用的标签，增加标签的数量，比如：
```html
/* bad */
<span class='avatar'>
	<img src='./123.png'>
</span>

/* better */
<img class='avatar' src='./123.png'>
```

### a、img、audio、video标签

**`a`标签**

- 给 `<a>` 标签加上title属性。
- 外部链接页面间跳转，采用打开新窗口模式：`target="_blank"`。

**`img`标签**

- `img` 标签， 应该使用`alt`,用于图片不显示或者图片发生错误时的`文字提示`。
- PC端`img`图片必须填写`width、height`属性。
- `alt`不能为无意义字符，需要能表现出图片的含义。

**`audio、video`标签**

- `audio、video` 标签，加入文案和链接。
```html
<img src="imgUrl" alt="图片" />
<audio controls>
	<source src="horse.ogg" type="audio/ogg">
	<source src="horse.mp3" type="audio/mpeg">
	您的浏览器不支持 audio 元素。
</audio>
<video width="320" height="240" controls>
    <source src="movie.mp4" type="video/mp4">
    <source src="movie.ogg" type="video/ogg">
    您的浏览器不支持 video 标签。
</video>
```

### 避免使用table布局

- 不要使用table布局，现在基本上被淘汰了，而应该代之以div来布局，方便控制。

### 避免使用iframe

- 使用iframe会增加页面额外请求，影响性能
- 使用iframe不利于seo搜索引擎优化
- 使用iframe不利于代码维护

### 浏览器兼容

**PC端**
- 兼容IE9及以上、Firefox、chrome、QQ、360浏览器等浏览器
- 不兼容IE9的情况下，需要在页面顶部加入提示，并对.browser-tips使用醒目的颜色标识样式
```html
<!--[if lt IE 9]><p class="browser-tips">您的浏览器版本过低，请升级浏览器获得更好的体验<p><![endif]-->
```

**移动端兼容**
- 微信浏览器、android4.6，ios9.0以上

### 更多规范请参考[页面前端规范](http://tgideas.qq.com/doc/frontend/spec/common/)
