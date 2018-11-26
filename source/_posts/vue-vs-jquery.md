---
title: vue_vs_jquery
date: 2018-11-26 03:20:34
tags: vuejs
---

### 1. 如何在动态生成的标签元素上绑定事件

jquery：

```js
$().appendTo().bind()
```

VUE:

写成组件，不推荐在已经渲染好的页面上做dom修改

```js
<component :is="item.component" v-for="item in items" style="margin-button: 10px;" @rainData="rainData"></component>
```

点击事件生成组件即可！