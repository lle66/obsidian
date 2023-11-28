### 安装
```shell
sudo curl --output /usr/local/bin/gitlab-runner https://gitlab-runner-downloads.s3.amazonaws.com/latest/binaries/gitlab-runner-linux-amd64
gitlab-runner install --user=root --working-directory=/home/gitlab-runner
设置权限----文件权限问题，直接使用root权
# sudo useradd --comment 'GitLab Runner' --create-home gitlab-runner --shell /bin/bash
# sudo chmod +x /usr/local/bin/gitlab-runner
chown -R root:root /usr/local/bin/gitlab-runner
运行
gitlab-runner start
注册（貌似要把runner 停掉才有用）
gitlab-runner register  --url http://10.10.104.216:8080  --token glrt-do29zMJcCmekWXqJYDnt
```


### 报错
测试命令打包后---资源文件不显示 ----node版本问题？----nginx配置问题？10.16能修复图标问题以及import问题  14.17.5也可以，-----16.18.1 图片恢复正常？？

 gitlab地址连接失败，如何去修改ip配置----改了gitlab配置
 gitlab报错fatal: unable to access 'http://gitlab-ci-token:[MASKED]------项目成员把自己加进去


fatal: git fetch-pack: expected shallow list,fatal:----setting--ci/cd 第一项展开git clone 勾上

npm 拉包速度慢-----改完镜像之后---跑不起来了------装minio包7.0.18----node_modules 缓存问题 ----要删缓存包！