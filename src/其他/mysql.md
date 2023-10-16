1. 修改密码win+s搜索mysql ,输入密码（如果秒退要检查服务是否被手动关闭了）  
	ALTER USER ‘root’@’localhost‘ IDENTIFIED BY ‘新密码’;

### mysql: command not found解决
这个是因为/usr/local/bin目录下缺失mysql导致，只需要一下方法建立软链接，即可以解决：  
把mysql安装目录，比如MYSQLPATH/bin/mysql，映射到/usr/local/bin目录下： 
```
cd /usr/local/bin  
ln -fs /MYSQLPATH/bin/mysql mysql
```