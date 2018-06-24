@(开发规范)

# JS 规范

### 命名规则
***

**描述性**

避免单字母命名，命名应具备描述性。
```js
// bad
let p = 1;
function q () {
  	// .code
}

// good
let page = 1;
function query () {
	// code
}
```
**驼峰式**

使用`驼峰式(小驼峰，首字母小写)`命名对象、函数和实例
```js
// bad
const OBJWhat = {};
const this_is_my_object = {};
function c () {}

// good
const thisIsMyObject = {};
function thisIsMyFunction () {}
```

**帕斯卡式**

使用`帕斯卡式(大驼峰，首字母大写)`命名构造函数或类
```js
// bad
function person (options) {
  	this.name = options.name;
}

const person = new person({
  	name: 'better',
});

// good
class Person {
	constructor(options) {
		this.name = options.name;
	}
}

const person = new Person({
  	name: 'better',
});
```
**文件名与类名**

如果文件默认导出一个类或react组件时使用大驼峰命名，`文件名`必须和`类名`完全保持一致。
```js
// file contents
class CheckBox {
  	// code
}
export default CheckBox;

// in some other file
// bad
import CheckBox from './checkBox';

// bad
import CheckBox from './check_box';

// good
import CheckBox from './CheckBox';
```
**文件名与函数名**

如果文件默认导出函数时使用小驼峰式命名。`文件名`必须和`函数名`完全保持一致。
```js
function myDefaultFunction() {
	// code
}

export default myDefaultFunction;
```

### 变量
***

#### 变量的声明

**const**

对所有的引用使用 `const`；不要使用 `var`。
> 能确保你无法对引用重新赋值，也不会导致出现 bug 或难以理解。
```js
// bad
var a = 1;
var b = 2;


// good
const a = 1;
const b = 2;
```

**let**

如果你一定需要可变动的引用，使用` let `代替 `var`。
```js
// bad
var count = 1;
if (true) {
  	count += 1;
}

// good
let count = 1;
if (true) {
  	count += 1;
}
```
 

### 常量
***

`const` 声明常量，使用大写字母来命名，下划线来组合`_`
```js
// bad
var successCode = 1;

// good
const SUCCESS_CODE = 1;
```

### 数组与对象
***

**声明方式**

统一使用`字面量`的形式去声明（创建）
```js
// bad
const ownObj = new Object()
const ownArr = new Array()

// good
const ownObj = {}
const ownArr = []
```

**浅复制**

使用扩展运算符`...`进行对象和数组的浅复制
```js
// Array
const oldArr = [];
const newArr = [...oldArr];

// Object
const oldObj = {a: 1, b: 3};
const newObj = {...oldObj, c: 4};

```

**对象的方法和属性**

使用简写的属性和方法，这样更短更有描述性。
简写的属性，应该写在开头。
```js
// bad
const otherValue = 2;
const obj = {
	value: 1,
	otherValue: otherValue，
	addValue: function (value) {
		return obj.value + value;
	}
};

// good
const obj = {
	otherValue,
	value: 1,
	addValue(value) {
		return obj.value + value;
	}
};
```

**数组的解构**

使用数组的解构来存取某个值。
```js
// bad
const ownArr = [1, 2, 3, 4];
const first = ownArr[0]
const two = ownArr[1]

// good 
const {first, two} = ownArr
```

### 字符串
***

字符串超过 `80 `个字节应该使用字符串连接号换行
```js
// bad
const errorMessage = 'This is a super long error that was thrown because of Batman. When you stop to think about how Batman had anything to do with this, you would get nowhere fast.';

// good
const errorMessage = 'This is a super long error that was thrown because ' +
  	'of Batman. When you stop to think about how Batman had anything to do ' +
  	'with this, you would get nowhere fast.';
```
字符串和变量拼接时，使用模板字符串
```js
 // bad
function sayHi (name) {
  	return 'How are you, ' + name + '?';
}

// good
function sayHi (name) {
  	return `How are you, ${name}?`;
}
```


### 类型转换
***

**字符串**

```js
//  => this.reviewScore = 9;

// bad
const totalScore = this.reviewScore + '';

// good
const totalScore = String(this.reviewScore);
```

**数字**

对数字使用 `parseInt `转换，并带上类型转换的基数。
```js
const inputValue = '4';

// bad
const val = new Number(inputValue);

// bad
const val = +inputValue;

// bad
const val = parseInt(inputValue);

// good
const val = Number(inputValue);

// good
const val = parseInt(inputValue, 10);
```

**布尔**

```js
const age = 0;

// bad
const hasAge = new Boolean(age);

// good
const hasAge = Boolean(age);

// good
const hasAge = !!age;
```

### 判断条件
***

**嵌套**

> 嵌套层数太深，代码阅读性太差。容易把自己绕进去，应进行合理的方式组织代码结构。

**if...elsae**

使用`if ... else...`最大嵌套层数应该不超过二层。

**三元操作符**

禁止使用嵌套的 `三元操作符 (? :)`。
```js
// not good
let value = 0;
status === 1 ?  value = 1 : status === 2 ?  value = 2  :  status = 3

// better
let value = 0;
if (status === 1) {
  	value = 1;
} else if (status === 2) {
  	value = 2;
} else {
  	value = 3;
}

```

**|| 与 &&**

当混合使用`||`操作符和`&&`操作符，合理的使用`()`进行分组。
```js
// bad
 code === 1 && status === 2 || payCode === 3 && payStatus === 4

// good
(code === 1 && status === 2) || (payCode === 3 && payStatus === 4)
```

### 格式化
***

**缩进**

使用 `4个`空格作为缩进。
```js
// bad
function () {
∙∙const name;
}

// bad
function () {
∙const name;
}

// good
function () {
∙∙∙∙const name;
}
```

**缩进**

在花括号前放一个空格。
```js
// bad
function test () {
  	console.log('test');
}

// good
function test () {
  	console.log('test');
}

// bad
dog.set('attr',{
	age: '1 year',
	breed: 'Bernese Mountain Dog',
});

// good
dog.set('attr', {
	age: '1 year',
	breed: 'Bernese Mountain Dog'
});
```

在控制语句`（if、while 等）`的小括号前放一个空格。在函数调用及声明中，不在函数的参数列表前加空格。

```js
// bad
if(passed) {
	fight ();
}

// good
if (passed) {
	fight();
}

// bad
function fight() {
  	console.log ('Swooosh!');
}

// good
function fight () {
  	console.log('Swooosh!');
}
```
使用空格把运算符(`— + = * / % === !== || && `)隔开。
```js
// bad
const x=y+5;
const z= a===b&&c===d

// good
const x = y + 5;
const z = a === b && c === d
```

### 请求数据

返回一个promise, 可以使用async/await同步写法

```js
fetch('/userLogin', {
	method: 'POST',
	headers: {
		'Content-Type': 'application/json'
	},
	body: JSON.stringify({
		name: 'better',
		password: '123456',
	})
});

async handleUserLogin () {
	let result = await userLogin({
		name: 'better',
		password: '123456',
	});
	if (result) {
		// code
	}
}
```
### 更多JS规范，请参考

- [eslint](http://eslint.cn/)
- [standard规范](https://github.com/standard/standard/blob/master/docs/RULES-zhcn.md)
