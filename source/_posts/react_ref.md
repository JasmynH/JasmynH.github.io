---
title: react ref的用法
tag: react
categories: 
    - [框架,react,知识点]
cover: https://upload-images.jianshu.io/upload_images/11060508-3d58ff4aa4dc20c8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
---
refs提供了一种方式，允许我们访问DOM节点或在render方法中创建的React元素

在典型的React数据流中，props是父组件与子组件交互的唯一方式。
要修改一个子组件，需要使用新的props来重新渲染它。
但是，在某些情况下，需要在典型数据流之外强制修改子组件。被修改的子组件可能是一个React组件的实例，也可能是一个DOM元素。对于这两种情况，react都提供了解决办法。
## 适合使用refs的情况
* 管理焦点，文本选择或媒体播放。
* 触发强制动画。
* 集成第三方DOM库。

避免使用refs来做任何可以通过声明式实现来完成的事情。
举个例子，避免在Dialog 组件里暴露open( )和close()方法，最好传递isOpen 属性。
## 不能过度使用Refs
你可能首先会想到使用refs在你的app中"让事情发生"。如果是这种情况，请花一点时间，认真再考虑一下state属性应该被安排在哪个组件层中。通常你会想明白，让更高的组件层级拥有这个state，是更恰当的。查看状态提升以获取更多有关示例。

__注：__ 
下面的例子已经更新为使用在React 16.3版本引入的React.createRef()API。如果你正在使用一个较早版本的 React，我们推荐你使用回调形式的refs。
ref不能使用在函数组件上，因为函数组件没有实例，只能使用在类组件上。

![image.png](https://upload-images.jianshu.io/upload_images/11060508-195e071a5cb57611.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## react ref的三种用法：
1、字符串类型 string （已不被最新版的react推荐使用，可能会被遗弃）
2、回调函数类型
3、React.creactRef()（React16.3提供）

## 回调函数类型
```
const App =(params)=>{
    let textInp;
    const setInpTef=(ele)=>{
        textInp=ele
    }
    const btnOnclick=()=>{
        //直接使用原声api使text输入框获得焦点
        //注意：通过“current”来访问DOM节点
        textInp.focus();
    }
    return(
        <>
            <input type="text" ref={setInpTef}>
            <input type="button" value="focus the text input" onClick={btnOnclick}>
        </>
    )
}
```

## React.creactRef()
在React 16.3版本后，使用此方法来创建ref。将其赋值给一个变量，通过ref挂载在dom节点或组件上，该ref的current属性
将能拿到dom节点或组件的实例
```
class Child extends React.Component{
    constructor(props){
        super(props);
        this.myRef=React.createRef();
    }
    componentDidMount(){
        console.log(this.myRef.current);
    }
    render(){
        return <input ref={this.myRef}/>
    }
}
```


## 函数组件使用ref（useRef/creactRef)

回调函数类只能在类组件里使用，在函数组件里使用要使用useRef/creactRef
```
    import React,{Component,useRef,creactRef} from 'react'
    const App=(params)=>{
        const inputRef=useRef() //方法一（useRef）
        const inputRef=creactRef() //方法二（creatRef）

        const onClick=(params)=>{
            inputRef.current.focus()
        }
        return(
            <>
                <input type="text" ref={inputRef}/>
                <button onClick={onClick}>聚焦</button>
            </>
        )
    }
```