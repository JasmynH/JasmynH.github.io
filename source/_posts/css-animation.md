---
title: css-animation动画
date: 2020-12-23 15:19:56
tags: 
- css
- 基础 
categories:
- [基础,css]
---
## animation属性详细介绍
https://www.jianshu.com/p/a7ffdd72c199

## 案例特效
动态效果网站：https://www.17sucai.com/pins/tag/8524.html
基本动态效果：https://www.17sucai.com/pins/demo-show?id=10148
（直接用F12省查元素就可查看代码）

### 闪烁效果
```
<div class="flash"></div>
```
```
.flash {
    width：100px；
    height：100px；
    background:lightblue;

    -webkit-animation: lightAnimate 3s ease infinite;
    -moz-animation: lightAnimate 3s ease infinite;
    -o-animation: lightAnimate 3s ease infinite;
    -ms-animation: lightAnimate 3s ease infinite;
    /* 以上为处理兼容 */
    animation: lightAnimate 3s ease infinite;
}

@keyframes lightAnimate {

    0%,
    50%,
    100% {
        opacity: 1;
    }

    25%,
    75% {
        opacity: 0;
    }
}
```