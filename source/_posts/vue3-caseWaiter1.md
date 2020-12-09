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
## 方法一-ref()
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
## 方法二-reactive()
```
<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png" />
    <h2>欢迎光临</h2>
    <div>请选择</div>
    <div>
      <button
        v-for="(item, index) in waiters"
        v-bind:key="index"
        @click="selectWaiterFun(index)"
      >
        {{ index }}:{{ item }}
      </button>
    </div>
    <div>你选择了：【{{ selectWaiter }}】服务员</div>
  </div>
</template>

<script lang="ts">
// reactive()优化
import { ref,reactive,toRefs } from "vue";

// ts为了程序的严谨，添加类型注解
interface DataProps {
  waiters: string[];
  selectWaiter: string;
  selectWaiterFun: (index: number) => void;
}
export default {
  name: "App",
  // setup是vue3的写法，vue2的写法是data:{}，method:{}
  setup() {
    // 使用reactive好处是，改变或获取值无需再写value，还可以减少return里的参数
    const data: DataProps = reactive({
      waiters: ["jack", "emma", "jean"],
      selectWaiter: "",
      selectWaiterFun: (index: number) => {
        data.selectWaiter = data.waiters[index];
      },
    });
    // 用toRefs定义data，再template里使用数据就无需在再用data.了，可以直接使用data里面的属性
    const refData=toRefs(data);
    return {
      // 使用扩展运算符
      ...refData,
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
## Ref()和reactive()
都是把普通的数据变成有响应能力的数据，可用于整页可用的数据