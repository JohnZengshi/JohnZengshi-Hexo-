---
title: Object.create()和new object()和{}的区别
date: 2018-07-26 17:42:14
categories: Javascript
---
### Object.create()

​	详细文档: [Object.create()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/create)

### new Object()

​	和new操作符相关：[new](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/new)

### {}

​	字面量申明

> *列如*
>

```javascript
let NewObj03 = {
    num: "123"
}
```

### 区别

1. ##### new Object

   ```javascript
   let NewObj01 = new Object({
       num:"123"
   });
   console.log(NewObj01);
   ```

   > *new Object()控制台打印的结果*

   {% asset_img 01.png new Object返回的结果 %}

   ------

2. ##### Object.create

   ```javascript
   let NewObj02 = Object.create({
       num:"123"
   })
   console.log(NewObj02);
   ```

   > *Object.create()控制台打印的结果*

   {% asset_img 02.png Object.create()返回的结果%}

   ------

3. ##### {}

   ```javascript
   let NewObj03 = {
       name:"123"
   }
   console.log(NewObj03)
   ```

   > *{}控制台打印的结果*

   {% asset_img 01.png {}返回的结果 %}