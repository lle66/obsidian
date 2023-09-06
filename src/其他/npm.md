### yarn安装
```
npm install --global yarn
```
### taobao镜像
有些包，国内镜像拉取会报错(包不同步、包缺少)，建议恢复原始地址

```text
npm config set registry http://registry.npmmirror.com 
npm install -g cnpm --registry=https://registry.npm.taobao.org

//恢复npm官方
 npm_ config set registry https://registry.npmjs.org/
```

### 下载nvm控制nodejs版本

```
nvm ls 查看已有
nvm install v10.16.0 //安装版本
nvm use 10.16.0
nvm uninstall vXX

uniapp小程序用的node 14.17.5
react切换成12.16.0
```

n 14.17.5

# 问题
1. 拉取一个新项目，第一次装包失败，之后的装包很难成功？-----淘宝镜像的锅（有的可能是node版本与包版本不兼容）
2. 