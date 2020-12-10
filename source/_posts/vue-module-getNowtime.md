---
title: vue3模块化案例（获取当前日期时间）new Data()
date: 2020-12-10 14:42:24
tags: vue3
categories: 
- [框架,vue,vue3]
cover: /assets/cover-vue.png
---
## new Date()获取日期时间
| | |
| --- | --- |
|getYear|获取当前年份（2位）|
|getFullYear|获取完整年份（4位）|
|getMonth|获取当前月份（0-11），写法 __getMonth()+1__|
|getDate|获取当前日（1-31）|
|getDay|获取当前星期（0-6），0为周日|
|getTime|获取当前时间（从1970.1.1开始的毫秒数）|
|getHours|获取当前小时数（0-23）|
|getMinutes|获取当前分钟数（0-59）|
|getSeconds|获取当前秒数（0-59）|
|getMilliseconds|获取当前毫秒数（0-999）|
|toLocaleDateString|获取当前日期，如：2020/12/10|
|toLocaleTimeString|获取当前时间，如：下午3:19:45|
|toLocaleString|获取当前日期和时间，如：2020/12/10 下午3:19:45|

## 案例
实现点击获取时钟
![](3.png)
点击后
![](4.png)
代码
![](1.png)
![](2.png)

