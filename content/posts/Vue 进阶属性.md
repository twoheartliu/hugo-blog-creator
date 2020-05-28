+++ 
draft = false
date = 2020-05-28T16:18:41+08:00
title = "Vue 进阶属性"
description = "指令、minxins、extends……"
slug = "" 
tags = [
  "Vue", "JavaScript"
]
categories = ["前端"]
externalLink = ""
series = []
+++

## Direvtives 指令

### 自定义指令

我们已经学习了一些内置指令，如：v-html/v-for/v-text
我们也可以自定义指令，如 v-x

#### 写法一

Vue.directive('x', directiveOptions);
