---
title: gulp2-构建后端开发体系
date: 2018-11-24 11:45:41
tags: gulp
---

### 前言

gulp这个工具非常轻便，用做开发中控制项目流程非常实用。gulp可以过简单的逻辑和语法就实现按事件顺序控制开发的流程。



### 一、项目环境说明

按功能主要可以分为开发环境development，测试环境test和生产环境production。

1. 开发环境：开发环境是程序猿们专门用于开发的服务器，配置可以比较随意， 为了开发调试方便，一般打开全部错误报告。

2. 测试环境：一般是克隆一份生产环境的配置，一个程序在测试环境工作不正常，那么肯定不能把它发布到生产机上。

3. 生产环境：是指正式提供对外服务的，一般会关掉错误报告，打开错误日志。

在**package.json**里面可以设定不同的启动选项来配合不同的项目环境。

一般来说将三个环境配置成如下：

```js
 "scripts": {
    "dev": "gulp dev",
    "test": "gulp test",
    "deploy": "pm2 start --no-daemon process.json" //Docker部署 不支持deamon后台运行
},
```

其中pm2是一款非常好用的监控软件，常用于部署。



### 二、定义gulp任务

在package.json同级项目根目录下建立gulpfile.js，该文件为gulp的入口文件。

引入gulp文件夹下所有gulp定义文件，并设置`’dev‘`任务为默认执行。

```js
'use strict';

var gulp = require('gulp');
var fs = require('fs');

fs.readdirSync('./gulp').forEach(function (file) {
  if((/\.(js|coffee)$/i).test(file)){
    require('./gulp/' + file);
  }
});

gulp.task('default', ['dev']);
```



在gulp文件夹下分别建立dev.js, test.js, config.js, 其中config文件是用来方便的定义一些环境变量。

接下来就需要分别定义dev，test 环境的任务，视项目不同定义内容有所区别。但基本遵照如下：

```js
//默认development模式
gulp.task('nodemon',function () {
  nodemon({
    script: path.join(config.paths.server,'/app.js'), 
    ext: 'js',
    watch: [
      path.join(config.paths.server,'/')
    ]
  })
});
//前后端合并测试模式
gulp.task('nodemon:test',function () {
  nodemon({
    script: path.join(config.paths.server,'/app.js'), 
    ext: 'js json',
    watch: [
      path.join(config.paths.server,'/')
    ],
    env: { 'NODE_ENV': 'test' }
  })
});

gulp.task('dev',['nodemon']);
gulp.task('dev:test',['nodemon:test']);
```

使用不同环境只需要分别输入

```bash
gulp dev
gulp dev:test
```

