---
title: vue1-介绍
date: 2018-11-25 04:51:09
tags: vuejs
---

### 简介



mvvm 框架，容易上手，小巧

html + json（属性方法） ，new vue obj 



### 一、概念介绍

模块化：从代码的角度，复用代码

组件化：从UI界面角度，复用ui元素

便利！

vue：.vue模板（结构template，行为script，样式style），component（），extends（）

react：无模板，组件即js（template.js, scrpt.js ,style.js）：es6+es7 学！！



MVC：view（页面） ==》controller（业务逻辑，不涉及数据操作） ==》model（数据元操作curd）



MVVM（仅仅前端VIEW层的开发思想）：M（每个页面的post get数据）<=\=>VM（调度，双向绑定）<=\=> V（页面）；

### 二、vue指令

el: 基本上就是选择器, **不同于 Vue 1.x，所有的挂载元素会被 Vue 生成的 DOM 替换。因此不推荐挂载 root 实例到 `<html>`或者 `<body> `上**

v-cloak：解决差值表达式闪烁。网速慢或者差值表达式在**js脚本执行前**被加载时，浏览器端可以查看到差值表达式，涉及用户体验及安全问题，需注意！！

v-text：等于差值表达式，但是作为HTML标签属性可很好的解决如上问题！！但是不具有**差值表达式**易于编辑（前后加内容，如：`年龄：{{age}}`）的优点，以及有会覆盖标签元素内部的内容的缺点！！

**注：差值表达式和v-text都不能输出数据中的标签以及样式，会被转义为正常字符串！！！！**

v-html：可解决如上问题，输出为html。（便于展示一些已排版文章数据）

v-bind: 用于绑定属性的指令（title，display，input...等）`v-bind:title="变量名"`

**注：可简写为`:title` , 且v-bind中可写js运算表达式（字符串+字符串）！！！**

v-on：绑定事件，类似$().on()   。v-on:click="变量" `@click`

```js
new vue({
    el:'#app',
    data:{
        
    },
    methods:{
        lang(){
            
        }
        
    }
})
```



