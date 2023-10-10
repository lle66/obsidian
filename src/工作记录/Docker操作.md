https://www.runoob.com/docker/docker-container-usage.html
1. 拉取镜像文件
```
docker pull ubuntu
```
2. 从镜像运行容器
```
sudo docker run --name [容器名] -p [主机端口]:80  -v [主机禅道目录]:/www/zentaopms -v [主机mysql目录]:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=[数据库密码] -d easysoft/zentao:[镜像标签]
```
2. 查看正在运行的容器
```
docker ps
```
3. 重启容器
```
docker restart 容器ID
```


docker 安装的目录在哪里



K8S，就是基于容器的集群管理平台

kubesphere  Rancher 是搭建一个K8S环境的可视化工具