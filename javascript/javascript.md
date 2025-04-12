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
* [12. 说一说 call apply bind 的作用和区别？](#12-说一说-call-apply-bind-的作用和区别)
* [13. 说一说原型与原型链？](#13-说一说原型与原型链)
* [14. 说一说 new 会发生什么？](#14-说一说-new-会发生什么)
* [15. 说一说 defer 和 async 区别？](#15-说一说-defer-和-async-区别)
* [16. 说一说 promise 是什么与使用方法？](#16-说一说-promise-是什么与使用方法)
* [17. 说一说 JS 实现异步的方法？](#17-说一说-JS-实现异步的方法)
* [18. 说一说 cookie、sessionStorage、localStorage 区别？](#18-说一说-cookie、sessionStorage、localStorage-区别)
* [19. 说一说如何实现可过期的 localstorage 数据？](#19-说一说如何实现可过期的-localstorage-数据)
* [20. 说一下 token 能放在 cookie 中吗？](#20-说一下-token-能放在-cookie-中吗)
* [21. 说一说 axios 的拦截器原理及应用？](#21-说一说-axios-的拦截器原理及应用)
* [22. 说一说创建 ajax 过程？](#22-说一说创建-ajax-过程)

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
    ② 内部函数引用外部作用域的变量
    ③ 返回值是函数
    ④ 创建一个对象函数，让其长期驻留
3 闭包形成的原理：作用域链，当前作用域可以访问上级作用域中的变量。
```

> [【bilibili】什么是闭包，理解闭包是什么，弄懂闭包](https://www.bilibili.com/video/BV1sd4y1S7Ed/?spm_id_from=333.337.search-card.all.click&vd_source=59a7d9ad927e21d4f309b9c4fd077245)

#### 10. 说一说 JS 变量提升？

```
1 变量提升是指 JS 的变量和函数声明会在代码编译期，提升到代码的最前面。
2 变量提升成立的前提是使用 var 关键字进行声明的变量，并且变量提升的时候只有声明被提升，赋值并不会被提升，同时函数的声明提升会比变量的提升优先。
3 变量提升的结果，可以在变量初始化之前访问该变量，返回的是 undefined；在函数声明前可以调用该函数。
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

#### 13. 说一说原型与原型链？

```
1 函数都有 prototype 属性,称之为原型，也称为原型对象，原型可以放一些属性和方法，共享给实例对象使用，也可以做继承。
2 对象都有 __proto__ 属性,这个属性指向它的原型对象,原型对象也是对象,也有 __proto__ 属性,指向原型对象的原型对象,这样一层一层形成的链式结构称为原型链，最顶层找不到则返回 null
```

> [【bilibili】前端八股文原型和原型链](https://www.bilibili.com/video/BV1LY411d7Yt/?spm_id_from=333.337.search-card.all.click&vd_source=59a7d9ad927e21d4f309b9c4fd077245)

#### 14. 说一说 new 会发生什么？

```
1 创建一个新对象
2 将新对象的 __proto__（原型）指向构造函数的 prototype（原型对象）
3 构造函数绑定新对象的 this 并执行返回结果
4 判断返回结果是否为 null，如果为 null,返回新对象，否则直接返回执行结果。
```

> [【掘金】new 做了哪些操作？手写一个 new 方法！](https://juejin.cn/post/7095977046462955534?searchId=20250411142951AC074EBDA2BDC3735B13)

#### 15. 说一说 defer 和 async 区别？

```
1 html 文件都是按顺序执行的，script 标签中没有加 defer 和 async 时，浏览器在解析文档时遇到 script 标签就会停止解析阻塞文档解析，先加载 JS 文件，加载完之后立即执行，执行完毕后才能继续解析文档。
2 在 script 标签中写入 defer 或者 async 时，就会使 JS 文件异步加载，即 html 执行到 script 标签时，JS 加载和文档解析同时进行。
3 async 是在 JS 加载完成后立即执行 JS 脚本，阻塞文档解析，而 defer 则是 JS 加载完成后，在文档解析完成后执行 JS 脚本。
```

> [【bilibili】script 标签 defer 和 async 的区别](https://www.bilibili.com/video/BV1PA411x7jA/?spm_id_from=333.337.search-card.all.click&vd_source=59a7d9ad927e21d4f309b9c4fd077245)

#### 16. 说一说 promise 是什么与使用方法？

```
1 概念：Promise 是异步编程的一种解决方案，用于解决回调地狱问题，让代码可读性更高，更利于维护。 
2 Promise 有三种状态 fulfilled/resolved(成功)、rejected(失败)、pending(执行中)。
3 使用方法：
	① 可以通过 new Promise((resolve,reject) => { resolve(); reject(); }) 将构造函数实例化；
	② 实例创建完成后，可以使用 .then 方法指定成功或者失败的回调函数，也可以用 .catch 捕获失败，
	then 和 catch 最后也是返回 promise 对象，所以可以链式调用。
	③ Promise.all([p, p2, p3])，p1,p2,p3 都是 promise 对象，只有里面的参数都返回成功，它的结果才会成功
	④ Promise.race([p1, p2, p3])，p1,p2,p3 都是 promise 对象，第一个完成的 promise 的结果就是最终的结果
```

> [【bilibili】异步编程: 一次性搞懂 Promise, async, await](https://www.bilibili.com/video/BV1WP4y187Tu/?spm_id_from=333.337.search-card.all.click&vd_source=59a7d9ad927e21d4f309b9c4fd077245)

#### 17. 说一说 JS 实现异步的方法？

```
1 回调函数
2 事件监听
3 setTimeout（定时器）
4 Promise
5 generator 生成器
6 async/await
```

> [【掘金】JavaScript 异步编程的 6 种方法](https://juejin.cn/post/6844903776780828685?searchId=20250411163615E6548F370DD46496CFC6)

#### 18. 说一说 cookie、sessionStorage、localStorage 区别？

```
1 Cookie、SessionStorage、LocalStorage 都是浏览器的本地存储。
2 它们的共同点：都是存储在浏览器本地的。
3 它们的区别：
	① cookie 是由服务器端写入的，而 SessionStorage、LocalStorage 都是由前端写入的
	② cookie 的生命周期是由服务器端在写入的时候就设置好的，LocalStorage 是写入就一直存在，SessionStorage 是页面关闭的时候就会自动清除
	③ cookie 的存储空间比较小大概 4KB，SessionStorage、LocalStorage存储空间比较大，大概5M
	④ 三者的数据共享都遵循同源原则，sessionStorage 还限制必须是同一个页面
	⑤ 在前端给后端发送请求的时候会自动携带 Cookie 中的数据，但是 SessionStorage、 LocalStorage 不会
    ⑥ cookie 一般存储登录验证信息或者 token，localStorage 常用于存储不易变动的数据，减轻服务器压力，
    sessionStorage 可以用来监测用户是否是刷新进入页面，如音乐播放器恢复进度条功能 
```

#### 19. 说一说如何实现可过期的 localstorage 数据？

```
1 localStorage 如果不手动删除，会长久保存整个网站的数据。
2 实现可过期的 localStorage 有两种方法，一种是惰性删除，另一种是定时删除。
3 惰性删除是指获取数据的时候，拿到存储的时间和当前时间做对比，如果超过过期时间就清除。
4 定时删除是指每隔一段时间执行一次删除操作，并通过限制删除操作执行的次数和频率，来减少删除操作对CPU的长期占用。
5 LocalStorage 清空应用场景：token 存储在 LocalStorage 中，要清空。
```

> [【掘金】运用惰性删除和定时删除实现可过期的 localStorage 缓存](https://juejin.cn/post/7064197186480766984?searchId=2025041120523639B3F6908C58B08AFC1A)

#### 20. 说一下 token 能放在 cookie 中吗？

```
1 能。
2 token 一般是用来判断用户是否登录的，它内部包含的信息有：uid(用户唯一的身份标识)、time(当前时间的时间戳)、sign（签名，token 的前几位以哈希算法压缩成的一定长度的十六进制字符串）。
3 token 可以存放在 Cookie 中，token 是否过期，应该由后端来判断，不该前端来判断，所以 token 存储在 cookie 中只要不设置 cookie 的过期时间就行
4 如果 token 失效，就让后端在接口中返回固定的状态表示 token 失效，需要重新登录，再重新登录的时候，重新设置 cookie 中的 token 就行。
5 token 认证流程：
	① 客户端使用用户名跟密码请求登录 
	② 服务端收到请求，去验证用户名与密码 
	③ 验证成功后，服务端签发一个 token ，并把它发送给客户端 
	④ 客户端接收 token 以后会把它存储起来，比如放在 cookie 里或者 localStorage 里 
	⑤ 客户端每次发送请求时都需要带着服务端签发的 token（把 token 放到 HTTP 的 Header 里） 
	⑥ 服务端收到请求后，需要验证请求里带有的 token ，如验证成功则返回对应的数据
```

#### 21. 说一说 axios 的拦截器原理及应用？

```
1 Axios 是一个基于 promise 的 HTTP 库，可以用在浏览器和 node.js 中。从浏览器中创建 XMLHttpRequests,从 node.js 创建 http 请求,支持 Promise API,可拦截请求和响应，可转换请求数据和响应数据，可取消请求，可自动转换 JSON 数据，客户端支持防御 XSRF。
2 axios 拦截器分为 请求（request）拦截器和 响应（response）拦截器。
3 请求拦截器用于在接口请求之前做的处理，比如为每个请求带上相应的参数（token，时间戳等）
4 响应拦截器用于在接口返回之后做的处理，比如对返回的状态进行判断（token 是否过期）。
5 拦截器原理：创建一个 chn 数组，数组中保存了拦截器相应方法以及 dispatchRequest（dispatchRequest 这个函数调用才会真正的开始下发请求），把请求拦截器的方法放到 chn 数组中 dispatchRequest 的前面，把响应拦截器的方法放到 chn 数组中 dispatchRequest 的后面，把请求拦截器和相应拦截 forEach 将它们分 unshift,push 到 chn 数组中，为了保证它们的执行顺序，需要使用 promise，以出队列的方式对 chn 数组中的方法挨个执行。
```

> [【掘金】axios 请求拦截器&响应拦截器](https://juejin.cn/post/7100470316857557006?searchId=202504120858391352C61B3495CBA331FD)

#### 22. 说一说创建 ajax 过程？

```
1 创建异步对象，即 XMLHttpRequest 对象。 
2 使用 open 方法设置请求参数。open(method, url, async)。参数解释：请求的方法、请求的 url、是否异步。第三个参数如果不写，则默认为 true。
3 发送请求：send()。 
4 注册事件：注册 onreadystatechange 事件，状态改变时就会调用。如果要在数据完整请求回来的时候才调用，我们需要手动写一些判断的逻辑。 
5 服务端响应，获取返回的数据。 
```

> [【掘金】Ajax 原理一篇就够了](https://juejin.cn/post/6844903618764603399?searchId=20250412091905DD062E4A88B06CB01989)

