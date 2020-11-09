---
title: hexo页面添加分类（categories）
date: 2020-11-09 15:29:08
tags: hexo
categories: [hexo]
---

### 页面添加单个分类
方法一：
```
categories: 
    - [hexo]
```
方法二：
```
categories: [hexo]
```
方法三：
```
categories: hexo
```
效果图：
![image.png](https://upload-images.jianshu.io/upload_images/11060508-11fb565cef0b7b54.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
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
![image.png](https://upload-images.jianshu.io/upload_images/11060508-0ba19633abf4fe72.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 页面添加多个同级分类
```
categories: 
    - [hexo]
    - [hexo2]
```
效果图：
![image.png](https://upload-images.jianshu.io/upload_images/11060508-ad1a2dd6961e86d3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 页面添加多个不同级分类
```
categories: 
    - [框架,hexo]
    - [hexo]
```
效果图：
![image.png](https://upload-images.jianshu.io/upload_images/11060508-45d260067372ff2d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

写的时候需要注意空格和格式