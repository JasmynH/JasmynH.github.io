---
title: bizcharts水滴图
date: 2020-12-02 10:15:23
tags: bizcharts
cover: /assets/cover-bizcharts.png
categories: 
    - [框架,bizCharts]
---
水滴图只有3.x版本有，4.x版本没有
官方给的水滴图案例
![](1.png)
但是那个高度太长了，需要调小，直接在charts中设置设置height，设置比较小的时候（如设置80）就容易出现顶部和底部被削掉了的样式问题
![](2.png)
这个问题困扰了我许久，后来发现了一个属性就是 __<Coord scale={[0.7, 0.7]} />__ ，他会把水滴图整体缩小，这样就能解决顶部和底部被削掉的问题
![](3.png)
中间的百分比文字
![](4.png)


