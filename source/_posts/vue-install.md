---
title: vue安装与创建项目
date: 2020-12-08 15:54:43
tags: vue
categories: 
    - [框架,vue]
cover: /assets/cover-vue.png
---

## 命令行安装
### 第一步-全局安装
推荐使用npm方式
```
npm i -g @vue/cli-init
或 
npm install -g @vue/cli(本人选择了此项，以下步骤也以此项为例)
```
或者
```
yarn global add @vue/cli
```

### 第二步-查看版本
```
vue --version
```
版本不要小于4.5.6，小于则更新安装（同安装步骤npm install -g @vue/cli），否则老版本没有创建vue3的选项，只有创建vue2的模板

### 第三步-创建项目
```
vue create vue3tsc(项目名：自定义)
或
vue init webpack vue3tsc
（根据需要酌情选择Yes和No）
```
是否使用淘宝源，yes
![](1.png)
![](2.png)
手动选择自定义安装，因为我需要搭配TypeScript，所以选择了，根据需要自行选择即可
![](3.png)
![](4.png)
![](5.png)
安装需要一些时间
![](6.png)
安装成功

### 第四步-运行打开项目
根据提示输入命令：如
```
cd my-project
npm run dev或yarn serve（根据之前选择的市npm还是yarn创建的）
```
![](7.png)
打开网址后
![](8.png)

## 图形界面安装
### 第一步-打开图形界面
```
cd ..(如果需要回退一级，则使用该命令)
vue ui
```
![](9.png)
自动打开网页，选择创建
![](10.png)
层建过vue项目则会显示
![](11.png)
填写好项目名，管理器推荐选择yran，速度相对比npm快
![](12.png)
模板选择，我需要搭配TypeScript,所以选择自定义，格局需要选择即可
![](13.png)
根据需要我选择以几项，其他根据需要自行选择
![](14.png)
![](15.png)
![](16.png)
此时vscode的终端在创建项目，需要等候一会
![](17.png)
创建完成后，回到vscode
```
cd vue3tsc-2
yarn serve（根据之前选择的市npm还是yarn创建的）
```
![](18.png)

推荐在VScode中安装高亮插件
![](19.png)
