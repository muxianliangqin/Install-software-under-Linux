## 使用指南

### 启用后台管理
```
rabbitmq-plugins enable rabbitmq_management
```
* 默认用户 `guest` 只能localhost登录，需要新增用户
### 查看当前所有用户
```
rabbitmqctl list_users
```
### 查看用户权限
```
rabbitmqctl list_user_permissions ${user}
```
### 新增用户
```
rabbitmqctl add_user ${user} ${password} 
```
### 设置用户tag
```
rabbitmqctl set_user_tags ${user} ${tag}
```
### 设置用户权限
```
rabbitmqctl set_permissions -p / ${user}  '.*' '.*' '.*'
```
访问 `http://47.106.140.189:15672/` 输入账号密码登录
