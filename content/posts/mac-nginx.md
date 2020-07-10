---
title: "Mac nginx 相关命令"
date: 2016-11-15T09:40:42+08:00
description: ""
draft: false
tags: []
categories: []
---

各个系统下的nginx的相关命令类似，就OS下使用。（注意如果权限不足需要在下述命令前输入 “sudo”）。

## 停止操作（两个步骤）

+ 查询nginx主进程号
```
ps -ef | grep nginx
```

+ 停止命令（3种，酌情使用）
```
## 从容停止
kill -QUIT 主进程号
## 快速停止
kill -TERM 主进程号
## 强制停止
kill -9 主进程号
```

## 平滑重启


+ 如果更改了配置，并不需要总是关闭再打开。同样要先拿到主进程号，同上第一步骤。
```
## 后面是主进称号或进程号文件路径
kill -HUP 主进程号
```

+ 另外推荐的重载配置的方式
```
/usr/local/nginx/sbin/nginx -s reload
```

+ 如果修改了配置文件后最好先检查一下修改过的配置文件是否正确

```
nginx -t -c config文件路径
```
