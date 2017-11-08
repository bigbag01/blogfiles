title: JavaScript Array 对象

date: 2017-04-06 16:29:39

categories: 前端

tags: [js,数组]

---

## JavaScript Array 的创建

```javascript
var arr1=new Array();//返回空数组，arr1.length为0
var arr2=new Array(3);//参数为数组元素个数，创建完成时，arr2.length为3，元素为undefined
var arr3=new Array('a','b','c');//新数组被初始化为['a','b','c']
var arr4=['a','b','c'];//直接赋值初始化
```

<!--more-->

## Array 对象属性

**constructor** ：返回对创建此对象的数组函数的引用

**length** ：设置或者返回数组中元素个数

**prototype** ：用来向对象添加属性和方法。（大概可以理解为动态改写对象结构？？）

*注* ：**length**和**prototype**都非常常用！



## Array对象方法

### Part 1 拼接

#### concat()

​	连接多个数组并返回结果。新数组是函数的返回值，原数组不被改变。

```javascript
var arr1=[1,2];
var arr2=[3,4];
var arr3=[5,6,7]
console.log(arr1.concat(9,10));
console.log(arr1.concat(arr2));
console.log(arr1.concat(arr2,arr3));
//输出
//[1,2,9,10]
//[1,2,3,4]
//[1,2,3,4,5,6,7]
```

#### join()

​	join方法把数组中所有元素放入一个字符串，通过分隔符分隔，若不指定就是逗号。

```javascript
var arr1=[1,2,3];
console.log(arr1.join());
console.log(arr1.join(';'));
//输出
//1,2,3
//1;2;3
```

#### toString()

​	把数组转为string对象，元素之间用','分隔



### Part 2 增删改

#### push() pop()

​	push方法向数组末尾添加元素并返回新的长度；

​	pop方法删除并返回数组的最后一个元素；

```javascript
var arr1=[1,2];
console.log(arr1.push(3,5));
console.log(arr1);
console.log(arr1.pop());
console.log(arr1);
//输出
//4
//[1,2,3,5]
//5
//[1,2,3]
```

#### shift() unshift()

​	shift方法删除并返回数组的第一个元素；

​	unshift方法向数组的开头添加一个或更多元素，并返回新的长度

用法类似push, pop

#### splice()

​	用于插入、删除或替换数组元素。函数返回值为被删除的子数组。函数第一参数为开始index,第二个参数为被删除或替换的元素个数，后面的参数可选，如果有就是删除了指定元素后添加到原数组后面的元素。

```javascript
var arr=[1,2,3,4];
console.log(arr.splice(2));
console.log(arr);
console.log(arr.splice(2,1));
console.log(arr);
console.log(arr.splice(2,2,7,8));
console.log(arr);
console.log(arr.splice(2,2,7,8,9));
console.log(arr);
//输出
//[3,4]
//[1,2]
//[3]
//[1,2,4]
//[3,4]
//[1,2,7,8]
//[3,4]
//[1,2,7,8,9]
```

#### copyWith()

​	将指定范围元素复制到指定位置

​	`array.copyWith(target,start,end)`

​	target为指定目标索引位置，start为元素复制的起始位置，end为终止位置。前两个参数必需，end可选。



### Part 3 顺序调整

#### reverse()

​	反转数组的元素顺序 `arr.reverse()`

#### sort()

​	对数组元素进行排序 `arr.sort()`可以加一个参数规定排序顺序，这个参数必须是函数



### Part 4 遍历

#### every()

​	用指定函数检测数组中所有元素是否都符合条件，检测过程中任一元素不满足**就停止**检测,返回false,全部满足条件则返回true。

​	`array.every(function(currentValue,index,arr),thisValue)` 

​	currentValue表示当前元素的值，这个参数是必需的。

​	index表示当前元素索引，arr表示当前数组对象，这两个参数不是必需。

​	thisValue是调用的function中的‘this’关键字指明的对象，这个参数不必需，如果不指明，函数中this的value为undefined

#### some()

​	用指定函数检测数组中元素是否满足符合条件，检测过程中任一元素满足条件就停止检测，返回true，没有符合条件的元素则返回false。

`array.some(function(currentValue,index,arr),thisValue)`

*注：* every和some可以看作一个是&&，一个是||

#### filter()

​	filter方法返回一个新数组，新数组中元素是符合filter筛选的原数组中元素。原数组不变。`array.filter(function(currentValue,index,arr),thisValue)`

#### forEach()

​	forEach方法用于调用数组的每个元素，并将元素传给回调函数。

​	`array.forEach(function(currentValue,index,arr),thisValue)`

​	对应jquery中的$.each方法

​	`$.each(array,function(index,currentValue,arr))`

#### map()

​	通过指定函数处理数组的每个元素，并返回处理后的数组，原数组不变

​	`array.map(function(currentValue,index,arr),thisValue)`

​	同样有对应的jquery中的$.map方法

​	`$.map(array,function(index,currentValue,arr))`

```javascript
var array=[4,9,16];
console.log(array.map(Math.sqrt));
console.log($.map(array,Math.sqrt));
console.log(array);
//输出
//[2,3,4]
//[2,3,4]
//[4,9,16]
```



### Part 5 查找数组元素

#### find()  findIndex()

​	find返回满足测试条件（指定函数）的第一个数组元素

​	findIndex返回满足测试条件的第一个数组元素的索引

​	`array.find(function(currentValue,index,arr),thisValue)`

​	`array.findIndex(function(currentValue,index,arr),thisValue)`

#### indexOf() lastIndexOf()

​	indexOf()返回某个元素值在数组中首次出现的位置

​	lastIndexOf()返回某个元素值在数组中最后一次出现的位置

​	`array.indexOf(item,start)` `array.lastIndexOf(item,start)`

​	item为要查找的元素，此参数必需。start为数组中开始检索的位置，不必需，默认为0。

#### slice()

​	slice()返回原数组中选定范围元素构成的新数组，不改变原数组

​	`array.slice(start,end)`

​	start为开始处索引，end为结束处索引，选取范围为[start,end)

​	end不必需，默认为array.length



*注*： 查找时的索引如果是负值，那它表示的是从数组末尾开始往前算的元素。然而直接用[]取数组元素不能用负的索引。但可以像下面这样

```javascript
arr=[1,2,3];
console.log(arr[-1]);
arr[-1]=5;
console.log(arr[-1]);
console.log(arr['-1']);
console.log(arr);
//输出
//undefined
//5
//5
//[1,2,3,-1:5]  
//这相当于给array数组中增加了一个key为-1，value为5的键值对。神奇的js
```



### Part 6 其他函数

#### fill()

​	使用一个固定值来填充数组 `array.fill(value,start,end)`

#### reduce() reduceRight()

​	将数组元素计算为一个值。reduce()从左到右，reduceRight()从右到左

​	`array.reduce(function(total,currentValue,currentIndex,arr),initialValue)`

​	total必需，初始值和计算结束后的返回值。

​	currentValue必需，当前元素

​	currentIndex不必需，当前元素索引

​	arr不必需，当前数组

​	initialValue不必需，传递给函数的初始值

```javascript
var array=[15.5,2.3,1.1,4.7];
var result=array.reduce(function(total,num){
	return total+Math.round(num);
},0)
console.log(result);
//输出为 24
```

#### valueOf()

​	返回数组对象的原始值 `array.valueOf()`

> 该原始值由 Array 对象派生的所有对象继承。

> valueOf() 方法通常由 JavaScript 在后台自动调用，并不显式地出现在代码中。

​	这个函数大概不太需要用...