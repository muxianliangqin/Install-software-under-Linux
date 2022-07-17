### yum安装
```
sudo apt-get install -y git
```
如果报错：
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package git is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'git' has no installation candidate
```
对apt升级 `sudo apt-get update` 再执行
查看git版本
```
git --version
```
