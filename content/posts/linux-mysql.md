---
title: "Linux中使用mysql"
date: 2017-01-24T09:40:42+08:00
description: ""
draft: false
tags: []
categories: []
---
**新年第一更。在node中连接了mysql，记录一下。**

## 使用yum安装
```
$ yum install mysql mysql-server mysql-devel -y
```
## 查看是否生成了mysqld服务
```
$ chkconfig --list |grep mysql
```

## 设置随机启动

```
$ chkconfig mysqld on
```

## 启动／停止／重启mysqld服务
```
##启动：这两种方法都可以，执行一个就可以
$ /etc/init.d/mysqld start    
$ service mysqld start 
##停止：这两种方法都可以，执行一个就可以
$ /etc/init.d/mysqld stop   
$ service mysqld stop
##重启：这两种方法都可以，执行一个就可以
$ /etc/init.d/mysqld restart   
$ service mysqld restart
```

## 启动后，ps一下，看下进程是否起来
```
$ ps -ef |grep mysql|grep -v grep
```

## 查看都有哪些库
```
$ cd /var/lib/mysql 
$ ls -l
```

## 设置初始密码\权限
```
##设置新的密码并同时授权限
$ mysql> grant all on *.* to root@'%' identified by 'youpassword';
##刷新使之生效
$ mysql> flush privileges;
##退出 
$ mysql> exit;
```

## 登录mysql
```
$ mysql -u root -p
```