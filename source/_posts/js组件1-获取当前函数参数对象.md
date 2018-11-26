---
title: js组件1-获取当前函数参数对象
date: 2018-11-21 20:31:18
tags: js
---

arguments 参数在如下情况并不好使

```
Test({ name: "李四", age: 30 });//obj,undefined
Test({ name: "王五"}, 18);//obj, 18
```

所以采用如下组件：

```js
/*------------------------------------------
 * 清除字符串两端空格，包含换行符、制表符
 *------------------------------------------*/
String.prototype.Trim = function () { return this.replace(/(^[\s\n\t]+|[\s\n\t]+$)/g, ""); }
 
/*----------------------------------------
 * 获取当前函数的参数对象
 *----------------------------------------
 * diffCase 是否区分大小写，默认 false
 *----------------------------------------*/
function GetArgs(diffCase) {
 
 //返回参数对象
 var result = new Object();
 
 //获取调用函数
 var caller = arguments.callee.caller;
 if (caller == null || caller.arguments.length == 0) return result;
 
 //获取函数的参数集合
 var matchs = caller.toString().match(/\s*function[\w\s]*\(([\w\s,]*)\)/);
 if (matchs == null) return result;
 var argArray = matchs[1].split(",");
 
 //获取参数对象
 var params = caller.arguments[0];
 var index = typeof (params) == "object" ? 1 : 0;
 if (index == 1) {
  for (var p in params) {
   for (var i = 0; i < argArray.length; i++) {
    var arg = argArray[i].Trim();
    if (diffCase) {
     if (arg == p) {
      result[arg] = params[p];
      break;
     }
    } else {
     if (arg.toLocaleLowerCase() == p.toLocaleLowerCase()) {
      result[arg] = params[p];
      break;
     }
    }
   }
  }
 }
    
 //多个参数将第一个后面的参数覆盖对象传入的参数
 for (var i = index; i < argArray.length && i < caller.arguments.length; i++)
  result[argArray[i].Trim()] = caller.arguments[i];
 
 return result;
}
```

```js
//测试函数
function Test(name, age) {
 
 //获取参数对象
 var args = GetArgs();
 
 alert("姓名：" + args.name + "，年龄：" + args.age);
 
}
 
//调用测试
Test("张三", 25);
Test({ name: "李四", age: 30 });
Test({ name: "王五" }, 18);
```