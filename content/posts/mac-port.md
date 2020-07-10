---
title: "Mac 解决端口占用"
date: 2016-11-17T09:40:42+08:00
description: ""
draft: false
tags: []
categories: []
---

## Tomcat启动时报以下错误

```
java.rmi.server.ExportException: Port already in use: 1099; nested exception is: 
java.net.BindException: Address already in use
```

## 查看占用该端口的进程

```
lsof -i tcp:1099
```

## 显示如下列表

```
COMMAND  PID      USER   FD   TYPE             DEVICE SIZE/OFF NODE NAME
 java    1376 achefinil   20u  IPv6 0xbf8ce0cb4c234839      0t0  TCP
```

## 直接kill掉

```
kill -9 1099
```
