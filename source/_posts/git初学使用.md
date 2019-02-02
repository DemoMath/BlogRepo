---
title: Git初学使用
comments: false
date: 2016-03-02 12:22:11
tags:
  - Git
  - 版本管理
categories: 版本控制
---

记忆账号密码

```shell
git config --global credential.helper store
```

**配置全局信息**

配置全局的用户名、邮箱信息，作为提交人信息

```shell
git config --global user.name “name"
```

```shell
git config --global user.email "email”
```

用户密码输错的话windows解决办法

​	控制面板-用户账户-管理你的凭据-git 保存的用户信息在普通凭据列表里-修改-完成

克隆 仓库

```shell
git clone 地址
```

拉代码 

```shell
git pull origin master     
```

提交、推送代码

```shell
git add -A 做了修改要先写这个命令
git commit -m "提交的信息" 
git push origin master 推送代码到远程 master是分支名

****重要**** 以后每次提交代码，要先拉取代码，整个流程即add-commit-pull-push,保证远程代码不要有冲突，有冲突在本地修改，再次add-commit-pull-push
```

分支相关

```shell
git branch 查看本地所有分支
git branch -a 查看本地和远程所有分支

git checkout 分支名      切换到某个分支
git checkout -b 分支名   创建分支并切换到该分支
git rm -r --cached .
```

