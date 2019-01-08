---
title: ES6-箭头函数
date: 2018-11-26 03:20:34
tags: js
---

## 预备知识1--函数的声明

**1.function a(){}**

该方法的定义是全局性的，就算在调用之后定义，系统也不会报错，可以理解为，系统在**执行到**该方法时再去找该方法的定义位置进行初始化。

**2.var a=function(){}**

**匿名函数的定义方法，若是在定义之前调用了，系统会报错**。可以理解为，只用**运行到这个方法时**才能对变量a进行初始化，若是没有对变量a初始化，则会报错。此时，**a代表后面匿名函数的返回值**。

**3.var a=new function(){}**

在js中，方法被当作**一个类**来处理，这中定义方式下，a即带表了这个方法的类，也就是这个方法本身。但是有一种特殊情况，若是在该方法中，存在`return` 数组、方法、或是别的类，**那么a不表示一个方法**，而是表示一个**返回**的**新类**了。



##  预备知识2--`this` 的工作原理

JavaScript 有一套完全不同于其它语言的对 `this` 的处理机制。 在不同的情况下 ，`this` 指向的各不相同。

this 指向其所有者的作用域。

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

这里 函数内部`this` 也会指向*全局*对象。

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

### 对象内函数

因为new关键字可以改变this的指向，将这个this指向新建立的对象。

使用new关键字调用函数（**new** ClassA**(…)**）的具体步骤：

1. 创建空对象；
```js
var obj = {};
```
2. 设置新对象的constructor属性为构造函数的名称，**设置新对象的__proto__属性指向构造函数的prototype对象；**　　
```js
obj.__proto__ = ClassA.prototype;//this.function = function
```
3. 使用新对象调用函数，函数中的this被指向新实例对象：
```js
ClassA.call(obj);　　//{}.构造函数();          
```
4. 将初始化完毕的新对象地址，保存到等号左边的变量中

注意：若构造函数中返回this或返回值是基本类型（number、string、boolean、null、undefined）的值，则返回新实例对象；若返回值是引用类型的值，则实际返回值为这个引用类型。



### 匿名函数

在全局函数中，this等于window，而当函数被作为某个对象的方法调用时，this等于那个对象。不过，匿名函数的执行环境具有全局性，因为其this对象通常指向window。

**以下为特例情况：**

```js
var a = {};
var a.b=function(){console.log(this)}//obj a;    b被赋值为方法，a是b的调用者
```



## 一、理解this

考虑this 的指向问题时，把函数看成`this.function`，思考 **在真正执行该函数时**，谁扮演`this` 的角色（调用者）是合适的，**obj** 或者 **window**(严格模式：undefined)？

```js
var o = {
    user:"me",
    fn:function(){
        console.log(this.user); 
    }
}
window.o.fn();//this.user = me
```

window是js中的全局对象，我们创建的变量实际上是给window添加属性，所以这里可以用window点o对象。window调用的是对象o，o对象调用的是fn。



## 二、箭头函数！！

```js
() => console.log('Hello')
```

和普通函数相比，箭头函数主要就是以下三个方面的特点

1. 不绑定this，arguments
2. 更简化的代码语法
3. **与父作用域共享关键字this**（内部this指向外部this）



x =>x * x;

相当于：

```js
function (x){
    return x*x;
}
```

箭头函数简化的了函数的定义，省略了“function” “{}”“return”

包含多个语句时，不能省略“{}”和“return”
```js
x => {
    if (x > 0) {
        return x * x;
    } else {
        return - x * x;
    }
}
```

如果参数不是一个，要用括号括起来

```js
(x, y) => x * x + y * y;
```

如果要返回一个对象，就要注意，如果是单表达式，这么写的话会报错：
```js
var a = (x)=>{age:x};console.log(a(12)); //undefined
//因为和函数体的{ ... }有语法冲突，所以要改为：
var b = (x)=>({age:x});console.log(b(12)); // { age: 12 }
```
