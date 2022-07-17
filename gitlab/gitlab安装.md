## gitlab安装
### 首先信任 GitLab 的 GPG 公钥
- `curl https://packages.gitlab.com/gpg.key 2> /dev/null | sudo apt-key add - &>/dev/null`
### 添加清华源
- `cd /etc/apt/sources.list.d/`
- 新建文件 `sudo touch gitlab-ce.list`
- 编辑 `sudo vim sudo vim /etc/apt/sources.list.d/gitlab-ce.list`
- 写入内容：`deb https://mirrors.tuna.tsinghua.edu.cn/gitlab-ce/ubuntu focal main`
### 安装
- `sudo apt-get update`
- `sudo apt-get install gitlab-ce`

**参考[Gitlab Community Edition 镜像使用帮助](https://mirrors.tuna.tsinghua.edu.cn/help/gitlab-ce/)**

### 启动gitlab
- 先执行配置 `sudo gitlab-ctl reconfigure` 等待执行完成
- 启动 `sudo gitlab-ctl start`
- 查看状态 `sudo gitlab-ctl status`

**[gitlab Maintenance commands](https://docs.gitlab.com/omnibus/maintenance/index.html#get-service-status)**

### 登陆主页
url：`http://localhost:80`  
账号：`root`
- 密码  
`sudo cat /etc/gitlab/initial_root_password`  
密码就是： `Password: xxx`
- 登陆之后修改新密码即可

### 配置邮箱发送邮件
`sudo vim /etc/gitlab/gitlab.rb`
进入按 `i` -> 按 `ESC` -> 按 `G` -> 按 `enter` 到文件最后一行，添加一下配置： 
```
gitlab_rails['smtp_enable'] = true
gitlab_rails['smtp_address'] = "smtp.qq.com"
gitlab_rails['smtp_port'] = 465
gitlab_rails['smtp_user_name'] = "你的QQ号@qq.com"
gitlab_rails['smtp_password'] = "QQ邮箱授权码"
gitlab_rails['smtp_domain'] = "smtp.qq.com"
gitlab_rails['smtp_authentication'] = "login"
gitlab_rails['smtp_enable_starttls_auto'] = true
gitlab_rails['smtp_tls'] = true
gitlab_rails['gitlab_email_from'] = "你的QQ号@qq.com"
```
刷新gitlab配置 `gitlab-ctl reconfigure`
测试是否配置成功
- `gitlab-rails console`
- `Notify.test_email('你的QQ号@qq.com', '邮件主题', '邮件内容').deliver_now` 
- 查看邮件
**[SMTP#qq-exmail](https://docs.gitlab.com/omnibus/settings/smtp.html#qq-exmail)**
### 配置 nginx监听端口
- `sudo vim /etc/gitlab/gitlab.rb` 最后一行 添加 `nginx['listen_port'] = 8088` 保存  
- 执行 `gitlab-ctl reconfigure`即可
