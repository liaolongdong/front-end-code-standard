@(开发规范)

# CSS 规范

### css样式引入方式

- 推荐使用link引入外部css样式文件到`head`标签中
- 避免使用`@import`引入样式
- 避免使用内联样式

### class命名空间

 - 页面采用`p-`的命名空间，比如`p-home, p-about, p-pay`, p = page;
 <br />
 - 通用的组件使用`c-`的命名空间。 比如`c-popup, c-nav, c-slidebar`, c = component;
 <br />
 - 通用工具类的统一使用`t-`的命名空间。比如`t-clearfix, t-ellipsis`, t = tool;
 <br />
 - 状态类的使用`s-`的命名空间。 比如： `s-current, s-active` s = status;
 <br />
 - js钩子类的使用`j-`的命名空间。一般用于需要提供给ios，类似于用于写业务逻辑。使用了react，除非必要，不要使用。 比如： `j-name， j-doc`。 j = javascrpt.
 <br />
 -  这种命名方式，最多只能拥有俩个破折号，即`p-about-head`。页面下其他的功能，依次向下类推，
 比如`about`页面的`head`区域有个`sell`的类名，推荐使用`about-head-sell`这样的风格去命名。
 
 > **注意**：类名的命名方式，应该以语义化为前提，不要出现类似取每个汉字首字母拼音的方式命名，不利于阅读和维护。

**所有的class命名以此为标准，全部采取英文小写, 尽量避免使用`数字`，不允许出现`大写`和类似`_拼接`和`驼峰命名法`**

### 数值与长度单位
***

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
***

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
.element p{
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

**font-family**

使用`单引号`或`双引号`去括起来
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

**!important**

不要使用`!important`。
