---
title: ES6
date: 2018-11-26 03:20:34
tags: js
---

### 1. 箭头函数

## `this` 的工作原理

JavaScript 有一套完全不同于其它语言的对 `this` 的处理机制。 在**五**种不同的情况下 ，`this` 指向的各不相同。

### 全局范围内

```
this;
```

当在全部范围内使用 `this`，它将会指向*全局*对象。

**译者注：**浏览器中运行的 JavaScript 脚本，这个全局对象是 `window`。

### 函数调用

```
foo();
```

这里 `this` 也会指向*全局*对象。

**ES5 注意:** 在严格模式下（strict mode），不存在全局变量。 这种情况下 `this` 将会是 `undefined`。

### 方法调用

```
test.foo(); 
```

这个例子中，`this` 指向 `test` 对象。

### 调用构造函数

```
new foo(); 
```

如果函数倾向于和 `new` 关键词一块使用，则我们称这个函数是 [构造函数](https://bonsaiden.github.io/JavaScript-Garden/zh/#function.constructors)。 在函数内部，`this` 指向*新创建*的对象。

### 显式的设置 `this`

```js
function foo(a, b, c) {}

var bar = {};
foo.apply(bar, [1, 2, 3]); // 数组将会被扩展，如下所示
foo.call(bar, 1, 2, 3); // 传递到foo的参数是：a = 1, b = 2, c = 3
```

当使用 `Function.prototype` 上的 `call` 或者 `apply` 方法时，函数内的 `this` 将会被 **显式设置**为函数调用的第一个参数。

因此*函数调用*的规则在上例中已经不适用了，在`foo` 函数内 `this` 被设置成了 `bar`。

### 箭头函数

```js
() => console.log('Hello')
```

和普通函数相比，箭头函数主要就是以下两个方面的特点

1. 不绑定this，arguments
2. 更简化的代码语法



