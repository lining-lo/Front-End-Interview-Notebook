## JavaScript 面试知识点总结

本部分主要是笔者在复习 JavaScript 相关知识和一些相关面试题时所做的笔记，如果出现错误，希望大家指出！

### 目录

* [1. 说一说 JS 数据类型有哪些,区别是什么？](#1.-说一说 JS 数据类型有哪些,区别是什么？)
* [2. 说一说 null 和 undefined 的区别，如何让一个属性变为 null？](#2.-说一说-null-和-undefined-的区别，如何让一个属性变为-null？)

#### 1. 说一说 JS 数据类型有哪些,区别是什么？

```
	JS 数据类型分为两类：一类是基本数据类型，也叫简单数据类型，另一类是引用数据类型也叫复杂数据类型。
	基本数据类型包含7种类型，分别是 Number 、String、Boolean、BigInt、Symbol、Null、Undefined。
	引用数据类型通常用 Object 代表，普通对象、数组、正则、日期、Math 函数都属于 Object。
 	二者区别：基本数据类型的存放在栈中；引用数据类型存放在堆中，它的地址在栈中，一般我们访问就是它的地址。
```

#### 2. 说一说 null 和 undefined 的区别，如何让一个属性变为 null？

```
	null 是定义并赋值 null，undefined 是定义未赋值。
	当一个变量没有被赋值或者一个函数没有返回值或者某个对象不存在某个属性却去访问或者函数定义了形参但没有传递实参，这时候都是undefined。
	undefined 通过 typeof 判断类型是 undefined，undefined == undefined  undefined === undefined。 
	null 通过 typeof 判断类型是 object，null === null  null == null  null == undefined null !== undefined undefined。
	让一个变量为 null，直接给该变量赋值为 null 即可。
```

