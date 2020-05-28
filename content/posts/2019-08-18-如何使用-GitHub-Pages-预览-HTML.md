---
title: 如何使用 GitHub Pages 预览 HTML
abbrlink: 643e72ee
date: 2019-08-18 10:54:45
tags:
  - Github
  - HTML
---

> 当你想要将自己写好的网页分享给其他人看到展示效果的时候，使用 Github Pages 是个快速高效的选择。

<!-- more -->

如果你还不懂 Github 的注册登录以及基本使用，推荐阅读 [知乎：如何使用 Github？](https://www.zhihu.com/question/20070065)

## 创建新 repo

![4871c945ly1g63nlam6xmj20pu0iw400](https://i.loli.net/2020/05/20/eAPpwMzhHat39k1.jpg)
如果你阅读了上面的链接应该不用我过多介绍了，填写了 repo 名和必要的描述信息之后，点击 Create repository，就创建好了一个新 repo。

## 上传代码

![4871c945ly1g63nrtmznwj20ut0mqq58](https://i.loli.net/2020/05/20/oSTwt2bcEMj3GV6.jpg)

创建后的界面如图所示

创建完成后你会看到这样一个界面。你可以通过 Git 命令（如果你没有使用过需要做一些配置 [配置 github 配置 git 使用 git](https://zhuanlan.zhihu.com/p/48209762)。

当然你也可以点击 `uploading an existing file` 按钮，直接把 nHTML 文件直接通过文件上传的形式上传到 Github 仓库。

## 预览 HTML

![4871c945ly1g63pcm2vfoj20v40fz75r](https://i.loli.net/2020/05/20/DOGE3kgoMld6sJS.jpg)
上传后的文件目录如图所示

点击右上角的 Settings

![4871c945ly1g63pfu0uwej20ur0mjjt3](https://i.loli.net/2020/05/20/Bx1pz7PEtoXFGhl.jpg)

下拉到这个区域
![4871c945ly1g63ph5s86gj20mw0azaal](https://i.loli.net/2020/05/20/TQq7maiIMz9vogF.jpg)

将 None 改为 master branch
![4871c945ly1g63pib71ffj20lg0h875a](https://i.loli.net/2020/05/20/qupHiE5Mm142K8k.jpg)

这时候上面会出现一个网址，这个网址`http://twoheart.cn/html-view-demo/`就是预览网址。

你的看到的网址可能是`xxx.github.io/html-view-doemo/`，这是正常的。如果显示的是 404，你需要在网址最后加上 html 的路径，如果你的文件名是`main.html`,则路径为`xxx.github.io/html-view-doemo/main.html`，如果你的 html 主文件在文件夹内，如果文件名为`build`则改成`xxx.github.io/html-view-doemo/build/main.html`.

---

the end
