---
title: hexo图片显示问题
date: 2020-11-03 15:29:08
tags: hexo
categories: 
    - [hexo]
cover: cover.png
---

## hexo图片在本地显示，但是上传到github里后，在通过github的地址去看就没有显示。

本地首页图：
![本地背景图](1.png)

github地址打开没有显示首页图：
![github不显示首页图](2.png)

去gitbub里查看代码，明明是上传成功了，但就是不显示图片，想着是不是因为是网上下载的图片地址的原因，就下载图片到img文件里，也还是在本地显示，在github里不显示。
去网上搜原因
找到最多的答案都是要下载插件（网上的解决办法： https://blog.csdn.net/qq_36408085/article/details/104117319 ）

但是感觉有点麻烦，也不太想下载插件。在github地址打开的网页里F12审查元素，找到首页图的标签位置。看到在css栏里background-image警示的是  __invalid property value__

## 最终解决办法
通过 __简书__ ,打开简书 __写文章__
![image.png](3.png)


把点击 __图片复制__ 后，直接在简书的编辑栏里 __粘贴__ ，就会自动转变为md格式的图片代码
![image.png](4.png)

把 __括号里的的图片地址__ 复制到_config,yml里设置背景图的地方
![image.png](5.png)

再上传到github里，从github地址里打开就会显示了

这个方法也适用于其他图片的显示，因为简书里就是把图片转化成md格式的图片地址，把里面全部复制到要写的md格式页面就可以直接显示图片
![image.png](6.png)

包括 __本地图片需要转换为图片地址__ 也适用此方法。主要可以不用将图片再保存带img文件夹里，可以节省本地文件内存。

__注：__
使用简书转化图片，需要将简书里的文章发布或者保存，否则过几天，临时图片将会被清空，若不想麻烦使用简书，就将图片下载到img文件里。缺点就是，图片多的话会文件会比较大。

## 本地上传图片方法
安装插件
```
npm install https://github.com/CodeFalling/hexo-asset-image --save
```
打开_config.yml文件,搜索post_asset_folder
将其改为true
![如图](8.png)
之后新建post文件时，会自动增加一个同级同名的文件夹
之后在同名文件夹里放置图片
![文件](7.png)

如果已经建了的md文件，只需要在同级下自己再新建一个同名的文件夹即可。
