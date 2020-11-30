---
title: react生命周期函数
tags: react
date: 2020-11-25 12:40:19
categories: 
    - [框架,react]
cover: /img/cover-react.png
---
## 概念
在组件创建、组件属性更新、组件被销毁的过程中，总是伴随着各种各样的函数执行，这些在组件特定时期，被触发执行的函数，统称为组件的生命周期函数。

## 组件生命周期的三个阶段

 * Mounting：已插入真实DOM
 只在第一次渲染时执行
 * Ｕpdation：正在被重新渲染
 数据发生改变会触发updation
 * Ｕnmounting：已移出真实DOM