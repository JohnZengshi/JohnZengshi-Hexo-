---
title: javascript变量的生命周期:为什么let不被提升
date: 2018-11-29 14:50:27
tags: Javascript
---

原文链接：[https://dmitripavlutin.com/variables-lifecycle-and-why-let-is-not-hoisted/](https://dmitripavlutin.com/variables-lifecycle-and-why-let-is-not-hoisted/)

> 一般的，***变量声明var***和***函数声明function fun() {...}***，都会发生变量提升，即把变量和函数的定义移到作用域的顶部。

> 但是let不会被提升，（有提升，但是无效，在定义之前不能使用）

1. #### var的变量提升

   ```javascript
   console.log(num); // => nudefined
   var num;
   num = 10;
   console.log(num); // => 10
   ```

   变量在声明之前被访问，会被认定为**undefined**。

   ```javascript
   console.log(fun); // => function fun() {....}
   fun(); // => 123
   function fun(){
   	return 123;
   }
   ```

   函数在声明之前被调用，可以执行，因为末尾定义的函数被提升到作用域顶部了。

   ```javascript
   console.log(fun()); //fun is not a function
   var fun = function() {
   	return 123;
   };
   ```

   上面的这种属于变量的声明，fun在声明之前被访问了。

2. #### 底层：变量的生命周期

   > 当引擎访问变量的时候，生命周期包括以下几个阶段：

   1. 声明阶段：在作用域当中注册一个变量。
   2. 初始化阶段：分配内存，给作用域中的变量创建绑定，变量会自动初始化为undefined。
   3. 赋值阶段：给已经初始化的变量赋值。

   > 通过声明阶段但是没有达到初始化阶段的变量处于未定义状态。
   >
   > 通过初始化阶段但是没有达到赋值阶段的变量处于undefined状态。

   ​		{% asset_img 变量的生命周期.png 变量的生命周期%}

3. #### var 变量的生命周期

   {% asset_img var变量的生命周期.png var变量的生命周期%}

   > 引擎处理var的过程

   1. javascript引擎遇到作用域里面的所有***var***声明的变量或函数。都会让她们在其他任何语句执行之前，通过变量的***声明阶段和初始化阶段（初始化undefined）***。
   2. 在赋值语句（赋值阶段）之前，这些变量的值都为undefined并且都可以访问。
   3. 严格来说，提升的概念是在函数作用域的顶部声明和初始化变量。并且在声明阶段和初始化阶段之间是没有间隙的。

4. #### 函数声明的生命周期

   {% asset_img 函数声明的生命周期.png 函数声明的生命周期%}	

   > 引擎处理function fun() {...}的过程

   1. javascript引擎遇到作用域里面所有的***function fun() {...}***声明的函数，都会让它们在其他语句执行之前通过***声明，初始化，赋值阶段***。
   2. 三个阶段之间是没有间隙的。

5. #### let 变量的生命周期

   {% asset_img let变量的生命周期.png let变量的生命周期%}	

   > let变量的处理方式和var不同，最主要的区别就是**声明阶段**和**初始化阶段**被分开了

   1. javascript引擎遇到作用域里面所有的***let*** 语句，所声明的变量或者函数就会在其他语句执行之前通过***声明阶段***。在作用域中注册它的名字。
   2. 接着javascript引擎便一行一行的解析语句。
   3. 当解析到***let variable***语句的时候，引擎便会让变量通过***初始化阶段***，变量从未定义变成undefined。
   4. 当解析到***variable = 'value'***语句的时候，引擎便会让变量通过***赋值阶段***，变量从undefined变成有值。

   ```javascript
   console.log(num) // => Throws ReferenceError
   let num;
   console.log(num) // => nudefined
   num = 5;
   console.log(num) // => 5
   ```

   > **const**和**class**类型和let有相同的生命周期，只是const和class只能**赋值一次**。

​	

