---
title: github-git push报错
date: 2020-12-15 09:25:06
tags: github
categories: 
- [软件/平台,github]
cover: /assets/cover-github.png
---
## git push后报错显示
![](1.png)
## 使用命令
`git config --global http.postBuffer 2428000`
或
`git config http.postBuffer 524288000`
## 报错原因
可能是因为git库较大，而curl的postBuffer的默认值较小，所以将postBuffer设置大一些就可以解决