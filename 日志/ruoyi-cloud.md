RuoYi-Cloud是一款基于Spring Boot、Spring Cloud & Alibaba、Vue、Element的前后端分离微服务极速后台开发框架。
##  环境搭建

```
JDK >= 1.8 (推荐1.8版本)
Mysql >= 5.7.0 (推荐5.7版本)
Redis >= 3.0
Maven >= 3.0
Node >= 12  //直接安装最新版会无法启动，使用12.16.0
nacos >= 1.1.0 (ruoyi-cloud >= 3.0.0需要下载nacos >= 2.x.x版本)
sentinel >= 1.6.0
```

### Maven 
项目管理工具，配合自建的本地库和国内镜像来使用速度也得以提升，能够大大减少建立项目时导包的麻烦。

1. 配置环境变量（maven3.3.9）
```
MAVEN_HOME  D:\tools\apache-maven-3.3.9 配置系统变量
%MAVEN_HOME%\bin 配置Path新建 
mvn -v 查看是否配置成功
```

2. 设置maven使用镜像，国内镜像速度更快 (不必须)
```
//conf/setting.xml
<mirror>
    <id>alimaven</id>
    <mirrorOf>central</mirrorOf>
    <name>aliyun maven</name>
    <url>http://maven.aliyun.com/nexus/content/repositories/central/</url>
</mirror>
```

3. setting.xml 修改仓库所在地址 (不必须)
```text
<localRepository>D:\toos\apache-maven-3.6.3\repository</localRepository>
```

4. idea设置maven路径 setting-->bulid tools---修改仓库所在位置
	Maven项目自带一个pom.xml,这是项目的设置文件，pom.xml中的dependencies部分就是添加依赖的地方
5. 新建项目/已新建项目右键重新加载maven
6. 解决maven Could not find artifact org.apache.maven.plugins:maven
```
https://blog.csdn.net/qq_54737884/article/details/122429754
maven---importing以及Runner下添加证书后重启
-Dmaven.wagon.http.ssl.insecure=true -Dmaven.wagon.http.ssl.allowall=true
```

### Redis
Redis 是一个高性能的key-value数据库，很大程度补偿了memcached这类key/value存储的不足。
1. 启动redis:   
	``redis-server.exe redis.windows.conf   //redis-server.exe：服务端程序，提供 redis 服务
2. 执行操作
	`redis-cli.exe -h 127.0.0.1 -p 6379 //另开一个cmd窗口
	redis-cli.exe: ,redis命令行工具 ，执行redis命令
3. 退出
	通过在redis-server中按下 【ctrl+c】正常退出redis，redis就会将内存中数据持久化到硬盘上，下次在连接的时候还在。

### Nacos
Nacos可以实现微服务的服务发现、服务配置、服务元数据及流量管理。可以帮助我们更敏捷和容易地构建、交付和管理微服务平台。
1. 本地开发下windows版本：https://github.com/alibaba/nacos/releases/tag/1.4.0
2. 运行sql脚本，ry-config数据库
3. 打开conf下的application.properties文件，修改数据库连接
```
spring.datasource.platform=mysql
db.num=1
db.url.0=jdbc:mysql://localhost:3306/ry-config?characterEncoding=utf8&connectTimeout=1000&socketTimeout=3000&autoReconnect=true&useUnicode=true&useSSL=false&serverTimezone=UTC
db.user=root
db.password=xxx
```
2. 修改单机模式
	如果不是部署nacos集群,则将模式修改为单机模式, 打开bin/startup.cmd 文件，将MODE从cluster改为 standalone
3. 启动
	修改完后双击bin/startup.cmd文件
	打开浏览器访问：http://localhost:8848/nacos/index.html

4. nacos控制台编辑配置
	从上往下挨个编辑，把设计到连接Mysql和Redis的所有地方，改为自己对应的用户名和密码。
	ruoyi-system-dev.yml
	ruoyi-gen-dev.yml
	ruoyi-job-dev.yml


6. 运行（在启动nacos、redis的前提下）
	Idea找到文件，右键一个个运行（（启动没有先后顺序））,启动成功后，可在nacos服务列表中查看。
	-   RuoYiGatewayApplication （网关模块 必须）
	-   RuoYiAuthApplication （认证模块 必须）
	-   RuoYiSystemApplication （系统模块 必须）
	-   RuoYiMonitorApplication （监控中心 可选）
	-   RuoYiGenApplication （代码生成 可选）
	-   RuoYiJobApplication （定时任务 可选）
	-   RuoYFileApplication （文件服务 可选）
7. 运行ruoyi-ui项目
	npm install
	npm run dev
8. 访问 http://localhost   整个项目本地启动完成。

## 项目结构

### 1. 整体项目结构
com.ruoyi 
|── ruoyi-ui              // 前端框架 [80]
├── ruoyi-gateway         // 网关模块 [8080]
├── ruoyi-auth            // 认证中心 [9200]
├── ruoyi-api             // 接口模块
│       └── ruoyi-api-system                          // 系统接口
├── ruoyi-common          // 通用模块
│       └── ruoyi-common-core                         // 核心模块
│       └── ruoyi-common-datascope                    // 权限范围
│       └── ruoyi-common-datasource                   // 多数据源
│       └── ruoyi-common-log                          // 日志记录
│       └── ruoyi-common-redis                        // 缓存服务
│       └── ruoyi-common-seata                        // 分布式事务
│       └── ruoyi-common-security                     // 安全模块
│       └── ruoyi-common-swagger                      // 系统接口
├── ruoyi-modules         // 业务模块
│       └── ruoyi-system                              // 系统模块 [9201]
│       └── ruoyi-gen                                 // 代码生成 [9202]
│       └── ruoyi-job                                 // 定时任务 [9203]
│       └── ruoyi-file                                // 文件服务 [9300]
├── ruoyi-visual          // 图形化管理模块
│       └── ruoyi-visual-monitor                      // 监控中心 [9100]
├──pom.xml                // 公共依赖


### 2. 前端项目结构
 ruoyi-ui
├── build                // 项目构建(webpack)相关代码
├── bin                   // 批处理文件
├── node_modules // npm 加载的项目依赖模块
├── public               // 存放静态资源，存放在该文件夹的东西不会被打包影响
├── src                    // 开发目录
│       └── api                          // 各模块请求
│       └── assets                     // 静态资源
│       └── components          // 公共组件
│       └── directive                 // 指令
│       └──layout                      // 主体框架组件
│       └── router                     //路由相关配置
│       └── store                       // vuex状态数据
│       └── plugin                     // 插件js
│       └── utils                        // 全局公共js工具
│       └── views                      // 存放各模块页面组件
│       └── App.vue                  // 路由组件的顶层路由
│       └── main.js                    // 入口文件
├──.editorconfig     //不同的编辑器和IDE之间定义和维护一致的编码样式规范
├──.gitignore         //git忽略的文件列表
├──.env.xxx            // 环境配置文件
├──package.json    // 应用包配置文件
├──vue.config.js     //可选的配置文件,被 @vue/cli-service 自动加载


## 相关技术
1.  scss   ​​css​​​ 预编译语言
2. axios 基于 promise 的 HTTP 库
3. vuex 应用共享状态
4. vue-router vue路由配置管理
5. element-ui  ui库
6. echarts 图表实现
7. screenfull 浏览器全屏插件
8. quill 富文本编辑器
9. clipboard 复制粘贴功能
10. jsencrypt 加密
11. vue-treeselect 树形结构
...

## 二次封装组件
- Pagination分页组件
- RightToolbar自定义表格工具组件
- Editor 富文本组件
- FileUpload 文件上传组件
- ImageUpload 图片上传组件
- ImagePreview 图片预览组件
- DictTag 字典标签组件
- DictData 字典数据组件


## 路由
- 静态路由
	代表那些不需要动态判断权限的路由，如登录页、404、等通用页面，在@/router/index.js

- 动态路由
 代表那些需要根据用户动态判断权限并通过`addRoutes`动态添加的页面。
	1. 动态路由可以在系统管理-菜单管理进行新增和修改操作，在@/store/modules/permission.js 请求接口获取菜单信息并转换成前端对应的路由,。
	2. 也可在@/router/index.js可手动加一些复杂规则的动态路由。
	加了菜单后要重启本地服务才生效。

## 权限

封装了一个指令权限，能简单快速的实现按钮级别的权限判断。
	1. 使用权限字符串 v-hasPermi
	2. 使用角色字符串 v-hasRole  //某个角色才有的权限
	3. 手动设置v-if：如元素标签组件，不适合使用v-hasPermi， 可以使用全局权限判断函数：checkPermi, checkRole

## 请求
axios 封装位置@/utils/request.js 统一处理 POST，GET 等请求参数，请求头，以及错误提示信息等
	封装了全局 request拦截器、response拦截器、统一的错误处理、统一做了超时处理、baseURL设置等，如果有自定义错误码可以在errorCode.js中设置对应key value值

## 页面缓存

编写路由 router 和路由对应的 view component 的时候一定要确保 两者的 name 是完全一致的，菜单设置的路径匹配组件的 **name**，必须唯一