### mysql安装失败重装：
	1. 以管理员身份运行，输入sc delete MySQL80删除服务，删除sql相关注册表，点击安装程序移除mysql; 删除c盘下各种sql相关
	2. 计算机--->右键--->管理。找到mysql，右键属性点击登录，允许服务于桌面交互
	navicat 导入数据库报错---`birthday` date NOT NULL DEFAULT '2005-06-08' COMMENT '生日',
	3. 缺少网络权限？？--win+R键输入compmgmt.msc进入，计算机管理-系统工具-本地用户和组-组-Administrators，点击“添加”，在输入对象名称来选择栏，输入NETWORK SERVICE->点击检查名称->确认。

### navicat运行sql脚本报错
1. 配置my.in  innodb_strict_mode=0  再输入命令 show variables like '%innodb_strict_mode%';看是否为off
2. sql-mode="ONLY_FULL_GROUP_BY,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION"

### IDea意外关闭，重新启动端口占用问题
	//列出所有端口占用情况
	netstat -ano
	//找到被占用的端口对应的PID
	netstat -ano|findstr "6644"
	//杀死进程
	tasklist|findstr "PID"