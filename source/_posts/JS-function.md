---
title: JS函数
date: 2020-11-11 17:15:12
tag: JS
categories: JS
cover: /img/cover-js.png
---
__JavaScript 函数是被设计为执行特定任务的代码块。__
__JavaScript 函数会在某代码调用它时被执行。__
## 函数概念、声明、调用
[https://blog.csdn.net/qq_34569497/article/details/95379260](https://blog.csdn.net/qq_34569497/article/details/95379260)
### 概念
把一段需要重复使用的代码，用function语法包起来，方便重复调用，分块和简化代码。复杂一点的，也会加入封装、抽象、分类等思想。

### 声明
* 方法一：
```
function 方法名(){
     //要执行的代码
}
```
* 方法二：
ES6中声明方式箭头函数，()=>{} 
* 方法三：
匿名函数，将函数存到变量里 var func=function(){};

### 调用
* 方法一：函数名()【可以多次调用】
```
//函数声明
function fn(){
    console.log(1);
}
//函数的调用
fn();
```
* 方法二：
在事件中调用，直接写函数铭，__不使用括号__
```
//函数声明
function fn(){
    console.log(1);
}
//函数在事件中的调用
document.onclick = fn;
```

## 函数语法
JavaScript 函数通过 function 关键词进行定义，其后是函数名和括号 ()。
函数名可包含字母、数字、下划线和美元符号（规则与变量名相同）。
圆括号可包括由逗号分隔的参数：
```
(参数 1, 参数 2, ...)
```
__函数参数（Function parameters）__ 是在函数定义中所列的名称。
__函数参数（Function arguments）__ 是当调用函数时由函数接收的真实的值。
在函数中，参数是局部变量。

## 函数返回
当 JavaScript 到达 __return__ 语句，函数将停止执行。
如果函数被某条语句调用，JavaScript 将在调用语句之后“返回”执行代码。
函数通常会计算出返回值。这个返回值会返回给调用者：
```
var x = myFunction(7, 8);        // 调用函数，返回值被赋值给 x

function myFunction(a, b) {
    return a * b;                // 函数返回 a 和 b 的乘积(56)
}
```
本例调用函数把华氏度转换为摄氏度
![](1.png)
不使用 () 访问函数将返回函数声明而不是函数结果

## 局部变量
在 JavaScript 函数中声明的变量，会成为函数的局部变量。
局部变量只能在函数内访问。
```
//此处使用carName——>未定义
myFunction();
function myFunction() {
    var carName = "Volvo";
    console.log(typeof carName + " " + carName) //string Volvo
}

console.log(typeof carName) //undefined

```