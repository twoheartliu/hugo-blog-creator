---
title: 前端（只）需要掌握这些命令行（就还行了）
tags:
  - 前端
  - 命令行
abbrlink: 74aac220
date: 2019-05-15 00:56:59
---

| 命令        | 全拼             | 缩写  |
| ----------- | ---------------- | ----- |
| 创建目录    | make directory   | mkdir |
| 删除        | remove           | rm    |
| 移动/重命名 | move             | mv    |
| 复制        | copy             | cp    |
| 罗列        | list             | ls    |
| 改变目录    | change directory | cd    |

<!-- more -->

## 练习

1. windows 用户在任意目录使用 shift + 右键 打开 cmd 或者 powershell；或通过其他方式打开命令行
2. `cd ~/Desktop` 回车
3. 恭喜你在命令行里进入了桌面
4. 输入命令 `mkdir demo1`
5. `cd demo1` 进入目录
6. `cd ..` 回退到桌面
7. `rm -rf demo1` 删除目录，其中 -r 表示递归地删除路径下的所有文件，如果删除的是文件夹必须加 -r；-f 表示强制删除，不加的话在 Linux / Unix 系统下每删除一个文件都会提示是否删除
8. `touch 1.txt` 创建文件
9. `mv 1.txt 2.txt` 将 1.txt 移动到 2.txt 可以理解为重命名
10. `ls` 列出桌面上所有的文件
11. `echo 'hello' > 2.txt` 将 hello 字符串写入到 2.txt 中
12. `cat 2.txt` 在命令行中展示 2.txt 中内容

## 使用 explainshell

以上这些命令足以覆盖日常工作中 60% 以上的使用场景，但总有看到命令一时想不起或者就是一个非常少见的命令，如果你需要快速权威的使用指南，请使用 <https://explainshell.com/>

<img class="shadow" src="/img/in-post/post-command-line/post-command-line-1.png" >
<br />
输入命令后指向命令的一部分查看简单释义，如果不过瘾，点击根命令查看命令引申的所有命令。
<br />
<img class="shadow" src="/img/in-post/post-command-line/post-command-line-2.png" >

没了。
