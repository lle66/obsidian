## 一、JSP( Java Servlet Pages)
### 1. 基础语法
JSP 技术允许在页面中嵌套 java 代码，为用户提供动态数据。
- JSP 字面量
	-   布尔值(boolean)：true 和 false;
	-   整型(int)：与 Java 中的一样;
	-   浮点型(float)：与 Java 中的一样;
	-   字符串(string)：以单引号或双引号开始和结束;
	-   Null：null。
-  JSP声明  一个声明语句可以声明一个或多个变量、方法，供后面的Java代码使用
	``<%! int i = 0; %>
-   注释：包含在`<%--`和`--%>`之间的是JSP的注释，它们会被完全忽略；
-   包含在`<%`和`%>`之间的是Java代码，可以编写任意Java代码；
	```html
	<%! int day = 3; %>
	<html>
	<% if (day == 1 || day == 7) { %>
	      <p>今天是周末</p>
	<% } else { %>
	      <p>今天不是周末</p>
	<% } %>
	</html>
	```
	
	```html
	<%! int fontSize; %> 
	<!DOCTYPE html>
	<body>
	<h3>For 循环实例</h3>
	<%for ( fontSize = 1; fontSize <= 3; fontSize++){ %>
	   <font color="green" size="<%= fontSize %>">
	    循环实例
	   </font><br />
	<%}%>
	```
-   jsp表达式 ：使用`<%= xxx %>`则可以快捷输出一个变量的值。
- JSP页面内置了几个变量：
	-   out：表示HttpServletResponse的PrintWriter；
	-   session：表示当前HttpSession对象；
	-   request：表示HttpServletRequest对象。
-  中文编码问题
	如果要在页面正常显示中文，可在 JSP 文件头部添加以下代码：
	`<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>`


### 2. JSP指令
|指令|描述|
|---|---|
|<%@ page import="java.io.*" %> |定义页面的依赖属性，可以通过`page`指令引入Java类|
|<%@ include file="header.jsp"%>|使用`include`指令可以引入另一个JSP文件|
|<%@ taglib ... %>|引入标签库的定义，可以是自定义标签|
- taglib
	# Spring MVC的标签库
	
	Spring FORM可在JSP页面中渲染HTML元素的标签  标签库,Spring MVC提供了一个JSP标签库（Spring Form），使将表单元素绑定到Model 数据变得更加容易
	``<%@ taglib prefix="mvc"  uri="http://www.springframework.org/tags/form" %>
	引入标签声明之后就可使用Spring表单标签
```html
<mvc:form/>
<mvc:input/>
<mvc:password/>
<mvc:hidden/>
<mvc:textarea/>
<mvc:radiobutton/>
<mvc:checkbox/>
<mvc:select/>
<mvc:error/>
```
	mvc标签的两个重要属性
	-   commandName
> 	form绑定的模型属性名称，默认为command
	-   modelAttribute
> 	form绑定的模型属性名称，默认为command
	`<fmt:message>`标签将键映射到本地化消息并执行参数替换
	`<%@taglib prefix="fmt" uri="http://www.springframework.org/tags" %> 

## 二、代码结构
![[1683788110565.png]]
