---
title: "gulp.js 简单配置"
date: 2016-01-04T09:40:42+08:00
description: ""
draft: false
tags: []
categories: []
---

+ gulp.js是一个前端开发中对前端代码构建的工具，是自动化的构建利器。
+ 基于node.js
+ gulp官方网址：http://gulpjs.com http://www.gulpjs.com.cn/


## 安装nodejs
1. gulp是基于nodejs，理所当然需要安装nodejs；
2. 安装：打开nodejs官网，点击硕大的绿色Download按钮，它会根据系统信息选择对应版本（.msi文件）。然后像安装QQ一样安装它就可以了（安装路径随意）。

## npm
1. 说明：npm（node package manager）nodejs的包管理器，用于node插件管理（包括安装、卸载、管理依赖等）；
2. 使用npm安装插件：命令提示符执行npm install [-g] [–save-dev]；
3. node插件名称。例：npm install gulp-less –save-dev
4. -g：全局安装。将会安装在C:\Users\Administrator\AppData\Roaming\npm，并且写入系统环境变量； 非全局安装：将会安装在当前定位目录； 全局安装可以通过命令行在任何地方调用它，本地安装将安装在定位目录的node_modules文件夹下，通过require()调用；
5. –save：将保存配置信息至package.json（package.json是nodejs项目配置文件）；
6. dev：保存至package.json的devDependencies节点，不指定-dev将保存至dependencies节点；
install，则会根据package.json下载所有需要的包）。
8. 使用npm卸载插件：npm uninstall [-g] [–save-dev] PS：不要直接删除本地插件包
9. 使用npm更新插件：npm update [-g] [–save-dev]
10. 查看npm帮助：npm help
11. 当前目录已安装插件：npm list

## 安装 gulp

> #全局安装  
> $ npm install gulp -g  
#切到工作目录初始化项目，并填写相关项目信息。之后会在目录中生成一个package.json的文件。  
> $ gulp init
#在项目目录下安装一遍  
> $ npm install gulp --save-dev

## 安装 gulp 插件
我们将要使用Gulp插件来完成我们以下任务：  
+ sass的编译（gulp-ruby-sass）
+ 自动添加css前缀（gulp-autoprefixer）
+ 压缩css（gulp-minify-css）
+ js代码校验（gulp-jshint）
+ 合并js文件（gulp-concat）
+ 压缩js代码（gulp-uglify）
+ 压缩图片（gulp-imagemin）
+ 自动刷新页面（gulp-livereload）
+ 图片缓存，只有图片替换了才压缩（gulp-cache）
+ 更改提醒（gulp-notify）
+ 清除文件（del）

```
$ npm install gulp-ruby-sass gulp-autoprefixer gulp-minify-css gulp-jshint gulp-concat gulp-uglify gulp-imagemin gulp-notify gulp-rename gulp-livereload gulp-cache del --save-dev
```

## gulpfile.js

> 在gulpfile.js文件中开始写码，是不是很熟悉了

```js
var gulp = require('gulp'),
sass = require('gulp-ruby-sass'),
autoprefixer = require('gulp-autoprefixer'),
minifycss = require('gulp-minify-css'),
jshint = require('gulp-jshint'),
uglify = require('gulp-uglify'),
imagemin = require('gulp-imagemin'),
rename = require('gulp-rename'),
concat = require('gulp-concat'),
notify = require('gulp-notify'),
cache = require('gulp-cache'),
livereload = require('gulp-livereload'),
del = require('del');
obfuscate = require('gulp-obfuscate'); 

//css
gulp.task('styles', function() {
  return gulp.src('src/main/webapp/res/css/*.css')
.pipe(rename({ suffix: '.min' }))
.pipe(minifycss())
.pipe(gulp.dest('src/main/webapp/res/css/min'))
.pipe(notify({ message: 'Styles task complete' }));
});

// Scripts
gulp.task('scripts', function() {
  return gulp.src('src/main/webapp/res/js/*.js')
.pipe(rename({ suffix: '.min' }))
// .pipe(obfuscate())
.pipe(uglify())
.pipe(gulp.dest('src/main/webapp/res/js/min'))
.pipe(notify({ message: 'Scripts task complete' }));
});

gulp.task('help',function () {
console.log('   gulp ache   执行');
console.log('   gulp help   gulp参数说明');
});

// Clean
gulp.task('clean', function() {
del(['src/main/webapp/res/css/min/*.css',
 'src/main/webapp/res/js/min/*.js'])
});

gulp.task('ache',['clean'],function () {
gulp.start('styles', 'scripts');
});

gulp.task('default', function() {
gulp.start('help');
});
```