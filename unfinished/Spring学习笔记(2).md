# Spring学习笔记(2)

### 一、IoC的类型

1. **构造函数**注入

   在对象被实例化时即注入

   ```java
   public class Order{
     private User user;
     public Order(User user){
       this.user=user;
     }
     public void checkUserAge(){
       user.printAge();
     }
   }
   public class gatherData{
     User user=new Damean();
     /*一旦构造了Order类的对象，无论如何都会注入user对象*/
     Order order=new Order(user);
     order.checkUserAge();
   }
   ```

2. **属性**注入

   在对象被实例化后，需要用到某属性时才调用其setter方法来注入。

   ```java
   public class Order{
     private User user;
     public void setUser(User user){
       this.user=user;
     }
     public void checkUserAge(){
       user.getAge();
     }
   }
   public class gatherData{
     User user=new Sally();
     Order order=new Order();
     /*如果不调用checkUserAge则不必注入user*/
     order.setUser(user);
     order.checkUserAge();
   }
   ```

3. **接口**注入

   需要额外声明一个接口，且效果和属性注入差不多，不提倡。

*注：Spring支持1、2* 

### 二、IoC通过容器完成

​	Spring通过配置文件或注解描述类和类之间的依赖关系，自动完成类的初始化和依赖注入的工作。

### 三、相关JAVA知识

1. java反射机制、类加载器。。。**TODO** 

