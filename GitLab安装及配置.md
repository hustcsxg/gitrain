**1.UBUNTU服务器安装Docker**

```plain
curl -fsSL https://get.docker.com -o get-docker.sh
chmod +x get-docker.sh
./docker.sh
systemctl enable docker
```

**2.安装GitLab**

```plain
docker pull gitlab/gitlab-ce:13.6.3-ce.0
mkdir -p /home/gitlab/config
mkdir -p /home/gitlab/data
mkdir -p /home/gitlab/logs
docker run -d  -p 8443:443 -p 8000:8000 -p 5122:22 --name gitlab --restart always -v /home/gitlab/config:/etc/gitlab -v /home/gitlab/logs:/var/log/gitlab -v /home/gitlab/data:/var/opt/gitlab gitlab/gitlab-ce
```
**3. 配置修改**

```plain
vim /home/gitlab/config/gitlab.rb
# 文尾最后加入
external_url "http://192.168.0.115:8000"
gitlab_rails['gitlab_shell_ssh_port']=5122
gitlab_rails['smtp_enable'] = true
gitlab_rails['smtp_address'] = "smtp.163.com"
gitlab_rails['smtp_port'] = 25
gitlab_rails['smtp_user_name'] = "xxx@163.com"
gitlab_rails['smtp_password'] = "xxxx客户端访问密码非登录邮箱密码"
gitlab_rails['smtp_domain'] = "163.com"
gitlab_rails['smtp_authentication'] = "login"
gitlab_rails['smtp_enable_starttls_auto'] = true
gitlab_rails['smtp_tls'] = false
gitlab_rails['gitlab_email_from'] = "xxx@163.com"
user["git_user_email"] = "xxx@163.com"
```
****
**4. 重启服务**

```plain
docker exec -ti gitlab /bin/bash
gitlab-ctl reconfigure
```
**5. ToDoList**

配置https配置slacks配置域名

**6. 踩坑记录**

1. AWS EC2实例 中国区节点限制80，443,8080端口，需要备案

2. AWS EC2实例 SMTP邮件服务器25，456等端口限制，需要人工申请开通，只配置安全组无用！！！中国节点不支持SES邮件服务。。。

7. **日常维护**
1. 查看日志

docker logs -f -t --tail=10 gitlab

2. 注意不要全局关闭cicd否则无法创建新项目。单个项目创建后去关闭cicd
