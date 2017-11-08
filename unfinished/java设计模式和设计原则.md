title: java设计模式和设计原则

date: 2017-03-29 22:34:05

categories: java web

tags: [设计模式, spring]

---

## 设计模式

java中常用的设计模式有24种

#### 一、创建型模式

* abstract factory pattern
* Builder pattern
* **factory method pattern**
* prototype pattern
* **singleton pattern**
* **multition pattern**

#### 二、结构型模式

* adapter pattern
* bridge pattern
* composite pattern
* decorator pattern
* facade pattern
* flyweight pattern
* proxy pattern

#### 三、行为型模式

* chain of responsibility pattern
* command pattern
* interpreter pattern
* iterator pattern
* mediator pattern
* memento pattern
* observer pattern
* state pattern
* strategy pattern
* template pattern
* visitor pattern

## 七大设计原则

* 单一职责原则（single responsibility principle）
* 里氏替换原则（liskov substitution principle）
* 依赖倒置原则（dependence inversion principle）
* 接口隔离原则（interface segregation principle）
* 迪米特法则（low of demeter）
* 开闭原则（open close principle）
* 组合/聚合复用原则（composition/aggregation reuse principle）CARP

[参考链接](http://www.cnblogs.com/zhoubang521/p/5200179.html)



## spring中的设计模式

​	目前做过的java web项目都使用了spring框架，spring中大量使用以下两种设计模式：工厂模式（factory method pattern）和单例模式（singleton pattern）

​	**工厂模式** 将java对象的调用者从被调用者的实现逻辑中分离出来，调用者只需关心被调用者必须满足的规则（接口），而不必关心实例的具体实现过程。这是面向接口编程的优势，能提高程序的解耦性。接口产生的全部实例，通常用于实现相同接口，其中定义了所有实例共同拥有的方法，这些方法在不同类中的实现可能不同，但调用者所使用的接口是一致的。如果要对原有代码进行重构也很方便。

​	spring 容器是管理和实例化所有bean的工厂，所有bean默认为**singleton** ，即对所有相同id的bean的请求都会返回同一个共享实例。单例模式让相同类的全部实例共享同一内存区，避免类被多次实例化，可以减少java对象的创建和销毁时的开销。