---
title: Vue 进阶属性之 computed/watch
abbrlink: '60739017'
date: 2020-05-21 10:38:11
categories:
  - 前端
tags:
  - Vue
  - JavaScript
---

首先复习一下响应式原理：

- Vue 对传入的 data 进行监听
- 传入的 data 会被 Vue 代理
- 每次对 data 的读写都会通过代理处理
- Vue 会在 data 变化时更新 UI

这里要讲 Vue 除了可以更新 UI 还可以做什么

<!-- more -->

## computed 计算属性

### 用途

[示例代码 1](https://codesandbox.io/s/wizardly-cookies-1d9h3?file=/src/main.js)

1. 当模版内需要使用复杂逻辑、表达式来展示时，使用 computed 是比较好的实践
2. 同时当模版内有多处包含复杂逻辑时，可以用 computed
3. 自定义计算属性可以是一个 function，也可以是一个包含 get、set 的对象。

[示例代码 2](https://codesandbox.io/s/stoic-jang-lc976?file=/src/main.js)

1. 使用 methods 属性 filter 筛选性别
2. 使用 v-for 指令渲染数组

有没有更优雅的办法？使用 computed 属性
[示例代码 3](https://codesandbox.io/s/new-dream-pigr8?file=/src/main.js)

1. computed 消除相同逻辑代码，避免重复（DRY：Don't repeat yourself）
2. 逻辑清晰，方便增加功能
3. computed 有缓存，当数据没有发生变化，便不会重新渲染页面

## watch

### 简单举例

watch 即当数据发生变化时，执行一个函数。
[示例代码 1 ：用 watch 实现撤消](https://codesandbox.io/s/lucid-shamir-cpcw3)
[示例代码 2 ：用 watch 模拟 computed ](https://codesandbox.io/s/lucid-shamir-cpcw3))
由此可见，watch 更偏向于监听记录，而非进行计算，该根据需要选择适用的属性

[示例代码 3：哪些数据变了](https://codesandbox.io/s/priceless-rhodes-fzh3q?file=/src/main.js)

1. 当数据是简单类型时，数据变了就是变了
2. 当数据是 obj 时，对 obj.key 重新赋值不会导致 obj 变化
3. 当数据是 obj 时，对 obj 本身被重新赋值，则监听到整个对象发生了变化，根据 key/value 值的不同，判断 obj.key 是否变化

即：简单类型看值，复杂类型看地址

### deep:true

当我们需要让 watch 每当 obj.key 发生变化，就会执行 obj 变了，就需要设置 deep:true，反之不设置，或设置 deep:false

```
watch: {
  obj: {
    handler() {
      console.log('obj 变了')
    },
    deep: true
  }
}
```

### immediate

当设置 immediate:true 则将立即以表达式的当前值触发回调
简单的说，就是页面初次渲染是否视为变化

### watch 的完整语法

#### 语法 1

```
watch: {
  // 注意：不能使用箭头函数，因为箭头函数会绑定父级作用域，this 将会指向 window/global
  /* o1: () => {}, */
  o2: (value, oldValue) {},
  o3() {},
  // 回调数组，他们将依次执行
  o4: [f1, f2],
  o5: 'methodsName',
  o6: {
  handler() {},
  deep: true,
  immediate: true
  }
}
```

#### 语法 2

```
// 'x' 为监听的键路径
vm.$watch('x', fn, {deep: ..., immediate: ...})

// 表达式 `this.a + this.b` 每次得出一个不同的结果时
// 处理函数都会被调用。
// 这就像监听一个未被定义的计算属性
vm.$watch(
  function() {
    return this.a  + this.b
  },
  function(value, newValue) {
    console.log('do something')
  }
)
// 取消观察函数,用来停止触发回调
var unwatch = vm.$watch('a', cb);
unwatch();
```

### computed 和 watch 的区别

1. 含义。computed 就是计算属性的意思，watch 就是监听属性的意思。
2. 描述。
3. computed：
   1. 是用来计算出一个值的，本身的 value 是一个 obj，自定义的 computed 方法可以是一个函数也可以是一个 obj 包含了 getter 和 setter。
   2. computed 属性会进行缓存，如果数据没有发生改变则使用缓存，不会重新加载。
4. watch：
   1. watch 是用来监听数据的。
   2. 有两个选项：immediate 表示初次渲染是否执行，deep，表示 obj.key 里层的值发生变化要不要监听的问题。
   3. 如果某个属性变化了，就会执行一个函数。
   4. watch 的外层 key 与数据名一致，表示要监听哪个数据。
