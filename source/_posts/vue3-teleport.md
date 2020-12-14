---
title: vue3-teleport组件
date: 2020-12-10 17:05:08
cover: /assets/cover-vue.png
tags:
- vue
- vue3
- typescript
categories: 
- [框架,vue,vue3]
---
__案例__

## 未使用teleport组件时
### 效果
![](1.png)

### app.vue代码
```
<template>
  <div>
    <h2>练习axios</h2>
    <div>随机显示</div>
    <modal/>
    <div v-if="loading">Loading...</div>
    <img v-if="!loading" :src="result.imgUrl" />
  </div>
</template>

<script lang="ts">

// 使用axios远程访问接口
import urlAxios from "./hooks/mod-UrlAxios";
import modal from "./components/Modal.vue" //teleport组件案例model
export default {
  name: "App",
  components:{
    modal
  },
  setup() {
    const { result, loading } = urlAxios(
      "https://apiblog.jspang.com/default/getGirl"
    );
    return {
      result,
      loading,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
```
### model.vue组件代码
```
<template>
    <div>
        <div id="center">
            <h2>XXXXX</h2>
        </div>
    </div>
</template>
<script lang="ts">
export default {
    
}
</script>
<style>
#center{
    width: 200px;
    height: 200px;
    border: 1px solid #000;
    background: #fff;
    position: fixed;
    left: 50%;
    top: 50%;
    margin-left: -100px;
    margin-top: -100px;
}
</style>
```
### ts组件代码
```
import { ref } from 'vue'
import axios from 'axios'
// url:string，只接受字符串（远程地址）
function urlAxios(url: string) {
    const result = ref(null)
    const loading = ref(true)
    const error = ref(null)

    axios.get(url).then(res => {
        loading.value = false
        result.value = res.data
    }).catch(err => {
        error.value = err
        console.log('err',err)
        loading.value = false
    })
    return { result, loading, error }
}
export default urlAxios
```
![](3.png)
但是F12审查元素
center这个div在app这个div里
样式有点小问题，原本center（div）并未设置文字居中，因为app（div）里设置了文字居中，所以XXXXX居中了
## 使用teleport组件后

![](2.png)
![](4.png)
效果
![](5.png)
因为center（div)未在app(div)的里层了，所以XXXXX没有受app（div)的影响，文字没居中了