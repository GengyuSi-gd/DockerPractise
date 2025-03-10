## Docker命令
### 1、帮助命令
```
　　docker version #显示docker的版本信息。
　　docker info #显示docker的系统信息，包括镜像和容器的数量
　　docker --help #帮助命令
    docker-compose version
```
![alt text](image.png)


### 2、镜像命令
需要先在windows上打开docker desktop运行docker

```
docker images#查看所有本地主机上的镜像可以使用docker image ls代替
Usage:docker images[OPTIONS][REPOSITORY[:TAG]]
-q#只显示镜像id
-a#列出本地所有镜像（含中间映像层）
--digests#显示镜像的摘要信息
--no-trunc#显示镜像完整信息
[root VM_0_5_centos~]#docker images-a
REPOSITORY TAG IMAGE ID CREATED SIZE
docker.io/hello-world latest bf756fb1ae65 5 months ago 13.3 kB
```
```
　docker search#搜索镜像
　　Usage:docker search[OPTIONS]TERM
　　-f#根据指定条件删选镜像
　　[root VM_0_5_centos~]#docker search mysql-f stars=5000#搜索MySQL镜像stars超过5000的
　　INDEX NAME STARS
　　docker.io docker.io/mysql 9623
```
```
　　docker pull#下载镜像docker image pull
　　Usage:docker pull[OPTIONS]NAME[:TAG|DIGEST]
　　[root VM_0_5_centos~]#docker pull tomcat:8.0#如果不指定tag，默认下载最新版本
　　[root VM_0_5_centos~]#docker images-a
　　REPOSITORY TAG IMAGE ID CREATED SIZE
　　docker.io/tomcat 9.0.36-jdk8-openjdk b79665757bae 4 days ago 530 MB
　　docker.io/tomcat latest 2eb5a120304e 4 days ago 647 MB
　　docker.io/hello-world latest bf756fb1ae65 5 months ago 13.3 kB
　　docker.io/tomcat 8.0 ef6a7c98d192 21 months ago 356 MB
```
```
　　docker rmi#删除镜像docker image rm
　　Usage:docker rmi[OPTIONS]IMAGE[IMAGE...]
　　Remove one or more images
　　Options:
　　-f,--force#强制删除
　　[root VM_0_5_centos~]#docker rmi tomcat#删除最新版本的tomcat
　　[root VM_0_5_centos~]#docker rmi ef6a7c98d192#根据镜像id删除指定的tomcat
　　[root VM_0_5_centos~]#docker rmi-f$
    docker images-aq
    #强制删除全部的镜像
```

### 3、容器命令


