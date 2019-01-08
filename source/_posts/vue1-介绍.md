---
title: vue1-介绍
date: 2018-11-25 04:51:09
tags: vuejs
---



![](../../public/images/hero-1543343158745.png)

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



### this

在vm实例中，如果想要获取`data：`中的数据， 或者想要调用`methods：`中的方法，必须通过`this.方法名/数据名` 来进行访问，this表示`new`出来的VM实例对象。

**注：在方法内部可以通过箭头函数保持this！！！！**



### 三、事件修饰符

**事件冒泡（默认状态）：**事件冒泡指的是当前的目标元素触发事件的发生，事件再一次向祖先元素传播，在祖先元素上触发相同类型的事件。当子元素都有同一事件处理程序时，利用事件的冒 泡可以减少代码的冗余度。

 **事件捕获：**事件捕获过程与事件的冒泡阶段是一个相反的阶段，即事件由祖先元素向子元素传播，和一个石子儿从水面向水底下沉一样

事件.修饰符

1. click.stop="" 阻止事件冒泡
2. .prevent 阻止默认行为
3. .capture 更改冒泡机制为捕获机制
4. .self 对自己既不执行捕获也不执行冒泡，只有**点击该元素自己**才触发。(不会阻止冒泡的进行，不等于stop)
5. .once 只触发一次事件修饰符

.once.prevent == .prevent.once 顺序无影响



### 四、v-model

vm 实例创建于了浏览器内存，vm对象存在于window里。

**v-bind：只能实现model==>view单向绑定，不能实现双向绑定**

**v-model：双向绑定,仅能用在表单元素中：input(radio, address, text, email... ), select, textare, checkb0x...**

```html
<input type="text" v-model="msg">
```



### 五、eval

解析执行字符串

```js
var str='praseInt(a) + praseInt(b)'
result = eval(str) // 计算值：a+b 
```



### 六、VUE写style

1. 数组:使用v-bind

    ```html
    <h1 :class="['style名1','style名2','style名3']">h1</h1>
    ```

2. 在数组中使用使用三元表达式

    ```html
    <h1 :class="['style名1','style名2', flag?'active':'' ]">h1</h1>
    <!--当vm中data中flag值为true时设置样式'active'-->
    ```

3. 在数组中使用对象的形式

    ```html
    <h1 :class="['style名1','style名2', {'active':flag} ]">h1</h1>
    <!--当vm中data中flag值为true时设置样式'active'-->
    ```

4. 直接使用对象

    ```html
    <h1 :class="{ style名1: flag1, style名2: flag2, active: flag3 }">h1</h1>
    
    <==>
    
    <h1 :class="obj">h1</h1>
    ------------------------
    data: {
       obj: { style名1: flag1, style名2: flag2, active: flag3 }
    }
    
    ```


### 七、内联样式

```html
<h1 v-bind:style=”obj“>
------------------------
data: {
   obj: { inlinestyle1: 'red', inlinestyle2: '40px', inlinestyle3: '200' }
}
```

**注： 键值对属性名称尽量不要`xx-xx`形式，否则必须加引号    `  'font-style':'40px' `    ！！！！**





### 八、v-for

1. 迭代数组

    ```html
    <p v-for="(item,i) in listname">index:{{i}}--value:{{item}}</p>
    ---------------------------------------------------------------
    data: {
       listname: [1,2,3,4,5,6]
    }
    
    <p v-for="(item,i) in listname">index:{{i}}--value:{{item.id}}+{{item.name}}</p>
    ---------------------------------------------------------------------------------
    data: {
       listname: [
              {id:1,name:'id1'},
              {id:2,name:'id2'},
              {id:3,name:'id3'},
              {id:4,name:'id4'},
              {id:5,name:'id5'}
             ]
    }
    ```

2. 迭代对象

    ```html
    <p v-for="(item,i) in tasks">value:{{item.name}}+{{item.time}}--index:{{i}}</p>
    ---------------------------------------------------------------------------------
    data: {
    tasks:{  
            taskname:{  
                name:"完成验收模块的调整",  
                time:new Date(2017,10,11)  
            },  
            taskname1:{  
                name:"完成巡视模块的调整",  
                time:new Date(2017,10,14)  
            },  
            taskname2:{  
               name:"完成验收发文模块的调整",  
                time:new Date(2017,10,17)  
            },  
            taskname3:{  
                name:"完成旁站模块的调整",  
                time:new Date(2017,10,20)  
            }  
    }
    }
    
    ```



3. **迭代数字(count 从1开始:1,2,3,4.....)**

    ```html
    
    <p v-for="count in num">value:{{count}}</p>
    ---------------------------------------------------------------------------------
    data: {
     num : 10
    }
    }
    ```



4. **注意！！！在组件中设置key属性是必须的！！！！标识当前循环唯一身份，可指定！！**

    使用v-bind绑定`key`，值只能为数字或字符串.

    使用`v-for`更新已渲染的元素列表时,默认用`就地复用`策略;列表数据修改的时候,他会根据key值去判断某个值是否修改,如果修改,则重新渲染这一项,否则复用之前的元素;

    ```html
    <p v-for="(item,i) in tasks" :key="item.id"></p>
    ```



### 九、v-if 和 v-show

```html
<p v-if="flag"></p> <!--if会删除或创建元素-->
<p v-show="flag"></p><!--show都会创建元素，但是会切换 display:none 样式-->
```

