---
title: 引入图标（阿里巴巴矢量图库）
date: 2020-11-30 15:22:17
tags: 
    - [react]
    - [icon]
categories: 
    - [框架,react,icon]
cover: /img/cover-react.png
---
【提前登录巴里巴巴矢量图库】

挑选图标，将选中的图标加入购物车
![](2.png)
选择好图标加购完成后，再点击右上角的购物车图标进入购物车
![](3.png)
点击添加至项目，并取好项目名

![](4.png)
![](5.png)
点击symbel，之后再点击图标的编辑，提前选好图标颜色
![](1.png)
之后在页面引用IconFont
```
import { createFromIconfontCN } from '@ant-design/icons'; 
const IconFont = createFromIconfontCN({ scriptUrl: '//at.alicdn.com/t/font_2237835_wpvhd8k09qp.js', });
<!-- scriptUrl里的地址是之前复制的地址 -->
```
```
<IconFont type="icon-tiaodu" style={{fontSize: 55 }} />
```
