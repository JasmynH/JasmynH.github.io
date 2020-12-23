---
title: 数组遍历循环
date: 2020-11-20 14:10:09
tags: 
    - [js]
    - [JQ]
categories: 
    - [基础,js]
    - [基础,JQ]
cover: /assets/cover-js.png
---
## JS数组遍历
### for循环遍历
```
for(j = 0; j < arr.length; j++) {
   
}
### map
```
points.map((item,index)=>{
     console.log('item2',item)
     console.log('index2',index)
})
```

### forEach
```
arr.forEach((item,index)=>{
    console.log('item3',item)//单条
    console.log('index3',index)//下标
})
```
## JQ遍历循环
### $.each
$.each()是对数组，json和dom结构等的遍历
```
$.each(arr,function(index,item){
     console.log('index',index)
     console.log('item',item)
})
```

