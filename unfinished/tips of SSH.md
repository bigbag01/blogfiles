# tips of java and SSH

### Hibernate

* mapping file
    - `<generator class="XXX" />` class的值
    > **increment** :生成long,short或者int类型的主键，不能在cluster环境下使用。适用于所有数据库 identity：生成long, short或者int类型的主键。适用于DB2, MySQL, MS SQL Server,  Sybase and HypersonicSQL 
    > **sequence** ：生成long, short或者int类型的主键。适用于DB2, PostgreSQL, Oracle, SAP DB, McKoi，Interbase. 
    > **hilo**：生成long, short或者int类型的主键。需要提供一个数据库的表来存放生成的主键信息。当采用应用服务器的JTA提供的数据库连接或者用户自定义的数据库连接的时候，不要使用这种主键生成方式。适用于所有数据库 
    > **seqhilo**：采用给定的数据库的sequence来生成long,short或者int类型的主键。适用于DB2,PostgreSQL, Oracle, SAP DB, McKoi，Interbase. 
    > **uuid.hex**：采用128位的算法来生成一个32位字符串。最通用的一种方式。适用于所有数据库 
    > **uuid.string**：同样采用128位的UUID算法。将生成的字符编码位16位。适用于除PostgreSQL.以外的数据库 
    > **native**：根据具体连接的数据库从identity,sequence或者hilo选择一种来生成主键。适用的数据库根据选择的生成方式确定.
    > **assigned**： 交给应用自己给主键赋值。要注意的是赋值必须在调用save()方法之前完成。适用的数据库根据选择的生成方式确定。

### SSH框架
##### 用配置文件和用注解的比较
> 什么时候用 **xml配置文件**
> 1.外部jar包依赖bean配置
> 2.用注解无法实现，或者用注解无法轻易实现的情形
> 3.项目组内部达成一致的约定的地方
> 4.特殊的配置（如：定义一个map）
> 优：容易编辑，配置比较集中，方便修改，在大业务量的系统里面，通过xml配置会方便后人理解整个系统的架构
> 缺：比较繁琐，类型不安全，配置形态丑陋,配置文件过多的时候难以管理

> 什么时候用 **注解**
> 除了上面4点，其他情况都可以用
> 优：方便，简洁，配置信息和 Java 代码放在一起，有助于增强程序的内聚性。
> 缺：分散到各个class文件中，所以不宜维护