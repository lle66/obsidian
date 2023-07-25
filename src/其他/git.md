## ssh密钥生成
ssh-keygen -t rsa -C "xxx@xxx.com"
cat ~/.ssh/id_rsa.pub
验证：ssh -T git@github.com

git 修改远程仓库
	git remote rm origin（删除远程地址）
	git remote add origin [url]

## Mac密钥报错
1. 可能网络有关，开了代理
2. git ssh 密钥生成规则github官网做了更新,
```
ssh-keygen -t ed25519 -C "your_email@example.com" //生成新规则密钥

eval "$(ssh-agent -s)" //在后台启动 ssh 代理

open ~/.ssh/config //检查你的 `~/.ssh/config` 文件是否在默认位置，若不在touch ~/.ssh/config
粘贴一下内容到config文件
Host github.com
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_ed25519

ssh-add ~/.ssh/id_ed25519 //将 SSH 私钥添加到 ssh-agent

pbcopy < ~/.ssh/id_ed25519.pub //粘贴到GitHub中添加ssh

//如果还是失败，可尝试：
ssh -vT git@github.com //尝试连接到 `git@github.com` 来检查使用的密钥
```



