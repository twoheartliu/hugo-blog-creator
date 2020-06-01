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

## mixins 混入

directive 的作用是减少 DOM 操作重复
而 mixins 的作用则是减少构造选项 data、methods、钩子的重复

[示例代码](https://codesandbox.io/s/recursing-pike-h1d0r?file=/src/App.vue)

### mixin 技巧

- 选项智能合并
  当组件和混入对象含有同名选项时，这些选项将以恰当的方式进行“合并”
- Vue.mixin
  **不推荐** 使用，因为不需要使用 mixins 选项进行引入，全局都会默认使用 mixin 中的属性

## extends

与 mixins 需求一致，不想要每次都写一个 mixins，可以使用 Vue.extends 或者 options.extends

```
const myVue = Vue.extends({
  data() {
    return {
      name: '',
      time: undefined
    },
    create() {
      if (!this.name) {
        console.log('no name')
      }
      this.name = new Date();
    },
    beforeDestroy() {
      const duration = (new Date()) - this.time
      console.log(`${this.name} 存活时间 ${duration}`)
    }
  }
})
```

然后就可以使用 new MyVue(options) 了

extends 是比 mixins 更抽象一点的封装
如果你嫌写五次 mixins 麻烦，可以考虑 extends 一次，不过实际工作中用的很少

## provide 和 inject （提供和注入）

[示例代码](https://codesandbox.io/s/clever-frost-28luh)
作用： 大范围的 data 和 method 公用
注意： 不能只传 themeName 不传 changeTheme，因为 themeName 的值是被复制给 provide 的
可以传引用，但是不推荐，会导致你任意组件都可以修改其中的值，容易导致数据错乱

## 总结

- directive 指令
  - 全局用 Vue.directive('x', {...})
  - 局部用 options.directives
  - 作用是减少 DOM 操作相关代码重复
- mixins 混入
  - 全局用 Vue.mixin(...)，不推荐
  - 局部用 `options.mixins:[mixin1, mixin2]`
  - 作用是减少 options 里的重复
- extends 继承、扩展
  - 全局用 Vue.extends({...})
  - 局部用 options.extends: {...}
  - 作用跟 mixins 差不多，只是形式不同
- provide/inject 提供和注入
  - 祖先提供东西，后代注入东西
  - 作用是大范围、隔 N 代共享信息
