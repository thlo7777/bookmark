# Docker command line

```
docker run --name mysql_master -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 -d mysql:latest  --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
```