---
title: hexo图片显示问题
date: 2020-11-03 15:29:08
tags: hexo
categories: 
    - [框架,react/antd]
    - [hexo]
    
---

## hexo图片在本地显示，但是上传到github里后，在通过github的地址去看就没有显示。

本地首页图：
![本地背景图](https://upload-images.jianshu.io/upload_images/11060508-a7fd51dfe44ccbed.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

github地址打开没有显示首页图：
![github不显示首页图](https://upload-images.jianshu.io/upload_images/11060508-61bccb319e2a262a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

去gitbub里查看代码，明明是上传成功了，但就是不显示图片，想着是不是因为是网上下载的图片地址的原因，就下载图片到img文件里，也还是在本地显示，在github里不显示。
去网上搜原因
找到最多的答案都是要下载插件（网上的解决办法： https://blog.csdn.net/qq_36408085/article/details/104117319 ）

但是感觉有点麻烦，也不太想下载插件。在github地址打开的网页里F12审查元素，找到首页图的标签位置。看到在css栏里background-image警示的是  __invalid property value__

## 最终解决办法
通过 __简书__ ,打开简书 __写文章__
![image.png](https://upload-images.jianshu.io/upload_images/11060508-c50e18b4a769eee9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


把点击 __图片复制__ 后，直接在简书的编辑栏里 __粘贴__ ，就会自动转变为md格式的图片代码
![image.png](https://upload-images.jianshu.io/upload_images/11060508-144c3ee370a2ae90.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

把 __括号里的的图片地址__ 复制到_config,yml里设置背景图的地方
![image.png](https://upload-images.jianshu.io/upload_images/11060508-1c2de84210b415bd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

再上传到github里，从github地址里打开就会显示了

这个方法也适用于其他图片的显示，因为简书里就是把图片转化成md格式的图片地址，把里面全部复制到要写的md格式页面就可以直接显示图片
![image.png](https://upload-images.jianshu.io/upload_images/11060508-c0918b6fc9e96dfd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

包括 __本地图片需要转换为图片地址__ 也适用此方法。主要可以不用将图片再保存带img文件夹里，可以节省本地文件内存。