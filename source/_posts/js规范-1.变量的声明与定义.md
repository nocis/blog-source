---
title: js规范-1.变量的声明与定义
date: 2018-11-21 20:31:18
tags: js
---

#### 1 变量提升

JavaScript 中，函数及变量的声明都将被提升到函数的最顶部。 

JavaScript 中，变量可以在使用后声明，也就是变量可以先使用再声明。

**注: JavaScript 只有声明的变量会提升，初始化的不会。**

```js
var x = 5; // 初始化 x
elem = document.getElementById("demo"); // 查找元素 
elem.innerHTML = x + " " + y;           // 显示 x 和 y
var y = 7; // 初始化 y
```

等价于

```js
var x = 5; // 初始化 x
var y;     // 声明 y

elem = document.getElementById("demo"); // 查找元素
elem.innerHTML = x + " " + y;           // 显示 x 和 y

y = 7;    // 设置 y 为 7
```

故y值在调用时是未定义变量，undefined

**js中的严格模式strict mode不允许使用未声明变量，故建议在每个作用域开始前声明这些变量，这也是正常的 JavaScript 解析步骤。**





**注：js中虽然函数声明和变量声明都会被提升，但是函数会首先被提升，然后才是变量。**



```js
var getName=function(){
  console.log(2);
}

function getName(){
  console.log(1);
}

getName();
//结果为2
```

等价于

```js
//函数、变量声明提升后
function getName(){    //函数声明提升到顶部
  console.log(1);
}

var getName;    //变量声明提升
getName = function(){    //变量赋值依然保留在原来的位置
  console.log(2);
}

getName();    // 最终输出：2
```

 

#### 2 js的解析机制

遇到 script 标签的话 js 就进行**预解析**，将变量 var 和 function 声明提升，但不会执行 function，然后就进入上下文执行，上下文执行还是执行预解析同样操作，直到没有 var  和 function，就开始执行上下文。



####  3 变量声明的方式及作用域

1. **使用var（最常见）** 

 　 var声明的变量可以是全局的（函数外面），也可以是局部的（函数内部）**

​     **注：在函数外面使用var声明一个变量后，再在函数内部使用var再次声明一次并改变其值，函数外面的该变量的值不会发生改变。 **



2. **使用let**

​       let声明的变量在{}中使用，变量的作用域限制在块级域中（**并不等价于 **函数内的局部变量）

```js
var children = buttons.children //用var声明了一个全局变量children，储存buttons的所有子元素 
for(var i=0; i<children.length; i++)
{ 
    children[i].onclick = function(){ //执行点击事件的时候输出对应的第几个按钮 
        console.log(i)
    } 
}
//无论你点击什么，输出结果都是4，因为内存里只存了一个i，这个i的最终运算结果是4
```

但是如果你把`var i = 0`改成`let i = 0`就可以得到你想要的结果。因为如果你使用let的话，每次循环都是引用的都是不同的i（引用了i变量的不同实例）。

#### 4 一条语句多个变量

```js
var name="Gates", age=56, job="CEO";
```

```js
var name="Gates",
    age=56,
    job="CEO";
```

以上两种都可行

#### 5. 语句的解析顺序

第一种：var a = b = 3;

```js
var a = b = 3; //实际是以下声明的简写：

var a; //变量提升 
b = 3; //文法树
a = b;

//不等于如下声明
var b = 3;
var a = b;

----------------
----------------
(function(){
    var a = b = 3;
})(); 

console.log("a defined? " + (typeof a !== 'undefined')); //false, var a 在立即执行函数的内部，成为了局部变量
console.log("b defined? " + (typeof b !== 'undefined')); //true, b=3 使得b成为了全局变量（js 弱类型语言，变量不声明直接使用，则默认作为全局变量）
```

第二种：var a,b = 3;


```js
var a,b = 3 //实际是以下声明的简写：

var a; //a = undefined 局部变量
var b = 3; //b = 3 局部变量， 注意，初始化不会变量提升
```



#### 6. 逗号运算符

**逗号运算符**：逗号之前所有的运算表达式都会执行,但整个语句的值是最后一个表达式的值

```js
a = (b=2, c=3, 4==4); // a=true，b=2，c=3
```

#### 7. js 函数参数

javascript中的函数定义**并未指定**函数形参的类型，函数调用也**未**对传入的实参值做**任何类型检查**。实际上，javascript函数调用甚至**不检查**传入形参的个数

##### 7.1. 同名形参

在非严格模式下，函数中可以出现同名形参，且只能访问**最后出现**的该名称的形参

```js
function add(x,x,x){
    return x;
}

console.log(add(1,2,3));//3
```

而在严格模式下，出现同名形参会抛出语法错误

```js
function add(x,x,x){
    return x;
}
console.log(add(1,2,3));//SyntaxError: Duplicate parameter name not allowed in `
```

##### 7.2. 参数个数

1. 当实参比函数声明指定的形参个数要少，剩下的形参都将设置为undefined值

```js
function add(x,y){
    console.log(x,y);//1 undefined
}
add(1);
```

2. 当实参比形参个数要多时，剩下的实参没有办法直接获得，需要使用即将提到的**arguments对象**

   javascript中的参数在内部是用一个数组来表示的。函数接收到的始终都是这个数组，而不关心数组中包含哪些参数。在函数体内可以通过arguments对象来访问这个参数数组，从而获取传递给函数的每一个参数。arguments对象并不是Array的实例，它是一个类数组对象，可以使用方括号语法访问它的每一个元素

```js
function add(x,y){
    console.log(arguments.length)  //3
    return x+1;
}
add(1,2,3);//2，只传入x，y，return x+1;
console.log(add.length);  //2
//arguments对象的length属性显示实参的个数，函数的length属性显示形参的个数
```

```js
alert(3,4)  // 3, 只传入了3
alert((3,4)) // 4,（3，4）的结果是4，传入alert的参数值也是4
```

**注:   形参只是提供便利，但不是必需的**

```js
function add(){
    return arguments[0] + arguments[1];
}
console.log(add(1,2));//3
```

**注：在普通模式下，arguments对象的值和形参的值是同步的，当且仅当形参与实参的个数相同时。但！！在严格模式下，arguments对象的值和形参的值是！！独立的！！**

虽然命名参数和对应arguments对象的值相同，但并不是相同的命名空间，它们的命名空间是独立的。

```js
function test(num1,num2){
'use strict';
console.log(num1,arguments[0]);//1 1
arguments[0] = 2;
console.log(num1,arguments[0]);//1 2
num1 = 10;
console.log(num1,arguments[0]);//10 2
}
test(1);
```

**注：当形参并没有对应的实参时，arguments对象的值与形参的值并不对应**
```js
function test(num1,num2){
console.log(num1,arguments[0]);//undefined,undefined
num1 = 10;
arguments[0] = 5;
console.log(num1,arguments[0]);//10,5
}
test();
```



##### 7.3. 对象参数

可以通过名/值对的形式来传入参数，这样参数的顺序就无关紧要了。定义函数的时候，传入的实参都写入一个单独的对象之中，在调用的时候传入一个对象，对象中的名/值对是真正需要的实参数据

```js
function easycopy(args){
arraycopy(args.from,args.form_start || 0,args.to,args.to_start || 0, args.length);
}
var a = [1,2,3,4],b =[];
easycopy({form:a,to:b,length:4});
```



#### 8. 函数的内部属性

**一、callee**

arguments的作用是保存传入函数中的所有参数，而且这个arguments有一个名叫callee的属性，这个属性是一个指针，指向拥有arguments对象的函数。

举个递归算法---阶乘函数的例子：

```js
function factorial(num){
    if(num<=1){
        return 1;
    }else{
        return num*factorial(num-1)
    }  
}    
```

上面的代码，在函数有名字，而且名字以后也不会变的情况下，这样定义没有啥问题。不过，这样这个函数的执行与函数名紧紧耦合在一起了。所以为了消除这种紧密耦合，我们可以使用arguments.callee。

```js
function factorial(num){
    if(num<=1){
        return 1;
    }else{
        return num*arguments.callee(num-1)
    }  
} 
```
这样，无论引用函数时使用什么名字，都可以保证正常完成递归调用。举个例子：
```js
var trueFactorial = factorial;
factorial = function(){
  return 0;  
}
console.log(trueFactorial(5));      //120
console.log(factorial(5));          //0
```

变量trueFactorial获得了factorial的值，实际上是在另一个位置上保存了一个函数的指针。然后我们又把一个返回0的函数赋值给factorial变量。如果像原来的factorial()不使用arguments.callee，那么调用trueFactorial()就会返回0。但是，在解除了耦合之后，trueFactorial()依然能够正常的计算阶乘。而再次被赋值的factorial()，只能按照重新赋给的值进行计算。

严格模式下，不能通过脚本访问arguments.callee，可以使用命名函数表达式来达成相同的结果，栗如：

```js
var factorial = (function f(num){
    if (num <= 1){
        return 1;
    } else {
        return num * f(num-1);
    }
});    
```

以上代码创建了一个名为f()的命名函数表达式，然后将它赋值给变量factorial。即便把函数赋值给了另一个变量，函数的名字f依然有效。这种方式在严格模式和非严格模式下都行得通。



**二、this**

this引用的是函数执行的环境对象，当在网页的全局作用域中调用函数时，this对象引用的就是window。

```js
window.color = "red";
var o = { color: "blue"};
function sayColor(){
  console.log(this.color);  
}

sayColor();      // "red"

o.sayColor = sayColor;
o.sayColor();    // "blue"
```

函数sayColor()在全局作用域中定义，并且引用了this对象。在这个函数调用之前，this的值并不确定，**所以this可能在代码执行过程中引用不同的对象**。

当在全局作用域调用sayColor()，那么this引用的是全局对象window，换句话说就是，对this.color求值会转换成对window.color求值，所以结果就是“red”。

当把这个函数赋值给对象o并调用o.sayColor()时，this引用的是对象o，因此对this.color求值会转换成对o.color求值，所以结果就是“blue”。

**注：函数的名字仅仅是一个包含指针的变量，所以在不同的环境下执行，全局的sayColor()函数与o.sayColor()指向的仍然是同一个函数。**

**三、caller**

函数的caller属性保存着调用当前函数的函数的引用，**如果是在全局作用域中调用当前函数，它的值是null**
```js
function outer(){
inner();
}
function inner(){
console.log(inner.caller);//outer(){inner();}
}
outer(); 
function inner(){
console.log(inner.caller);//null
}
inner();
```
**注： 在严格模式下，访问这个属性会抛出TypeError错误**

#### 9. 函数重载

js 没有函数重载，**同名即会覆盖，即便参数不同**！！



#### 10. 参数类型

 javascript中所有函数的参数都是按值传递的。也就是说，把函数外部的值复制到函数内部的参数，就和把值从一个变量复制到另一个变量一样。**但是，对于基本类型和引用类型是有区别的**

##### 10.1. 基本类型

在向参数传递基本类型的值时，被传递的值会被复制给一个局部变量(命名参数或arguments对象的一个元素)，参数值的改变  **不会 ** 反映在函数外部。

##### 10.1. 引用类型

在向参数传递引用类型的值时，会把这个值在内存中的地址复制给一个局部变量，因此这个局部变量的变化 **会 ** 反映在函数的外部
```js
function setName(obj){
obj.name = 'test';
}
var person = new Object();
setName(person);
console.log(person.name);//'test'
```

**注：当在函数内部重写引用类型的形参时，这个变量引用的就是一个局部对象了。而这个局部对象会在函数执行完毕后立即被销毁（*如果按照类似c++的按引用传递参数&obj，当在函数中这个地址被指向另一个对象后，函数外的原参数也会改变*）**

```js
function setName(obj){
obj.name = 'test';
console.log(person.name);//'test'
obj = new Object();
obj.name = 'white';
console.log(person.name);//'test'
}
var person = new Object();
setName(person);
```

#### 11. 与或赋值小技巧

```js
var  a =  obj || " "  ;   //如果 obj 为空，a就赋值为 " " ；
var  a = check() &&  do(); //如果check()返回为真，就执行do()并将结果赋值给 a;
```