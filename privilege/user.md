新增用户
```
useradd -d /home/java -m java
```
设置密码
```
passwd java
```

## 改变目录属性
![目录原属性](https://github.com/muxianliangqin/learn-note-of-linux/blob/main/privilege/images/%E7%9B%AE%E5%BD%95%E6%9D%83%E9%99%90.png)
```
chown [-R] 属主名：属组名 文件名

chown -R java:java config/
```
-R：递归更改文件属组
