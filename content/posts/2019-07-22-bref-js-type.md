---
title: JavaScript 中的数据类型
tags:
  - JavaScript
  - 前端
abbrlink: a51d25b8
date: 2019-07-22 16:05:17
---

JavaScript 中大致分七种类型：

- String
- Boolean
- Number
- Symbol
- null
- undefined
- Object

<!-- more -->

## String

String 即字符串，`var a = 'Jack'` `Jack` 就是一个字符串。

### 多行字符串

多行字符串的表示方法：

```
1.
var a = 'a /
b /
c
'
2.
var a = 'a' +
'b' +
'c'
3. (es6新语法)
var a = `a
b
c`
```

### 转义符

当需要使用 `'` 或者`"` 这种本身标识字符串的符号的时候，需要使用`\`来转义，不然会报错。

```
var a = '\'';
var b = "\"";
// 以及 \ 本身
var c = '\\'; // 这里表示 c = '\'
```

## Boolean

Boolean 用来表示逻辑上的 true / false 。

### 逻辑运算符

- 与（&&）两者皆为 true 返回 true ，否则返回 false

- 或（||）两者皆为 false 返回 false， 否则返回 true

- 非（!）取反

```
var a = true;
var b = false;
var c = a || b; // true
var d = a && b; // false
var e = !a; // false
```

## Number

### 十进制

Number 分为整数和小数（浮点数）。可以用科学计数法表示。

[JavaScript 浮点数陷阱及解法](https://github.com/camsong/blog/issues/9)

### 二进制

`0b11`

### 八进制

`011`（ES5 添加了 0o11 语法）

### 十六进制

`0x11`

## null 与 undefined

null 和 undefined 类型和值都是他们自己。

- 变量没被赋值，默认为 undefined
- 对象没被赋值，默认约定为 null
- 非对象没被赋值，默认约定为 undefined

## Symbol

[方应杭：JS 中的 Symbol 是什么？](https://zhuanlan.zhihu.com/p/22652486)

一句话解释：Symbol 生成一个全局唯一的值。

## Object

以上被称为原始数据类型，或者基本数据类型。而 Object 被称为复杂数据类型，即各种基本数据类型的排列组合。

- object 里面可以有 object

  ```
    var person = {
        name: 'Frank',
        'child': {
            name: 'Jack'
        }, // 最后这个逗号可有可无
    }
  ```

- object 的 key 一律是字符串，不存在其他类型的 key

- object[''] 是合法的

- object['key'] 可以写作 object.key

- 注意 object.key 与 `object[key]` 不同

- delete object['key']

- 'key' in object

## typeof 操作符

| xxx 的类型 | string   | number   | boolean   | symbol   | undefined   | null         | object   | function   |
| ---------- | -------- | -------- | --------- | -------- | ----------- | ------------ | -------- | ---------- |
| typeof xxx | 'string' | 'number' | 'boolean' | 'symbol' | 'undefined' | **'object'** | 'object' | 'function' |

typeof 的 bug：

- `typeof null` // 输出 `object` 设计之初的 bug
- `typeof fn1` // 输出 `function` 其实应该是 object，function 并不是一种数据类型
