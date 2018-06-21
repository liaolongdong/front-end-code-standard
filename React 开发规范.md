@(开发规范)

# React 开发规范

#### 绑定this

统一使用箭头函数的形式绑定`this`。比如：
```javascript
handleClick = () => {
	//...一些代码
}

<span onClick={this.handleClick()} />
```
如果需要在方法中传递一些值，可以使用箭头函数的形式来实现:
```javascript
<span onClick={() => {
	this.handleClick(param1, param2)
}} />
```

#### 纯组件
什么是纯组件，简单来说就是一个只用于展示的数据，完全不需要去改变`props`和`state`的组件，比如：
```javascript
class Hello extends Component {
	render () {
		return (
			<div>
				{ this.props.txt }
			</div>
		)
	}
}

import Hello from './Hello';
class showTxt extends Component {
	render () {
		return (
			<Hello txt={hello world!} />
		)
	}
}
```
这个类的用法很简单，如果你有些组件是`纯组件`，那么把继承类从 `Component` 换成 `PureComponent` 即可。当组件更新时，如果组件的 `props` 和 `state` 都没发生改变，`render` 方法就不会触发，省去 `Virtual DOM` 的生成和比对过程，达到提升性能的目的。这种方式只适用于一些`简单的数据类型`。如果涉及到复杂数据类型`（引用类型数据）`,需要使用`immutable.js`插件,原理就是让原来的`props`发生变化。

#### props验证方式
统一使用对象属性的方式，进行数据类型验证，`static`的方式，无法应用在函数式组件中，为了统一写法。全部采取如下方式：
```javascript
	class A extends Component {
		render() {
			return (
				<div>{ this.props.someTxt }</div>
			);
		}
	}
	A.propTypes = {
		someTxt: PropTypes.String
	};
```
