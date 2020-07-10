---
title: "Git Quick Start"
date: 2016-09-13T09:40:42+08:00
description: ""
draft: false
tags: []
categories: []
---


## 配置

常用配置：

```
# 配置全局用户名、邮箱，主要用于 commit 身份信息
$ git config --global user.name "achefinil"
$ git config --global user.email "hi@achefinil.com"
 
# 配置缩写，强烈推荐，之后就不必敲那么多字符了
$ git config --global alias.br branch
$ git config --global alias.co checkout
$ git config --global alias.ci commit
```

可以通过如下命令确认配置是否生效：

```
$ git config --list
alias.br=branch
alias.co=checkout
alias.ci=commit
$ git config user.name
```

一些可能有用的配置：

```
# 配置编辑器，用于编辑 commit 信息
$ git config --global core.editor notepad
  
# 配置忽略文件权限的修改
$ git config --global core.filemode false

```

## 克隆仓库

有两种克隆仓库的方式，一种是 HTTP/HTTPS，一种是 SSH，由于 SSH 可以通过公钥来免密码，推荐使用：

```
# SSH，推荐使用
$ git clone git@ahcefinil.git
 
# HTTP
$ git clone http://ahcefinil.git
 
# 克隆到指定目录
$ mkdir myproject
$ git clone git@ahcefinil.git myproject
```

## 更新代码

更新代码的方式很简单：

```
# 拉取远程最新代码并和当前分支合并
$ git pull
 
# 实际上相当于如下两条命令
$ git fetch
$ git merge origin/master

```

## 修改代码并提交

完成代码的修改后，开始提交代码：

```
# 查看改动的文件
$ git status
 
# 查看改动内容
$ git diff
 
# 将修改代码添加到暂存区（Staged Area），以方便后续提交
$ git add your-file-A your-file-B
 
# 提交
$ git commit -m 'commit comment'
```

## 推送到远程分支

本地提交代码后，将提交推送到远程分支，方便让其他人获取你的代码，以及进行 Merge Request、Code Review、远程合并等操作：

```
# 将本地 fav-list 分支的提交推送到远程分支 fav-list
# -u 代表 --set-upstream，之后本地 fav-list 分支的提交，可以直接 git push 即自动推送到远程 fav-list 分支
$ git push -u origin fav-list:fav-list
 
# 之后本地的提交推送直接 push 即可
$ git push
```

## 本地分支合并

推荐走远程合并的方式，在 Gitlab 等系统上完成。也可以在本地进行：

```
# 切回 master 分支
$ git checkout master
 
# 合并分支
$ git merge fav-list
 
# 提交到远程 master，更新代码
$ git push
```

## 删除分支

代码成功合并后，可以删除分支：

```
# 删除本地分支
$ git branch -d fav-list
Deleted branch cartype-list (was 7003eb1).
# 强制删除：在本地修改未提交时，是不可以删除的，如确定删除分支并放弃所有修改，可以输入$ git branch -D fav-list
# 删除远程分支
$ git push origin :fav-list
To git@*****.git
 - [deleted]         fav-list
# 删除后，查看branch，就只剩下master分支了：
$ git branch
* master
```

## 取消修改 恢复版本

```
# 取消对文件的修改。还原到最近的版本，废弃本地做的修改。
git checkout -- <file>

# 取消已经暂存的文件。即，撤销先前"git add"的操作
git reset HEAD <file>...

# 修改最后一次提交。用于修改上一次的提交信息，或漏提交文件等情况。
git commit --amend

# 回退所有内容到上一个版本
git reset HEAD^

# 回退a.py这个文件的版本到上一个版本  
git reset HEAD^ a.py  

# 向前回退到第3个版本  
git reset –soft HEAD~3  

# 将本地的状态回退到和远程的一样  
git reset –hard origin/master  

# 回退到某个版本  
git reset 057d  

# 回退到上一次提交的状态，按照某一次的commit完全反向的进行一次commit.(代码回滚到上个版本，并提交git)
git revert HEAD

```


## 切换到远程分支

```
# 查看当前所有分支（本地+远程）
git branch -va
# 创建本地分支并切换到远程分支（例：ache为分支名）
git checkout -b ache origin/ache
```