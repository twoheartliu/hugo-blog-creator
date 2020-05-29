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

#### directiveOptions

directiveOptions 可以包含以下钩子函数：

- bind: 只调用一次，指令第一次绑定到元素时调用。在这里可以进行一次性的初始化设置。
- inserted：被绑定元素插入到父节点时调用
- update：所在组件的 Vnode 更新时调用
- componentUpdated: 指令所在组件的 VNode 及其子 VNode 全部更新后调用
- unbind：只调用一次，指令与元素解绑时调用

#### 写法一

全局声明：

Vue.directive('x', directiveOptions);

```
Vue.directive('x', {
  inserted: function (el) {
    el.addEventListener('click', () => {
      console.log('clicked')
    })
  }
})
```

#### 写法二

局部声明

只在组件内部使用自定义指令

```
export default {
  name: "App",
  components: {
    HelloWorld
  },
  directives: {
    y: {
      inserted: function(el) {
        el.addEventListener("click", () => {
          console.log("yyy");
        });
      }
    }
  }
};
```

#### 自制 v-on2 指令

```
import Vue from "vue/dist/vue.js";

Vue.config.productionTip = false;

new Vue({
  template: `<button v-on2:click="add">点我</button>`,
  methods: {
    add() {
      console.log("hi");
    }
  },
  directives: {
    on2: {
      inserted(el, info) {
        el.addEventListener(info.arg, info.value);
      },
      unbind(el, info) {
        el.removeEventListener(info.arg, info.value);
      }
    }
  }
}).$mount("#app");
```

### 指令的作用

- 主要用于 DOM 操作
  - Vue 实例、组件用于数据绑定、事件监听、DOM 更新
  - Vue 指令主要目的就是原生 DOM 操作
- 减少重复
  - 如果某个 DOM 操作你经常使用，就可以封装为指令
  - 如果某个 DOM 操作比较复杂，也可以封装为指令
