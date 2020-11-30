---
title: JS数据类型
date: 2020-11-11 10:58:39
tags: JS
categories: JS
cover: /img/cover-js.png
---

## 类型（两类）
### 一、基本类型(5种)
Number、String、Boolean、undefined、object、Null
```
var length = 7;                             // 数值
var lastName = "Gates";                      // 字符串
var y = false;                                  //布尔
var z = null                                    //null
var p = undefined                               //undefined
```
### 二、引用类型（1种）
Object 中包含了Data、function、Array等。这三种是常规用的。
```
var x = {firstName:"Bill", lastName:"Gates"};   // 对象 
var cars = ["Porsche", "Volvo", "BMW"];         // 数组
```

## 使用typeof检查变量类型
```
var x='123'
console.log(typeof x) //string
var y=123
console.log(typeof y) //number
```
JS 中 typeof 输出分别是
![](7.png)
__复杂数据__
typeof 运算符可返回以下两种类型之一：
* function
* object
typeof 运算符把对象、数组或 null 返回 object。
typeof 运算符不会把函数返回 object。
```
typeof {name:'Bill', age:62} // 返回 "object"
typeof [1,2,3,4]             // 返回 "object" (并非 "array")
typeof null                  // 返回 "object"
typeof function myFunc(){}   // 返回 "function"
```
__typeof 运算符把数组返回为 "object"，因为在 JavaScript 中数组即对象。__
isNaN() 函数用于检查其参数是否是非数字值。
如果参数值为 NaN 或字符串、对象、undefined等非数字值则返回 true, 否则返回 false。
 ![](8.png)
 Number() 函数把对象的值转换为数字。Number(object)

## 数值
整数时有无小数点均可
```
var x1 = 1.00; //1
var x2 = 2; //2
var x3 = 3.14; //3.14
```
123+456（整数计算），在JS里整数的运算基本可以保证正确
如果使用JS进行浮点元素的计算，可能得到一个不精确的结果（因为二进制是不可以表示小数的，在二进制不准确）
所以不要使用JS进行对精确度要求比较高的运算。

### 取得数值的最大值和最小值（MAX_VALUE/MIN_VALUE)
```
console.log(Number.MAX_VALUE)
console.log(Number.MIN_VALUE)
```
直接在控制台输入
![](1.png)
 如果使用Number表示的数字超过了最大值则会返回一个Infinity，表示正无穷。 -Infinity ，表示负无穷。使用typeof检验Infinity也会返回Number。
## 字符串
字符串单引号或者双引号都可使用
如遇到需要输出的内容有引号，只需要与字符串外包裹的引号不同即可，如：
```
var answer = "It's red";             // 双引号内的单引号
var answer = "He is called 'Bill'";    // 双引号内的单引号
var answer = 'He is called "Bill"';    // 单引号内的双引号
var answer = "他说：\"我想吃饭。\"" 
```
在字符串中可以使用（\）作为转义字符，当表示一特殊符号的时候可以使用（\）进行转义
![](3.png)
__注：__ 想打印‘\’时，需使用两个\(\\)
由Unicode字符、数字、标点组成。Unicode下所有的字符、数字、标点在内存中都占2字节。
查看字符"张"的十六进制表现方式，结果为  5f20
![](2.png)
\u4e00  汉字的起始字符
\u9fa5  汉字的结束字符
转义字符：\n 换行；\r回车；\t  一个制表符

__注__ ：代码执行的时候是按照顺序执行，只有上面的代码执行完了，下面的代码才会开始执行。

假设上一行代码是alert()，弹出一个对话框的效果。只有点完了对话框上面的确定按钮，这条代码才算是真正的执行完了。

### 其他类型转成string【toString（）】

支持：number、boolean、string、object 
不支持：null 、undefined

toLocaleString ( )把数组转成本地字符串  
![](9.png)

### 数值和字符串的运算

当数值和字符串相加时，Javascript 将把数值视作字符串。
```
var x = 123 + "JS"; //输出123JS
```
Javascript 从左向右计算表达式。不同的次序会产生不同的结果：
```
var x = 123 + 4 + "JS"; //输出127JS

var x = "JS" + 123 + 4; //输出JS1234
```
由于第一个例子js把123，和4是为数值，所以先相加后再转为字符串与JS相加
第二个例子先遇到JS是字符串，所以后面的数值都被是为字符串

## 布尔
做运算时，true可当1运算；false当做0运算
![](4.png)
加引号为字符串，不加为boolean
## 空值（null）
表示声明对象为赋值，Null类型的值只有一个就是null，null这个值专门用来表示这个为空的对象。
null是表示一个 __空对象指针__ ，这也是typeof操作符检测 null 值时会返回 object 的原因。
![](5.png)
使用typeof检查null时返回object。
## 未定义（undefined）
__两种情况：__
声明变量未赋值会输出undefined；
访问对象不存在的属性，也会输出undefined
![](6.png)
## 对象
大括号包裹：{}；逗号分隔；对象属性：name:value
```
var Jackson = {nickname:"Jack", sex:"male", age:62, hobby:"basketball"};
```
对象Jack，其nickname,sex,age,hobby分别为其4个属性

### 数组
中括号包裹：[]；逗号分隔；数组索引从0开始，末尾索引length-1
```
var name = ["Jack", "Vivian", "Emma"];
```
#### 检测数组类型的方法
__（1）instanceof  操作符__
![](10.png)
__（2）对象的 constructor 属性__
![](11.png)
__（3）Array.isArray( ) 检验值是否为数组__
![](12.png)

## null 和 undefined 有什么区别
Null 只有一个值，是 null。不存在的对象。
Undefined 只有一个值，是undefined。没有初始化。undefined 是从 null 中派生出来的。

简单理解就是：undefined 是没有定义的，null 是定义了但是为空。

## null 不存在的原因是什么？如何解决
不存在的原因是：
* 1、方法不存在
* 2､对象不存在
* 3､字符串变量不存在
* 4､接口类型对象没初始化 

__解决方法：__ 做判断处理的时候，放在设定值的最前面

## == 和 === 有什么区别，什么场景下使用？
* == 表示相同。
比较的是物理地址，相当于比较两个对象的 hashCode ，肯定不相等的。
类型不同，值也可能相等。

* === 表示严格相同。
例：同为 null／undefined ，相等。

简单理解就是 == 就是先比较数据类型是否一样。=== 类型不同直接就是 false。

## Undefined 与 Null 的区别
Undefined 与 null 的值相等，但类型不相等：
![](13.png)