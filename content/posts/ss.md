---
title: "Shadowsocks"
date: 2017-06-08T09:40:42+08:00
description: ""
draft: false
tags: []
categories: []
---
_注：适用于Debian / Ubuntu系统，其他系统未进行测试。_

## 安装
安装python-pip
```
apt-get install python-pip
```
如果出现以下问题，执行升级。
![ss1](/images/ss1.png)

```
pip install --upgrade pip
pip install shadowsocks ##安装shadowsocks
```

 如果出现以下问题，先安装 setuptppls 再执行上面的命令安装ss。

![ss2](/images/ss2.png)

```
pip install setuptools
```

## 配置
 创建json配置文件：/etc/shadowsocks.json. Example:
```
{
    "server":"my_server_ip",
    "server_port":8388,
    "local_address": "127.0.0.1",
    "local_port":1080,
    "password":"mypassword",
    "timeout":300,
    "method":"aes-256-cfb",
    "fast_open": false
}
```
## 启动与停止

To run in the background:

```
ssserver -c /etc/shadowsocks.json -d start
ssserver -c /etc/shadowsocks.json -d stop
```