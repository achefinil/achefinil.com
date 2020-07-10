---
title: "item2 ssh实现自动登录"
date: 2017-02-06T09:40:42+08:00
description: ""
draft: false
tags: []
categories: []
---
Mac 中可以使用 Iterm2 ssh访问远程机器。可以使用它的Profiles这个功能实现自动登录。

## 写一个脚本，记录相关需要信息。（~/.ssh/ache）存放位置自定
```
#!/usr/bin/expect -f
  set user <用户名>
  set host <ip地址>
  set password <密码>
  set timeout -1
  spawn ssh $user@$host
  expect "*assword:*"
  send "$password\r"
  interact
  expect eof
```

## 配置Profiles

打开iterm2， Preferences - Profiles - （+）新建一个。
填写Name与Command（expect ~/.ssh/ache）刚才写的脚本。

## 登录

这样就告一段落了。可以使用快捷键（command + o）来选择生效不同的配置。