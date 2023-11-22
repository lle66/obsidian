## 命令
```java
sudo apt-get update
sudo apt-get install nginx //安装nginx
systemctl start nginx //启动nginx
nginx -t //检查配置报错
nginx -s reload //重新加载配置
// Nginx的配置文件位于/etc/nginx/nginx.conf

```

以下是一个简单的Nginx配置文件：

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