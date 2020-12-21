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
cover: /assets/cover-react.png
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

 ### 凭借字符串并加'\n'（不使用dangerouslySetInnerHTML）
 ```
 var str='123'
var str1='nana'
var str2='jia'
console.log(str+'\n'+str1+'\n'+str2)
```