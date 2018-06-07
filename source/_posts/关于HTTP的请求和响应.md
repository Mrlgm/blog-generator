---
title: 关于HTTP的请求和响应
date: 2018-06-07 09:56:32
tags:
---
## 一、 HTTP的请求 ##

请求的格式
----

 1. 动词 路径 协议/版本
 2. Key1: value1
    Key2: value2
    Key3: value3
    Content-Type: application/x-www-form-urlencoded
    Host: www.baidu.com
    User-Agent: curl/7.54.0
    
 3. 回车
 4. 要上传的数据


----------

 - 请求最多包含四部分，最少包含三部分。（也就是说第四部分可以为空）
 - 第三部分永远都是一个回车（\\n）
 - 动词有 GET POST PUT PATCH DELETE HEAD OPTIONS 等
 - 这里的路径包括「查询参数」，但不包括「锚点」
 - 如果你没有写路径，那么路径默认为 /
 - 第 2 部分中的 Content-Type 标注了第 4 部分的格式
 - 第一部分叫请求行，第二部分叫首部行，第三部分叫空行，第四部分叫做实体主体

使用Chrome开发者工具查看 HTTP 请求内容
-------------------------

 1. 右键检查，打开 Network
 2. 地址栏输入网址
 3. 在 Network 点击，查看 request，点击「view source」
 4. 可以看到请求的前三部分
 5. 如果有请求的第四部分，那么在 FormData 或 Payload 里面可以看到

## 二、HTTP的响应 ##

响应的格式
----

 1. 协议/版本号 状态码 状态解释
 2. Key1: value1
    Key2: value2
    Content-Length: 17931
    Content-Type: text/html
    
 3. 回车
 4. 要下载的内容


----------

 - GET 请求和 POST 请求对应的响应可以一样，也可以不一样
 - 响应的第四部分可以很长很长很长
 - 状态码要背，是服务器对浏览器说的话
   1xx 不常用
   2xx 表示成功
   3xx 表示不存在
   4xx 表示请求错误
   5xx 表示服务器错误
 - 状态解释没什么用
 - 第 2 部分中的 Content-Type 标注了第 4 部分的格式
 - 第 2 部分中的 Content-Type 遵循 MIME 规范
 - 第一部分叫状态行，第二部分叫首部行，第三部分叫空行，第四部分叫实体体

使用Chrome开发者工具查看 HTTP 响应内容
----

 - 右键检查，打开 Network
 - 输入网址
 - 选中第一个响应
 - 查看 Response Headers，点击「view source」
 - 你会看到响应的前两部分
 - 查看 Response 或者 Preview，你会看到响应的第 4 部分
 
## 三、使用 curl 命令查看请求响应 ##
curl命令是一个功能强大的网络工具，它能够通过http、ftp等方式下载文件，也能够上传文件，但按传统，习惯称url为下载工具。类似的工具还有wget。

语法
----

```
# curl [option] [url]
```

参数
----
curl的参数很多，这里只是常见的几种
```
-v/--verbose 小写的v参数，用于打印更多信息，包括发送的请求信息，这在调试脚本是特别有用。

-m/--max-time <seconds> 指定处理的最大时长

-H/--header <header> 指定请求头参数

-s/--slient 减少输出的信息，比如进度

--connect-timeout <seconds> 指定尝试连接的最大时长

-x/--proxy <proxyhost[:port]> 指定代理服务器地址和端口，端口默认为1080

-T/--upload-file <file> 指定上传文件路径

-o/--output <file> 指定输出文件名称

-d/--data/--data-ascii <data> 指定POST的内容

--retry <num> 指定重试次数

-e/--referer <URL> 指定引用地址

-I/--head 仅返回头部信息，使用HEAD请求
```

实例
----
试一下返回结果吧
```
curl -X POST -d "1234567890" -s -v -H "xxx: xxx" -- "https://www.baidu.com"
```