### 前端模块化

1. commonjs`同步` `用于nodejs`

   1. 定义模块
      根据CommonJS规范，一个单独的文件就是一个模块。每一个模块都是一个单独的作用域，也就是说，在该模块内部定义的变量，无法被其他模块读取，除非定义为global对象的属性

   2. 模块输出：
      模块只有一个出口，`module.exports`对象，我们需要把模块希望输出的内容放入该对象

   3. 加载模块：
      加载模块使用`require`方法，该方法读取一个文件并执行，返回文件内部的`module.exports`对象

   4. exports是module.exports的引用 所以当exports = xxx时将丢失引用，正常用法应该为exports.xxx = xxx

      

2. AMD`异步` `用于浏览器` `主要有require.js库支持`

   1. 定义模块 define(id?, dependencies?, factory);
      1. id：可选参数，用来定义模块的标识，如果没有提供该参数，脚本文件名（去掉拓展名）
      2. dependencies：是一个当前模块依赖的模块名称数组
      3. factory：工厂方法，模块初始化要执行的函数或对象。如果为函数，它应该只被执行一次。如果是对象，此对象应该为模块的输出值
   2. 引用模块 require([dependencies], function(){});
      1. 第一个参数是一个数组，表示所依赖的模块
      2. 第二个参数是一个回调函数，当前面指定的模块都加载成功后，它将被调用。加载的模块会以参数形式传入该函数，从而在回调函数内部就可以使用这些模块

3. CMD `异步` `用于浏览器` `主要有SeaJs库支持`

      ```js
   // 定义模块  myModule.js
   define(function(require, exports, module) {
     var $ = require('jquery.js')
     $('div').addClass('active');
   });
   // 加载模块
   seajs.use(['myModule.js'], function(my){
   });
   ```

4. es6模块化 `统一` `由webpack支持`

   1. 是将所有文件打包到同一文件中，可使用代码分割插件进行分割。互相依赖
   2. 是用webpack内建函数进行require和define 其原理与cmd amd差不多



### 闭包

>  **闭包是指有权限访问(引用)另一个函数作用域的变量的函数**



### 基础

1. Object.defineProperty属性配置
   1. writeable,value无法与get set一起使用
   2. enumerable 设置是否可遍历该属性 默认是false

2. 函数和变量声明会提升到代码最前面，**如果函数和变量同名 则函数优先**

3. 判断一个变量是否声明可以使用typeof 有保护机制，可以判断出未声明的变量

4. Object.prototype.toString.call(arr) === "[object Array]"判断一个变量的类型

5. apply call bind区别
   1. apply第二个参数接收一个参数数组作为函数参数
   2. call第2~n个参数都作为函数参数
   3. bind与call一样 不同的是 bind是返回一个绑定this后的对象 不是立即执行

6. 事件流

   1. 捕获阶段(从外到里) -> 冒泡阶段(从里到外)
   2. addEventListener第三个参数false则为冒泡，true为捕获，默认为冒泡事件
   3. `e.stopPropatation()`取消冒泡，`e.preventDefault()`阻止浏览器默认行为（如表单提交等）

7. 事件代理（委托）

   > 给最外层的节点绑定事件，然后根据event.target来获取到触发事件的目标，进行处理委托任务

8. 跨域

   1. jsonp
   2. `"Access-Control-Allow-Origin", "*"`服务端设置允许指定源访问





### TODO



1. 节流防抖
2. 模块化及webpack怎么实现的
3. for in for of 区别
4. rem实现原理
5. 原型相关

