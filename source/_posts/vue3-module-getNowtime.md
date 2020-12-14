---
title: vue3模块化案例（获取当前日期时间）new Data()
date: 2020-12-10 14:42:24
tags: 
- [vue3]
- [vue]
- [typescript]
categories: 
- [框架,vue,vue3]
cover: /assets/cover-vue.png
---
## new Date()获取日期时间
| | |
| --- | --- |
|getYear|获取当前年份（2位）|
|getFullYear|获取完整年份（4位）|
|getMonth|获取当前月份（0-11），写法 __getMonth()+1__|
|getDate|获取当前日（1-31）|
|getDay|获取当前星期（0-6），0为周日|
|getTime|获取当前时间（从1970.1.1开始的毫秒数）|
|getHours|获取当前小时数（0-23）|
|getMinutes|获取当前分钟数（0-59）|
|getSeconds|获取当前秒数（0-59）|
|getMilliseconds|获取当前毫秒数（0-999）|
|toLocaleDateString|获取当前日期，如：2020/12/10|
|toLocaleTimeString|获取当前时间，如：下午3:19:45|
|toLocaleString|获取当前日期和时间，如：2020/12/10 下午3:19:45|

## 案例
实现点击获取时钟
![](3.png)
点击后
![](4.png)
__代码解析__
![](1.png)
![](2.png)

__app.vue代码__
```
<template>
  <div>
    <div>
      {{nowTime}}
    </div>
    <button @click="getNowTime">执行</button>
  </div>
</template>

<script lang="ts">
import {nowTime,getNowTime} from './hooks/mod-getNowTime'
import {
  ref,
} from "vue";

export default {
  name: "App",
  setup() {
    return{
      nowTime,
      getNowTime,
    }
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
__ts代码__
```
import {
    ref,
} from "vue";
const nowTime = ref("00:00:00")
const getNowTime = () => {
    const now = new Date();
    const year = now.getFullYear()
    const month = now.getMonth() + 1
    const date = now.getDate()
    const hour = now.getHours() < 10 ? "0" + now.getHours() : now.getHours();
    const minu = now.getMinutes() < 10 ? "0" + now.getMinutes() : now.getMinutes();
    const sec = now.getSeconds() < 10 ? "0" + now.getSeconds() : now.getSeconds();
    nowTime.value = year + '年' + month + '月' + date + '日' + hour + ":" + minu + ':' + sec;
    setTimeout(getNowTime, 1000)
}
export { nowTime, getNowTime }
```
