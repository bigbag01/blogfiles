title: java Array和Arrays

date: 2017-04-05 22:22:33

categories: java基础

tags: [数组]

---

## 二者区别

​	**Arrays** 继承自java.lang.Object,它属于java.util工具包，它是java中的工具类。它包含了很多直接操作数组的方法，比如数组的排序、搜索等。其中还包括一个可以将数组作为列表来查看的**静态工厂** 。这个类中方法全都是static的，可以直接用`类名.方法`来调用。

​	**Array** 数组类，它是java中最基本的一个存储结构。它提供了动态创建和访问java数组的方法。一个Array中的元素类型必须相同。Array效率高，但容量固定无法动态改变。array.length只能得到array的容量，无法判断其中实际元素个数

<!--more-->

## Arrays中的常用方法

### static void sort(T[] a[, int fromIndex, int toIndex])

* 数值属性默认是由小到大排序

* 字符串排序

  * `Arrays.sort(strarr)` 按照先大写后小写字母排序，


* `Arrays.sort(strarr,String.CASE_INSENSITIVE_ORDER)` 严格按照字母表排序，忽略大小写
  * `Arrays.sort(strarr,Collections.reverseOrder())` 可以反向排序

* 如果要对某个对象数组进行排序，需要自己实现java.util.Comparator接口。

### static void binarySearch(T[]a [,int fromIndex, int toIndex], T key)

* 对已排序的数组进行二元搜索，如果找到指定的值就返回它所在的索引位置，否则返回负值

### static void fill(T[]a [,int fromIndex, int toIndex], T val)

* 将数组a（指定范围）的元素的值全部设定为val

* 指定范围开闭区间 [fromIndex,toIndex) 左开右闭。

###static boolean equals(T[]a, T[]a2)

* 比较两个数组的元素值是否全部相等。
* 适用于一维数组，多维数组用 `deepEquals`方法（`deepEquals`不可用于一维数组）

### static String toString(T[]a)

* 将数组转为字符串表示出来

### static T[] copyOf(T[]original, int newLength)

* 复制原数组，将长度变为newLength，如果小于原长就截取所需，如果大于原长，就用默认值填充（对于对象，填null，数值型填0，布尔型填false）

### static T[] copyOfRange(T[], int from, int to)

* 将指定范围[from,to)的数组元素复制到新数组并返回新数组。

### static <T> List<T> asList(T...a)

* e.g. `List l=Arrays.asList("a","b","c");`
* Arrays.aslist(array) 返回的List不支持add和remove。这里返回的ArrayList和java.util.ArrayList不同。



## Array 和ArrayList

* ArrayList类似于一种容量可变的Array.

* Array也是一种对象，Array名称本身也是一个引用，指向heap之内的某个实际对象

### Array和ArrayList比较 

* **Array** 效率高，但容量固定
* **ArrayList** 容量可以动态增长，但是会牺牲效率
* **Array** 可以存放基本类型，**ArrayList** 如果要存放基本类型，只能放它们的包装类。
* **Array** 可以用`[ ]`操作符取元素，**ArrayList** 用`get(i)` 方法代替

### Array和ArrayList互相转换

查找资料的时候发现网上给的关于Array和ArrayList的转换都是像下面的代码中的写法，然而这里的Array是转换成了List， 对应的实现类**并不是ArrayList!!!!** 

我实验了一下发现它确实是不支持add和remove方法的

```java
public class Test {
	public static void main(String[] args)  {
		ArrayList<String> arrlist=new ArrayList<String>();
		arrlist.add("ele1");
		arrlist.add("ele2");
		arrlist.add("ele3");
		int size=arrlist.size();
		String [] array=arrlist.toArray(new String[size]);
		for(int i=0;i<arrlist.size();i++){
			System.out.println(array[i]);
		}
		System.out.println("--------");
		List<String> list=Arrays.asList(array);
		for(int i=0;i<arrlist.size();i++){
			System.out.println(list.get(i));
		}
		System.out.println("--------");
		list.add("ddd");list.remove(0);
		for(int i=0;i<list.size();i++){
			System.out.println(list.get(i));
		}
	}
}
```

运行该程序段的结果如下

```
ele1
ele2
ele3
--------
ele1
ele2
ele3
--------
Exception in thread "main" java.lang.UnsupportedOperationException
	at java.util.AbstractList.add(AbstractList.java:148)
	at java.util.AbstractList.add(AbstractList.java:108)
	at learnJavaDemo.Test.main(Test.java:29)
```