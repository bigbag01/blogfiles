title: Javascript零散笔记(1)——基本概念

date: 2017-10-30 22:51:22

categories: 前端

tags: [strict,typeof,数据类型]

description: 写过一些前端页面，对前端知识有浅显的了解，开始学习js的更多知识。这个系列是以读《JavaScript高级程序设计》为主，查看其他相关资料的笔记。

---

### 插入javascript脚本

* 建议用`<script src="some URL"></script>`引用外部js脚本而非将js代码嵌入html文件中，**原因**主要有可维护性好，且可缓存。
* 所有script标签在没有defer和async属性时，按照它们在页面中出现的顺序依次被解析。
* 由于浏览器会先解析script标签引用的代码，然后再解析之后的内容，因此，一般应该把script标签放最后，`</body>`之前。
* 使用**defer**属性可以让脚本再document加载完成之后再执行
* 使用**async**属性可以表示当前脚本不必等待其他脚本，也不阻塞文档加载。使用了**async**属性的脚本执行顺序无法保证


### strict模式

- 在strict模式下运行的js代码，强制通过var申明变量，未使用var申明变量就使用的，将导致运行错误

- 不启用strict模式时，不强制要求用var申明变量。未申明直接使用的变量会被默认当作全局变量。

- **启用方式**：在js代码第一行写上 

  ` 'use strict'` 

  这是一个字符串，引号不省略。在不支持strict模式的浏览器中，会将它当作一个字符串语句执行。

- *为了避免不同作用域同名变量互相影响，在写js代码时应尽可能全部使用* **strict** *模式* 


### typeof操作符

​	typeof是操作符不是函数，得到的结果为字符串，可能的值有6种

* “undefined"——这个值未定义
* ”boolean“——布尔值
* ”string“——字符串
* ”number“——数值
* ”object“——值为对象或者null
* ”function“——值为函数


### js数据类型

#### Undefined

​	Undefined类型只有一个值 undefined。未经初始化的已声明的变量的值默认为undefined。

#### Null

​	Null类型也只有一个值 null。null表示一个空对象指针，因此 `typeof null`返回‘object’

​	如果定义的变量未来**用于保存对象**，那么最好初始化为null

#### Boolean

​	字面值只有 true和false，但任何数据类型都可以通过调用Boolean()函数来转换成Boolean值。

#### Number

* 除了十进制外，八进制和十六进制也可直接表示。八进制第一位为0，十六进制前两位为0x。*注意：八进制字面量在strict模式下无效*
* ECMAScript能表示的最小数值存在Number.MIN_VALUE中，最大数值在Number.MAX_VALUE中。如果超出范围，表示为(-)Infinity。
* **NaN**和任何值都不相等，可以用isNaN()函数来判断一个参数是否“不是数值”。但在基于对象调用时，会先调用对象的valueOf方法。因此 `isNaN('a')` 返回true `isNaN('11')`返回false
* Number(), parseInt(), parseFloat() 可以把非数值转换为数值

#### String

* ECMAScript中字符串**不可变**的。要改变某个变量保存的字符串，首先要销毁原来的字符串，然后再用另一个包含新值的字符串填充该变量。（类似java）
* 把一个值转换成字符串，一种方式调用somevalue.toString(base)方法，但是null和undefined没有这个方法，另一种是调用String(somevalue)。base为可选参数，表示输出数值的基数，可用于进制转换。

#### Object

​	ECMAScript中，Object类型是所有它的实例的基础，它所具有的任何属性和方法也同样存在于更具体的对象中。

### 操作符

​	js其他操作符和别的语言差不多，就不写了。而它的相等操作符比较特别

* 相等和不相等

  `==`和`!=`  先将对象转换成相似的类型再比较

* 全等和不全等

  `===` 和`!==` 比较之前不转换操作数

![](https://pic3.zhimg.com/50/b922270259dece707ef6c6a50259a406_hd.png)

| 红色   | 橙色   | 黄色              | 蓝色   | 绿色   |
| ---- | ---- | --------------- | ---- | ---- |
| ===  | ==   | <=和>=同时满足，==不满足 | >=   | <=   |



### 语句

#### switch

​	switch中的比较用的是全等操作符，不会发生类型转换

#### for-in和 for-of

* for-in

  用来枚举对象的**属性**，顺序不可预测，如果被迭代的对象为null或undefined，循环体不执行

  ```javascript
  var object={a:2,b:3};
  var array=[2,3];
  for(var o in object) 
    console.log(o);		//输出 a\nb
  for(var a in array)
    console.log(a);		//输出 0\n1
  ```

* for-of

  可用来循环数组的value，顺序是保证的。对于对象的值，可以配合着Object.keys()来使用，for-of是ES6的标准。

  ```javascript
  // 以下两段都遍历输出 2\n3
  for(var a of array) 
    console.log(a);
  for(var k of Object.keys(object))
    console.log(object[k]);
  ```


### 函数

* 在js函数体内部，可以通过arguments对象来访问参数数组。

  ```javascript
  // 这两种写法实际是等价的
  function sayHi(arg1,arg2){
   	alert('hello'+arg1+arg2);
  }
  function sayHi(){
      alert('hello'+arguments[0]+arguments[1]);
  }
  ```

  函数定义的时候可以不写参数，直接在函数体内部通过arguments来对参数做处理。

* ECMAScript中所有参数传递的都是值，不可能通过引用传递参数

* ECMAScript中**没有重载**，定义同名函数的结果就是后面的覆盖前面的