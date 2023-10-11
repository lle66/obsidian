# 概念
K8S，就是基于docker容器的集群管理平台
kubesphere  Rancher 是搭建一个K8S环境的 容器管理平台可视化工具 ，一个Pod代表着集群中运行的一个进程
# 基本操作
1. 拉取镜像文件
```
docker pull ubuntu
```
2. 从镜像运行容器
```
sudo docker run --name [容器名] -p [主机端口]:80  -v [主机禅道目录]:/www/zentaopms -v [主机mysql目录]:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=[数据库密码] -d easysoft/zentao:[镜像标签]
```
3. 查看正在运行的容器
```
docker ps //查看正在运行的容器
docker restart 容器ID  //重启容器
docker stop 容器ID  //暂停容器
docker rm 255306ad2cc7 //移除容器
```
4. 进入容器空间
```
docker exec -it zentao /bin/bash
```



# docker禅道容器迁移方法
方法一：整个docker容器集合一起迁移：A_--B
	1. 停止docker服务
	2. B服务器docker版本跟A服务器保存一致
	3. 将整个docker目录(“/var/lib/docker”)复制到新服务器
	4. 环境变量和其他配置文件的路径
方法二：数据保留https://www.jianshu.com/p/03da97911126
```
2.1 将容器提交成镜像

docker commit -a “humingfeng” cid  
2.2 保存镜像到tar包

docker save imagesid > xxx.tar  
2.3 导出镜像并上传到目的服务器  
2.4 加载镜像并运行

docker load < xxx.tar  
2.5 数据恢复  
2.2.1 有管理员账号（docker如果没有将目录挂载出来，那么需要docker cp方式移动文件）  
管理员登录并点击后台，选择备份，最后进行备份
```
看看这篇文章https://www.jianshu.com/p/a59618c1bd66