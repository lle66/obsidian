# 组件
组件可以是页面的一个小部件，也可以是 一整个页面
1. React 组件是返回标签的 JavaScript 函数
```js
function MyButton() {  
	return (  
	<button>I'm a button</button>  
	);  
}
```
2. 组件的引用，React 组件必须以大写字母开头，而 HTML 标签则必须是小写字母。
```js
export default function MyApp() {  
	return (  
		<div>  
		<h1>Welcome to my app</h1>  
		<MyButton />  
		</div>  
	);  
}
```

3. JSX语法 (html标签放到 JavaScript)
	组件也不能返回多个 JSX 标签。你必须将它们包裹到一个共享的父级中，比如 `<div>...</div>` 或使用空的 `<>...</>` 包裹,
	jsx中使用{}显示变量
```js
return ( 
<div>
	<img className="avatar" src={user.imageUrl} />  
	<span>{user.name}</span>
</div>
);
```
4. 样式添加使用className,  或内联style={{}} 并不是一个特殊的语法，而是 `style={ }` JSX 大括号内的一个普通 `{}` 对象  
5. 条件语句、循环语句先写在js里面，再引用
6. 父子组件事件与变量传递
	```js
	export default function MyApp() {  
		const [count, setCount] = useState(0);  
		function handleClick() {  
		setCount(count + 1);  
		}  
		return (  
		<div>  
		<h1>Counters that update together</h1>  
		<MyButton count={count} onClick={handleClick} />  
		<MyButton count={count} onClick={handleClick} />  
		</div>  
		); 
		// 子组件
		function MyButton({ count, onClick }) {  
			return (  
			<button onClick={onClick}>  
			Clicked {count} times  
			</button>  
			);  
		}
	}
	```


# 实战
![[Pasted image 20230830162722.png]]

# 区别
1. 样式名=全局样式， 局部样式呢
2. 变量值的更新，除了使用state，不能直接赋值吗
3. 子组件与父组件通信，可传递事件作为子组件参数
4. 更分的明白 ，哪里做什么事情
5. 主组件的方法调用了两次是为什么？ 每次改变绑定变量都能掉两次？跟变量的数量无关
6. 函数内部调用上一层作用域的变量 只在初始化生效
7. 数组更新后，马上调用长度不刷新
```
setHistory([...history, nextSquares]);
history.length没有变化
```


# 编程思想
1. 将页面组件拆成成组件层级结构，组件即函数，元素即变量
2. 识别哪些是state（改变state实现可响应）
https://zh-hans.react.dev/learn/thinking-in-react

