---
title: vue3-suspense异步组件
date: 2020-12-14 16:18:14
tags: 
 - vue3
 - typescript
cover: /assets/cover-vue.png
categories: 
- [框架,vue,vue3]
---
## suspense用法

处理异步使用`<Suspense></template>`包裹，当数据在请求中是使用`<template #fallback>`，请求完成后使用`<template #default>`
## 案例
数据请求中显示Loading，q请求完成后显示数据
* 请求中
![](1.png)
* 请求后
![](2.png)
## App.vue 代码
![](3.png)
```
<template>
  <div>
   <Suspense>
     <!-- 请求回来的结果 -->
     <template #default> <AsyncShow/></template>
     <!-- 还未请求回来，加载中 -->
      <template #fallback>
       <h1>Loadding...</h1>
     </template>
   </Suspense>
  </div>
</template>

<script lang="ts">
import AsyncShow from "./components/AsyncShow.vue"
export default {
  name: "App",
  components:{AsyncShow},
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

## AsyncShow.vue 代码
![](4.png)
```
<template>
    <h1>{{result}}</h1>
</template>
<script lang="ts">
// defineComponent 会提示
import {defineComponent} from "vue"
export default defineComponent({
    setup() {
        return new Promise((resolve,reject)=>{
            setTimeout(() => {
                return resolve({result:'珈'})
            }, 2000);
        })
    }
})
</script>
```
