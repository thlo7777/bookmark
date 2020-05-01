## mongoDB

#### [How To Deploy And Manage MongoDB With Docker](https://phoenixnap.com/kb/docker-mongodb)

```
docker run -it -v /data/db:/mongoData -p 27017:27017 --restart=always --name mongodb -d mongo
```