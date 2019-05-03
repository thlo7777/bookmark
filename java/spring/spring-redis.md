#Redis with Spring

## spring boot 集成 redis lettuce
><https://www.cnblogs.com/taiyonghai/p/9454764.html>

## redis start
> + **start with persistent storage**  
```docker run --name some-redis -d redis redis-server --appendonly yes```
> + **start a redis instance**  
```$ docker run --name some-redis -d redis```
> + **docker export pot**  
```$ docker run --name some-redis -d redis -p 6380:6379```
