---
title: vue生命周期、钩子函数
date: 2020-12-09 16:17:31
tags: vue
categories: 
    - [框架,vue]
cover: /assets/cover-vue.png
---
## 生命周期函数对比
|vue3|vue2||
|---|---| --- |
|setup|可以与beforeCreate和created对应| 在组件 __创建__ 之前，也在beforeCreate和created之前执行，创建data和method|
| |beforeCreate|组件 __创建__ 之前|
| |created|组件创建之后 |
|onBeforeMount|beforeMount|组件 __挂载__ 到节点之前执行|
|onMounted|oMouted|组件挂载到节点之后执行|
|onBeforeUpdate|beforeUpdate|组件 __更新__　之前执行|
|onUpdated|updated|组件更新之后执行|
|onBeforeUnmount|beforeDestroy|在组件 __卸载__ 之前执行|
|onUnmounted|destroyed|组件卸载之后 执行|
|onActivated|activated|__激活__ 时执行（`<keep-alive></keep-alive>`组件中能使用）|
|onDeactivated|deactivated| 比如从 A 组件，切换到 B 组件，A 组件消失时执行（`<keep-alive></keep-alive>`组件中能使用）|
|onErrorCaptured|errorCaptured| 当捕获一个来自子孙组件的  __异常__ 时激活钩子函数|
|onRenderTrackered ||状态跟踪，参数event【vue3新增】|
|onRenderTriggered||状态触发，参数event【vue3新增】|

主要使用： __创建前后——>挂载前后 ——> 更新前后 ——> 卸载前后__

## vue3声明周期函数-案例
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
import {
  ref,
  reactive,
  toRefs,
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onRenderTracked,
  onRenderTriggered,
} from "vue";
interface DataProps {
  waiters: string[];
  selectWaiter: string;
  selectWaiterFun: (index: number) => void;
}
export default {
    name: "App",
    setup() {
        console.log("1-开始创建组件--setup");
        // 使用reactive好处是，改变或获取值无需再写value，还可以减少return里的参数
        const data: DataProps = reactive({
        waiters: ["jack", "emma", "jean"],
        selectWaiter: "",
        selectWaiterFun: (index: number) => {
            data.selectWaiter = data.waiters[index];
        },
        });

        onBeforeMount(() => {
        console.log("2-组件挂载到页面之前执行--onBeforeMount");
        });
        onMounted(() => {
        console.log("3-组件挂载到页面之后执行--onMounted");
        });
        onBeforeUpdate(() => {
        console.log("4-组件更新之前执行--onBeforeUpdate");
        });
        onUpdated(() => {
        console.log("5-组件更新之后执行--onUpdated");
        });
        // 用toRefs定义data，再template里使用数据就无需在再用data.了，可以直接使用data里面的属性
        const refData=toRefs(data);
        return {
        // 使用扩展运算符
        ...refData,
        };
    },
};
```
![](1.png)
## vue3和vue2案例对比
vue3生命周期函数写在setup里，并且需要提前在import里导入
vue2生命周期函数写在setup外
```
import {
  ref,
  reactive,
  toRefs,
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onRenderTracked,
  onRenderTriggered,
} from "vue";

// ts为了程序的严谨，添加类型注解(不让ts自己进行类型推断)
interface DataProps {
  waiters: string[];
  selectWaiter: string;
  selectWaiterFun: (index: number) => void;
}
export default {
  name: "App",
  // setup是vue3的写法，vue2的写法是data:{}，method:{}
  setup() {
    console.log("1-开始创建组件--setup");
    // 使用reactive好处是，改变或获取值无需再写value，还可以减少return里的参数
    const data: DataProps = reactive({
      waiters: ["jack", "emma", "jean"],
      selectWaiter: "",
      selectWaiterFun: (index: number) => {
        data.selectWaiter = data.waiters[index];
      },
    });
    onBeforeMount(() => {
      console.log("2-组件挂载到页面之前执行--onBeforeMount");
    });
    onMounted(() => {
      console.log("3-组件挂载到页面之后执行--onMounted");
    });
    onBeforeUpdate(() => {
      console.log("4-组件更新之前执行--onBeforeUpdate");
    });
     onUpdated(() => {
      console.log("5-组件更新之后执行--onUpdated");
    });
    // 用toRefs定义data，再template里使用数据就无需在再用data.了，可以直接使用data里面的属性
    const refData=toRefs(data);
    return {
      // 使用扩展运算符
      ...refData,
    };
  },
  beforeCreate() {
    console.log('1.1-组件创建之前*** beforeCreate')
  },
  beforeMount() {
    console.log('2.1-组件挂载之前*** beforeMount')
  },
  mounted() {
    console.log('3.1-组件挂载之后** mounted')
  },
  beforeUpdate() {
    console.log('4.1-组件更新之前** beforeUpdate')
  },
  updated() {
    console.log('5.1-组件更新之后** updated')
  },
};
```
![](2.png)
![](3.png)
__注：__ 实际使用中不要vue2和vue3生命周期函数混用，只需固定使用其中的一种就行
vue官方文档指出，如果使用的vue3框架，尽量使用新的生命周期函数
## onRenderTriggered 
```
onRenderTriggered((event) => {
    console.log("状态触发", event);
});
```
![](4.png)

## onRenderTracked
```
 onRenderTracked((event)=>{
   console.log('状态跟踪钩子函数————————————',event)
 })
```
![](5.png)
![](6.png)
