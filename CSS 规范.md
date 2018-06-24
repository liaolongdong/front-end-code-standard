@(开发规范)

# CSS 规范

### 文件命名规则
- 与`html`文件命名规则一样，采用小驼峰，比如：`index.css, orderDetail.css`

### css样式引入方式

- 推荐使用link引入外部css样式文件到`head`标签中
- 避免使用`@import`引入样式
- 避免使用内联样式

### class命名空间

- 页面采用`p-`的命名空间，比如`p-home, p-about, p-pay`, p = page;
- 通用的组件使用`c-`的命名空间。 比如`c-popup, c-nav, c-slidebar`, c = component/common;
- 通用工具类的统一使用`t-`的命名空间。比如`t-clearfix, t-ellipsis`, t = tool;
- 状态类的使用`s-`的命名空间。 比如： `s-current, s-active` s = status;
- js钩子类的使用`j-`的命名空间。一般用于需要提供给ios，类似于用于写业务逻辑。使用了react，除非必要，不要使用。 比如： `j-name， j-doc`。 j = javascrpt.
- 这种命名方式，最多只能拥有俩个破折号，即`p-about-head`。页面下其他的功能，依次向下类推，
比如`about`页面的`head`区域有个`contact`的类名，推荐使用`about-head-contact`这样的风格去命名。
 > **注意**：类名的命名方式，应该以语义化为前提，不要出现类似取每个汉字首字母拼音的方式命名，不利于阅读和维护。

**尽量避免使用id，如必须使用则区分`class`命名，采用小驼峰，如，`#myDialog`**
**所有的class命名以此为标准，全部采取英文小写, 英文之间用`-`连接, 尽量避免使用`数字`，不允许出现`大写`和类似`_拼接`和`驼峰命名法`**

### 统一语义理解和命名

- 布局（`.g-`）

| 语义 | 命名 |
| :--- | ---:|
| 文档 | doc |
| 头部 | head |
| 主体 | body |
| 尾部 | footer |
| 主栏 | main |
| 侧栏 | side |
| 盒容器 | warp/box |

- 模块（`m-`）, 组件（`c-`）

| 语义 | 命名 |
| :--- | ---: |
| 导航 | nav |
| 子导航 | subnav |
| 面包屑 | crumb |
| 菜单 | menu |
| 选项卡 | tab |
| 标题区 | head/title |
| 内容区 | body/content |
| 列表 | list |
| 表格 | table |
| 表单 | form |
| 热点 | hot |
| 登录 | login |
| 注册 | register |
| 幻灯 | slide |
| 排行 | rank |
| 标志 | logo |
| 图标 | icon |
| 搜索 | search |
| 提示 | tips |
| 帮助 | help |
| 新闻 | news |
| 栏目 | column |
| 下载 | download |
| 上传 | upload |
| 广告 | advertise |

- 功能 （`f-`）

| 语义 | 命名 |
| :--- | ---: |
| 清除浮动 | clear-float
| 左浮动 | float-left
| 内联 | inline-block
| 文本居中 | align-center
| 垂直居中 | vertical--middle
| 溢出隐藏 | overflow-hidden
| 完全消失 | display-none
| 字体大小 | font-size
| 字体粗细 | font-weight

- 状态（`s-`）

| 语义 | 命名 |
| :--- | ---: |
| 选中 | selected |
| 当前 | current/active |
| 显示 | show |
| 隐藏 | hide |
| 打开 | open |
| 关闭 | close |
| 出错 | error |
| 禁用 | disabled |

### css属性的书写顺序

1. 显示属性, 如：`display`
2. 定位属性, 如：`position, top, left, right, bottom, z-index`
3. 盒模型属性, 如：`width, height, margin, padding, border`
4. 字体属性, 如：`font-size, font-weight, font-family`
5. 背景属性, 如：`background-color, opacity`

```css
/** not good **/
.element {
    width: 100px;
    height: 100px;
    font-size: 20px;
    display: inline-block;
    position: relative;
    top: 50px;
    left: 50px;
    border-radius: 5px;
    z-index: 5;
    background: #fff;
    margin: 10px;
    padding: 20px;
}

/** better **/
.element {
    display: block;
    position: relative;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 5;
    width: 100px;
    height: 50px;
    margin: 10px;
    padding: 20px;
    border-radius: 5px;
    font-size: 20px;
    background: #fff;
}
```

### 数值与长度单位

**长度单位**

尽量使用`px、rem、%`。禁止使用比如`(in、pt、pc、mm、cm)`等其他不常用的数值单位
```css
/* not good */
.element {
	margin-top: 10pc;
	width: 20pt;
}

/* good */
.element {
	margin-top: 10px;
	width: 20px;
}
```

**颜色值**

颜色`16进制`用小写字母，用简写代替。

```css
/* not good */
.element {
    color: #ABCDEF;
    background-color: #001122;
}

/* good */
.element {
    color: #abcdef;
    background-color: #012;
}
```

**多余的数值**

去掉小数点前面的`0`
```css
/* not good */
.element {
    color: rgba(0, 0, 0, 0.5);
}

/* good */
.element {
    color: rgba(0, 0, 0, .5);
}
```
属性值`0`后面不要加单位
```css
/* not good */
.element {
    width: 0px;
}

/* good */
.element {
    width: 0;
}
```
用 `border: 0;` 代替 `border: none;`
```css
/* not good */
.element {
    border: none；
}

/* good */
.element {
   border: 0;
}
```

### 选择器

只有在必要的时候才将 class 限制在最近的父元素内
```css
/* not good */
.element-a > .element-b > .element-c {
  padding-top: 0;
  padding-bottom: 0;
  line-height: 40px;
}

/* good */
.element-a .element-b .element-c {
  padding-top: 0;
  padding-bottom: 0;
  line-height: 40px;
}
```

**class 嵌套**

嵌套层数控制再`3层`最大不超过`6层`, 进行合理区分。
```css
/* not good */
.parent > .child > div:first-child > table tr:first-child td {
  padding-top: 0;
  padding-bottom: 0;
  line-height: 40px;
}

/* good */
table.some-tablexs tr:first-child td {
  padding-top: 0;
  padding-bottom: 0;
  line-height: 40px;
}
```

**多个选择器同一份样式**

在一个规则声明中应用了多个选择器时，每个选择器独占一行。
```css
/* not good */
.customer-detail > div:first-child > table tr:first-child, .order-detail > div:first-child > table tr:first-child, .other-detail > div:first-child > table tr:first-child {
   background-color:#FFF; 
}

/* good */
.customer-detail > div:first-child > table tr:first-child, 
.order-detail > div:first-child > table tr:first-child, 
.other-detail > div:first-child > table tr:first-child {
   background-color:#fff; 
}
```

**ID选择器**

尽量少用`ID`选择器去书写样式，`class`选择器就足够用。
```css
/* not good */
#element .content p {
	display: inline-block;
}

/* good */
.element .content p {
	display: inline-block;
}
```

**禁止对纯元素选择器设置特定样式**

除非是样式reset需要，禁止对纯元素选择器设置特定样式，避免样式污染

```css
/* 会导致页面所有的a标签都被加上背景 */
a {
    background: url(xxx);
}

 /* 后期修改可能会添加一些span标签，如果刚好在div里面，会被污染；不利于后期维护 */
div span {
    display: block;
}
```


### 格式化

css属性，每一条属性独占一行

`/* not good */`
```css
.statistics-table td { padding: 0; line-height: 52px; width: 520px; color: #333333; font-family: '宋体'; font-size: 14px;  }
.goods-info { margin-top: 10px; margin-bottom: 10px; border-top: 1px solid #dddddd; }
.goods-info .form-section{ margin-bottom: 10px; color: #333333; border-bottom: 1px solid #dddddd; }
```

`/* good */`
```css
.goodsinfo-top-section .top-section-content .icon {
    display: inline-block;
    margin: 0 10px;
    width: 26px;
    height: 26px;
    vertical-align: middle;
    background-image: url("/assets/images/icon.png");
}
```
**空格符**
- 在规则声明的左大括号` { `前加上一个空格
- 在属性的冒号 `: `后面加上一个空格，前面不加空格
- 规则声明的右大括号 } 独占一行
- 规则声明之间用空行分隔开

```css
/* not good */
.element p {
	width:60px;
	height :50px;
}

/* good */
.element p {
	width: 60px;
	height: 50px;
}
```

### CSS属性

**z-index**
- 自己写的`z-index`的值不能超过 100 (通用组的除外);
- 页面中的元素内容的`z-index`不能超过10(popup poptip除外)，需要按照内容定义1 2 3 4不允许直接使用如1000，9999;
- `modal， toast, notice, popup, poptip`等通用组件的`z-index`需要按照内容使用 99以下，10以上的值（11,12,13，也可以小于10），不允许直接使用1000，9999之类大值;

**font-family**

- 使用`单引号`或`双引号`去括起来
> **提示**：移动端页面不需要设置微软雅黑、宋体等字体，终端浏览器字体取决于设备上的系统字体。
```css
/* not good */
body {
	font-family: 宋体, 黑体, 'Microsoft YaHei';
}

/* good */
body {
  font-family: 'Microsoft YaHei', '黑体', '\5b8b\4f53';
}
```

**background-image**
- background-image 的 url 内使用引号
- 如果路径里面有空格，旧版 IE 是无法识别的，会导致路径失效，建议不管是否存在空格，都添加上单引号或者双引号：
```css
/** not good **/
.element {
    background-image: url(/assets/images/icon.png);
}

/** better **/
.element {
    background-image: url('/assets/images/icon.png');
}
```

**!important**

- 尽量避免使用`!important`。
