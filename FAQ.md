# FAQ清单
```
Attention: 常见问题清单如下，更多问题可在issue中提问，通用统一记录到此处
```
## 1. 
```angular2html
1. 生成ssh-key
ssh-keygen -t rsa -C "email@xxxxx.com" 

2. 产生的密钥文件上传github或gitlab


3. 增加配置文件
vim ~/.ssh/config

Host xm_gitee.com
HostName gitee.com
User xiaoming
Port 22
IdentityFile ~/.ssh/id_rsa_xm

# 公司私有gitlabdizhi
Host gitlab.xxx.cn 或 私有gitlab IP
Port 2222
HostName gitlab.xxx.cn 或 私有gitlab IP
User yourusername
IdentityFile ~/.ssh/id_rsa_xxx

Host github.com
port 22
user yourgithubusername
IdentityFile ~/.ssh/id_rsa_github

4. 设置用户名，邮箱, 不同项目指定对应的user.name 及user.email

git config --global --unset user.name
git config --global  user.name=xxx

git config --global --unset user.email
git config --global user.email=xx@xx.com

```