## Vue 面试知识点总结

本部分主要是笔者在复习 Vue 相关知识和一些相关面试题时所做的笔记，如果出现错误，希望大家指出！

### 目录

* [1. 说一说 vue 钩子函数？](#1-说一说-vue-钩子函数？)
* [2. 说一说组件通信的方式？](#2-说一说组件通信的方式)
* [3. 说一说 computed 和 watch 的区别？](#3-说一说-computed-和-watch-的区别)

#### 1. 说一说 vue 钩子函数？

```
1 概念：Vue 实例创建和销毁过程中自动执行的函数。
2 常见的生命周期中的钩子函数：
	① 创建阶段：beforeCreate，create，beforeMount，mount
	② 更新阶段：beforeUpdate，update，activeted
	③ 销毁阶段：beforeDestroy，destroy
3 完整的父子组件生命周期执行顺序：
	① 加载渲染过程：父 beforeCreate —> 父 created —> 父 beforeMount —> 子 beforeCreate —> 子 created —> 子 beforeMount —> 子 mounted —> 父 mounted 
	② 子组件更新过程：父 beforeUpdate —> 子 beforeUpdate —> 子 updated —> 父 updated 
	③ 父组件更新过程：父beforeUpdate —> 父updated 
	④ 销毁过程：父 beforeDestroy —> 子 beforeDestroy —> 子 destroyed —> 父 destroyed   
```

#### 2. 说一说组件通信的方式？

```
1 父子组件通信常用 props 和 $emit 还有 $refs
2 兄弟组件通信常用定义的公共事件 bus 的 $on、$emit
3 祖先和子孙组件通信常用 $attrs、$listener、provide 和 inject
4 复杂通信常用 vuex   
```

> [vue 中 8 种组件通信方式, 值得收藏](https://juejin.cn/post/6844903887162310669?searchId=202504171531271BE6C87A8EBC1DC6CEB5)

#### 3. 说一说 computed 和 watch 的区别？

```
1 computed：是计算属性，依赖其它属性值，并且 computed 的值有缓存，只有它依赖的属性值发生改变，下一次获取 computed 的值时才会重新计算 computed 的值； 
2 watch： 更多的是观察的作用，支持异步，类似于某些数据的监听回调 ，每当监听的数据变化时都会执行回调进行后续操作；
3 computed 应用场景：需要进行数值计算，并且依赖于其它数据时，应该使用 computed，因为可以利用 computed 的缓存特性，避免每次获取值时，都要重新计算； 
4 watch 应用场景：需要在数据变化时执行异步或开销较大的操作时，应该使用 watch，使用 watch 选项允许我们执行异步操作 ( 访问一个 API )，限制我们执行该操作的频率，并在我们得到最终结果前，设置中间状态。这些都是计算属性无法做到的。
```
