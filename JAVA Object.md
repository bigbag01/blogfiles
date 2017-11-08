title: JAVA Object

date: 2017-04-02 16:18:33

categories: java基础

tags: [Object]

---

## JAVA Object

​	java中的Object 类来自**java.lang.Object** , java.lang包在使用的时候无需显示导入，编译时由编译器自动导入。

​	Object是java中所有类的祖先，老祖宗……所有的未显式声明extends的类都默认继承自Object

<!--more-->

## Object 类中的方法

​	因为所有的类都继承自Object, 所以以下方法是任何类都具有的，并且可以被重写。

### public Object()

* constructor

### protected Object clone()

​	**description**: creates and returns a copy of this object.

* 如果要在子类中覆盖父类的clone方法，必须声明为public
* 注意到clone()返回值为Object类型，所以在子类调用时，会需要类型强制转换
* 自定义类中要使用clone()则还需要implements cloneable()接口
* 深复制、浅复制与clone()  [参考](http://www.cnblogs.com/zhanht/p/5445478.html) 

### boolean equals(Object obj)

​	**description**: indicates whether some other object is "equal to" this one 

* '==' 运算符判断两个引用是否指向同一个对象，对于Object类的equals方法，它判断调用equals方法的引用与传入的引用是否指向同一对象
* Object类中的equals()方法等价于 '=='
* 当继承了Object的类重写了equals方法时，也应该重写hashCode()方法

### int hashCode()

​	**description**: returns a hash code value for the object

* 这个方法返回值是一个整型值，如果两个对象被equals方法判断为相等，那么它们拥有相同的hash code，但是hash code相同不一定equals方法返回true。
* Object类的hashCode()方法为不同的对象返回不同的值，hashCode值表示对象的地址　

### String toString()

​	**description**: returns a string representation of the object

* 当打印引用时，会自动调用对象的toString方法，打印出引用所指对象的toString()方法返回值。

* ```java
  //Object类中的toString()方法定义
  public String toString(){
  	return getClass().getName()+"@"+Integer.toHexString(hashCode()); 
  }
  ```

* ```java
  //一些集合中的toString
  Set<Integer> set=new HashSet();
  List<Integer> list=new ArrayList();
  int[] array;
  Map<String,Integer> map=new HashMap();
  // ......
  // set,list,array contains 1,2,3; map contains{a:1,b:2,c:3}
  System.out.println("set: "+set.toString());
  System.out.println("list: "+list.toString());
  System.out.println("array: "+array.toString());
  System.out.println("Arrays: "+Arrays.toString(array));
  System.out.println("map: "+map.toString());
  /* results:
   * set: [1, 2, 3]
   * list: [1, 2, 3]
   * array: [I@17b68215
   * Arrays: [1, 2, 3]
   * map: {b=2, c=3, a=1}
   */
  ```

### protected void finalize()

​	**description**: called by the garbage collector on an object when garbage collection determines that there are no more references to the object

> The general contract of `finalize()` is that it is invoked if and when the JavaTM virtual machine has determined that there is no longer any means by which this object can be accessed by any thread that has not yet died, except as a result of an action taken by the finalization of some other object or class which is ready to be finalized. The `finalize` method may take any action, including making this object available again to other threads; the usual purpose of `finalize()`, however, is to perform cleanup actions before the object is irrevocably discarded. For example, the finalize method for an object that represents an input/output connection might perform explicit I/O transactions to break the connection before the object is permanently discarded.

* finalize方法不需要显示调用，在GC时会被自动先行调用。
* finalize方法可能会重新使当前对象对其他线程可用
* 同一个对象的finalize方法绝不会被调用超过一次。
* finalize方法抛出的异常导致当前object的finalization暂停，但是会被忽视。

### Class<?> getClass()

​	**description**: returns the runtime class of the Object

* 利用这个方法可以获得一个实例的类型类。

  在获得类型类之后可以调用其中的一些方法

  * String getName() 获得该类型的全称名称
  * Class getSuperClass() 获得该类型的直接父类，如果没有就返回null
  * Class[] getInterfaces() 获得该类型实现的所有接口
  * boolean isArray()
  * boolean isEnum()
  * boolean isInterface()
  * boolean isPrimitive() 判断是否为基本类型
  * boolean isAssignableFrom(Class cls) 判断这个类型是否是cls的父（祖先）类或父（祖先）接口
  * Class getComponentType() 如果该类型是一个数组，就返回该数组的组件类型
  * ……



### 其他方法

​	以下方法都和线程相关，等之后了解了java线程相关知识再来补~~

* void notify()
* void notifyAll()
* void wait()
* void wait(long timeout)
* void wait(long timeout, int nanos)