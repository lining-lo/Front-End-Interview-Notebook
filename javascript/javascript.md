## JavaScript 面试知识点总结

本部分主要是笔者在复习 JavaScript 相关知识和一些相关面试题时所做的笔记，如果出现错误，希望大家指出！

### 目录

* [1. 说一说 JS 数据类型有哪些,区别是什么？](#1-说一说 JS 数据类型有哪些,区别是什么)
* [2. 说一说 null 和 undefined 的区别，如何让一个属性变为 null？](#2-说一说-null-和-undefined-的区别，如何让一个属性变为-null)
* [3. 说一说 JavaScript 有几种方法判断变量的类型？](#3-说一说-JavaScript-有几种方法判断变量的类型)
* [4. 说一说数组去重都有哪些方法？](#4-说一说数组去重都有哪些方法)
* [5. 说一说伪数组和数组的区别？](#5-说一说伪数组和数组的区别)
* [6. 说一说 map 和 forEach 的区别？](#6-说一说-map-和-forEach-的区别)
* [7. 说一说 es6 中箭头函数？](#7-说一说-es6-中箭头函数)

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
1 typeof：常用于判断基本数据类型，对于引用数据类型除了 function 返回 function，其余全部返回 object。
2 instanceof：主要用于区分引用数据类型(根据原型链判断)。
3 constructor：用于检测引用数据类型。
4 Object.prototype.toString.call()：适用于所有类型的判断检测，返回的是该数据类型的字符串([Object xxx])。
```

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

