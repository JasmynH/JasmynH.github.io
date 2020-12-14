---
title: vue3-axios
date: 2020-12-10 15:37:51
tags: 
- vue3
- vue
- typescript
categories: 
- [框架,vue,vue3]
cover: /assets/cover-vue.png
---

## axios安装
```
npm install axios --save
```
--save在正式的生产环境中也可以进行使用
所以不能使用dev--save

## 案例代码
### ts代码
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

### app.vue代码
```
<template>
  <div>
    <h2>练习axios</h2>
    <div>随机显示</div>
    <div v-if="loading">Loading...</div>
    <img v-if="!loading" :src="result.imgUrl" />
    <!-- 接口数据：imgUrl: "https://newimg.jspang.com/honglangman_2.jpg" -->
  </div>
</template>

<script lang="ts">

// 使用axios远程访问接口
import urlAxios from "./hooks/mod-UrlAxios";

export default {
  name: "App",
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
### 实现效果
每次接口只随机返回一张图片，图片出现，说明axios接口请求成功
![](1.png)