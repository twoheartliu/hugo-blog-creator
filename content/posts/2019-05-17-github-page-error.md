---
title: Github Page —— build warning 之坑
tags:
  - Github
  - 前端
abbrlink: ab561dfa
date: 2019-05-17 00:57:08
---

自从恢复使用博客以来，每次向 Github push 代码总会如期而至的收到一封发自 Github 的题为 Page build warning 的来信。

<!-- more -->
<img src="https://www.twoheart.cn/img/in-post/post-github-page-warning.jpg">

今天下班早，我决定试着解决一下这个问题。

道路是曲折的，通过 Google ，我发现似乎是由于顶级域名和 DNS 配置过期的量子纠缠而引发的问题。

似乎只有不多的几篇中文博客谈到了这个问题。

在试着通过 <a href="http://seanlook.com/2014/11/08/github-mail-warning-dns/">这篇博客<a/> 以及 <a href="https://zhangjh.me/2015/12/11/gitpages-warning/">另一篇博客<a/> 的方法设置之后，依然没有解决。

在群里问了大佬，大佬给出的建议是——将 @github 设置为垃圾邮件。

这当然是一个简单粗暴又省时的好办法。

但是作为一个江湖儿女，我决定再挣扎一番。

在尝试了多个语句之后，终于在 <a href="https://www.reddit.com/r/webdev/comments/av9e9z/custom_domain_for_github_pages_is_pointed_at_an/">reddit<a/> 以及 <a href="https://stackoverflow.com/questions/9082499/custom-domain-for-github-project-pages">stackoverflow<a/> 找到了几乎正确的方法。

在用顶级域名尝试了上面两个网站的设置之后，问题依旧。最后抱着死马当活马医的心情，设置了 www 域名前缀，问题终于算是解决了。

在 Github Warning 解除之后，顺便升级了下 HTTPS 。

今天的故事告诉我们：

1. 学好英文很重要
2. 勇于尝试很重要
3. 钻牛角尖很浪费时间

THE END
