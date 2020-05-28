---
title: HTTP 基础
tags:
  - HTTP
  - 前端
abbrlink: 93cfe9f7
date: 2019-05-23 01:06:01
---

# WWW 的发明

Tim Berners-Lee（下文中称为李爵士）在 1989 年至 1992 年间，发明了 WWW（World Wide Web），一种适用于全世界的网络。主要包含三个概念

1. URI，俗称网址
2. HTTP，两个电脑之间传输内容的协议
3. HTML，超级文本，主要用来做页面跳转
   URL 的作用是能让你访问一个页面，HTTP 的作用是让你能下载这个页面，HTML 的作用是让你能看懂这个页面。
   这是一个简单而完美的系统。李爵士除了发明了这些概念，还付诸了行动：
4. 发明了第一个服务器
5. 发明了第一个浏览器
6. 写出了第一个网页

<!-- more -->

# URI 是什么

Google URI 维基百科即可查看全称。
URI 分为 URL 和 URN，我们一般使用 URL 作为网址。

## URN

Google URN 维基百科即可查看全称。
ISBN: 9787115275790 就是一个 URN，通过 URN 你可以确定一个「唯一的」资源，ISBN: 9787115275790 对应的资源的是《JavaScript 高级程序设计（第三版）》这本书。你去是介绍任何一个图书馆、书店，他们都知道是这本书。

## URL

Google URL 维基百科即可查看全称。
https://www.baidu.com/s?wd=hello&rsv_spt=1#5 就是一个 URL，通过 URL 你可以确定一个「唯一的」地址（网址）。

# HTTP 请求与响应

## 请求的格式

1 动词路径协议/版本
2 Key1: value1
2 Key2: value2
2 Key3: value3
2 Content-Type: application/x-www-form-urlencoded
2 Host: www.baidu.com
2 User-Agent: curl/7.54.0
3
4 要上传的数据
请求最多包含四部分，最少包含三部分。（也就是说第四部分可以为空）
第三部分永远都是一个回车（\n）
动词有 GET POST PUT PATCH DELETE HEAD OPTIONS 等
这里的路径包括「查询参数」，但不包括「锚点」
如果你没有写路径，那么路径默认为 /
第 2 部分中的 Content-Type 标注了第 4 部分的格式

## 响应的格式

1 协议/版本号状态码状态解释
2 Key1: value1
2 Key2: value2
2 Content-Length: 17931
2 Content-Type: text/html
3
4 要下载的内容

## 用 Chrome 查看请求与响应

### 请求

打开 Network
地址栏输入网址
在 Network 点击，查看 request，点击「view source」
如果有请求的第四部分，那么在 FormData 或 Payload 里面可以看到

### 响应

查看 Response Headers，点击「view source」，点击「view source」，点击「view source」
你会看到**响应**的前两部分
查看 Response 或者 Preview，你会看到**响应**的第 4 部分

## cURL

cURL 是一个利用 URL 语法在命令行下工作的文件传输工具，1997 年首次发行。
它支持文件上传和下载，所以是综合传输工具，但按传统，习惯称 cURL 为下载工具。cURL 还包含了用于程序开发的 libcurl。
命令行工具大部分集成了 curl。

### 查看网页源码

`$ curl www.sina.com`

### 自动跳转

`$ curl -L www.sina.com`

### 显示头信息

`$ curl -i www.sina.com`

### 显示通信过程

`$ curl -v www.sina.com`

### HTTP 动词

`$ curl -X POST www.example.com`
等等。

THE END
