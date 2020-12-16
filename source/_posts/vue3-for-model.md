---
title: vue3-循环（v-for）、双向绑定（v-model）、组件（component）
date: 2020-12-16 17:38:45
tags:
- vue
- vue3
categories: 
- [框架,vue,vue3]
cover: /assets/cover-vue.png
---
## 案例一（循环、双向绑定）
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=\, initial-scale=1.0">
    <title>列表</title>
    <script src="https://unpkg.com/vue@next"></script>
</head>
<body>
    <div id="app"></div>
</body>
<script>
    Vue.createApp({ 
        data(){
            return{
                list:[],
                inputValue:''
            }
        },
        methods: {
            handleAddItem(){
                this.list.push(this.inputValue)
                this.inputValue=''
            }
        },
        // v-model:数据双向绑定
        template:`
            <div>
                <input v-model="inputValue"/>
                <button v-on:click="handleAddItem">增加</button>
                <ul>
                    <li v-for="(item,index) of list">[{{index}}]{{item}}</li>
                </ul>
            </div>
            `
    }).mount("#app")
</script>
</html>
```
![](1.png)

## 案例二（组件）
![](2.png)
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=\, initial-scale=1.0">
    <title>列表</title>
    <script src="https://unpkg.com/vue@next"></script>
</head>
<body>
    <div id="app"></div>
</body>
<script>
    // 赋值成变量
   const app= Vue.createApp({ 
        data(){
            return{
                list:[],
                inputValue:''
            }
        },
        methods: {
            handleAddItem(){
                this.list.push(this.inputValue)
                this.inputValue=''
            }
        },
        // v-model:数据双向绑定
        template:`
            <div>
                <my-component/>  <!-- 组件引用 -->

                <input v-model="inputValue"/>
                <button v-on:click="handleAddItem">增加</button>
                <ul>
                    <my-list
                        v-for="(item,index) of list"
                        v-bind:item="item"
                        v-bind:index="index"
                    />
                    <!-- 使用v-bind绑定数据传递给子组件 -->
                </ul>
            </div>
            `
    })
    // 声明一个单独的组件（参数一：组件名称，参数二：内容）
    // 静态组件
    app.component('my-component',{
        template:`<h2 style="text-align:center">标题XXXX</h2>`
    })
    // 动态组件（v-bind传值）
    app.component('my-list',{
        // 没有item和index，需要通过props接收父组件传来的参数
        props:['index','item'],
        template:`<li>[{{index}}]-{{item}}</li>
        `
    })
    // 要先声明组件，之后在mount绑定
    app.mount("#app")
</script>
</html>
```
