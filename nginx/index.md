## centos8系统
- 安装 `yum -y install nginx`
- 启动 `service nginx start`
## ubuntu系统
- 安装 `sudo apt install nginx`
- 启动 `sudo systemctl start nginx`  
- 状态查看 `sudo systemctl status nginx`

## 启动之后可以使用 `nginx` 来操作
- 版本号 `nginx -v`
- 重新加载 `sudo nginx -s reload`

### 其他
- 默认配置文件：`/etc/nginx/nginx.conf`
- 日志路径 `/var/log/nginx`
- 配置文件 `/etc/nginx/sites-available/default`  
[default](./default)

