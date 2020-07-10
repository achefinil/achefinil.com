---
title: "Git无密码操作 添加SSHKey"
date: 2016-11-10T09:40:42+08:00
description: ""
draft: false
tags: []
categories: []
---

> Git仓库之间的代码传输协议主要使用ssh协议。而一般搭建Gitlab的时候使用的git用户是没有密码的，因此直接ssh是不能登录的，就需要使用ssh-keygen上传公钥，使用非对称加密传输。下面讲述如何上传你的ssh公钥：

-- 在Terminal / git Bash中敲下面的命令：

```
## 生成密钥，一路回车即可（如果需要重新生成注意一下）
ssh-keygen -t rsa 
## 显示刚才生成的公钥内容，自行拷贝到Gitlab
cat ~/.ssh/id_rsa.pub
```

最后粘贴到账户的ssh配置处。