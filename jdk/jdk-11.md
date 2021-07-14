先使用yum搜索jdk可安装版本
```
yum search java|grep jdk
```
![yum搜索jdk版本](https://github.com/muxianliangqin/Install-software-under-Linux/blob/main/jdk/yum%E6%90%9C%E7%B4%A2jdk%E7%89%88%E6%9C%AC.png)

选定版本，安装
```
yum install -y java-11-openjdk.x86_64
```
> yum [options] [command] [package ...]
> options：可选，选项包括-h（帮助），-y（当安装过程提示选择全部为"yes"），-q（不显示安装的过程）

![yum安装jdk11](https://github.com/muxianliangqin/Install-software-under-Linux/blob/main/jdk/yum%E5%AE%89%E8%A3%85jdk11.png)

等待安装完毕即可。

检查是否jdk版本
```
java -version
```
![查看jdk版本](https://github.com/muxianliangqin/Install-software-under-Linux/blob/main/jdk/%E6%9F%A5%E7%9C%8Bjdk%E7%89%88%E6%9C%AC.png)
