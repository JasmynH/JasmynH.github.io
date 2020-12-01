---
title: http协议
date: 2020-11-13 09:53:56
tags: 
    - [http]
    - [面试]
categories: 
    - [面试]
cover:  /assets/cover-interview.png
---


## HTTP概念
Hyper Text Transfer Protocol（超文本传输协议）【超：超链接】【HTML是超文本标记语言】
用于从万维网服务器传输超文本到本地浏览器的传送协议
http协议是基于TCP的应用层协议，它不关心数据传输的细节，主要是用来 __规定客户端和服务端的数据传输格式__ ，最初是用来向客户端传输HTML页面的内容。默认的端口是80
http是基于请i去与响应模式的、无状态的、应用层的协议。
![](1.png)
可以使用Fiddler软件（抓包工具）抓取http请求（或者使用charles软件、wireshark软件【不仅仅是http的抓取，侧重于底层的抓取，用到较少】）
Fiddler软件mac通常使用不了

##  http请求报文
http请求报文主要由请求行、请求头部、空一行、请求正文4部分组成
![](2.png)
* ### 1、请求行
#### a、请求方法
|请求方法|备注|
|---|---|
|GET|请求资源|
|POST|提交资源|
|PUT|替换响应头|
|DELETE|删除资源|
|Head|获取响应头|
|CONNECT||
|OPTIOINS|允许客户端查看服务器额性能（不常用）|
|TRACE|回显服务器收到的请求，用于测试或诊断（不常用）|

涉及敏感数据提交的，如：账号名，密码等，一般用post，如需用get，则需要进行特殊处理加密等。

__get和post的区别：__
应用层：
* get：请求的参数在url后面添加（地址栏）相对不安全；POS：请求体（Request body）中间，所有操作对用户不可见，相对安全；
* get：传送的数据量较小，因为收URL长度限制；post：传送的数据量较大，一般被默认为不受限制；
* get：限制Form表单的数据集的值必须为ASCII字符；post：支持整个ISO10646字符集；
* get执行效率比post方法好，get是form提交的默认方法
* get请求参数会被完整保留在浏览器历史记录里；post中的参数不会被保留。
传输层：
* get产生一个TCP数据包；post产生两个TCP数据包；

对于GET方式的请求，浏览器会把http header和data一并发送出去，服务器响应200（返回数据）；而对于POST，浏览器先发送header，服务器响应100 continue，浏览器再发送data，服务器响应200 ok（返回数据）。

1. GET与POST都有自己的语义，不能随便混用。

2. 据研究，在网络环境好的情况下，发一次包的时间和发两次包的时间差别基本可以无视。而在网络环境差的情况下，两次包的TCP在验证数据包完整性上，有非常大的优点。

3. 并不是所有浏览器都会在POST中发送两次包，Firefox就只发送一次。


#### b、请求URL
* __Uniform Resource Locator__ ：同意资源定位符
用于描述网上的资源
* 格式：schema://host [:port#]/path/.../[?query-string]
scheme:协议，如http，https，ftp等
host：域名或者IP地址
port：端口
path：资源路径
query-string：发送的参数

如：https://www.baidu.com/s?ie=UTF-8&wd=博客
![](3.png)

#### c、HTTP/1.1版本

* ### 2、请求头
附加的需要服务器知道的一些信息
理解即可

|请求头|描述|
|---|---|
|Host|主机IP地址或域名|
|User-Agent|客户端相关信息，如操作系统、浏览器等信息|
|__Accept__ |指定客户端接受信息类型，如：image/jpg,text/html,application/json|
|Accept-Charset|客户端接受的内容编码，如gb2312、iso-8859-1|
|Accept-Encoding|可接受的内容编码，如gzip|
|Accept-Language|接受的语言，如Accept-Language:zh-cn|
|__Authorization__|客户端提供给服务端，进行权限认证的信息（权限鉴定）|
|__Cookie__|携带的cookie信息|
|Referer|当前文档的URL，即从哪个链接过来的|
|Content-Type|请求体内容类型，如Content-Type:application/x-www-form-urlencoded|
|Content-Length|数据长度|
|Cache-Control|缓存机制，如Cache-control:no-cache|
|Pragma|防止页面被缓存，额Cache-Control:no-cache作用一样|

* ### 3、请求体
参数（有的放在请求行里，如：get请求参数放在请求行里，所以get请求没有请求体）

##  http响应报文
由状态行、消息报头、空一行、响应正文4部分组成。
![](4.png)
可能没有响应体
* ### 1、状态行
#### 状态码
用以表示网页服务器HTTP响应状态的3位数字代码

|状态码|描述|
|---|---|
|1XX|提示信息，请求被成功接收|
|2XX|成功，求情被成功处理，如：200|
|3XX|重定向相关，如：304|
|4XX|客户端错误，如：404|
|5XX|服务器端错误，如：500|

* ### 2、响应头

|响应头|描述|
|---|---|
|Server|HTTP服务器的软件信息|
|Date|响应报文的时间|
|Expires|指定缓存过期时间|
|__Set-Cookie（重要）__|种Cookie|
|Last-Modified|资源最后修改时间|
|__Content-Type__|响应的类型和字符串集，如Content-type:tex|
|Content-Length|内容长度|
|Connection|如Keep-Alive，表示保持tcp链接不关闭，不会|
|__Location__|指明重定向的位置，新的URL地址，如304的情况|
其他可以自定义

* ### 3、响应体
状态码为2XX，才有响应体