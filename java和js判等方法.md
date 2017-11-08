title: 一些关于"="的故事

layout: post

date: 2017-03-24 16:30:00

categories: java基础

tags: ["判等", js]

---

### JAVA中的 == 和 equals

​	简单的说，java中的"=="判断的是两个变量的值是否相同，而equals方法，判断两个对象的内容是否相同。

1. java中的基本数据类型之间的比较应该用"==",因为比较的是值。

   (**基本数据类型**：byte, short, char, int, long, float, double, boolean)

2. 复合数据类型（类）在比较时，"=="判断的是二者在内存中的地址是否相同，而"equals"方法判断的是二者的值是否相等。

   <!-- more -->

```java
//使用equals判等，以下均相同，用==判断的结果见表格
String str1="hello";
String str2="hello";
String str3=new String("hello");
String str4=new String("hello");
```

​	

| 真值表  | str1  | str2  | str3  | str4  |
| ---- | ----- | ----- | ----- | ----- |
| str1 | true  | true  | false | false |
| str2 | true  | true  | false | false |
| str3 | false | false | true  | false |
| str4 | false | false | false | true  |

3. **然而**！！ 对一个自定义类先后创建的两个内容相同对象进行比较时，无论equals还是==，返回值都是false。**原因** 是java中所有的自定义类都隐性继承自Object，而Object中的equals也是用==来实现的 ⊙﹏⊙b

   所以如果想判断两个内容相同的对象相同，需要在这个类中重写equals方法。而如果是在一个集合中调用contains方法，判断对象是否存在，还需要覆盖类中的hashCode()方法。（曾经困扰过我许久的一个bug就是因为这！）

   [参考链接](http://www.cnblogs.com/happyPawpaw/p/3744971.html)

### javascript中的判等

​	JavaScript中的判等可以用"=="和"==="

* 在基础类型（string，number等）之间进行比较时
  * 如果两者类型不同，"==" 会将二者转化成同一类型，看值是否相等，而"==="如果类型不同，结果就是不等。
  * 如果类型相同，则"=="与"==="比较的都是值，返回结果也相同
* 在高级类型（Array，Object等）之间进行比较时
  * 二者都是对内存中的地址进行比较，返回结果是相同的。
* 在一个基础类型和一个高级类型之间进行比较时
  * 对于"==",高级类型会被转化为基础类型再进行值比较
  * 对于"===",结果就是不等的。

下面是一张令人震撼的真值表(ノ-_-)ノ~┻━┻

![js判等真值表](https://github.com/bigbag01/blogfiles/blob/master/img/js判等真值表.jpg?raw=true)