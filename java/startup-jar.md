## jar包启动服务

### maven 打包(跳过测试用例)
```
mvn clean package -Dmaven.test.skip=true
```
首次运行会下载依赖的jar，可能会耗时较长，等待完成

## 启动Spring Cloud 分布式服务
注册中心**eureka**

1. 启动server

`nohup java -jar ***.jar >/home/java/logs/config-server.log 2>&1 &`