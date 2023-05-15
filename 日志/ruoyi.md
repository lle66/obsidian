RuoYi是一款基于SpringBoot+Bootstrap的极速后台开发框架。内置模块如：部门管理、角色用户、菜单及按钮授权、数据权限、系统参数、日志管理、通知公告等
###  环境搭建

```
JDK >= 1.8 (推荐1.8版本)
Mysql >= 5.7.0 (推荐5.7版本)
Redis >= 3.0
Maven >= 3.0
Node >= 12  //直接安装最新版会无法启动，使用12.16.0
nacos >= 1.1.0 (ruoyi-cloud >= 3.0.0需要下载nacos >= 2.x.x版本)
sentinel >= 1.6.0
```

nacos：一个更易于构建云原生应用的动态服务发现、配置管理和服务管理平台Windows启动命令(standalone代表着单机模式运行，非集群模式):
https://www.jianshu.com/p/419b4d91498a

`startup.cmd -m standalone`

maven3.3.9:配置 
```
https://blog.csdn.net/Small_Tsky/article/details/106870647
配置系统变量MAVEN_HOME  D:\tools\apache-maven-3.3.9
配置Path新建  %MAVEN_HOME%\bin
mvn -v 查看是否配置成功
```




相关技术
1. 