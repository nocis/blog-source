---
title: 如何让nodejs高效
date: 2018-11-23 04:51:09
tags: nodejs
---

### 1. __dirname

__dirname追加了自身的目录路径，一般这样做的好处是，可以避免文件的混乱调用



### 2. **通配符

```
src/**/*.js
```

该语句匹配`src`目录及其子目录下的所有`.js`文件



### 3. exports 和 module.exports

如果要对外暴露属性或方法，就用exports就行，要暴露对象(类似class，包含了很多属性和方法)，就用module.exports



### 4. redis 用作session 非常便利

