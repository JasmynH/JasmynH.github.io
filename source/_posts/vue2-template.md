---
title: vue2-template
date: 2020-12-28 09:29:49
tags:
- vue
- vue2
categories: 
- [框架,vue,vue2]
cover: /assets/cover-vue.png
---
template的三种写法
## 第一种（选项模板）
方法一：适合小模板，几句代码
```
<script type="text/javascript">
    var app =new Vue({
        el:"#app",
        data:{
            message:'hello World!!!!'
        },
        template:`
            <h2 style="color:red">我是选项模板</h2>
        `
    })
</script>
```
## 第二种（template标签模板）
适合大模板,可以把初级前端工程师切的图直接粘贴到template标签里
```
<h1>HelloWorld</h1>
    <hr>
    <div id="app">
        {{message}}
    </div>

    <template id="demo2">
        <h2 style="color:lightblue">我是template标签模板22222</h2>
    </template>
    <script type="text/javascript">
        var app =new Vue({
            el:"#app",
            data:{
                message:'hello World!!!!'
            },
            template:"#demo2"
        })
    </script>
```

## 第三种（script标签模板）
可以在script标签里用src外部引用模板，让页面更简洁
```
<script type="XTemplate" id="demo3" src="">
    <h2 style="color:lightgreen">我是script标签模板3333</h2>
</script>
<script type="text/javascript">
var app =new Vue({
    el:"#app",
    data:{
        message:'hello World!!!!'
    },
    template:"#demo3"
})
```
