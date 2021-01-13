---
title: vue2-component
date: 2020-12-28 11:00:55
tags:
- vue
- vue2
categories: 
- [框架,vue,vue2]
cover: /assets/cover-vue.png
---
# template
## 全局组件
```
<div id="app">
    <!-- 组件只能在#app下使用 -->
    <study></study>
</div>
<script type="text/javascript">
    Vue.component('study',{
        template:`<div style="color:red">全局的study组件</div>`
    })
    var app =new Vue({
        // el的命名需要需要挂在的div的id名对应上
        el:"#app",
        data:{
        },
    })
</script>
```
## 局部组件
```
<div id="app">
    <panda></panda>
</div>
<script type="text/javascript">
    var app =new Vue({
        el:"#app",
        data:{
        },
        components:{
            "panda":{
                template:`<div style="color:lightgreen">局部的panda组件</div>`
            }
        }
    })
</script>
```