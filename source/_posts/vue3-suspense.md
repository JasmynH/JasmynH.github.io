---
title: vue3-suspense异步组件
date: 2020-12-14 16:18:14
tags: 
 - vue3
 - vue
 - typescript
cover: /assets/cover-vue.png
categories: 
- [框架,vue,vue3]
---
## suspense用法

处理异步使用`<Suspense></template>`包裹，当数据在请求中是使用`<template #fallback>`，请求完成后使用`<template #default>`
## 简单案例1
数据请求中显示Loading，请求完成后显示数据
* __请求中__
![](1.png)
* __请求后__
![](2.png)
### App.vue 代码
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

### AsyncShow.vue 代码
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
## 简单案例2
请求接口异步处理,
`<async-show-2/>`（带“-”式）和`<AsyncShow2/>`（驼峰式）都可
使用onErrorCaptured捕获异常，要求必须要返回一个布尔值（true：向上反馈传递错误；false不传递）
### App.vue代码、
```
<template>
  <div>
   <Suspense>
     <!-- 请求回来的结果 -->
     <template #default>
       <!-- 可用驼峰式、页可用“-”区分式 -->
       <async-show-2/>
     </template>
     <!-- 还未请求回来，加载中 -->
      <template #fallback>
       <h1>Loadding...</h1>
     </template>
   </Suspense>
  </div>
</template>

<script lang="ts">
import AsyncShow2 from "./components/AsyncShow2.vue"
import {onErrorCaptured} from 'vue'
export default {
  name: "App",
  components:{AsyncShow2},
  setup(){
    // 捕获异常
    onErrorCaptured((error)=>{
      console.log('error=>',error)
      // onErrorCaptured要求必须return布尔值（true：向上反馈传递错误；false不传递）
      return true
    })
  }
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
### AsyncShow2.vue代码
```
<template>
    <div>
       <!-- <img :src="result && result.imgUrl" />  -->
       接口内容：{{result}}
    </div>
</template>
<script lang="ts">
import {defineComponent} from 'vue'
import axios from 'axios'//axios请求接口
export default defineComponent({
    async setup(){
        const res=await axios.get('https://apiblog.jspang.com/default/getGirl')
        return {
            result:res.data
        }
    }
})
</script>
```
### 尝试捕获异常
将接口写错`https://apiblog.jspang.com/default/getGirl---1`之后运行出来，控制台显示
![](5.png)