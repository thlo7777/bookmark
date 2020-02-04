# GIT 和 GITHUB 开发

## 图文详解如何利用Git+Github进行团队协作开发
><https://www.cnblogs.com/yhaing/p/8473746.html>

## Git常用命令解说
><https://blog.csdn.net/hangyuanbiyesheng/article/details/6731629>

## ssh自动登录的实现方法
><https://www.jianshu.com/p/ad67893d36ea>

## .git目录删不掉
><https://blog.csdn.net/ljh081231/article/details/68945734>

## Removing files from a repository's history
><https://help.github.com/en/articles/removing-files-from-a-repositorys-history>

##  git rm --cached \<file>
> \$fatal: pathspec file    
><https://stackoverflow.com/questions/35069660/git-rm-cached-results-in-fatal-pathspec>

## Bad owner or permissions on /Users/username/.ssh/config
><https://github.com/ddollar/heroku-accounts/issues/15>
> ```
>Just chmod 600 ~/.ssh/config
>```

### clone github

```text
配置
# github
Host github.com
   User thlo7777
   HostName github.com
   PreferredAuthentications publickey
   IdentityFile ~/.ssh/github_rsa


$ ssh-add ~/.ssh/github_rsa
$ git clone xxxxxx

```

### git pull git解决non-fast-forward冲突
```text
1. git fetch origin debug 
获取远程分支debug的修改 
2. git merge origin debug 
合并远程分支debug 
3. git pull origin debug 
更新本地分支 
```

#### [发布模式与分支策略](https://cloud.tencent.com/developer/news/372717)
#### [源代码主干分支开发四大模式](https://blog.csdn.net/zhangmike/article/details/38613429)
#### [基于Git的主干开发工作流](https://juejin.im/post/5d96a219e51d4577f4608b2c)