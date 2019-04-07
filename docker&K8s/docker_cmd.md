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