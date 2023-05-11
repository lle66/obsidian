ssh-keygen -t rsa -C "xxx@xxx.com"
cd ~/.ssh 
cat id_rsa.pub
验证：ssh -T git@github.com