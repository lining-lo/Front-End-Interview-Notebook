## JavaScript 面试知识点总结

本部分主要是笔者在复习 JavaScript 相关知识和一些相关面试题时所做的笔记，如果出现错误，希望大家指出！

### 目录

* [1. 说一说 JS 数据类型有哪些,区别是什么？](#1-说一说-JS-数据类型有哪些,区别是什么)
* [2. 说一说 null 和 undefined 的区别，如何让一个属性变为 null？](#2-说一说-null-和-undefined-的区别，如何让一个属性变为-null)
* [3. 说一说 JavaScript 有几种方法判断变量的类型？](#3-说一说-JavaScript-有几种方法判断变量的类型)
* [4. 说一说数组去重都有哪些方法？](#4-说一说数组去重都有哪些方法)
* [5. 说一说伪数组和数组的区别？](#5-说一说伪数组和数组的区别)
* [6. 说一说 map 和 forEach 的区别？](#6-说一说-map-和-forEach-的区别)
* [7. 说一说 es6 中箭头函数？](#7-说一说-es6-中箭头函数)
* [8. 事件扩展符用过吗，什么场景下？](#8-事件扩展符用过吗，什么场景下)
* [9. 说一说你对闭包的理解？](#9-说一说你对闭包的理解)
* [10. 说一说 JS 变量提升？](#10-说一说-JS-变量提升)
* [11. 说一说 this 指向（普通函数、箭头函数）？](#11-说一说-this-指向（普通函数、箭头函数）)
* [12. 说一说 call apply bind 的作用和区别？](#12-说一说-call-apply-bind-的作用和区别？)

#### 1. 说一说 JS 数据类型有哪些,区别是什么？

```
1 JS 数据类型分为两类：一类是基本数据类型，也叫简单数据类型，另一类是引用数据类型也叫复杂数据类型。
2 基本数据类型包含7种类型，分别是 Number 、String、Boolean、BigInt、Symbol、Null、Undefined。
3 引用数据类型通常用 Object 代表，普通对象、数组、正则、日期、Math 函数都属于 Object。
4 二者区别：基本数据类型的存放在栈中；引用数据类型存放在堆中，它的地址在栈中，一般我们访问就是它的地址。
```

#### 2. 说一说 null 和 undefined 的区别，如何让一个属性变为 null？

```
1 null 是定义并赋值 null，undefined 是定义未赋值。
2 当一个变量没有被赋值或者一个函数没有返回值或者某个对象不存在某个属性却去访问或者函数定义了形参但没有传递实参，这时候都是undefined。
3 undefined 通过 typeof 判断类型是 undefined，undefined == undefined  undefined === undefined。 
4 null 通过 typeof 判断类型是 object，null === null  null == null  null == undefined null !== undefined undefined。
5 让一个变量为 null，直接给该变量赋值为 null 即可。
```

#### 3. 说一说 JavaScript 有几种方法判断变量的类型？

```
1 typeof xxx：常用于判断基本数据类型，对于引用数据类型除了 function 返回 function，其余全部返回 object。
2 xxx instanceof 数据类型：主要用于区分引用数据类型(根据原型链判断)，返回值是布尔值。
3 xxx.constructor === 数据类型：用于检测引用数据类型。
4 Object.prototype.toString.call(xxx)：适用于所有类型的判断检测，返回的是该数据类型的字符串([Object 数据类型])。
```

> [【掘金】谈一谈 JavaScript 数据类型判断](https://juejin.cn/post/7029111905956397070?searchId=202504102041503DCB9FB4AA83CF133BA7)

#### 4. 说一说数组去重都有哪些方法？

```
1 new Set()：Array.from(new Set(arr)) 或者 [...new Set(arr)]
2 双重for循环去重
3 indexOf：新建一个空的结果数组，for 循环原数组，判断结果数组中是否存在当前元素，如果存在则跳过，如果不存在，就 push 到结果数组
4 includes：新建一个空的结果数组，for 循环原数组，判断结果数组中是否存在当前元素，如果存在则跳过，如果不存在，就 push 到结果数组
5 filter + indexOf：arr.filter((item,index) => arr.indexOf(item,0) === index);
```

> [【掘金】数组去重的五种方法](https://juejin.cn/post/7152759573978284040?searchId=20250410182438A55BDFF4B323C5FD67FC)

#### 5. 说一说伪数组和数组的区别？

```
1 数据类型不同，伪数组的类型 Object，而数组的类型是 Array。
2 伪数组可以获取长度、可以通过下标获取某个元素、也可以使用for in 遍历，但是不能使用数组的方法。
3 伪数组的常见场景：函数的参数 arguments、获取的 DOM 节点等。
4 伪数组转换为数组的方法：Array.prototype.slice.call()、Array.from()、扩展运算符等。
```

#### 6. 说一说 map 和 forEach 的区别？

```
1 map 有返回值，可以开辟新空间，return 出来一个 length 和原数组一致的数组，即便数组元素是 undefined 或者是 null。
2 forEach 默认无返回值，返回结果为 undefined，可以通过在函数体内部使用索引修改数组元素。
3 map 的处理速度比 forEach 快，而且返回一个新的数组，方便链式调用其他数组方法（filter、reduce）。
```

#### 7. 说一说 es6 中箭头函数？

```
1 箭头函数相当于匿名函数，简化了函数定义。
2 箭头函数的写法：当函数体是单条语句的时候可以省略 {} 和 return；另一种是包含多条语句，不可以省略 {} 和 return。
3 箭头函数最大的特点就是没有 this，继承上一个作用域的 this（一般指向 window）。
4 箭头函数没有 arguments，也不能作为 generator 函数，不能使用 yield 命令。
```

#### 8. 事件扩展符用过吗，什么场景下？

```
1 数组拷贝：let a = [1,2,3];let b = [...a] 
2 数组合并：let a = [1,2,3];let b = [4,5,6];let c = [...a,...b] 
3 伪数组转成真正的数组：let a = new Set([1,2,3]); let b = [...a]
```

#### 9. 说一说你对闭包的理解？

```
1 闭包解决的问题：因为全局变量容易污染环境，而局部变量又无法长期驻留内存，于是我们需要一种机制，即能长期保存变量又不污染全局，这就是闭包。
2 实现条件：
    ① 有函数嵌套
    ② 内部函数引用外部作用域的变量参数
    ③ 返回值是函数
    ④ 创建一个对象函数，让其长期驻留
3 闭包形成的原理：作用域链，当前作用域可以访问上级作用域中的变量。
```

> [【bilibili】什么是闭包，理解闭包是什么，弄懂闭包](https://www.bilibili.com/video/BV1sd4y1S7Ed/?spm_id_from=333.337.search-card.all.click&vd_source=59a7d9ad927e21d4f309b9c4fd077245)

#### 10. 说一说 JS 变量提升？

```
1 变量提升是指 JS 的变量和函数声明会在代码编译期，提升到代码的最前面。
2 变量提升成立的前提是使用 var 关键字进行声明的变量，并且变量提升的时候只有声明被提升，赋值并不会被提升，同时函数的声明提升会比变量的提升优先。
3 变量提升的结果，可以在变量初始化之前访问该变量，返回的是undefined；在函数声明前可以调用该函数。
4 使用 let 和 const 声明的变量是创建提升，形成暂时性死区，在初始化之前访问 let 和 const 创建的变量会报错。
```

> [【bilibili】纯干货  js 变量和函数提升动画详解](https://www.bilibili.com/video/BV1ah411M7n4/?spm_id_from=333.337.search-card.all.click&vd_source=59a7d9ad927e21d4f309b9c4fd077245)

#### 11. 说一说 this 指向（普通函数、箭头函数）？

```
1 普通函数中的 this 总是指向它的直接调用者,例如 obj.function,那么 function 中的 this 就是 obj。
2 普通函数在默认情况(非严格模式下,未使用'use strict'),没找到直接调用者,则 this 指的是 window;在严格模式下,this 指的则是 undefined。
3 箭头函数没有 this，继承上一个作用域的 this，所以也不能作为构造函数。
```

> [【bilibili】普通函数和箭头函数this指向问题](https://www.bilibili.com/video/BV1SZ4y1f7ML/?spm_id_from=333.337.search-card.all.click&vd_source=59a7d9ad927e21d4f309b9c4fd077245)

#### 12. 说一说 call apply bind 的作用和区别？

```
1 call、apply、bind 的作用都是改变函数运行时的 this 指向。
2 bind、call、apply 在使用上有所不同：
	① fn.call (newThis,params)，函数的第一个参数是 this 的新指向，后面依次传入函数 fn 要用到的参数，会立即执行 fn 函数。  
	② fn.apply (newThis,paramsArr)，函数的第一个参数是 this 的新指向,第二个参数是 fn 要用到的参数数组，会立即执行 fn 函数。  
	③ fn.bind (newThis,params)，函数的第一个参数是 this 的新指向，后面的参数可以直接传递，也可以按数组的形式传入，
	不会立即执行 fn 函数，且只能改变一次 fn 函数的指向，后续再用 bind 更改无效，返回的是已经更改 this 指向的新 fn。
```

> [【bilibili】两分钟说完 call, apply 和 bind](https://www.bilibili.com/video/BV1Ug411F7fZ/?spm_id_from=333.337.search-card.all.click&vd_source=59a7d9ad927e21d4f309b9c4fd077245)

