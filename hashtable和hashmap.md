title: 关于HashMap和HashTable

layout: post

date: 2017-03-24 16:20:33

categories: java基础

tags: [HashMap, HashTable]

---

### 相同点

​	HashMap和HashTable都实现了Map接口

### 区别

#### 同步性

**HashTable** 是synchronized，多个线程可以共享一个HashTable，java5后可用ConcurrentHashMap替代，扩展性更好。

**HashMap** 非synchronized，如果没有正确同步，多个线程不可共享HashMap。

<!-- more -->

#### null键值

**HashTable** 不可接受为null的key和value

**HashMap** 可以接受一个null的key和多个null的value。



**原因**： HashMap计算key的hash值时调用单独的方法，在该方法中会判断key是否为null，如果为null则返回0。而HashTable中直接调用key的hashCode()方法，如果key为null，会抛出空指针异常。

（深层原因：HashTable继承自Dictionary,HashMap继承自AbstractMap）

*注：ConcurrentHashMap虽然也继承自AbstractMap,但是也过滤了为null的key和value*  

### 性能

HashTable是synchronized，所以单线程环境下比HashMap慢。不需要同步，只要**单一线程** 的情况下，**HashMap**性能好过HashTable。

### 更多参考

http://blog.csdn.net/tgxblue/article/details/8479147

http://docs.oracle.com/javase/7/docs/api/