---
title: "Mac Finder 显示隐藏文件和文件夹"
date: 2016-09-27T09:40:42+08:00
description: ""
draft: false
tags: []
categories: []
---

最近Mac上使用一些命令 总有一些记不住的 记录一下
以下命令 需在「终端 Terminal」中执行

> 显示隐藏文件

```
defaults write com.apple.finder AppleShowAllFiles -boolean true ; killall Finder
```

> 隐藏文件

```
defaults write com.apple.finder AppleShowAllFiles -boolean false ; killall Finder
```

注：以上命令适用于 OS X Mavericks 和 OS X Yosemite 系统