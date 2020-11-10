---
title: hexo页面添加分类（categories）
date: 2020-11-09 15:29:08
tags: hexo
categories: 
    - [hexo]
cover: cover.png
---

### 页面添加单个分类
方法一：
```
categories: 
    - [hexo6]
```
方法二：
```
categories: [hexo6]
```
方法三：
```
categories: hexo6
```
效果图：
![image.png](1.png)
### 页面添加一个子级分类
方法一：
```
categories: 
    - hexo4
    - hexo5
```
方法二：
```
categories:[hexo4,hexo5]
```
效果图：
![image.png](2.png)

### 页面添加多个同级分类
```
categories: 
    - [hexo4]
    - [hexo5]
```
效果图：
![image.png](3.png)

### 页面添加多个不同级分类
```
categories: 
    - [hexo7,hexo8]
    - [hexo9]
```
效果图：
![image.png](4.png)

写的时候需要注意空格和格式