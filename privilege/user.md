### 查看所有用户
```
cat /etc/passwd
```
### 新增用户
```
useradd -d /home/java -m java
```
* -d 目录 指定用户主目录，如果此目录不存在，则同时使用-m选项，可以创建主目录

### 设置密码
```
passwd java
```

## 改变目录属性
![目录原属性](images/目录属性.png)
```
chown [-R] 属主名：属组名 文件名

chown -R java:java config/
```
-R：递归更改文件属组
