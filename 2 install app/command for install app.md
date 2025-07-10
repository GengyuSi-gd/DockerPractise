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

### 2、安装tomcat
```
　　#拉取镜像
　　[root localhost docker]#docker pull tomcat
　　#创建容器运行
　　[root localhost docker]#docker run-d-p 8080:8080--name mytomcat tomcat
　　#测试访问（记得关闭防火墙此时会发现访问成功出现404响应，原因是webapps下面没有资源）
　　ip:8080
　　#进入容器 可以使用容器名称或容器id
　　[root localhost docker]#docker exec-it mytomcat/bin/bash
　　#将webapps.dist下的内容复制到webapps下面，重新访问即可看到正常页面
　　root ebef54554573:/usr/local/tomcat#cp-r webapps.dist/*webapps/
　　#部署项目到tomcat
　　[root localhost docker]#docker cp demo.war mytomcat:/usr/local/tomcat/webapps/
　　#重启tomcat容器
　　[root localhost docker]#docker restart mytomcat
```

 