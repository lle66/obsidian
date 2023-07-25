
### 1. publicPath: 设置静态资源打包所在的目录

-  ``publicPath: '/'，使用绝对路径，即默认配置
![[Pasted image 20230516150542.png]]
- ``publicPath: './'，使用相对路径，不用服务器就能启动进行访问的index.html
![[Pasted image 20230516151501.png]]


- **总结**: 使用相对路径，可以看到只是比绝对路径在静态资源访问上少了 '/'，这样的优点就是可以让当前应用被部署在任意目录，而不必担心静态资源有丢失的情况。比如本地访问。
如果服务器上的应用被部署到http://www.xxxx.xxx/test/,则需要设置publicPath:'/test'
```
module.exports = {
  publicPath: process.env.NODE_ENV === 'production'
    ? '/test/'
    : '/'
}
```