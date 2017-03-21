

title: String StringBuilder StringBuffer

layout: post

date: 2017-03-20 12:53:59

tags: [java基础]

---

### 基本比较
* **String** 定义后不可变，可理解为常量，线程安全  
* **StringBuffer**、 **StringBuilder** 定义后可变 
* **StringBuffer** 对方法加了同步锁线程安全，**StringBuilder**非线程安全

### 性能比较
* 在每次对**String 类型**进行改变的时候，都会生成一个新的 String 对象，然后将指针指向新的 String 对象，每次生成对象都会对系统性能产生影响，当内存中无引用对象多了以后， JVM 的 GC 就会开始工作，性能就会降低。

* 使用 **StringBuffer 类**时，每次都会对 StringBuffer 对象本身进行操作，而**不是**生成新的对象并改变对象引用。

<!-- more -->

###使用策略

* **基本原则**：如果要操作少量的数据，用**String** ；单线程操作大量数据，用**StringBuilder** ；多线程操作大量数据，用**StringBuffer**。

* 使用StringBuffer或StringBuilder类的append方法代替String的‘+’，这在Java的优化上是一条比较重要的原则

* ```java
  StringBuilder sb = new StringBuilder();  
  for (String s : hugeArray) {  
      sb.append(s);  
  }  
  String result = sb.toString();
  ```

* 为了获得更好的性能，在构造 StringBuffer 或 StringBuilder 时应尽可能**指定它们的容量**。

*参考*：[Java：String、StringBuffer和StringBuilder的区别](http://blog.csdn.net/kingzone_2008/article/details/9220691)