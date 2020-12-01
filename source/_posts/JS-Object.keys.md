---
title: Object.keys方法
date: 2020-11-19 20:49:01
tags: js
categories: js
cover: /assets/cover-js.png
---

### array类型
有时候接口返回的对象里的字段是对象形式或者数组形式，需要 __判断__ 字段里的值或者字段里是否有值
直接用  字段===[]或字段===null判断时，有时会失效
![](1.png)
![](2.png)
这时就需要转换思路，判断字段里的值的长度，
同样适用于Object.kdys({...数组}).length，
__注：__ 数组在使用此方法判断时，需要先转化为对象形式（外包大括号，并加三个点）{...数组}
当Object.kdys({...数组}).length>0为true时，说明数组里有值，为false则空
![](3.png)

### object类型
```
 Object.keys(对象).length>0
```
![](4.png)