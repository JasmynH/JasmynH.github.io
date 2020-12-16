---
title: 前端页面对后端数据换行显示-dangerouslySetInnerHTML
date: 2020-12-16 10:47:53
tags: 
    - js
    - 基础
    - react
categories: 
    - js
    - 基础
    - [框架,react]
---
## react方法
### 当后后端传过来的数据是是`<br/>`，前端需要自动识别，并换行
 ```
 <p dangerouslySetInnerHTML={{__html:data}}></p>
 ```

### 当后后端传过来的数据是有`\n`，前端需要自动识别，并换行
data为获取的需要转换的数据
 ```
 <p dangerouslySetInnerHTML={{__html:String(data).replace(/[\r\n]/g, '<br/>')}}></p>
 ```