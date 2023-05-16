RuoYi是一款基于SpringBoot+Bootstrap的极速后台开发框架。内置模块如：部门管理、角色用户、菜单及按钮授权、数据权限、系统参数、日志管理、通知公告等
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

### maven 
项目管理工具，配合自建的本地库和国内镜像来使用速度也得以提升，能够大大减少我们平时建立项目时导包的麻烦。

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

4. idea设置maven路径 setting-->bulid toos---修改仓库所在位置
	Maven项目自带一个pom.xml,这是项目的设置文件，pom.xml中的dependencies部分就是添加依赖的地方
5. 新建项目/已新建项目右键重新加载maven
6. 解决maven Could not find artifact org.apache.maven.plugins:maven
```
https://blog.csdn.net/qq_54737884/article/details/122429754
maven---importing以及Runner下添加证书后重启
-Dmaven.wagon.http.ssl.insecure=true -Dmaven.wagon.http.ssl.allowall=true
```

### nacos
一个更易于构建云原生应用的动态服务发现、配置管理和服务管理平台Windows启动命令
1. 本地开发下windows版本：https://github.com/alibaba/nacos/releases/tag/1.4.0
2. 新建nacos数据库
3. 打开conf下的application.properties文件，修改数据库连接
```
db.url.0=jdbc:mysql://127.0.0.1:3306/nacos?characterEncoding=utf8&connectTimeout=1000&socketTimeout=3000&autoReconnect=true
&useUnicode=true&useSSL=false&serverTimezone=UTC
db.user=root
db.password=root
```
2. 修改单机模式
	如果不是部署nacos集群,则将模式修改为单机模式, 打开bin/startup.cmd 文件，将MODE从cluster改为 standalone
3. 启动
	修改完后双击bin/startup.cmd文件
	打开浏览器访问：http://localhost:8848/nacos/index.html



相关技术
1. 