## meta
### viewport：用于移动端显示优化的
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	视口是网页的用户可见区域。它因设备而异——它在手机上会比在电脑屏幕上小。
	这为浏览器提供了有关如何控制页面尺寸和缩放比例的说明。
	`width=device-width`部分将页面宽度设置为遵循设备的屏幕宽度（这将因设备而异）。
	`initial-scale=1.0`当浏览器首次加载页面时，该部分设置初始缩放级别。

### http-equiv 属性
相当于http的文件头作用，它可以向浏览器传回一些有用的信息，以帮助正确和精确地显示网页内容
	-  Expires(期限)
		可以用于设定网页的到期时间。一旦网页过期，必须到服务器上重新传输。
		 <meta http-equiv="Expires" content="0">//设置每次访问都需要请求最新html代码
	- content-Type设定页面使用的字符集
		- HTML5已经不需要使用 http-equiv 规定 HTML 文档的字符集：
		-  HTML 4.01： <meta http-equiv="content-type" content="text/html; charset=UTF-8">
		-  HTML5： <meta charset="UTF-8">
		
	- 定义文档自动刷新的时间间隔。
		<meta http-equiv="refresh" content="300"> 每300s刷新一次文档
		 "refresh" 应该慎重使用，因为它会使得页面不受用户控制
	
	-  Pragma(cache模式)
		用于设定禁止浏览器从本地机的缓存中调阅页面内容，设定后一旦离开网页就无法从Cache中再调出
		<meta http-equiv="Pragma" content="no-cache"> 
	- Set-Cookie(cookie设定)
		如果网页过期，那么存盘的cookie将被删除
		<meta http-equiv="Set-Cookie" content="cookievalue=xxx;expires=Wednesday, 20-Jun-2007 22:33:00 GMT； path=/">
	- keywords### 关键字,给搜索引擎用
		<meta http-equiv="keywords" content="keyword1,keyword2,keyword3">
	- X-UA-Compatible 设置浏览器兼容模式
		<meta http-equiv="X-UA-Compatible" content="IE=Edge,chrome=1">
		IE=edge告诉IE使用最新的引擎渲染网页，chrome=1则可以激活Chrome Frame.

## Spring MVC的标签库
	Spring FORM可在JSP页面中渲染HTML元素的标签  标签库,Spring MVC提供了一个JSP标签库（Spring Form），使将表单元素绑定到Model 数据变得更加容易(数据绑定，数据模型定义的工作给了后端代码？)
	
#### 属性值：
	表单标签除了具有 HTML 表单元素属性以外，还具有 acceptCharset、commandName、cssClass、cssStyle、htmlEscape 和 modelAttribute 等属性。mvc标签的两个重要属性
	1. commandName: form绑定的模型属性名称，默认为command
	2. modelAttribute: form绑定的模型属性名称，默认为command
	```
	<mvc:form/>
	<mvc:input/>
	<mvc:password/>
	<mvc:hidden/>
	<mvc:textarea/>
	```
#### 具体使用
	1. 将 form 表单与模型数据进行绑定，通过 modelAttribute 属性完成绑定，将 modelAttribute 的值设置为模型数据对应的 key 值。
	```
	Handeler:modelAndView.addObject("student",student);
	JSP:
	<%@ taglib prefix="mvc"  uri="http://www.springframework.org/tags/form" %>
	<form:form modelAttribute="student">]
	```
	2. form 表单完成绑定之后，将模型数据的值取出绑定到不同的标签中，通过设置标签的 path 属性完成，将 path 属性的值设置为模型数据对应的属性名即可。
	```
	<form:input path="id"/><br/>
	<form:input path="name"/><br/>
	<form:input path="age"/><br/>
	```