---
title: "vim visual block"
date: 2017-05-31T09:40:42+08:00
description: ""
draft: false
tags: []
categories: []
---
用注释举例

## 多行注释：
+ 进入命令行模式，按ctrl + v进入 visual block模式，然后按j, 或者k选中多行，把需要注释的行标记起来
+ 按大写字母I，再插入注释符，例如//
+ 按esc键就会全部注释了

## 取消多行注释：

+ 进入命令行模式，按ctrl + v进入 visual block模式，按字母l横向选中列的个数，例如 // 需要选中2列
+ 按字母j，或者k选中注释符号
+ 按d键就可全部取消注释