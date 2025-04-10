## CSS 面试知识点总结

本部分主要是笔者在复习 CSS 相关知识和一些相关面试题时所做的笔记，如果出现错误，希望大家指出！

### 目录

* [1. 说一说盒模型？](#1-说一说盒模型)
* [2. 说一下浮动？](#2-说一下浮动)
* [3. 说一说样式优先级的规则是什么？](#3-说一说样式优先级的规则是什么)
* [4. 说一说CSS尺寸设置的单位?](#4-说一说CSS尺寸设置的单位)
* [5. 说一说BFC？](#5-说一说BFC)
* [6. 说几个未知宽高元素水平垂直居中方法?](#6-说几个未知宽高元素水平垂直居中方法)
* [7. 说一说三栏布局的实现方案？](#7-说一说三栏布局的实现方案)

#### 1. 说一说盒模型？

```
1 css 盒子的组成包括 margin、border、padding、content。
2 盒模型分为两类，一是标准盒模型(content-box)，二是怪异盒模型(border-box)。一般我们的盒子默认是标准盒模型。
3 两者区别是标准盒模型的实际宽高会把 padding 和 border 计算在内，而怪异盒模型不会。
4 形成怪异盒模型的条件是 box-sizing:border-box；形成标准盒模型的条件 box-sizing:content-box。
```

#### 2. 说一下浮动？

```
1 浮动的作用：常用于图片，可以实现文字环绕图片。
2 浮动的特点：脱离文档流，容易造成盒子塌陷，影响其他元素的排列。
3 解决塌陷问题： 
    ① 父元素中添加 overflow：hidden; 
    ② 给父元素添加高度; 
    ③ 建立空白 div，添加 clear; 
    ④ 在父级添加伪元素::after{ content : ' ', clear : both , display : table} ; 
```

#### 3. 说一说样式优先级的规则是什么？

```
1 !important 。
2 内联样式（style）。
3 id 选择器（#id{}） 。
4 类选择器（.class{}） = 属性选择器（a[href="segmentfault.com"]{}） = 伪类选择器（ :hover{}） 。
5 标签选择器（span{}） = 伪元素选择器（ ::before{}）= 后代选择器（.father .child{}）。
6 子选择器（.father > .child{}） = 相邻选择器（ .bro1 + .bro2{}）。
7 通配符选择器（*{}）。
```

#### 4. 说一说CSS尺寸设置的单位?

```
1 css 一共有五个长度单位，分别是 px，em，rem，vw，vh，除了 px 是绝对单位，其他都是相对单位。
2 em 相对于自身大小（但在 font-size 中相对于父元素字体大小）。
3 rem 相对于根元素的字体大小。
4 vw 相对于可视化窗口的宽（1vw 就是 1% 可视化窗口宽度）。
5 vh 相对于可视化窗口的高（1vh 就是 1% 可视化窗口高度）。
6 一般采用 rem + 媒体查询或者 rem + vw 来实现响应式布局。原理是当窗口大小发生变化时，通过媒体查询或者 vw 改变根元素的字体大小，从而改变以 rem 为单位的元素大小。
```

#### 5. 说一说BFC？

```
1 定义：块级格式化上下文，独立的渲染区域，不会影响边界外的元素（可以看作一种属性）
2 形成条件：
    float 属性不为 none；
    position 为 absolute 或 fixed；
    overflow 不为 visible；
    display 为 inline-block、table-cell、table-caption、flex、inline-flex；
3 布局规则：
4 区域内容 box 从上到下排列 ；
    box 垂直方向的距离由 margin 决定 ；
    同一个 BFC 内 box 的 margin 会重叠；
    BFC 不会与 float 元素重叠；
    BFC 计算高度也会计算 float 元素；
5 解决的问题：
    解决浮动元素重叠问题；
    解决父元素高度塌陷问题；
    解决 margin 重叠问题；
```

> [【bilibili】带你用最简单的方式理解最全面的BFC](https://www.bilibili.com/video/BV1aZ4y1M7gW/?spm_id_from=333.337.search-card.all.click&vd_source=59a7d9ad927e21d4f309b9c4fd077245)

#### 6. 说几个未知宽高元素水平垂直居中方法?

```
1 绝对定位，设置父元素 position:absolute;top:50%;left:50%，transform: translate(-50%,-50%);
2 flex 布局，设置父元素 display:flex; justify-content:center; align-items:center
3 grid 布局，设置父元素 display: grid; justify-content:center; align-items:center 
4 表格布局，设置父元素 display: table-cell，text-align: center;vertical-align: middle;，设置子元素为行内块 display: inline-block; 
```

#### 7. 说一说三栏布局的实现方案？

```
1 定义：三栏布局一般指的是页面中一共有三栏，左右两栏宽度固定，中间自适应的布局。  
2 实现方式：
    ① 浮动 + margin / BFC，左右两栏设置固定大小，并设置对应方向的浮动。中间一栏设置左右两个方向的 margin 值 / 触发BFC。
    ② 利用 flex 布局的方式，左右两栏设置固定大小，中间一栏 flex 设置为 1。
    ③ 利用表格布局的方式，父元素设置 width:100%;display:table;，左中右设置 display:table-cell;并且左右设置固定大小。
    ④ 绝对定位 + margin，左右两栏设置为绝对定位，中间设置对应方向大小的 margin 的值
    ⑤ 圣杯布局，利用浮动和负边距来实现。父级元素设置左右的 padding，三列均设置向左浮动，中间一列放在最前面，宽度设置为父级元素的宽度，因此后面两列都被挤到了下一行，通过设置 margin 负值将其移动到上一行，再利用相对定位，定位到两边。圣杯布局中间列的宽度不能小于左边列的宽度，否则左边列上不	去，而双飞翼布局则不存在这个问题。
    ⑥ 双飞翼布局，双飞翼布局相对于圣杯布局来说，左右位置的保留是通过中间列的 margin值来实现的，而不是通过父元素的padding来实现的。本质上来说，也是通过浮动和外边距负值来实现的。
```

> [【bilibili】最简单最全面的三栏布局](https://www.bilibili.com/video/BV1gD4y1R7Ui/?spm_id_from=333.337.search-card.all.click&vd_source=59a7d9ad927e21d4f309b9c4fd077245)

