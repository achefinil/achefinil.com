---
title: "PM2"
date: 2016-12-14T09:40:42+08:00
description: ""
draft: false
tags: []
categories: []
---
**PM2 是一个带有负载均衡功能的 Node 应用的进程管理器。**  
当你要把你的独立代码利用全部的服务器上的所有 CPU，并保证进程永远都活着，0 秒的重载。

## 主要特性
+ 内建负载均衡（使用 Node cluster 集群模块）
+ 后台运行
+ 0 秒停机重载，我理解大概意思是维护升级的时候不需要停机.
+ 具有 Ubuntu 和 CentOS 的启动脚本
+ 停止不稳定的进程（避免无限循环）
+ 控制台检测
+ 提供 HTTP API
+ 远程控制和实时的接口 API ( Nodejs 模块，允许和 PM2 进程管理器交互 )

## 安装

```
npm install -g pm2
```

## 使用

```
$ npm install pm2 -g     # 命令行安装 pm2
$ pm2 start app.js -i 4  # 后台运行pm2，启动4个app.js
$ pm2 start app.js --name my-api # 命名进程
$ pm2 list               # 显示所有进程状态
$ pm2 monit              # 监视所有进程
$ pm2 logs               # 显示所有进程日志
$ pm2 stop all           # 停止所有进程
$ pm2 restart all        # 重启所有进程
$ pm2 reload all         # 0 秒停机重载进程 (用于 NETWORKED 进程)
$ pm2 stop 0             # 停止指定的进程
$ pm2 restart 0          # 重启指定的进程
$ pm2 startup            # 产生 init 脚本 保持进程活着
$ pm2 web                # 运行健壮的 computer API endpoint (http://localhost:9615)
$ pm2 delete 0           # 杀死指定的进程
$ pm2 delete all         # 杀死全部进程
```