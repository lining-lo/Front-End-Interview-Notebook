## Vue 面试知识点总结

本部分主要是笔者在复习 Vue 相关知识和一些相关面试题时所做的笔记，如果出现错误，希望大家指出！

### 目录

* [1. 说一说 vue 钩子函数？](#1-说一说-vue-钩子函数？)

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
