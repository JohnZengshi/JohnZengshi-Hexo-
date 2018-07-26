---
title: Object.create()和new object()和{}的区别
date: 2018-07-26 17:42:14
tags:
---
1. ### Object.create()

   ​	详细文档: [Object.create()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/create)

2. ### new Object()

   ​	和new操作符相关：[new](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/new)

3. ### {}

   ​	字面量申明

4. ### 区别

   ```javascript
       let NewObj01 = new Object({
           num:"123"
       });
       console.log(NewObj01);
   ```

   > ​	*控制台打印的结果*

   {% asset_img 01.png new Object返回的结果 %}