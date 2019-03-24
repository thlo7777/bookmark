# Docker command line

## 数据库
### mysql run
```
docker run --name mysql_single -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 -d mysql:5.7 --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
```