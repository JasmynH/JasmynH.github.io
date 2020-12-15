---
title: vue3-creatApp创建vue实例
date: 2020-12-15 17:04:30
tags: 
    - [vue3]
    - [vue]
cover: /assets/cover-vue.png
categories: 
    - [框架,vue,vue3]
---

新建一个html文件，使用！或者html:5快捷创建html页面基础代码，引用`<script src="https://unpkg.com/vue@next"></script>`，使用`createApp`挂载内容到某节点

## 案例一
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=\, initial-scale=1.0">
    <title>Document</title>
    <script src="https://unpkg.com/vue@next"></script>
</head>
<body>
    <div id="app"></div>
</body>
<script>
    Vue.createApp({  //创建一个vue实例
        template:'<div>Hello World!</div>'
    }).mount("#app")
</script>
</html>
```
## 案例二————计数器
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=\, initial-scale=1.0">
    <title>计数器</title>
    <script src="https://unpkg.com/vue@next"></script>
</head>
<body>
    <div id="app"></div>
</body>
<script>
    Vue.createApp({  //创建一个vue实例
        data(){
            return{
                counter:1
            }
        },
        mounted() {
            setInterval(()=>{
                // this.counter写法相当于this.$data.counter
                this.counter+=1
            },1000)
        },
        template:'<div>{{counter}}</div>'
    }).mount("#app")
</script>
</html>
```