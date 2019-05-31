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


### git pull git解决non-fast-forward冲突
```text
1. git fetch origin debug 
获取远程分支debug的修改 
2. git merge origin debug 
合并远程分支debug 
3. git pull origin debug 
更新本地分支 


        public static final String IAM_USER_GUID_USERNAME_KEY = "guid:user_name";
        
        /*
         * only for guid:user_name key. when IM need find user name by guid
         */
        hashOperations.put(AppConstants.IAM_USER_GUID_USERNAME_KEY,
                iamUser.getGuid() + ":user_name", iamUser.getUserName()== null ? "null" : iamUser.getUserName());

```