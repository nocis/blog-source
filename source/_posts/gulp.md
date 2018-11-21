---
title: gulp笔记-基础配置
date: 2018-11-21 07:09:17
tags: gulp vue 
---

### 1. JavaScript 严格模式

```javascript
'use strict';
// .js文件 首句加入 进入严格模式
//  用严格模式编写的javascript代码是可以在所有javascript的解释器中正常运行的
//  所以为了达到更好的兼容不同的环境，一定要在严格模式下编写代码并测试
```





### 2. require gulp文件夹

```javascript
// 遍历获取文件名字和路径, 都require
fs.readdirSync('./gulp').forEach(function (file) {
    if((/\.(js|coffee)$/i).test(file)){
        require('./gulp/' + file);
    }
});
//  使用立即执行代码（function(){}()),除了可以执行并获得相应的对象以外，还能保证其他使用者使用   gulp脚本链接多个库文件的时候，不同文件之间不会相互污染严格模式，造成失效
```



### 3. 配置mocha测试和istanbul覆盖率

```javascript
exports.paths = {
    mocha: 'test',
    istanbul: 'test_coverage',
    server:'server'
};
```



### 4.错误处理

```js
exports.errorHandler = function() {
    return function (err) {
        gutil.beep();
        gutil.log(err.toString());
    }
};
```

### 5. 自动刷新

使用**gulp-nodemon**在修改代码后刷新浏览器页面

并分别设置develop模式、test模式、production模式

```
gulp.task('serve',['nodemon']);
gulp.task('serve:test',['nodemon:test']);
gulp.task('serve:production',['nodemon:production']);
```

