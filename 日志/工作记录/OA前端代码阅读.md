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
-  JSP表达式 ：使用`<%= xxx %>`则可以快捷输出一个变量的值。
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
- taglib 项目中用于多语言实现: 中文、英文、繁体


## 二、web代码结构
- WebRoot
	- META-INF ----存放应用程序元信息MANIFEST.MF
	- WEB-INF ----核心目录，存放JSP页面和Web应用程序配置页面
		- app---各个功能模块JSP文件
		- classes---编译后的文件
		- lib----web应用所需JAVA库和Jar文件
		- login---登录jsp文件
		- web.xml----web配置文件
	- ui
		- css----各个模块样式文件
		- file----包括各种文件模板
		- fonts---字体文件
		- img----存放图片文件
		- js------各模块以及依赖库js
		- lib-----引入ui库代码

## 三、项目依赖库
-  1. Spring MVC 表单标签库Tag
项目中用于多语言实现: 中文、英文、繁体
	```
	<%@taglib prefix="fmt" uri="http://www.springframework.org/tags" %> 
	<fmt:message code="main.th.AllPasswordsEmpty"/>
	```
-  2.  jsencrypt.js进行RSA加密
	应用场景是在用户注册或登录的时候，用公钥对密码进行加密，再去传给后台，后台用私钥对加密的内容进行解密，然后进行密码校验或者保存到数据库。
	- RSA
		RSA加密算法是一种非对称加密算法，RSA加密使用了"一对"密钥.分别是公钥和私钥,这个公钥和私钥其实就是一组数字。其长度越长其加密强度越大,目前为止公之于众的能破解的最大长度为768位密钥,只要高于768位,相对就比较安全.所以目前为止,这种加密算法一直被广泛使用.
	- RSA加密与解密
		使用**公钥**加密的数据,利用**私钥**进行解密
		使用**私钥**加密的数据,利用**公钥**进行解密
	- jsencrypt就是一个基于rsa加解密的js库
	```javascript
	// 加密
	var result = encryptPadding();//向后端请求公钥/利用工具网站在线生成秘钥
	var encryptor = new JSEncrypt();// 创建加密对象实例
	encryptor.setPublicKey(result);// 设置公钥
	var pwd = encryptor.encrypt($('#password').val());// 对内容进行加密
	//解密
	  var decrypt = new JSEncrypt()//创建解密对象实例
	  //之前ssl生成的秘钥
	  var priKey  = '-----BEGIN RSA PRIVATE KEY-----xxx-----END RSA PRIVATE KEY----'
	  decrypt.setPrivateKey(priKey)//设置秘钥
	  var uncrypted = decrypt.decrypt(encrypted)//解密之前拿公钥加密的内容
``` 
- 3. JQuery JavaScript 函数库
-  4. qrcode.min.js生成二维码
```js
$('#qrcode').qrcode({
	render: "canvas",//设置渲染方式(有两种方式 table和canvas，默认是canvas）
	width: 100,//二维码宽
	height:100,//二维码高        
	text:''//二维码内容(不支持中文…据说是UTF-16格式的编码,中文的话需要转换下, 要不然是乱码)
 });
```
- 5. ztree  “树插件”
- 6.swiper 实现页面轮播
- 7. echart 图表
- 8. easyui
- 9......