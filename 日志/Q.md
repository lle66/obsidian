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

### vue 语法
1. ``v-bind="$attrs"  v-on="$listeners"
```
子组件,只接收了name和age两个属性，其他属性没有接收，子组件可使用 v-bind="$attrs" 属性，vm.$attrs` 是一个属性，其包含了父作用域中不作为 prop 被识别 (且获取) 的特性绑定 (class 和 style 除外)。这些未识别的属性可以通过 `v-bind="$attrs"` 传入内部组件。未识别的事件可通过`v-on="$listeners"`传入
```

![[1684403546246.png]]

2. v-slot:[name]="data"   简写 #[name]="data"

### 私有云、公有云
一般买的云服务器都算是公有云，比如你部署了一个项目到阿里云，访问ip地址对所有人都是公开的；私有云就是可以设置防火墙等等网络安全策略，限制只有企业内部用户可以使用（可以理解为把本地机房放在云端）

### eslint 
安装esling, ctr+p  查找setting.json 添加一下配置
不生效问题
1. 编辑区下方无明显显示eslint检测-----eslintIngore 里边给忽略了.vue
```js
 //eslint
    "eslint.format.enable": true,
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true
    },
    "eslint.validate": [
        "javascript",
        "javascriptreact",
        "html",
        "vue",
        {
            "language": "html",
            "autoFix": true
            },
            {
            "language": "vue",
            "autoFix": true
            }
    ],
    "eslint.options": { //指定eslint配置文件位置
        "configFile": ".eslintrc.js", //指定项目根目录中的eslint配置文件
        "extensions": [
            ".js",
            ".vue"
        ]
    },
    "editor.defaultFormatter": "dbaeumer.vscode-eslint",
    "editor.formatOnPaste": false, // required
    "editor.formatOnType": false, // required
    "editor.formatOnSave": true, // optional
    "editor.formatOnSaveMode": "file", // required to format on save
    "files.autoSave": "onFocusChange", // optional but recommended
    "vs-code-prettier-eslint.prettierLast": false,
```
### vscode报错解决 类型注释只能在 TypeScript 文件中使用
	 ctr+p  **输入** **"javascript.validate.enable": false**

### el-date-range 报错
Error in v-on handler: "TypeError: Cannot read properties of undefined (reading 'value')"
change方法里面加一层非空判断

## gitlab提交报错
1. RPC failed; curl 56 Recv failure: Connection was reset
git config --global http.sslVerify true
git config --global http.postBuffer 524288000

2. gitlab Permission denied, please try again.-----


## 小程序
1.  **app.json: app.json 未找到**
	"miniprogramRoot": "./unpackage/dist/dev/mp-weixin/",


## nginx
1. 刷新页面404
web单页面开发模式，只有一个index.html入口，其他路径是前端路由去跳转的，[nginx](https://so.csdn.net/so/search?q=nginx&spm=1001.2101.3001.7020 "nginx")没有对应这个路径，所以就会报404了
```
location / {
    try_files $uri $uri/ /index.html;
    }
```

```
//完整写法
  server {
    listen 81;
    location / {
      root /opt/web/notice-web/dist;
      try_files $uri $uri/ /index.html;
    }
    location /prod-api {
      proxy_pass https://127.0.0.1:19999/;
      proxy_set_header Host $host;
      proxy_set_header X-Real-IP $remote_addr;
      proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      proxy_set_header X-Forwarded-Host $http_host;
      proxy_set_header X-Forwarded-Port $server_port;
      proxy_set_header X-Forwarded-Proto $scheme;
    }
  }
```


## 使用vpn后某些ip地址被限制访问

1. 使用vpn是改了哪些系统配置？
	vpn: 虚拟个人网咯，比如我现在在中国的机器A，我有另一台机器B在美国，通过把B一堆配置可以将其包装为一台VPN服务器，A与B直接可以建立一条私密连接，请求过程B会给A生成一个虚拟IP。
	当你发送请求访问外部网站时，请求首先发送到VPN服务器。VPN服务器会解密请求并将其转发到外部网络。外部网络将响应发送回VPN服务器，然后再通过加密的隧道将响应传输回你的设备。

2. 关闭了VPN连接后，为什么有些ip还是被限制了？+浏览器之前一直重复访问123网址，中毒？还是浩哥在服务器设置了上传文件限制？还是我自己的代理问题？
3. 网址打不开了是什么原因？