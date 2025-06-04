## Docker安装软件
### 1、安装mysql
```
　　#1.搜索镜像search上hub.docker.com搜索
　　[root localhost docker]#docker search mysql
　　#2.拉取镜像pull
　　[root localhost docker]#docker pull mysql:5.7
　　#3、运行测试
　　#-d后台运行
　　#--name给容器命名
　　#-p宿主机端口：容器内部端口
　　[root localhost docker]#docker run-d-p 3355:3306-e MYSQL_ROOT_PASSWORD=root--name mysql1 mysql:5.7
　　#测试 关闭防火墙或授权远程访问 外部连接访问正常
　　#进入容器命令：docker exec-it容器id/bin/bash
　　------------------------------容器启动进行数据挂载-----------------------------
　　#mysql容器正常启动数据挂载成功
　　$docker run-d-p 3344:3306-v/data/mysql/conf:/etc/mysql/conf.d-v/data/mysql/data:/var/lib/mysql-e MYSQL_ROOT_PASSWORD=root--name mysql01 mysql:5.7
　　#开放3344端口及安全组，在容器内部创建用户并授权，测试OK
```