---
title: mathjax-solution
date: 2018-11-20 23:47:40
tags: 
- mathjax
- hexo
---

### 前言

在配置博客的时候，希望能使用mathjax来编译latex风格的数学公式，现找到一种完美解决办法。

#### 一、原理

考虑采用在静态页面内通过引用外部的mathjax.js 对页内数学公式进行解析。

#### 二、创建模板文件

在hexo的主题文件夹内找到js资源文件夹，创建一个名为math.js的文件

并将以下内容粘贴：

```javascript
MathJax.Hub.Config({ jax: ["input/TeX", "output/HTML-CSS"],tex2jax: { inlineMath: [ ['$', '$'] ], displayMath: [ ['$$', '$$']], processEscapes: true, skipTags: ['script', 'noscript', 'style', 'textarea', 'pre', 'code'] }, messageStyle: "none", "HTML-CSS": { preferredFont: "TeX", availableFonts: ["STIX","TeX"] } });
```

该段内容的作用是调用Mathjax的api对页内公式进行解析。



#### 三、引入Mathjax库并调用刚刚创建的math.js

在你的主题中找到整体调用JavaScript资源的模板文件，并添加如下列形式的语句（我的是pug模板所以是这种形式）：

```jade
script(src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-MML-AM_CHTML')
```

该语句功能是引入cdn的mathjax库，



再添加下列语句：

```jade
script(src= url_for('js/math.js'))
```

该语句功能是引入之前创建的math.js



以上两部分语句作为主题模板文件的一部分会在渲染你的资源静态页面时自动被加入，并完成对页面内的latex数学公式的解析



#### 四、修改转移规则

在如下文件中：

```
nodes_modules/marked/lib/marked.js
```

修改

```
escape: /^\\([\\`*{}\[\]()# +\-.!_>])/,
```
为：


```
escape: /^\\([`*{}\[\]()# +\-.!_>])/,
```
再修改
```
em: /^\b_((?:[^_]|__)+?)_\b|^\*((?:\*\*|[\s\S])+?)\*(?!\*)/,
```
为：
```
em:/^\*((?:\*\*|[\s\S])+?)\*(?!\*)/,
```



最后，重新渲染即可

```
hexo clean
hexo d -g
```

