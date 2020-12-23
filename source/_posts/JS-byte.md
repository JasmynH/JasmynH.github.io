---
title: 字节数
date: 2020-12-04 11:03:29
tags: js
categories: 
    - [基础,js]
cover: /assets/cover-js.png
---
## 简介
数据存储是以“字节”（Byte）为单位，数据传输大多是以“位”（bit，又名“比特”）为单位，一个位就代表一个0或1（即二进制），每8个位（bit，简写为b）组成一个字节（Byte，简写为B），是最小一级的信息单位;
8个二进制位构成1个"字节(Byte)"，它是存储空间的基本计量单位。1个字节可以储存1个英文字母或者半个汉字，换句话说，1个汉字占据2个字节的存储空间.
## 计算字节数
```
const strLen=(str)=>{
    return str.replace(/[^x00-xFF]/g,'**').length;
}
console.log(strLen('112测试')) //7
```

```
var arr='12测试x8'
function strLen(str) {
// 在GBK编码里，除了ASCII字符，其它都占两个字符宽
return str.replace(/[^\x00-\xff]/g, 'xx').length;}
console.log(strLen(arr))//8
```
```
var lenFor = function(str){
　　var byteLen=0,len=str.length;
　　if(str){
　　　　for(var i=0; i<len; i++){
　　　　　　if(str.charCodeAt(i)>255){
　　　　　　　　byteLen += 2;
　　　　　　}
　　　　　　else{
　　　　　　　　byteLen++;
　　　　　　}
　　　　}
　　　　return byteLen;
　　}
　　else{
　　　　return 0;
　　}
}
console.log(lenFor('2测试test')
```