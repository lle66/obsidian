
基于 CentOS 7 下安装配置 Nginx 操作实践记录整理。
### 一、配置 EPEL 源

```javascript
sudo yum install -y epel-release
sudo yum -y update
```

### 二、安装 Nginx

```javascript
sudo yum install -y nginx
```

安装成功后，默认的网站目录为： /usr/share/nginx/html
默认的配置文件为：/etc/nginx/nginx.conf
自定义配置文件目录为: /etc/nginx/conf.d/

### 三、开启端口 80 和 443
如果你的[服务器](https://cloud.tencent.com/act/pro/promotion-cvm?from_column=20065&from=20065)打开了防火墙，你需要运行下面的命令，打开 80 和 443 端口。
```javascript
sudo firewall-cmd --permanent --zone=public --add-service=http
sudo firewall-cmd --permanent --zone=public --add-service=https
sudo firewall-cmd --reload


firewall-cmd --zone=public --add-port=1935/tcp --permanent //开启指定端口
```

### 命令
```java
systemctl start nginx //启动nginx
nginx -t //检查配置报错
nginx -s reload //重新加载配置
// Nginx的配置文件位于/etc/nginx/nginx.conf
```

## 以下是一个简单的Nginx配置文件：

```text
http {
    server {
        listen 80;
        server_name Example Domain;

        location / {
            root /var/www/example/dist;
            index index.html;
        }
    }
}
```

 HTTPS配置
如果需要使用HTTPS协议提供安全的访问，需要进行HTTPS配置。以下是一个简单的HTTPS配置示例：

```java
http {
    server {
        listen 80;
        server_name Example Domain;

        location / {
            root /var/www/example/dist;
            index index.html;
        }

        return 301 https://$server_name$request_uri;
    }

    server {
        listen 443 ssl;
        server_name Example Domain;

        ssl_certificate /path/to/cert.pem;
        ssl_certificate_key /path/to/key.pem;

        location / {
            root /var/www/example/dist;
            index index.html;
        }
    }
}
```
## 报错解决
如果是使用默认的hash模式，可以正常刷新，然而在history模式下，刷新出现404的错误
web单页面开发模式，只有一个index.html入口，其他路径是前端路由去跳转的，没有对应这个路径，所以就会报404了
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

**代理访问失败connect() to 10.10.103.4:8080 failed (13: Permission denied) while connecting to upstream

setsebool -P httpd_can_network_connect 1

## 纪委小程序nginx老配置
```
load_module /usr/lib/nginx/modules/ngx_stream_module.so;
worker_processes auto;
events {
    worker_connections  1024;
    accept_mutex on;
  }
http {
  include mime.types;
  default_type application/octet-stream;
  server {
    server_name chat.2shoufang.org.cn;
    listen 19999 ssl http2;
    ssl_certificate /home/nginxWebUI/cert/chat.2shoufang.org.cn.pem;
    ssl_certificate_key /home/nginxWebUI/cert/chat.2shoufang.org.cn.key;
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2 TLSv1.3;
    location /notice/ {
      proxy_pass http://127.0.0.1:30016/notice/;
      proxy_set_header Host $host;
      proxy_set_header X-Real-IP $remote_addr;
      proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      proxy_set_header X-Forwarded-Host $http_host;
      proxy_set_header X-Forwarded-Port $server_port;
      proxy_set_header X-Forwarded-Proto $scheme;
    }
    location /jwn-notice {
      proxy_pass http://127.0.0.1:30009;
      proxy_set_header Host $host;
      proxy_set_header X-Real-IP $remote_addr;
      proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      proxy_set_header X-Forwarded-Host $http_host;
      proxy_set_header X-Forwarded-Port $server_port;
      proxy_set_header X-Forwarded-Proto $scheme;
    }
  }
  server {
    listen 81;
    location /prod-api/ {
      proxy_pass http://127.0.0.1:30016/;
      proxy_set_header Host $host;
      proxy_set_header X-Real-IP $remote_addr;
      proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      proxy_set_header X-Forwarded-Host $http_host;
      proxy_set_header X-Forwarded-Port $server_port;
      proxy_set_header X-Forwarded-Proto $scheme;
    }
    location / {
      root /opt/web/notice-web/dist;
      index index.html;
    }
  }
}

```