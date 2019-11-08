---
title: JS Array对象的reduce方法
author: vear
avatar: https://cdn.jsdelivr.net/gh/vearvip/cdn@v0.0.13/img/avatar/avatar.webp
authorLink: /
authorAbout: vear
authorDesc: 唯二
categories: 技术
date: 2019-08-11 22:22:31
comments: true
keywords: Sakura
description: reduce方法是一个神奇的方法
photos: https://cdn.jsdelivr.net/gh/vearvip/cdn@v0.0.13/img/article/林深时见鹿01.webp
---
# JS Array对象的reduce方法
## reduce的用法
> **array.prototype.reduce()**

### reduce 方法接受2个参数，一个回调函数，一个可选的自定义值

- **回调函数**

  执行数组中每个值的函数，包含四个参数：

   - **累积变量**，默认为数组的第一个成员
   
      或'自定义累积变量'（见于下方）

   - **当前变量**，默认为数组的第二个成员

     数组中正在处理的元素

   - **当前位置** *可选*

     数组中正在处理的当前元素的索引。 如果提供了initialValue，则起始索引号为0，否则为1

   - **原数组** *可选*

     调用reduce()的原数组

- **自定义累积变量** *可选*

  作为第一次调用 **回调函数** 时的第一个参数的值。 如果没有提供初始值，则将使用数组中的第一个元素。 在没有初始值的空数组上调用 reduce 将报错。
  
  注意：自定义累积变量 不是替换掉数组的第一个元素！

### reduce的使用

#### 数组求和
```js
[1, 3, 5, 7, 9].reduce((x, y) => x + y) // 25
```
#### 数组求积
```js
[2, 3, 5].reduce((x, y) => x * y) // 30
```
#### [1, 3, 5, 7, 9]变换成整数13579
```js
[1, 3, 5, 7, 9].reduce((x, y) => x * 10 + y) // 13579
```
#### 把一个字符串`'13579'`先变成Array [1, 3, 5, 7, 9]，再利用reduce() 写出一个把字符串转换为Number的函数
不要使用JavaScript内置的parseInt()函数，利用map和reduce操作实现一个string2int()函数
```js
'use strict';

function string2int(s) {
  return s.split('').map(ele => ele * 1).reduce((x, y) => {
    return x * 10 + y
  })
}

// function string2int(s) {
//   return s.split(',').reduce((x, y) => y - 0, 0)
// }

// 测试:
if (string2int('0') === 0 && string2int('12345') === 12345 && string2int('12300') === 12300) {
  if (string2int.toString().indexOf('parseInt') !== -1) {
    console.log('请勿使用parseInt()!')
  } else if (string2int.toString().indexOf('Number') !== -1) {
    console.log('请勿使用Number()!')
  } else {
    console.log('测试通过!')
  }
}
else {
  console.log('测试失败!')
}
```
## reduceRight的用法
> **array.prototype.reduceRight()**

`reduce`方法和`reduceRight`方法依次处理数组的每个成员，最终累计为一个值。它们的差别是，`reduce`是从左到右处理（从第一个成员到最后一个成员），`reduceRight`则是从右到左（从最后一个成员到第一个成员），其他完全一样。

```js
function subtract(prev, cur) {
  return prev - cur
}

[3, 2, 1].reduce(subtract) // 0
[3, 2, 1].reduceRight(subtract) // -4
```

由于这两个方法会遍历数组，所以实际上还可以用来做一些遍历相关的操作。比如，找出字符长度最长的数组成员。

```js
function findLongest(entries) {
  return entries.reduce(function (longest, entry) {
    return entry.length > longest.length ? entry : longest;
  }, '');
}

findLongest(['aaa', 'bb', 'c']) // "aaa"
```
上面代码中，reduce的参数函数会将字符长度较长的那个数组成员，作为累积值。这导致遍历所有成员之后，累积值就是字符长度最长的那个成员。

## 参考资料
[廖雪峰-JavaScript教程](https://www.liaoxuefeng.com/wiki/1022910821149312/1024322552460832)

[阮一峰-JavaScript教程](https://wangdoc.com/javascript/stdlib/array.html#reduce%EF%BC%8Creduceright)

[MDN-火狐开发者文档](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

注：本文不以盈利为目的，仅做学习交流使用，若有侵权，请联系我删除，万分感谢！
