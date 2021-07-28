rabbitMQ依赖erlang
## 安装erlang
查看erlang的rpm版本
```
http://mirrors.nju.edu.cn/epel/
```
![rabbitmq的rpm版本](https://github.com/muxianliangqin/learn-note-of-linux/blob/main/rabbitmq/images/rabbitmq%E7%9A%84rpm%E7%89%88%E6%9C%AC.png)

这里选择最新版
```
rpm -Uvh http://mirrors.nju.edu.cn/epel/epel-release-latest-8.noarch.rpm
```
[rpm学习] : https://www.runoob.com/linux/linux-comm-rpm.html  

错误：
```
error: can't create transaction lock on /var/lib/rpm/.rpm.lock (Permission denied)
```
需要使用root用户安装
