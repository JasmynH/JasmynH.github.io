---
title: 引入图标（阿里巴巴矢量图库）
date: 2020-11-30 15:22:17
tags: 
    - [react]
    - [icon]
categories: 
    - [框架,react,icon]
cover: /assets/cover-react.png
---
## 方法一（在线引用）
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
## 方法二(下载引用)
前几步与方法一相同，添加至项目后
![](6.png)
下载完成后最后阿斗啊iconfont.js文件，并复制
![](7.png)
将iconfont.js文件复制到项目里（如果之前复制过相同名字的文件，就重命名后再粘贴）
之后在需要引入图标的页面里引入文件
```
const MyIcon = Icon.createFromIconfontCN({
    scriptUrl: 'js/common/iconfont.js', //iconfont.js文件的路径
});
```
引用图标
```
<MyIcon type="icon-huifu"/>
```

