ssh-keygen -t rsa -C "xxx@xxx.com"
cd ~/.ssh 
cat id_rsa.pub
验证：ssh -T git@github.com

```text
npm config set registry http://registry.npmmirror.com

//下载nvm控制nodejs版本
nvm ls 查看已有
nvm install v10.16.0 //安装版本
nvm use 10.16.0
nvm uninstall vXX
```