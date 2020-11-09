---
title: react生命周期函数
tags: react
categories: 
    - [框架,react/antd,知识点]
cover: https://upload-images.jianshu.io/upload_images/11060508-3d58ff4aa4dc20c8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
---
## 概念
在组件创建、组件属性更新、组件被销毁的过程中，总是伴随着各种各样的函数执行，这些在组件特定时期，被触发执行的函数，统称为组件的生命周期函数。

## 组件生命周期的三个阶段

 * Mounting：已插入真实DOM
 只在第一次渲染时执行
 * Ｕpdation：正在被重新渲染
 数据发生改变会触发updation
 * Ｕnmounting：已移出真实DOM
 ![image.png](https://upload-images.jianshu.io/upload_images/11060508-22e6206e2d371370.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)