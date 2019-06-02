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

