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