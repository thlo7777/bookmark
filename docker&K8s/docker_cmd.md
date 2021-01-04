# Docker command line

## 数据库

### mysql run

```bash
$ sudo docker pull mysql/mysql-server:5.7
# docker run --name mysql_single  --restart=always  -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 -d mysql:5.7
copy file between container and local machine
# docker cp 2506:/etc/mysql/mysql.conf.d/mysqld.cnf   mysqld.cnf
# docker cp mysqld.cnf 25061311d968:/etc/mysql/mysql.conf.d/mysqld.cnf

//进入容器
$ docker exec -it ubuntu_bash bash

//删除镜像

sudo docker ps
sudo docker stop  container ID
sudo docker images
sudo docker rmi -f 857eadf53a54

```

### mysql utf8mb4 配置
```aidl
# vim /etc/mysql/mysql.cnf
!includedir /etc/mysql/conf.d/
!includedir /etc/mysql/mysql.conf.d/

[client]
default-character-set = utf8mb4

[mysql]
default-character-set = utf8mb4

[mysqld]
character-set-client-handshake = FALSE
character-set-server = utf8mb4
collation-server = utf8mb4_unicode_ci

```
### Configure Docker to start on boot
> ````
> systemd
>
> $ sudo systemctl enable docker
>
> To disable this behavior, use disable instead.
>
> $ sudo systemctl disable docker
>
> ````
### start docker
> ```
> $ sudo systemctl start docker
> ```

### 在使用docker run启动容器时，使用--restart参数来设置：
```
# docker run -m 512m --memory-swap 1G -it -p 58080:8080 --restart=always 
--name bvrfis --volumes-from logdata mytomcat:4.0 /root/run.sh

--restart具体参数值详细信息：
    no -  容器退出时，不重启容器；

    on-failure - 只有在非0状态退出时才从新启动容器；

    always - 无论退出状态是如何，都重启容器；
```

### docker启动,重启,关闭命令
```
docker启动命令,docker重启命令,docker关闭命令

启动        systemctl start docker
守护进程重启   sudo systemctl daemon-reload
重启docker服务   systemctl restart  docker
重启docker服务  sudo service docker restart
关闭docker   service docker stop   
关闭docker  systemctl stop docker
```

### 用户加入docker组，避免使用sudo
```
//Use the usermod command to add the user to the wheel group.
//By default, on CentOS, members of the wheel group have sudo privileges.
usermod -aG wheel username

查看用户组中有没有docker组
sudo cat /etc/group | grep docker
创建docker分组, -g 999为组ID，也可以不指定
sudo groupadd -g 999 docker 

增加用户到docker组
sudo usermod -aG docker $USER

退出当前用户登陆状态，然后重新登录，以便让权限生效,或重启docker-daemon
sudo systemctl restart docker
```

#### [Docker 之 Jenkins自动化部署](https://www.jianshu.com/p/a1aef2f7da56)

```
official jenkins docker
docker pull jenkins/jenkins

sudo chown -R 1000 volume_dir

docker run -d -p 49001:8080 -v ~/jenkins:/var/jenkins_home --name jenkins --restart=always jenkins

docker run -u 1000 -d -p 8080:8080 -v ~/jenkins:/var/jenkins_home --name jenkins --restart=always jenkins/jenkins:lts

docker run -d -p 8080:8080 -v ~/jenkins:/var/jenkins_home --name jenkins --restart=always jenkins/jenkins:lts

```

#### [Hyperledger Fabric 的第一个长期支持发布版本](https://hyperledger-fabric.readthedocs.io/zh_CN/release-1.4/whatsnew.html)


#### docker volume command
##### Differences between -v and --mount behavior
```
As opposed to bind mounts, all options for volumes are available for both --mount and -v flags.

When using volumes with services, only --mount is supported.
```
##### Start a container with a volume
```
If you start a container with a volume that does not yet exist, Docker creates the volume for you. The following example mounts the volume myvol2 into /app/ in the container.

The -v and --mount examples below produce the same result. You can’t run them both unless you remove the devtest container and the myvol2 volume after running the first one.

$ docker run -d  --name devtest  -v {宿主机目录/home/xxxx}:{容器内目录/app}  nginx:latest
$ docker run -d  --name devtest  --mount source=myvol2,target=/app  nginx:latest

```


#### [Docker安装太慢，使用国内镜像服务快速安装](https://blog.csdn.net/weixin_39806100/article/details/105925731?utm_medium=distribute.pc_relevant.none-task-blog-baidulandingword-2&spm=1001.2101.3001.4242)

#### [Docker安装Redis](https://www.cnblogs.com/linjiqin/p/10472023.html)
```
docker run --restart=always --log-driver json-file --log-opt max-size=100m --log-opt max-file=2 -p 6379:6379 --name myredis -v /opt/data/redis/redis.conf:/etc/redis/redis.conf -v /opt/data/redis:/data -d redis redis-server /etc/redis/redis.conf --appendonly yes --requirepass "lynch#1508"

```