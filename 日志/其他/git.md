ssh-keygen -t rsa -C "xxx@xxx.com"
cd ~/.ssh 
cat id_rsa.pub
验证：ssh -T git@github.com

git 修改远程仓库
	git remote rm origin（删除远程地址）
	git remote add origin [url]