---
title: vue3小案例1
date: 2020-12-09 10:29:38
tags: 
    - [vue3]
    - [typescript]
categories: 
    - [框架,vue,vue3]
cover: /assets/cover-vue.png
---
实现点击哪个按钮就显示哪个服务员
![](1.png)
```
<template>
  <div>
      <img alt="Vue logo" src="./assets/logo.png">
      <h2>欢迎光临</h2>
      <div>请选择</div>
      <div>
          <button 
            v-for="(item,index) in waiters" 
            v-bind:key="index"
            @click="selectWaiterFun(index)"
          >
            {{index}}:{{item}}
          </button>
          
      </div>
      <div>你选择了：【{{selectWaiter}}】服务员</div>
  </div>
  

</template>

<script lang="ts">
import { defineComponent,ref } from 'vue';

export default defineComponent({
  name: 'App',
  // setup是vue3的写法，vue2的写法是data:{}，method:{}
  setup(){
    const	waiters=ref(['jack','emma','jean'])
    const selectWaiter=ref("")
    const selectWaiterFun=(index: number)=>{
      // 在js和ts代码中，所有使用了ref的，要改变值或获取值，需要加.value，html中不需要加value
      selectWaiter.value=waiters.value[index];
    }
    return{
      // 定义的在template中需要使用的就return
      waiters,
      selectWaiter,
      selectWaiterFun
    }
  }
});
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
* __注：__

## template里面需要再包裹一层才可以写

```
<template>
    <div>
        <div>写内容</div>
        <div>写内容</div>
    </div>
<template>
```
不能这样多层直接写，有的会报错
```
<template>
    <div>写内容</div>
    <div>写内容</div>
<template>
```
## setup(){}
* setup是vue3的写法，vue2的写法是data:{}，method:{}
* 如果需要setup里的数据不仅用于ts/js中，需用于整页，就需要retrun数据，仅用于ts/js中就无需return
* 在js和ts代码中，所有使用了ref的，要改变值或获取值，需要加.value，html中不需要加value
ts中需要加
```
selectWaiter.value=waiters.value[index];
```
html中不需要加value
```
<div>你选择了：【{{selectWaiter}}】服务员</div>
```
