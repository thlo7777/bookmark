# Docker command line

## 数据库

### mysql run

```bash
$ sudo docker pull mysql/mysql-server:5.7
# docker run --name mysql_single  --restart=always  -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 -d mysql:5.7
copy file between container and local machine
# docker cp 2506:/etc/mysql/mysql.conf.d/mysqld.cnf   mysqld.cnf
# docker cp mysqld.cnf 25061311d968:/etc/mysql/mysql.conf.d/mysqld.cnf
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
