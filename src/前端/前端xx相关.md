
## 一、业务相关
**做过哪些项目+承担的角色+实现了哪些功能+涉及到哪些技术（框架、js库、UI库）
 1. 做过哪些项目：后台管理系统（角色与权限 路由管理  请求封装  登录授权 单点登录）、小程序、大屏(echart GIS  三维建模)

### 1. 1 具体技术点
1. 登录相关流程     前置路由守卫----浏览器本地存储有哪几种 有什么区别？  token的有效时间     
2. 如何做的角色权限、菜单权限、按钮权限控制（自定义指令用过吗 ） --前端再怎么做权限控制都不是绝对安全的，后端的权限验证是逃不掉的
3. 请求接口权限控制--`axios`请求拦截器进行拦截

## 二、知识点

### js 基础
3. 讲DOM事件模型，如何阻止事件冒泡
4. Promise
5. JavaScript原型，原型链
6. 闭包
7. 事件循环
8. 箭头函数跟其他函数有什么不一样
9. 口述如何创建一个ajax
10. 深拷贝和[浅拷贝](https://www.zhihu.com/search?q=%E6%B5%85%E6%8B%B7%E8%B4%9D&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra=%7B%22sourceType%22%3A%22article%22%2C%22sourceId%22%3A%22151728272%22%7D)的区别？
### css  html基础
1. 实现两栏布局有哪些方法
2. css 盒模型有哪些

### vue基础 
5. .如何获取dom  
6. .说出几种[vue](https://www.zhihu.com/search?q=vue&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra=%7B%22sourceType%22%3A%22article%22%2C%22sourceId%22%3A%22151728272%22%7D)当中的指令和它的用法？  
7. 为什么使用key
- [vue笔面试题汇总(上篇)](https://juejin.cn/post/7208005892313579576?searchId=20240509091507AF92B4EEA19A5A75C852#heading-1 "vue笔面试题汇总(上篇)")
    - [1. 谈一谈对 MVVM 的理解？](https://juejin.cn/post/7208005892313579576?searchId=20240509091507AF92B4EEA19A5A75C852#heading-2 "1. 谈一谈对 MVVM 的理解？")
    - [2. 说一下 Vue 的优点](https://juejin.cn/post/7208005892313579576?searchId=20240509091507AF92B4EEA19A5A75C852#heading-3 "2. 说一下 Vue 的优点")
    - [3. 解释一下对 Vue 生命周期的理解](https://juejin.cn/post/7208005892313579576?searchId=20240509091507AF92B4EEA19A5A75C852#heading-4 "3. 解释一下对 Vue 生命周期的理解")
    - [4. Vue 实现双向数据绑定原理是什么？](https://juejin.cn/post/7208005892313579576?searchId=20240509091507AF92B4EEA19A5A75C852#heading-5 "4. Vue 实现双向数据绑定原理是什么？")
    - [5. 说一下对 Vue2.x 响应式原理的理解](https://juejin.cn/post/7208005892313579576?searchId=20240509091507AF92B4EEA19A5A75C852#heading-6 "5. 说一下对 Vue2.x 响应式原理的理解")
    - [6. 说一下在 Vue2.x 中如何检测数组的变化？](https://juejin.cn/post/7208005892313579576?searchId=20240509091507AF92B4EEA19A5A75C852#heading-7 "6. 说一下在 Vue2.x 中如何检测数组的变化？")
    - [7. Vue3.x 响应式数据](https://juejin.cn/post/7208005892313579576?searchId=20240509091507AF92B4EEA19A5A75C852#heading-8 "7. Vue3.x 响应式数据")
    - [8. v-model 双向绑定的原理是什么？](https://juejin.cn/post/7208005892313579576?searchId=20240509091507AF92B4EEA19A5A75C852#heading-9 "8. v-model 双向绑定的原理是什么？")
    - [9. vue2.x 和 vuex3.x 渲染器的 diff 算法分别说一下？](https://juejin.cn/post/7208005892313579576?searchId=20240509091507AF92B4EEA19A5A75C852#heading-10 "9. vue2.x 和 vuex3.x 渲染器的 diff 算法分别说一下？")
    - [10. vue 组件的参数传递](https://juejin.cn/post/7208005892313579576?searchId=20240509091507AF92B4EEA19A5A75C852#heading-11 "10. vue 组件的参数传递") vue 各种组件通信方法（父子 子父 兄弟 爷孙 毫无关系的组件） 
    - [11. Vue 的路由实现](https://juejin.cn/post/7208005892313579576?searchId=20240509091507AF92B4EEA19A5A75C852#heading-12 "11. Vue 的路由实现")
    - [12. vuex 是什么？怎么使用它？什么场景下我们会使用到 vuex](https://juejin.cn/post/7208005892313579576?searchId=20240509091507AF92B4EEA19A5A75C852#heading-13 "12. vuex 是什么？怎么使用它？什么场景下我们会使用到 vuex")
    - [13. 说一下 v-if 与 v-show 的区别](https://juejin.cn/post/7208005892313579576?searchId=20240509091507AF92B4EEA19A5A75C852#heading-14 "13. 说一下 v-if 与 v-show 的区别")
    - [14. 如何让 CSS 值在当前的组件中起作用](https://juejin.cn/post/7208005892313579576?searchId=20240509091507AF92B4EEA19A5A75C852#heading-15 "14. 如何让 CSS 值在当前的组件中起作用")
    - [15. keep-alive 相关](https://juejin.cn/post/7208005892313579576?searchId=20240509091507AF92B4EEA19A5A75C852#heading-16 "15. keep-alive 相关")
    - [16. Vue 中如何进行组件的使用？Vue 如何实现全局组件的注册？](https://juejin.cn/post/7208005892313579576?searchId=20240509091507AF92B4EEA19A5A75C852#heading-17 "16. Vue 中如何进行组件的使用？Vue 如何实现全局组件的注册？")
    - [18. nextTick 的作用是什么？他的实现原理是什么？](https://juejin.cn/post/7208005892313579576?searchId=20240509091507AF92B4EEA19A5A75C852#heading-19 "18. nextTick 的作用是什么？他的实现原理是什么？")
    - [20. Vue 组件的 data 为什么必须是函数](https://juejin.cn/post/7208005892313579576?searchId=20240509091507AF92B4EEA19A5A75C852#heading-21 "20. Vue 组件的 data 为什么必须是函数")
    - [21. 说一下 Vue 的 computed 的实现原理](https://juejin.cn/post/7208005892313579576?searchId=20240509091507AF92B4EEA19A5A75C852#heading-22 "21. 说一下 Vue 的 computed 的实现原理")
    - [23. vue 如何快速定位那个组件出现性能问题的]
    - [24. Proxy 相比 defineProperty 的优势在哪里](https://juejin.cn/post/7208005892313579576?searchId=20240509091507AF92B4EEA19A5A75C852#heading-25 "24. Proxy 相比 defineProperty 的优势在哪里")
    - [25. Vue 与 Angular 以及 React 的区别是什么？]
    - [26. 说一下 watch 与 computed 的区别是什么？以及他们的使用场景分别是什么？](https://juejin.cn/post/7208005892313579576?searchId=20240509091507AF92B4EEA19A5A75C852#heading-27 "26. 说一下 watch 与 computed 的区别是什么？以及他们的使用场景分别是什么？")
    - [27. scoped 是如何实现样式穿透的？](https://juejin.cn/post/7208005892313579576?searchId=20240509091507AF92B4EEA19A5A75C852#heading-28 "27. scoped 是如何实现样式穿透的？")

## 浏览器
1. 缓存机制：强缓存、协商缓存（Last-Modified 或者 ETag）--如何解决版本更新问题，在文件名中添加 hash
2. 本地存储方式有哪些？对比
3. histoty跟hash有什么区别？深层区别--基于H5新增的pushState()和replaceState()两个api，实现路由页面更新。
4. 12. 前后端通信：同源策略：协议域名端口。通信方式：ajax(同源策略下的通信方式) websocket（不受同源策略控制） CORS（支持跨域也支持同源）----实现跨域的方式
5. 请求  有使用哪些状态码
6. 浏览器渲染过程
## 三、 高级
1. 内存泄漏的可能情况： 闭包使用不当引起内存泄漏 全局变量 分离的DOM节点 控制台的打印 遗忘的定时器
2. webpack如何实现打包的（构建流程）
3. jenkins自动化部署 实现
4. nginx配置
5. web安全问题有哪些--csrf  xss -如何防范

## 四、如何对项目进行优化
### 4.1 项目优化：

1. 打包体积（通过externals加载外部CDN资源，图片svg图片或者字体图标）
2. 加载速度（路由懒加载，webpack懒加载，图片的懒加载，虚拟列表）
3. 请求大小（开启gzip压缩，减少对cookie的使用）
4. 请求数量（善用本地存储，合并图片)
5. 骨架屏,进度条（vue的骨架屏插件vue-skeleton-webpack-plugin）

### 4.2 代码优化
1. 事件代理
2. 事件的节流和防抖-----节流跟防抖应用在什么场景   有什么区别？
3. 页面的回流和重绘
4. EventLoop事件循环机制
5. 少使用闭包
6. CSS 放在文件头部，JavaScript文件放在底部，async和defer
7. vue的代码：computed 和 watch，v-if 和 v-show，v-for ，合理组件化

## 排查问题
1. 页面卡顿
	- 先会检查是否是网络请求太多，导致数据返回较慢，可以适当做一些缓存
	- 也有可能是某块资源的bundle太大，可以考虑拆分一下
	- 然后排查一下js代码，是不是某处有过多循环导致占用主线程时间过长
	- 浏览器某帧渲染的东西太多，导致的卡顿
	- 在页面渲染过程中，可能有很多重复的重排重绘
	- 内存泄漏引起的-


# 项目中遇到什么难题
遇到什么兼容性问题如何解决


# 小程序
1. 微信小程序生命周期：应用生命周期(onLaunch全局触发一次、onShow、onHide、onError)、页面生命周期（onLoad、onShow、onReady、onHide）、组件生命周期(created加载、attached、ready初次渲染完成)

2. 常见的微信小程序页面跳转方式有如下：
	- wx.navigateTo(Object)
	- wx.redirectTo(Object)
	- wx.switchTab(Object)
	- wx.navigateBack(Object)
	- wx.reLaunch(Object)
3. 提示小程序性能的手段有哪些？---可以从加载、渲染两个维度进行切入
	加载：
	 - 及时清理无用的代码和资源文件、压缩代码体积、图片资源使用网络下载
	- 分包加载：将用户访问率高的页面放在主包里，将访问率低的页面放入子包里，按需加载
	渲染
	-  不要过于频繁调用setData，应考虑将多次setData合并成一次setData调用
	- 骨架屏
4. 如何实现登录----wx.login获取code---->后端请求微信服务器获取解密信息(获取用户信息等等) 或者输入手机号及短信验证码进行登录
5. 发布流程：上传代码、提交审核、发布版本
6. 支付流程：小程序需要将购买的商品Id，商品数量，以及用户的openId传送到服务器------->服务器生成服务期订单数据，同时经过一定的签名算法，向微信支付发送请求，获取到签名信息向小程序端响应必要的信息----->小程序端在获取对应的参数后，调用wx.requestPayment()发起微信支付----->展示支付结果
# 移动端
## 安卓
- 通信 – 网络连接（HttpClient，HttpUrlConnetion），Socket
- 据持久化 – SQLite，SharedPreferences，ContentProvider
- 性能优化 – 布局优化，内存优化，电量优化
- 安全 – 数据加密，代码混淆，WebView/Js调用，https
- 四大组件
- 设计模式： mvc mvp mvvm
- https://cloud.tencent.com/developer/article/2089359
## iOS
1. tableView 有什么好的性能优化方案？
2. 如何降低APP包的大小？
3. 启动时间如何优化
4. 谈谈你对离屏渲染的理解？
5. iOS中数据持久化方案有哪些？
	NSUserDefault 简单数据快速读写
	Property list (属性列表)文件存储
	Archiver (归档)
	SQLite 本地数据库
	CoreData（是iOS5之后才出现的一个框架，本质上是对SQLite的一个封装，它提供了对象-关系映射(ORM)的功能，即能够将OC对象转化成数据，保存在SQLite数据库文件中，也能够将保存在数据库中的数据还原成OC对象，通过CoreData管理应用程序的数据模型）
https://www.jianshu.com/p/98f2bacf9fb2


## UI
1. **你接到一个项目后，设计思路是怎么样的？**
2. **iOS和Android的APP设计区别是什么** ？**你之前的项目需要适配哪些版本?你怎么做的?**
3. ## **你是怎么决定一个产品的配色的**
4. 有没有已上线的项目
5. 在 UI 设计中，PC 端和移动端有什么区别？体现在哪些方面
![[Pasted image 20231031175325.png]]

![[Pasted image 20231031175451.png]]
https://www.zhihu.com/tardis/zm/art/40533921?source_id=1003
https://zhuanlan.zhihu.com/p/134111417