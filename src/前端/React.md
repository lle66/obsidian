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
1. 样式名=全局样式， 局部样式呢，----也可使用scss\less,
2. 变量值的更新，除了使用state，不能直接赋值吗-----这个useState相当于vue的data初始化变量值
3. 子组件与父组件通信，可传递事件作为子组件参数
4. 更分的明白 ，哪里做什么事情
5. 主组件的方法调用了两次是为什么？ 每次改变绑定变量都能掉两次？跟变量的数量无关
6. 函数内部调用上一层作用域的变量 只在初始化生效
7. 数组更新后，马上调用长度不刷新
```
setHistory([...history, nextSquares]);
history.length没有变化
```
8. tsx,,使用ts 的一些语法
```ts
1. 
	const [enabled, setEnabled] = useState<boolean>(false);
2. 取集合
	type Status = "idle" | "loading" | "success" | "error";  
	const [status, setStatus] = useState<Status>("idle");
3. 对象描述分组
	type CounterAction =
	  | { type: "reset" }
	  | { type: "setCount"; value: State["count"] }
function stateReducer(action: CounterAction){}
stateReducer({ type: "reset" })
5. 使用`type` 或 `interface` 描述的对象类型
	interface MyButtonProps {
	  title: string;
	  disabled: boolean;
	};
	function MyButton({ title, disabled }: MyButtonProps){}


```
9. `useReducer`怎么用，， react 的ts规则有点难理解。
# 编程思想
1. 将页面组件拆成成组件层级结构，组件即函数，元素即变量
2. 识别哪些是state（改变state实现可响应）
https://zh-hans.react.dev/learn/thinking-in-react



# redux
Redux 帮你管理“全局”状态 - 应用程序中的很多组件都需要的状态。
相当于vuex
setXxxx( 函数 ) -----
## action
描述应用程序中发生了什么的事件。是一个具有 `type` 字段的普通 JavaScript 对象。
```js
const addTodoAction = {  
type: 'todos/todoAdded',   // 域/事件名
payload: 'Buy milk'  //附加信息
}
```
## Action Creator
创建并返回一个 action 对象的函数。它的作用是让你不必每次都手动编写 action 对象。
```js
const addTodo = text => {  
	return {  
	type: 'todos/todoAdded',  
	payload: text  
	}  
}
```
## Reducer
**reducer** 是一个函数，接收当前的 `state` 和一个 `action` 对象。 **reducer 是一个事件监听器，它根据接收到的 action（事件）类型处理事件。
(state, action) => newState

更新 state 的唯一方法是调用 `store.dispatch()` 并传入一个 action 对象, store 将执行所有 reducer 函数并计算出更新后的 state，调用 `getState()` 可以获取新 state
```js
const increment = () => {  
	return {  
	type: 'counter/increment'  
	}  
}
store.dispatch({ type: 'counter/increment' })
//store.dispatch(increment)
console.log(store.getState())
```


# DvaJS
