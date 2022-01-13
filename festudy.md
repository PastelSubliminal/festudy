# 前端基础知识

## HTML + CSS问题

### 如何清除浮动？
clear 清除浮动（添加空div法）在浮动元素下方添加空 div，并给该元素写 CSS 样式 {clear:both; height:0; overflow:hidden;}
给浮动元素父级设置高度
父级同时浮动（需要给父级同级元素添加浮动）
父级设置成 inline-block
给父级添加 overflow: hidden
万能清除法 after伪类 清浮动（现在主流方法，推荐使用）

BFC 触发条件
根元素
position: absolute/fixed
display: inline-block / table
float 元素
ovevflow 不为 visible

### 行内元素和块元素有哪些，本质区别
行内元素：span、img、button、input、b、q、i、a、em、label
块元素：div、p、h1-h6、ul、ol、dl、li、header、footer、aside、section、article、form、table

区别：行内元素设置 width，height 属性无效，起边距作用的只 有margin-left、margin-right、padding-left、padding-right，其它属性不会起边距效果（可以设置 line-height），设置 margin 和 padding 的上下不会对其他元素产生影响。块级元素可以设置 width，height 属性

### 水平、垂直居中
水平：行内元素：父元素 text-align: center
块元素：宽度已知用 margin: auto，宽度未知：用 display: inline 变成行内元素后在父元素上设置 text-align: float
垂直：display: flex; align-item: center

### flex
Flex 意为弹性布局，任何一个容器都可以指定为 Flex 布局。行内元素也可以使用 Flex 布局。
flex-direction属性 该属性定义了子元素的排列方向
```CSS
.box{
    flex-direction: row | row-reverse | column | column-reverse;
}
```
flex-wrap属性 该属性称“轴线”的方向
```CSS
.box{
    flex-wrap: nowrap | wrap | wrap-reverse;
}
```
flex-flow属性：|| ; flex-direction 和 flex-wrap 的简写，默认值为 row nowrap
justify-content 属性 该属性定义了子元素在主轴上的对齐方式
```CSS
.box{
    justify-content: flex-start | flex-end | center | space-between | space-around;
}
```
align-items 属性 该属性定义了项目在交叉轴上如何对齐
```CSS
    .box{
        align-items: flex-start | flex-end | center | baseline | stretch;
    }
```
align-content 属性，该属性定义了多跟轴线的对齐方式，如果项目只有一根轴线，该属性不起作用
```CSS
    .box{
    align-content: flex-start | flex-end | center | space-between | space-around | stretch;
    }
```

### CSS让元素不可见的方法
display: none | z-index: -9999（只能在定位元素上生效） | opacity:0 | position: absolute; left: -9999; top: -9999

### 如何设计移动端页面和响应式界面

### 选择器优先级
!important - 内联 - id - 类 - 标签 - 通配符 - 继承

### px、em、rem、%、vw、vh、vm这些单位的区别
em：参考的是父元素的 font-size，具有继承的特点，如果自身定义了 font-size 则按自身来计算（浏览器默认字体是16px），整个页面内 1em 不是一个固定的值
rem：相对于根元素 html，可以设置根元素 html 的 font-size 为 10px，则 1.2em 就是12px；
vw：css3 新单位，view width 的缩写，是指可视窗口的高度，假如宽度是1200px，则10vw就是120px；举个例子：浏览器宽度1200px， 1 vw = 1200px/100 = 12 px。
Vh：类似vw，指的是可视窗口的高度。
Vm：相对于视口的宽度或高度中较小的那个，其中最小的单位被均分为100个单位，举个例子：浏览器高度900px，宽度1200px，取最小的浏览器高度，1vm = 900px/100 = 9 px

### 说一下对HTML语义化的理解
语义化就是选择与语义相符合的标签，使代码语义化，这样不仅便于开发者进行阅读，同时也能维护和写出更优雅的代码，还能够让搜索引擎和浏览器等工具更好地解析。
通俗的讲语义化就是让正确的标签做正确的事情，比如段落用p标签，头部用 header 标签，主要内容用 main 标签，侧边栏用 aside 标签等等。

### meta viewport 是做什么用的
将视口大小设置为可视区域的大小。

### 两种盒模型
content-box 和 border-box 的区别：计算最大尺寸时是否包含边距，border-box 最大尺寸是包含了边距的（width:100， content(80) + border(10) = 100），content-box 最大尺寸是不包含边距（width: 100， content(100) + border(10) = 120）

### 响应式布局实现原理和方案
原理：响应式开发一套界面，通过检测视口分辨率，针对不同客户端在客户端做代码处理，来展现不同的布局和内容
方案
媒体查询：@media 可以针对不同的屏幕尺寸设置不同的样式，当你重置浏览器大小的过程中，页面也会根据浏览器的宽度和高度重新渲染页面。
百分比布局：通过百分比单位，可以使得浏览器中组件的宽和高随着浏览器的高度的变化而变化，从而实现响应式的效果。Bootstrap 里面的栅格系统就是利用百分比来定义元素的宽高，CSS3 支持最大最小高，可以将百分比和 max(min) 一起结合使用来定义元素在不同设备下的宽高。
rem布局：rem 是 CSS3 新增的单位，rem 单位都是相对于根元素 html 的 font-size 来决定大小的。当页面的 size 发生变化时，只需要改变 font-size 的值，那么以 rem 为固定单位的元素的大小也会发生响应的变化（而 em 是相对于父元素的）。

### DOM和BOM是什么
BOM是浏览器对象模型，用来获取或设置浏览器的属性、行为，例如:新建窗口、获取屏幕分辨率、浏览器版本号等。
DOM是文档对象模型，用来获取或设置文档中标签的属性，例如获取或者设置input表单的value值。

### CSS加载会造成阻塞吗
1. css 加载不会阻塞 DOM 树的解析。
2. css 加载会阻塞 DOM 树的渲染。
3. css 加载会阻塞后面 js 语句的执行。

### 伪类和伪元素的区别
都是不存在于 DOM 文档中的虚拟元素，虽然逻辑上存在，但并不实际存在于 DOM 树中。
伪类的效果可以通过添加实际的类来实现。
伪元素的效果可以通过添加实际的元素来实现。
所以它们的本质区别就是是否抽象创造了新元素。
伪类只能使用 “:”，伪元素可以使用 “:” 也可以使用 “::”。

## JavaScript问题

### JS 基本数据类型和引用数据类型，解释一下引用数据类型
基本：null、undefined、boolean、number、string、symbol
引用：Obect、Array、Function、Data
基本数据类型指的是简单的数据段，是按值访问的，因为可以直接操作保存在变量中的实际值。引用数据类型指的是有多个值构成的对象，改变引用数据类型是操作对象在栈内存中的引用地址。
引用数据类型的值可以改变、可以添加属性和方法、赋值是对象引用

### 原型和原型链
每个"构造函数"中都有一个默认的属性， 叫做 prototype， prototype 属性保存着一个对象， 这个对象我们称之为"原型对象"， prototype 指向它的原型对象

每个"原型对象"中都有一个默认的属性， 叫做 constructor， constructor 指向当前原型对象对应的那个"构造函数"
通过构造函数创建出来的对象我们称之为"实例对象"， 每个"实例对象"中都有一个默认的属性， 叫做__proto__， \__proto__ 指向创建它的那个构造函数的"原型对象"

### JS 的传参
按值传递(call by value)是最常用的求值策略：函数的形参是被调用时所传实参的副本。修改形参的值并不会影响实参。（深拷贝？）通过自定义函数实现深拷贝（递归遍历对象）
1. for in 遍历对象中所有属性，取出对应值
2. 通过 sourceValue.constructor 拿到这个对象的构造函数的类型，新建对象或数组
3. 取值如果是引用数类型，将遍历到的属性值复制给新建的空对象或数组，否则直接复制之前属性
```JavaScript
//通过遍历拿到 source 中的所有属性，取出当前遍历到的属性对应的值，判断当前的取值是否是引用数据类型（对象、数组、函数，一般是对象嵌套），通过 sourceValue.constructor 拿到这个对象的构造函数的类型，然后新建这个对象或数组，再次调用深拷贝，将遍历到的属性的值拷贝给新建的对象或数组，如果不是引用数据类型，之前的属性拷贝即可
function deCopy(target， source){
    for(let key in source){
        let sourceValue = souce[key];
        if(sourceValue instanceof Object){
            let subTarget = new sourceValue.constructor;
            deCopy(subTarget， sourceValue);
        }else{
            target[key] = sourceValue
        }
    }
}
```

按引用传递(call by reference)时，函数的形参接收实参的隐式引用，而不再是副本。这意味着函数形参的值如果被修改，实参也会被修改。同时两者指向相同的值。（浅拷贝？）

按引用传递会使函数调用的追踪更加困难，有时也会引起一些微妙的 BUG。按值传递由于每次都需要克隆副本，对一些复杂类型，性能较低。两种传值方式都有各自的问题。可能很多人都是做后端的，所有会想到“引用传递”，然而实际上却不是，导致了问题的产生。

### 跨域
协议、域名、端口三者有一个不同就会引起跨域的错误问题
严格的说，浏览器并不是拒绝所有的跨域请求，实际上拒绝的是跨域的读操作。浏览器的同源限制策略是这样执行的：
通常浏览器允许进行跨域写操作（Cross-origin writes），如链接，重定向；
通常浏览器允许跨域资源嵌入（Cross-origin embedding），如 img、script 标签；
通常浏览器不允许跨域读操作（Cross-origin reads）。
解决：JSONP：通过创建 script 标签，其 src 指向非同源的 url，并传递一个 callback 参数作为函数名的函数的调用和一系列参数，页面接收到响应后执行回调并对数据进行处理。CORS：服务器端操作，设置 http header

### 数组去重
方法一：倒进集合再倒出来
```JavaScript
[...new Set([1， 2， 2， 3， 4， 5， 5])]
//[1， 2， 3， 4， 5]
```
方法二：indexOf()
方法三：双重循环（先排序然后用 splice ）

### ES6 的symol是什么，适用场景有什么
一种特殊的数据类型，定义不可更改，适合用来作为属性名标识独一无二的对象
```JavaScript
//创建一个symbol类型的值
const s = Symbol();
console.log(typeof s);//"symbol"
```
用作对象属性、模拟类的私有方法

### async 和 await，如何捕获异常
写法跟 generator 很像，就是将星号替换成 async，将 yield 替换成 await。async 函数返回一个 promise 对象，如果 async函数没有返回值，它会返回 Promise.resolve(undefined)。如果 await 等到的不是一个 promise 对象，那跟着的表达式的运算结果就是它等到的东西。
使用场景：需要 promise 链式调用的时候，每个步骤都是异步的，且依赖上一步的执行结果
try{} catch{} finally
try 语句：里面是填写 js 代码，里面可以接 throw 语句，抛出自己填写的报错信息（一般抛出 throw new Error(""))，并且 try 里面的执行语句终止，catch 的变量 e 会接收这个错误；throw 会在离自己最近的 try 语句中生效.
catch: 如果 try 语句里面有错误，catch 会返回错误的具体信息；需要一个变量 e 来接收错误，e 只在自己的 catch 语句中生效。变量 e 有几个属性，e.stack 调用栈信息；e.message 具体的错误原因；e.name: 错误类型函数
finally：里面的代码永远可以运行，不管前面有没有错误。

### 防抖和节流
防抖是事件触发 n 秒后执行会掉，如果在这 n 秒内又被触发，则重新计时。使用场景：提交按钮时防止多次提交，只执行最后一次提交。
实现
```js
  function debounce(f,time){
    let timeId = null
    return function(...argments){
      clearTimeout(timeId)
        var timeId = setTimeout(f(argments),time)
    }
  }
```
节流是 n 秒内只能触发一次函数，如果 n 秒内多次触发，只有一次生效。使用场景：拖拽在固定时间内只执行一次，防止超高频率触发位置变动；缩放时监控浏览器 resize
实现
```js
function throttle(f, duration) {
  var timerId
  var lastRunTime = 0
  return function(...args) {
    clearTimeout(timerId)
    var now = Date.now()
    if (now - lastRunTime > duration) {
      f(...args)
      lastRunTime = now
    } else {
      timerId = setTimeout(() => {
        f(...args)
        lastRunTime = Date.now()
      }, duration)
    }
  }
}
```

#### 类数组转换为数组的方法
使用 Array.from()
使用 Array.prototype.slice.call()
使用 Array.prototype.forEach() 进行遍历并生成新的数组
转换后数组的长度由 length 属性决定。索引不连续时转换结果是连续的，会自动补位

#### ES6 新特性
const和let
模板字符串
箭头函数
对象和数组解构
对象超类：ES6 允许在对象中使用 super 方法
for...of 和 for...in，for...of 用于遍历一个迭代器，如数组，for...in 用来遍历对象中的属性
ES6中的类：ES6 中支持 class 语法，不过，ES6 的 class 不是新的对象继承模型，它只是原型链的语法糖表现形式。
函数的参数默认值
Spread / Rest 操作符
二进制和八进制字面量

#### 语句和表达式的区别
语句和表达式的区别在于，语句是为了进行某种操作，一般情况下不需要返回值，而表达式都是为了得到返回值，一定会返回一个值（这里的值不包括undefined）。
例如：var a = 1 + 2 是语句
1 + 2 是表达式

#### 前端模块化和组件化
我们把每一个 .js 文件都视为一个 块，模块内部有自己的作用域，不会影响到全局。并且，我们 约定一些关键词来进行依赖声明和 API 暴露。而这些约定的关键词就是通过制定一些 规范 去进行规范的。比较有名模块化规范的是 CMD、AMD、CommonJS 和 ES6 Module。Webpack 是模块化工具

将模板、样式和逻辑都抽象出来独立出来的做法称之为组件化。比如说，我们在开发 Button 组件的时候，不再需要分别在几个文件夹之间跳来跳去，去修改它们的模板、样式和逻辑。我们只需要在公共的 Button 组件的文件夹里修改就好了。Vue 和 React 也是组件化的框架

#### 为什么对象在JavaScript中不可迭代
直接原因：ES6中的 Object.prototype 没有实现 Symbol.iterator 属性。
对象的哪个属性先遍历，哪个属性后遍历是不确定的，需要开发者手动指定。
部署了遍历器接口的对象其实就是 ES6 里的 Map 结构，现在 ES6 中内置了数据结构 Map，所以很方便地实现了集合对象。

### js继承方式
原型链继承：将父类的实例作为子类的原型
构造继承：使用 call()、apply() 或 bind() 方法继承父类构造函数中的属性
实例继承：为父类实例添加新特性，作为子类实例返回
组合继承：通过调用父类构造，继承父类的属性并保留传参的优点，然后通过将父类实例作为子类原型，实现函数复用
寄生组合继承：通过寄生方式，砍掉父类的实例属性，这样，在调用两次父类的构造的时候，就不会初始化两次实例方法/属性，避免的组合继承的缺点

### 实现call，apply，bind


### const定义的变量真的不可改变吗
仅限于 const 定义基本数据类型

### 什么是DOM事件流，如何阻止事件冒泡
一个事件的生命周期有三个阶段：捕捉，目标，冒泡。

1. 捕捉阶段
当某个事件被触发时，浏览器会找到涉及的元素。涉及的元素称为目标。浏览器会找出 body 元素和目标之间所有的元素并分别检查它们，看其有没有事件绑定。浏览器会先触发外层事件的处理器，最后才会轮到目标的事件处理器。
2. 目标阶段
当捕捉阶段完成后，浏览器会触发目标元素上任何已添加的事件类型监听器，这里的先后顺序是按照事件定义的先后顺序来的。
3. 冒泡阶段
冒泡阶段的顺序与捕捉阶段的顺序刚好相反，在此阶段，浏览器会优先处理目标的事件处理器，然后一层层往外处理其余的事件处理器。

阻止事件冒泡，防止事件冒泡而带来不必要的错误和困扰。
这个方法就是：stopPropagation()

### 事件委托
在外部节点添加一个事件处理器，并根据 target 属性判断事件来源，这样可以把内部共用的事件绑定到外部

### 事件循环
js 是单线程执行的，同时它又是基于事件驱动的非阻塞 IO 编程模型，事件循环机制是实现这一特性的原理
异步操作时，将任务给到另外的线程（CPU 的其它核），异步事件触发之后，就会通知主线程，主线程执行相应事件的回调。

执行顺序
程序运行会从上至下依次执行所有的同步代码
在执行的过程中如果遇到异步代码会将异步代码放到事件循环中
当所有同步代码都执行完毕后，JS 会不断检测 事件循环中的异步代码是否满足条件
一旦满足条件就执行满足条件的异步代码

### ES6的Class有什么好处
Class 是 ES6 提供的更接近于传统语言的的写法，作为对象的模板.通过 class 关键字，可以定义类
class 写法只是一个语法糖，它只是让对象原型的写法更加清晰，更像面向对象编程的语法

### 全局作用域和函数作用域
全局作用域在页面打开时被创建，页面关闭时被销毁
编写在 script 标签中的变量和函数，作用域为全局，在页面的任意位置都可以访问到
在全局作用域中有全局对象 window，代表一个浏览器窗口，由浏览器创建，可以直接调用
全局作用域中声明的变量和函数会作为 window 对象的属性和方法保存

调用函数时，函数作用域被创建，函数执行完毕，函数作用域被销毁
每调用一次函数就会创建一个新的函数作用域，他们之间是相互独立的
在函数作用域中可以访问到全局作用域的变量，在函数外无法访问到函数作用域内的变量
在函数作用域中访问变量、函数时，会先在自身作用域中寻找，若没有找到，则会到函数的上一级作用域中寻找，一直到全局作用域
在函数作用域中也有声明提前的特性，对于变量和函数都起作用，此时函数作用域相当于一个小的全局作用域，详细声明提前请看声明提前部分

### forEach 和 map
共同点
只能遍历数组
都是循环遍历数组中的每一项
每一次执行匿名函数都支持三个参数，数组中的当前项 item，当前项的索引 index ，原始数组 input
匿名函数中的 this 都是指 window

不同点
forEach 没有返回值，不能 return；map 有返回值，可以 return

### this
this 指向什么取决函数的调用形式，而不取决于函数的在哪调用，也不取决于在哪定义。
当一个函数以方法的形式被调用时，如 array.length，函数的 this 就是调用它的对象。
以纯函数形式调用时，this 就是 window，但用 new 来调用 this 时，this 就是那个新建的对象，如构造函数。
this 永远不能被赋值，即 this 不能写在等号左边。

### 图片懒加载原理
一张图片就是一个 img 标签，浏览器是否发起请求图片是根据 img 的 src 属性，所以实现懒加载的关键就是，在图片没有进入可视区域时，先不给 img 的 src 赋值，这样浏览器就不会发送请求了，等到图片进入可视区域再给 src 赋值。
实现懒加载有四个步骤，如下：
1.加载 loading 图片
2.判断哪些图片要加载【重点】
3.隐形加载图片
4.替换真图片

### 什么操作会引起内存泄漏
引擎中有垃圾回收机制，调用函数的时候，系统会分配对应的空间给这个函数使用（空间大小的情况一般由这个函数的变量和形参决定），当函数试用完毕以后，这个内存空间要释放，还给系统，在函数内部声明的变量和形参是属于当前函数的内存空间的。
其实引擎虽然针对垃圾回收做了各种优化从而尽可能的确保垃圾得以回收，但并不是说我们就可以完全不用关心这块了，我们代码中依然要主动避免一些不利于引擎做垃圾回收操作，因为不是所有无用对象内存都可以被回收的，那当不再用到的对象内存，没有及时被回收时，我们叫它 内存泄漏
1. 不合理的使用闭包，两个函数嵌套，内部 return 的函数中存在对外部函数中变量的引用。在函数调用后，把外部的引用关系置空就好了。
2. 隐式全局变量，可以在使用完之后将其置空（null）或重新分配。
3. 遗忘的定时器，也就是 setTimeout 和 setInterval。调用 clearInterval 和 clearTimeout 清除。
4. 遗忘的事件监听器、监听者模式
5. 遗忘的Map、Set对象。如果使用 Map ，对于键为对象的情况，可以采用 WeakMap，WeakMap。如果需要使用 Set 引用对象，可以采用 WeakSet，WeakSet 对象允许存储对象弱引用的唯一值。
这里可能需要简单介绍下，谈弱引用，我们先来说强引用，之前我们说 JS 的垃圾回收机制是如果我们持有对一个对象的引用，那么这个对象就不会被垃圾回收，这里的引用，指的就是 强引用 ，而弱引用就是一个对象若只被弱引用所引用，则被认为是不可访问（或弱可访问）的，因此可能在任何时刻被回收。
6. 未清理的 Console 输出
内存泄漏如何排查和定位：https://juejin.cn/post/6984188410659340324

### 垃圾回收机制
标记清除
大部分浏览器以此方式进行垃圾回收，当变量进入执行环境（函数中声明变量）的时候，垃圾回收器将其标记为“进入环境”，当变量离开环境的时候（函数执行结束）将其标记为“离开环境”，在离开环境之后还有的变量则是需要被删除的变量。标记方式不定，可以是某个特殊位的反转或维护一个列表等。
垃圾收集器给内存中的所有变量都加上标记，然后去掉环境中的变量以及被环境中的变量引用的变量的标记。在此之后再被加上的标记的变量即为需要回收的变量，因为环境中的变量已经无法访问到这些变量。

### 浏览器不同页面之间怎么传递消息
1. 通过 form 表单传递参数：注意表单元素隐藏按钮的使用
2. 通过带参数的 url 传递：url?参数名1=值1&参数名2=值2
3. 请求 request 对象：将数据绑定到 request 对象上，通过 request 对象 getAttribute 和 setAttribute 方法读写
4. 用户会话 session 对象：将数据绑定到 session 对象上，通过 session 对象 getAttribute 和 setAttribute 方法读写
5. application 对象：将数据绑定到 application 对象上，通过 application 对象 getAttribute 和 setAttribute 方法读写
6. cookie 对象：将数据写到到客户端浏览器 cookie 文件中
其中方式一、方式二只能实现字符串参数的传递，方式三、四、五、六可以实现对象的传递（方式六需要对象序列化后进行存储）。
方式一、方式二、方式三数据传递只能请求页面获取数据，而方式四、五、六可以在多个不同页面获取数据对象。
方式四和六保存的数据对象都是和某个用户相关的信息，不同的是方式四将数据保存到服务器内存中，方式六将数据保存到客户端内存中。
方式五保存的数据对象都是和所有用户相关的信息，数据也是保存到服务器内存中。

### 如果一个地区的页面加载特别慢，是因为什么原因，该怎么处理
使用 cdn，使用户就近获取所需内容，降低网络拥塞，提高用户访问响应速度和命中率

### 预检请求和简单请求
对那些可能对服务器数据产生副作用的 HTTP 请求方法，浏览器必须首先使用 OPTIONS 方法发起一个预检请求（preflight request），从而获知服务端是否允许该跨域请求。服务器确认允许之后，才发起实际的 HTTP 请求。在预检请求的返回中，服务器端也可以通知客户端，是否需要携带身份凭证（包括 Cookies 和 HTTP 认证相关数据）。

按照预检请求的理解，简单请求就是对服务器无副作用的请求。

### 箭头函数没有arguments，怎么获取不知道数量的参数
可以使用 ES6 的解构语法来代替。
```JavaScript
let func = (...args) => {
	console.log('函数的参数是：'， args);
}

func(1， 2， 3);
// 函数的参数是： [1， 2， 3]
```

### promise如何执行？promise.all和promise.race
异步函数返回一个 promise，一个 promise 对象代表一个异步操作结果
* promise.then(f1，f2)
      如果异步函数状态为 resolved 执行 f1，状态为 rejected 执行 f2;
      f1 或者 f2 的参数是 promise 的 [[PromiseValue]]
      f1 和 f2 函数调用结果都要有返回值
      promise.then 的返回值是一个新的 promise 对象
    * promise1 = promise.then(f1，f2)
      如果 f1 或者 f2 正常执行，那么 promise1 的状态就是 resolve，promise1.then(f3，f4) 会执行 f3
      如果 f1 或者 f2 抛出了一个错误（throw），那么 promise1 的状态就是 reject，promise1.then(f3，f4) 会执行 f4
      如果 f1 或者 f2 返回了一个新的 promise，那么 promise1 就是返回的新的 promise 对象，promise1.then(f3，f4) 的执行方式取决于新 promise 对象的状态
    * 如果 promise.then() 里面没有传递参数
      promise2  = promise1.then() 相当于下面
      promise2 = promise1.then(val=>val，reason=>{throw reason})
    * 如果 promise.then() 里面没有传递第一个参数，可以用 catch 代替 then
      promise2  = p1.then(null，f1) 相当于下面
      promise2  = p1.catch(f1)
    * promise 的链式跳转
      promise1.then(f1).catch(f2).then(f3).catch(f4)，promise 状态为 resolve 直接可以跳转执行 then，为 reject 可以跳转执行 catch
    * Promise.resolve(val)
      创建一个 [[PromiseStatus]]: "resolved"，[[PromiseValue]]: val 的 promise
      Promise.reject(val)
      创建一个 [[PromiseStatus]]: "rejected"，[[PromiseValue]]: val 的 promise

Promise.race(values)，返回一个在迭代器中遇到的第一个状态确定（settled）的 promise
```js
Promise.race=function(values){
  return new Promise((resolve，reject)=>{
    for(let i = 0 ; i< values.length;i++){
      Promise.resolve(values[i]).then(resolve，reject)
    }
  })
}
```

Promise.all(values)，返回一个 promise 实例。如果迭代器中所有的 promise 参数状态都是 resolved， 则 promise 实例的状态为 resolved，其 [[PromiseValue]] 为每个参数的 [[PromiseValue]] 组成的数组；
如果参数中的 promise 有一个失败（rejected），此实例的状态为 rejected，其 [[PromiseValue]] 为是第一个失败 promise 的 [[PromiseValue]]
```js
Promise.all = function(values) {
  return new Promise((resolve， reject) => {
      var result = []
      var resolvedCount = 0
      if (value.length == 0) {
        resolve([])
        return
      }
      for (let i = 0; i < values.length; i++) {
        Promise.resolve(values[i]).then(val => {
            result[i] = val
            resolvedCount++
            if (resolvedCount == values.length) {
              resolve(result)
            }
        }， reason => {
            reject(reason)
        })
      }
  })
}
```

### JS面向对象编程的理解
1. 抽象性：抽取核心数据,剔除无关属性和行为组成一个对象
2. 封装性：封装就是隐藏内部的实现细节
3. 继承性：所谓继承即为自己没有的继承别人有的，即在已有的对象的基础上进行拓展从而得到一个新的对象。
4. 多态性：即同一操作对于不同的对象会有不同的结果。

### SEO是什么
搜索引擎优化，提高网站在搜索引擎里面的自然排名

### 箭头函数和普通函数的区别
1. 外形不同：箭头函数使用箭头定义，普通函数中没有
2. 箭头函数都是匿名函数。普通函数可以有匿名函数，也可以有具体名函数，但是箭头函数都是匿名函数。
3. 箭头函数不能用于构造函数，不能使用 new。普通函数可以用于构造函数，以此创建对象实例。
4. 箭头函数中 this 的指向不同。在普通函数中，this 总是指向调用它的对象，如果用作构造函数，this 指向创建的对象实例。箭头函数本身没有 this，但是它在声明时可以捕获其所在作用域的 this 供自己使用。call()、bind()、apply() 均不能改变其指向
5. 箭头函数不绑定 arguments，取而代之用 rest 参数 ... 解决
6. 其他区别：
箭头函数不能 Generator 函数，不能使用 yeild 关键字。
箭头函数不具有 prototype 原型对象。
箭头函数不具有 super。
箭头函数不具有 new.target。

### 对fetch的理解
fetch() 方法是比 XMLHttpRequest 更简洁的 Ajax 请求。fetch 是全局量 window 的一个方法，第一个参数为 URL。
```JavaScript
// url (必须), options (可选)
fetch('/some/url', {
    method: 'get'
}).then(function(response) {

}).catch(function(err) {
    // 出错了;等价于 then 的第二个参数,但这样更好用更直观 :(
});
```
https://blog.csdn.net/qq_36754767/article/details/89645041

### 什么是闭包
* 可以访问其他函数内变量的函数，叫做闭包。
* 闭包可以理解为作用域嵌套。作用域里面的函数要访问作用域里面的变量，作用域不能销毁，作用域里面的函数在调用时会产生新的作用域，嵌套在当前作用域里面；
* 函数运行时创建作用域，函数结束时作用域不一定销毁；函数不产生闭包会在结束时销毁；如果还有代码使用作用域里面的变量值，产生了闭包，作用域不会销毁，里面的变量值还是可以被调用它的函数使用；
* 函数本身处在哪个作用域（A），它运行时创建的作用域（B）就在哪个作用域（A）内部；函数本身也是处于一个作用域的。是创建它的函数运行时所创建的作用域。

### []\==[]的结果和[]==![]的结果？
[]\==[] 的结果是 false，因为每次使用 [] 都是新建一个数组对象，比较的时候比较的是它们的引用，尽管两两边看起来都是空数组但实际上从引用看是不相等的，[]==![] 的结果也是 false。如果想判断数组为空，可以判断 array.length === 0。

\[]==![] 的结果是 true
1. ! 运算符优先级比 == 高，所以先运算 ![]，得到 false.
2. false 在运算中会强制转换为 0.
3. [] 强制转换为原始类型为 ""。
4. "" 会强制转换为 0。
5. 两侧都是 number 类型为 0，所以 0==0 为 true。

### 路由原理 history 和 hash 两种路由方式的特点
#### hash 模式
1. location.hash 的值实际就是 URL 中#后面的东西 它的特点在于：hash 虽然出现 URL 中，但不会被包含在 HTTP 请求中，对后端完全没有影响，因此改变 hash 不会重新加载页面。
2. 可以为 hash 的改变添加监听事件
```js
window.addEventListener("hashchange", funcRef, false);
```
#### history 模式
利用了 HTML5 History Interface 中新增的 pushState() 和 replaceState() 方法。
这两个方法应用于浏览器的历史记录站，在当前已有的 back、forward、go 的基础之上，它们提供了对历史记录进行修改的功能。这两个方法有个共同的特点：当调用他们修改浏览器历史记录栈后，虽然当前 URL 改变了，但浏览器不会刷新页面，这就为单页应用前端路由“更新视图但不重新请求页面”提供了基础。

### 前端设计模式
1. 单例模式
2. 工厂模式
3. 策略模式
4. 代理模式
5. 观察者模式
6. 模块模式
7. 构造函数模式
8. 混合模式
https://www.jianshu.com/p/4f3014fb8b8b

### 对前端的异步编程的了解有哪些

## 计算机网络问题

### http 和 https
http：超文本传输协议。是一个客服端和服务器端请求和应答的标准（tcp），使浏览器更加高效，使网络传输减少
https：是以安全为目标的 HTTP 通道，简单讲是 HTTP 的安全版本，通过 SSL 加密

### http1.0 和 http2.0
HTTP1.x 的解析是基于文本。HTTP2.0 的协议解析采用二进制格式
HTTP2.0 比HTTP1.0 有多路复用，一个连接可以并发处理多个请求
header 压缩：HTTP1.x 的 header 带有大量信息，而且每次都要重复发送，HTTP2.0 使用 encoder 来减少需要传输的 header 大小
服务器推送：我们对支持 HTTP2.0 的 web server 请求数据的时候，服务器会顺便把一些客户端需要的资源一起推送到客户端，免得客户端再次创建连接发送请求到服务器端获取。这种方式非常合适加载静态资源
多路复用：只通过一个 TCP 连接就可以传输所有的请求数据。解决了浏览器限制同一个域名下的请求数量的问题，同时也接更容易实现全速传输

### Cookie、SessionStronge、LocalStronge 的区别
#### 相同
HTTP 协议是一种无状态协议，即每次服务端接收到客户端的请求时，都是一个全新的请求，服务器并不知道客户端的历史请求记录；Session 和 Cookie 的主要目的就是为了弥补 HTTP 的无状态特性。
#### 在同一浏览器下有效期不同
Cookie:         默认是关闭浏览器后失效， 但是也可以设置过期时间
SessionStorage: 仅在当前会话(窗口)下有效，关闭窗口或浏览器后被清除， 不能设置过期时间
LocalStorage:   除非被清除，否则永久保存
#### 容量不同
Cookie 容量限制：大小(4KB左右)和个数(20~50)
SessionStorage 和 LocalStorage 容量限制：大小(5M左右)
#### 网络请求不同
Cookie 网络请求：每次都会携带在 HTTP 请求头中，如果使用 cookie 保存过多数据会带来性能问题
SessionStorage 和 LocalStorage 网络请求：仅在浏览器中保存，不参与和服务器的通信
#### 应用场景不同
Cookie:         判断用户是否登录
sessionStorage: 表单数据
LocalStorage:   购物车
#### 相关方法
Express 中使用 res.cookie() 一个验证身份的字符串，网站在用户验证成功之后都会设置一个 cookie，只要 cookie 没有过期，用户就可以自由浏览这个网站的任意页面不需要再次登录
localStorage.setItem(item，value)
localStorage.getItem(item)
localStorage.removeItem(item)
sessionStorage 和 localStorage 用法一样，但是它只保存数据到浏览器关闭，不会触发 onstorage 事件

#### 强缓存和协商缓存
强缓存：服务器通知浏览器一个缓存时间，在缓存时间内的请求会直接实用缓存，不在执行比较缓存策略
协商缓存：让客户端和服务器之间实现缓存文件是否更新的验证、提升缓存的复用率，将缓存信息种的 Etag 和 Last-Modified 通过请求发送给服务器，由服务器校验，返回 304 时直接使用缓存

### 进程和线程
进程是资源分配的最小单位，线程是 CPU 调度的最小单位。一个进程里面可以有多个线程，线程是共享了进程的上下文环境，的更为细小的 CPU 时间段。CPU 运行一个软件相当于打开一个了进程，执行该软件里面的 1 个功能相当于打开一个线程

### https加密原理
1. HTTPS 对称加密
服务器每次发送真实数据前，会先生成一把密钥传输（以明文方式传输密钥容易被劫持）给客户端，服务器给客户端发送的真实数据会先用这把密钥进行加密，客户端收到加密数据后再用密钥进行解密（客户端给服务器发送数据同理）

2. HTTPS 非对称加密
客户端和服务器都有两把密钥，一把公钥一把私钥（公钥加密的数据只有私钥才能解密，私钥加密的数据只有公钥才能解密），服务器在给客户端发送真实数据前，先用客户端明文传输给服务器的公钥进行加密，客户端收到后用自己的私钥进行解密，反之同理

3. HTTPS 对称加密 + 非对称加密
鉴于 HTTPS 非对称加密在加密时速度特别慢，可使用 HTTPS 对称加密 + 非对称加密（以非对称加密的方式传输对称加密密钥），接着就可使用对称加密的密钥传输数据。非对称加密之所以不安全是因为客户端不知道接收的公钥是否属于服务器

4. HTTPS 数字证书
核心在于证明客户端接收的公钥是属于服务器的，解决这个问题方法是使用数字证书（即找到一个大家都认可的认证中心 CA）
服务器在给客户端传输公钥的过程中，会将公钥+服务器个人信息通过 hash 算法生成信息摘要，为防止信息摘要被掉包服务器会用 CA 提供的私钥对信息摘要加密形成数字签名。最后还会将没有进行 hash 算法计算的服务器个人信息+公钥和数字签名合并在一起形成数字证书。
客户端拿到数字证书后，用 CA 提供的公钥对数字签名进行解密得到信息摘要，然后对数字证书中服务器个人信息+公钥进行hash 得到另一份信息摘要，两份信息摘要进行比对，若一样则是目标服务器，否则不是。
服务器会申请证书，客户端会内置证书。

### 安全管理
* XSS 注入：往 web 页面插入恶意的 html 标签或者 js 代码。对用户输入的内容，需要转码（大部分时候要服务端来处理，偶尔也需要前端处理），禁止使用 eval 函数，尽量采用 post 而不使用 get 提交表单；
* https：这个显然是必须的，好处非常多；
* CSRF：通过伪装来自受信任用户的请求。要求服务端加入 CSRF 的处理方法（至少在关键页面加入），添加校验 token 等；

### 304 是什么意思 一般什么场景出现，命中强缓存返回什么状态码
304 状态码或许不应该认为是一种错误，而是对客户端有缓存情况下服务端的一种响应。
客户端在请求一个文件的时候，发现自己缓存的文件有 Last Modified ，那么在请求中会包含 If Modified Since ，这个时间就是缓存文件的 Last Modified 。因此，如果请求中包含 If Modified Since，就说明已经有缓存在客户端。服务端只要判断这个时间和当前请求的文件的修改时间就可以确定是返回 304 还是 200 。
强缓存命中返回 200（200 from cache）

## 数据结构与算法问题

### 栈(stack)和堆(heap)的区别
1. 空间分配：栈由操作系统自动分配释放；堆需要由程序员释放或程序结束时由 OS 回收
2. 结构区别：堆类似于一棵树，如堆排序；栈是一种先进后出的数据结构，类似于往箱子里放书取书，最先放进去的书在最底，拿出来时最后拿
3. 缓存方式：堆使用二级缓存，生命周期由虚拟机的垃圾回收算法决定；栈使用的是一级缓存，调用时处于存储空间中，调用完毕立刻释放

### 递归求斐波那契数列
```JavaScript
function fibonacci(n){
    if(n < 1) return 0;
    if(n <= 2) return 1;
    return fibonacci(n - 1) + fibonacci(n - 2)
}
```

### 递归方式求1到100的和
```JavaScript
function add(n， m){
    var x = n + m;
    if(m + 1 > 100){
        return n
    }else{
        return add(n， m + 1)
    }
}
var sum = add(1， 2)
```

### 数组有哪些方法
对象继承方法：数组是一种特殊的对象，继承了 Object 的这三个方法
toString()       返回由数组中每个值的字符串形式拼接而成的一个以逗号分隔的字符串
toLocaleString() 是 toString() 方法的本地化版本，经常返回与 toString() 方法相同的值，但也不总如此
valueOf()        返回数组对象本身

转换方法：
concat()	    连接两个或更多的数组，并返回结果。
copyWithin()	从数组的指定位置拷贝元素到数组的另一个指定位置中。
entries()	    返回数组的可迭代对象。
every()	        检测数值元素的每个元素是否都符合条件。
fill()	        使用一个固定值来填充数组。
filter()	    检测数值元素，并返回符合条件所有元素的数组。
find()	        返回符合传入测试（函数）条件的数组元素。
findIndex()	    返回符合传入测试（函数）条件的数组元素索引。
forEach()	    数组每个元素都执行一次回调函数。
from()	        通过给定的对象中创建一个数组。
includes()	    判断一个数组是否包含一个指定的值。
indexOf()	    搜索数组中的元素，并返回它所在的位置。
isArray()	    判断对象是否为数组。
join()	        把数组的所有元素放入一个字符串。
keys()	        返回数组的可迭代对象，包含原始数组的键(key)。
lastIndexOf()	搜索数组中的元素，并返回它最后出现的位置。
map()	        通过指定函数处理数组的每个元素，并返回处理后的数组。
pop()	        删除数组的最后一个元素并返回删除的元素。
push()	        向数组的末尾添加一个或更多元素，并返回新的长度。
reduce()	    将数组元素计算为一个值（从左到右）。
reduceRight()	将数组元素计算为一个值（从右到左）。
reverse()	    反转数组的元素顺序。
shift()	        删除并返回数组的第一个元素。
slice()	        选取数组的一部分，并返回一个新数组。
some()	        检测数组元素中是否有元素符合指定条件。
sort()	        对数组的元素进行排序。
splice()	    从数组中添加或删除元素。
toString()	    把数组转换为字符串，并返回结果。
unshift()	    向数组的开头添加一个或更多元素，并返回新的长度。
valueOf()	    返回数组对象的原始值。

### 遍历栈和树的时间复杂度
树的四种遍历方式时间复杂度和空间复杂度都为O(N)
栈遍历的时间复杂度是O(N)

### JS怎么遍历字符串
可以用 for 循环配合 charAt 函数遍历字符串。循环从 0 开始，循环次数为 str.length ，在for循环中添加 str.charAt(i) ，charAt 中的值为循环中的次数，然后将结果输出，这样字符串就被遍历出来了

## 性能优化问题

### 让加载更快
减少资源体积：压缩代码
减少访问次数：合并代码、SSR服务器端渲染，缓存
使用更快的网络：CDN

### 让渲染更快
CSS 放在 head，JS 放在 body 最下面
尽早开始执行 JS，用 DOMContentLoaded 触发
懒加载（图片懒加载、下滑加载更多、分页器）
对 DOM 查询进行缓存
将频繁的 DOM 操作，合并到一起插入到 DOM 结构
节流、防抖等常用性能优化方法
script 标签加上 defer属性 和 async属性 用于在不阻塞页面文档解析的前提下，控制脚本的下载和执行。
defer属性： 用于开启新的线程下载脚本文件，并使脚本在文档解析完成后执行。
async属性： HTML5新增属性，用于异步下载脚本文件，下载完毕立即解释执行代码。

### Webpack
loader 将除 js 以外的其它资源也当成 require 的资源，如图片，CSS， json， svg，字体，通过把这些非 js 资源转化为等价的 js 文件来实现
plugin 在 webpack 则是对整体的打包结果进行处理的一种插件机制（如混淆和压缩代码、编译时配置全局变量、自动加载模块、单独抽离样式等）
babel-loader 将 ES6 转化为 ES5
file-loader 将文件输出到一个文件夹中，在代码中通过相对URL去引用
url-loader 与 file-loader 类似，但是能在文件很小的情况下以 base64 的方式把文件内容注入到代码中

### 有哪些常见的 loader 和 plugin
Loader:
* babel-loader：把 ES6 转换成 ES5
* css-loader：加载 CSS，支持模块化、压缩、文件导入等特性
* style-loader：把 CSS 代码注入到 JavaScript 中，通过 DOM 操作去加载 CSS。
Plugin:
* define-plugin：定义环境变量
* commons-chunk-plugin：提取公共代码
* uglifyjs-webpack-plugin：通过UglifyES压缩ES6代码

### 如何实现按需加载
见CSDN收藏夹

### 浏览器工作流程
构建DOM -> 构建CSSOM -> 构建渲染树 -> 布局 -> 绘制。
CSSOM会阻塞渲染，只有当CSSOM构建完毕后才会进入下一个阶段构建渲染树。
通常情况下DOM和CSSOM是并行构建的，但是当浏览器遇到一个不带defer或async属性的script标签时，DOM构建将暂停，如果此时又恰巧浏览器尚未完成CSSOM的下载和构建，由于JavaScript可以修改CSSOM，所以需要等CSSOM构建完毕后再执行JS，最后才重新DOM构建。

### 从输入url地址栏到所有内容显示到界面上做了哪些事？
1. 浏览器向 DNS 服务器请求解析该 URL 中的域名所对应的 IP 地址;
2. 建立 TCP 连接（三次握手）;
3. 浏览器发出读取文件(URL 中域名后面部分对应的文件)的 HTTP 请求，该请求报文作为 TCP 三次握手的第三个报文的数据发送给服务器;
4. 服务器对浏览器请求作出响应，并把对应的 html 文本发送给浏览器;
5. 浏览器将该 html 文本并显示内容;
6. 释放 TCP 连接（四次挥手）;

## Vue

### Vuex作用
Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式。它采用集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化。可以将共享的数据保存到 Vuex 中，方便整个程序中的任何组件都可以获取和修改 Vuex 中保存的公共数据

每个 Vuex 应用的核心是 store，store 基本上是一个容器，包含着应用中的大部分状态。Vuex 的状态存储是响应式的，当 Vue 组件从 store 中读取状态的时候，若 store 中的状态发生变化，那么响应的组件也会得到更新

改变 store 中状态的唯一途径是提交 mutation。这样可以方便的跟踪每个状态的变化
* State：定义了应用状态的数据结构，可以在这里设置默认的初始状态。
* Getter：允许组件从 Store 中获取数据。mapGetters 辅助函数仅仅是将 store 中的 getter 映射到局部计算属性。
* Mutation： 唯一更改 store 中状态的方法，且必须是同步函数。
* Action：用于提交 Mutation，而不是直接更改状态，可以包含任意异步操作。
* Module：允许将单一的 Store 拆分为多个 store 且同时保存在单一的状态树中

### 聊聊双向绑定
Vue.js 是采用数据劫持结合发布者-订阅者模式的方式，核心是通过 ES5（所以vue不支持 IE8 及以下） 的 Object.defineProperty() 来劫持各个属性的 setter、getter，在数据变动时发布消息给订阅者，触发相应的监听回调。

实现数据监听器 Observer，能够对数据对象的所有属性进行监听，如有变动可拿到最新值并通知订阅者
实现一个指令解析器 Compile
实现一个 Watcher，作为 Observer 和 Compile 的桥梁，能够订阅并收到每个属性变动的通知，执行指令绑定的相应回调函数，从而更新视图
Mvvm 入口函数，整合以上三者
```JavaScript
<input v-model="userName" />
<input v-bind:value="userName" v-on:input="userName = $event.target.value" />
```
第一行的代码其实只是第二行的语法糖。input 元素本身有个 oninput 属性，这是 HTML5 新增的，类似 onchange，每当输入框的内容发生变化，就会触发 oninput

### Vue生命周期
beforeCreate 阶段：vue 实例的挂载元素 el 和数据对象 data 都是 undefined，还没有初始化。
create d阶段：vue 实例的数据对象 data 有了，可以访问里面的数据和方法，未挂载到 DOM，el 还没有
beforeMount 阶段：vue 实例的 el 和 data 都初始化了，但是挂载之前为虚拟的dom节点
mounted 阶段：vue 实例挂载到真实 DOM 上，就可以通过 DOM 获取 DOM 节点
beforeUpdate 阶段：响应式数据更新时调用，发生在虚拟 DOM 打补丁之前，适合在更新之前访问现有的 DOM，比如手动移除已添加的事件监听器
updated 阶段：虚拟 DOM 重新渲染和打补丁之后调用，组成新的 DOM 已经更新，避免在这个钩子函数中操作数据，防止死循环
beforeDestroy 阶段：实例销毁前调用，实例还可以用，this 能获取到实例，常用于销毁定时器，解绑事件
destroyed 阶段：实例销毁后调用，调用后所有事件监听器会被移除，所有的子实例都会被销毁

### keep alive做了什么，对生命周期有什么影响
keep-alive 是 vue 内置的一个组件，可以被包含的组件保留状态，或避免重新渲染。

activated 和 deactivated
keep-alive 的生命周期
1. activated： 页面第一次进入的时候，钩子触发的顺序是 created->mounted->activated
2. deactivated: 页面退出的时候会触发 deactivated，当再次前进或者后退的时候只触发 activated

### 父子组件怎么传值
1. 父向子传值 props
2. 子组件向父组件传值 $emit
3. 父组件调用子组件的方法通过 ref，在 DOM 元素上使用 $refs 可以迅速进行 dom 定位，类似于 \\$("selectId")，使用 this.$refs.paramsName 能更快的获取操作子组件属性值或函数
4. 可以通过 $parent 和 $children 获取父子组件的参数，我们可以使用 \\$children[i].paramsName 来获取某个子组件的属性值或函数，\\$children 返回的是一个子组件数组
5. vue 全局事件 (eventBus)，在 main.js 里：window.eventBus = new Vue(); // 注册全局事件对象
6. 兄弟之间的传值Vuex，在 state 里定义数据和属性，在 mutations 里定义函数 fn，在页面通过 this.$store.commit('fn'，params) 来触发函数

### 为什么不建议用index作为key的值
当对数组进行下标有关的操作时，比如删除一个值，后面的值的index都会发生变化，那么key值自然也跟着全部发生改变。
在平时的开发过程中, 因为我们的数据绝大部分都是从后台获取来的. 数据库中每一条数据都会一个 id 作为唯一标识，而这个 id 也是我们最常使用作为 key 值的来源。

### 说说nextTick的用处？
Vue 采用的是异步更新的策略，通俗点说就是，同一事件循环内多次修改变量，会统一进行一次视图更新。所以数据一更新，视图却还没更新，所以拿到的还是上一次的旧视图数据，那么想要拿到最新视图数据怎么办呢？$nextTick 是在下一次 dom 更新循环结束之后执行延迟回调，在修改数据之后使用这个方法，立即更新 dom。

## React

### Redux 介绍和如何使用
redux 是为了解决 react 中组件与组件之间数据传递的问题。是一个全局的数据中心，监听 state 变更并将数据传递给下层组件
组建于组件之间的传递有三种情况：
1. 父组件传递数据给子组件：由于 redux 是一个单向数据流的框架，所以它的 props 就只能由父组件传递给子组件；
2. 子组件传递给父组件：而子组件想父组件的传值的话则需要使用回调函数，
3. 子组件与子组件：那么子组件与子组件之间的传递则相当麻烦，需要先将子组件的值传递给父组件，然后再由父组件在分发给指定的子组件，而 redux 则是解决这种问题的。
使用情况：非父子组件之间需要共享一些状态。需要将状态提升到最近的祖先

用法
引入
```HTML
<script src="https://unpkg.com/redux@4.0.4/dist/redux.js">
```
创造一个 store
```JavaScript
var store = Redux.createStore((state， action)=>{
    //do something
}，state)
```
第一个参数是一个 reducer 函数，函数有 2 个参数，state 表示储存的数据，action 是一个对象，子组件里面通过 dispatch 函数来传递这个对象，这个 reducer 函数通过 action 的信息来触发对 state 的相关操作，返回一个新的 state
创建的 store 上面有两个常用的方法，dispatch 和 subscribe 方法
dispatch， 传递给下层组件，下层组件利用这个方法操作 state 触发更新
subscribe， 用来监听 state 变更
var unSubscribe = store.subscribe(fn)
数据变更时 fn 会运行，这个 fn 不接参数，并返回一个函数 unSubscribe
调用 unSubscribe 就会把这次的监听函数 subscribe 解绑

### React 如何实现数据绑定
在 React 应用中，当某个组件的状态发生变化时，它会以该组件为根，重新渲染整个组件子树。可以通过 shouldComponentUpdate 这个生命周期进行控制 pureRender
通过 JSX 中标签加属性实现视图和数据的绑定，类组件中 render 里的大括号动态传递 state，this.state 记录数据状态，函数组件中则使用 hooks 管理状态（个人理解，不知道对不对）
Vue 实现数据绑定考的是数据劫持（Object.defineProperty()） + 发布-订阅模式。在 Vue 应用中，组件的依赖是在渲染过程中自动追踪的，所以系统能精确知晓哪个组件需要被被重新渲染。可以理解为每一个组件都已经自动获得了 shouldComponentUpdate，并且没有上面的子树问题限制

### React如何在重新加载页面时保留数据？
使用浏览器 localstorage 来保存应用程序的状态。我们将整个存储数据保存在 localstorage 中，每当有页面刷新或重新加载时，我们从 localstorage 加载状态。

### state 和 props 的区别
state 是组件自己管理数据，控制自己的状态，可变，必须通过 setState 更改。
props 是外部传入的数据参数，不可变，父组件通过传递 props 给子组件来更新视图，子组件不能将 prop 送回父组件。这有助于维护单向数据流，通常用于呈现动态生成的数据。

### 简述虚拟DOM和diff算法
无 key 时，如果两棵树的根元素类型不同，React 会销毁旧树，创建新树。对于类型相同的 React DOM 元素，只更新不同的属性，如果类型不同，直接替换。当处理完这个 DOM 节点，React 就会递归处理子节点。比较内容，如果有不同直接替换。
有 key 时，如果 key 相同，组件有所变化，React 会只更新组件对应变化的属性；如果 key 不同，组件会销毁之前的组件，将整个组件重新渲染。
使用 React 要注意的一点是，Key 值必须是稳定的, 可预测并且是唯一的，这里给我们性能优化提供了两个非常重要的依据：
  * 保持 DOM 结构的稳定性
  * 加唯一 key 值
虚拟 DOM 是 JS 和真实 DOM 之间的一个缓存，可以看作是一个使用 javascript 模拟了 DOM 结构的树形结构，这个树结构包含整个DOM结构的信息。利用 diff 算法比较虚拟 DOM 和真实 DOM 的不同后根据 diff 算法的替换规则更改真实 DOM，因为操作 DOM 非常耗费性能，所以虚拟 DOM 和 diff 算法是提高性能的一个重要方法。

### 函数组件和类组件
函数组件是一个纯函数，接收参数并返回 React 元素，并且没有任何副作用。没有生命周期函数和 state。
通过 class xx extends React.Component 这类组件可以通过 setState() 来改变组件的状态，并且可以使用生命周期函数

定义组件时，复杂场景用类组件，简单场景用函数组件。
简单：一个组件仅仅是为了展示数据。
复杂：一个组件中有一定业务逻辑，需要操作数据，并且此时需要使用 state。

### 受控组件和非受控组件
在 HTML 当中，像 input，textarea 和 select 这类表单元素会维持自身状态，并根据用户输入进行更新。 在 React 中，可变的状态通常保存在组件的 state 中，并且只能用 setState() 方法进行更新. React 根据初始状态渲染表单组件，接受用户后续输入，改变表单组件内部的状态。因此，将那些值由 React 控制的表单元素称为受控组件。

受控组件的特点：
1. 表单元素
2. 由 React 通过 JSX 渲染出来
3. 由 React 控制值的改变，想要改变元素的值，只能通过 React 提供的方法来修改

非受控组件的状态是不受 React 控制的，而是组件本身具有的

非受控 -> 受控组件的转化
首先把状态绑定到非受控组件的 value、checked 上。
然后监听该组件的 onChange 事件 用 e.target 获取 input 上面的数据 然后通过 setState 设置数据给 state 内的数据。

### Hooks及常用API
1. 基础API
    useState：通过在函数组件里调用它来给组件添加一些内部 state。React 会在重复渲染时保留这
    state。useState 会返回一对值：当前状态和一个让你更新它的函数，你可以在事件处理函数中或其他一些地方调用这个函数。它类似 class 组件的 this.setState，但是它不会把新的 state 和旧的 state 进行合并。
    useEffect：在函数组件中执行副作用操作（副作用：和函数业务主逻辑关联不大，特定时间或事件中执行的动作，比如Ajax 请求后端数据，添加登录监听或取消登录、手动修改DOM等），useEffect 在每次 state 更新时执行，主要用来代替常用的生命周期函数。
    useContext：与 Context 一样，是 React Hooks 中提供的更加高级的一种组件中传递值的方式，不再需要一层一层的向下传递 props，而是可以隔层传递。
2. 其他的API
    useReducer
    useCallback
    useMemo
    useRef
    useImperativeMethods
    useLayoutEffect

### useState、useEffect、useContext怎么用
1. useState 函数（状态钩子），接收的参数会设置为 state 的初始值，返回一个数组 [state, 操作 state 的函数 setState]
2. useEffect 函数（生命周期钩子），相当于一个生命周期函数 componentDidMount 或 componentDidUpdate，直接在函数组件内部使用，每次渲染时都会调用。
第一个参数是一个函数，可以挂载 componentDidMount 或 componentDidUpdate 阶段需要的操作。这个函数可以有一个返回值函数，返回值函数会在函数组件 componentWillUnmount 阶段运行，可有挂载一些解绑操作；对于函数组件来讲，每次更新都会卸载再挂载；所以每次更新都会运行这个返回值函数。第二个参数见下面
3. useContext 先在外部创建一个 context 实例 var ColorContext = React.createContext()，Context 实例对象上面有个 ColorContext.Provider 组件开始向下传递数据，用于组件内部，如 <ColorContext.Provider value={color}>
接收数据方法
在后代组件中直接使用 useContext(Context 实例对象）接收数据。var color = useContext(ColorContext) 接收数据

#### 注意：
避免在 循环/条件判断/嵌套函数 中调用 hooks，保证调用顺序的稳定；
不能在 useEffect 中使用 useState，React 会报错提示；
类组件不会被替换或废弃，不需要强制改造类组件，两种方式能并存


### useEffect无限调用、第二个参数是什么
当你在 useEffect 中监听对象或数组的时候，它会无条件无限执行.你可以理解为引用数据类型数据在监听时每次都生成了一个新的数据.所以必定会执行。要监听的对象修改后的值不同于修改前的就会执行，但是每次执行时监听对象都会变化，将会无限次执行。

解决办法
1. 同步更新一个可检测的数据，然后监听这个数据
2. 假如知道数据的走向，并且可以准确找到临界点，可以通过判断来打断无限更新的流程
3. 对象监听，通过监听对象属性来判断对象变化，不符合监听规则就不无限执行

第二个可选参数是一个数组，是要监听的数据，当组件刷新时如果发现数组的内容和上一次一样，那么就不会运行这个 useEffect 函数，用于性能优化；要确保数组中包含了外部作用域中会随时间变化并且在 effect 中使用的变量，否则你的代码会引用到先前渲染中的旧变量，如果是空数组表示每次都是完全一样的内容，不运行

### useEffect的作用，为什么在组件内部调用useEffect
1. 通过调用 useEffect，你可以告诉 React 组件需要在渲染后执行某些操作。React 会保存你传递的函数（我们将它称之为 “effect”），并且在执行 DOM 更新之后调用它。在这个 effect 中，我们设置了 document 的 title 属性，不过我们也可以执行数据获取或调用其他命令式的 API。
2. 与 componentDidMount 或 componentDidUpdate 不同，使用 useEffect 调度的 effect 不会阻塞浏览器更新屏幕，这让你的应用看起来响应更快。大多数情况下，effect 不需要同步地执行。

### useEffect什么时候会执行
在默认情况下、useEffect 在第一次渲染之后和每次更新之后都会执行。你可能会更容易接受 effect 发生在“渲染之后”这种概念，不用再去考虑“挂载”还是“更新”。React 保证了每次运行 effect 的同时，DOM 都已经更新完毕。

### useState
在使用 useState 时，修改值时传入同样的值，组件不会重新渲染。
只会在当前组件的第一次渲染执行 useState 函数。
setUseState 时获取上一轮的值：我们在使用 useState 的第二个参数时，我们想要获取上一轮该 state 的值的话，只需要在 useState 返回的第二个参数，也就是我们上面的例子中的 setCount 使用时，传入一个参数，该函数的参数就是上一轮的 state 的值。

### Hooks相对普通Class有什么优势
简化代码：声明一个简单的组件只要简单的几行代码；
容易上手：对于初学者来说，相对复杂的 class 的声明周期，hooks 的钩子函数更好理解；
简化业务：充分利用组件化的思想把业务拆分成多个组件，便于维护；
方便数据管理：相当于三种的提升，各个组件不用通过非常复杂的 props 多层传输，解耦操作；
便于重构：业务改变或者接手别人的代码，代码都是比较容易读懂；

### 什么情况下使用Class，什么情况下使用Hooks

### React 怎么获取到组件的 DOM
获取 DOM 是 ReactDOM.findDOMNode(this.refs.box_table)；
而 this.refs.box_table 直接取到的是组件，可以直接调用其内部的方法。

### React的生命周期方法有哪些
componentWillMount:在渲染之前执行，用于根组件中的 App 级配置。
componentDidMount：在第一次渲染之后执行，可以在这里做 AJAX 请求，DOM 的操作或状态更新以及设置事件监听器。
componentWillReceiveProps：在初始化 render 的时候不会执行，它会在组件接受到新的 Props 时被触发，一般用于组件状态更新时子组件的重新渲染
shouldComponentUpdate：确定是否更新组件。默认情况下，它返回 true。如果确定在 state 或 props 更新后组件在重新渲染，则可以返回false，这是一个提高性能的方法。
componentWillUpdate：在 shouldComponentUpdate 返回 true 确定要更新组件之前件之前执行。
componentDidUpdate：它主要用于更新 DOM 以响应 props 或 state 更改。
componentWillUnmount：它用于取消任何的网络请求，或删除与组件关联的所有事件监听器

### JXS是什么，有什么优势
JSX 是 JavaScript 的语法扩展
增强 js 语义、结构清晰、抽象程度高（诞生了跨平台 React Native）、代码模块化

### setState有哪些使用方式
1. 传入新的 state 对象
```JavaScript
this.setState({
  age: 2，
});
```
2. 传入回调函数，并在回调函数里面返回新的 state 对象
```JavaScript
this.setState((prevState， props) => {
  return {
    age: prevState.age + props.age，
  };

```

### 可以在Class组件里写Hook吗

### React组件间的通信
父组件向子组件通信：props
子组件向父组件通信：回调函数
跨级组件通信：context、useContext、redux
没有嵌套关系的组件通信：eventEmitter，利用全局对象来保存事件，用广播的方式去处理事件。

### 原生事件和React事件的区别
* React 事件使用驼峰命名，而不是全部小写。
* 通过 JSX , 你传递一个函数作为事件处理程序，而不是一个字符串。
* 在 React 中你不能通过返回 false 来阻止默认行为。必须明确调用 preventDefault。

### 什么是HOC，有什么好处和应用场景
高阶组件和高阶函数相同。我们实现一个函数，传入一个组件，然后在函数内部再实现一个函数去扩展传入的组件，最后返回一个新的组件，这就是高阶组件的概念，作用就是为了更好的复用代码。
常用场景：权限控制、组件性能渲染追踪、页面复用

### useInterval和useDebounce
useDebounce 钩子可让你消除任何快速变化的值。当在指定的时间段内未调用 useDebounce 钩子时，去抖动的值将仅反映最新的值。 你可以轻松地确保诸如 API 调用之类的昂贵操作不会过于频繁地执行。
```JavaScript
function useDebounce(value, delay) {
    const [debouncedValue, setDebouncedValue] = useState(value);

    useEffect(() => {
    const handler = setTimeout(() => {
        setDebouncedValue(value);
    }, delay);

    return () => {
        clearTimeout(handler);
    };
    }, [value, delay]);

    return debouncedValue;
}
```
useInterval 设置了一个计时器，并且在组件 unmount 的时候清理掉了。 这是通过组件生命周期上绑定 setInterval 与 clearInterval 的组合完成的。
```JavaScript
import React, { useState, useEffect, useRef } from 'react';
​
function useInterval(callback, delay) {
  const savedCallback = useRef();
​
  // Remember the latest callback.
  useEffect(() => {
    savedCallback.current = callback;
  });
​
  // Set up the interval.
  useEffect(() => {
    function tick() {
      savedCallback.current();
    }
    if (delay !== null) {
      let id = setInterval(tick, delay);
      return () => clearInterval(id);
    }
  }, [delay]);
}
```

## 其他
### 你遇到最难的问题是怎样的？
### 你在团队的突出贡献是什么？
### 最近在关注什么新技术
### lodash有什么印象深刻的
chunk，将数组进行切分
compact，去除假值（将所有的空值，0，NaN过滤掉）
uniq，数组去重。（将数组中的对象去重，只能去重数组不能去重对象）
merge，参数合并