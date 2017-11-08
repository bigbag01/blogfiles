title: java中的几个基本数值型数据类型，待完善~~~

layout: post

date: 2017-03-20 12:59:58

categories: java基础

tags: [基本数据类型]

---

### int, long 

* java中的**int**和**long**都是有符号的，正负区别在于取反加一。

* int总共32位，正数上限首位为0，即正数最大值为2^31-1，负数最小值为-2^31

* long总共64位

* int转long是向上转换可以直接隐式转换，long转int是向下，可能出现数据溢出情况！！

  ```java
  long ll=300000;
  //强制转换
  int ii=(int)ll;
  //调用intValue()
  int ii=new Long(ll).intValue();
  //先转为String
  int ii=Integer.parseInt(String.valueOf(ll));
  ```


<!-- more -->

### float, double

* float 32位，double 64位
* 在同等位数的情况下，浮点数可表示的数值范围比整数的大
* double 和 float 的区别是double精度高，有效数字16位，float精度7位。但double消耗内存是float的两倍，double的运算速度比float慢得多
* float和double只能用来做**科学计算**或者是**工程计算**，在商业计算中我们要用 java.math.BigDecimal

### Infinity NaN

* **Infinity** 无穷大，满足`i==i+1` 

  可以用被计算为无穷大的浮点算术表达式来初始化，例如：`double i= 1.0/0.0;` ,或者更好的方式是 `double i=Double.POSITIVE_INFINITY;` 

* **NaN** 非数，满足`i!=i` 

  * NaN不等于任何浮点数值，包括它自身。可以用被计算位NaN的浮点算术表达式来初始化i，例如：`double i=0.0/0.0;` ,或者用 `double i=Double.NaN;`
  * 任何浮点操作，只要它的一个或多个操作数为NaN,那么其结果为NaN。
  * NaN与任何数用`==`比较均返回false
  * 用`compare`方法返回true