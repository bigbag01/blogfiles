title: JAVA IO

date: 2017-07-04 11:21:33

categories: java基础

tags: [java io]

---

## 控制台IO

### 一、控制台输出

* System.out.print()	输出不换行
* System.out.println()   输出换行

### 二、控制台输入

​	控制台输入由System.in完成,创建BufferedReader对象来读

<!--more-->

#### 读取方式一：

```java
/* br.read()函数每次读取一个字符，且返回int型的值，流结束返回-1.*/
System.out.println("输入字符, 按下 'q' 键退出。");
BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
do{
  c=(char) br.read();
  System.out.println(c);
}while(c!='q');
```

#### 读取方式二：

```java
System.out.println("Enter 'end' to quit.");
BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
String str;
do {
  str = br.readLine();
  System.out.println(str);
} while(!str.equals("end"));
```

#### 读取方式三：

用**Scanner**类，java5之后推荐使用

```java
/* 输入aa bb */
System.out.println("next方式接收：");
Scanner scan=new Scanner(System.in);
if(scan.hasNext()){
  String str=scan.next();
  System.out.println(str);
  // 输出为aa
}

System.out.println("nextLine方式接收：");
Scanner scan1=new Scanner(System.in);
if(scan1.hasNextLine()){
  String str1=scan1.nextLine();
  System.out.println(str1);
  // 输出为aa bb
}
```

*注：* 

* next()方法以空白作为输入的分隔，不能得到带有空格的字符串
* nextLine()方法讲enter作为结束符，一行行获取输入，可以获得行内空白。

## 文件IO

### FileInputStream FileOutputStream

文件输入输出流，用于从文件读写数据。

```java
// 创建方式1
InputStream is=new FileInputStream("c:/java/hh.txt");
// 创建方式2
File f=new File("c:/java/hh.txt");
InputStream is=new FileInputStream(f);
//OutputStream创建方式相同
```

指定编码方式读写

```java
File f=new File("text.txt");
FileOutputStream fop=new FileOutputStream(f);
OutputStreamWriter writer=new OutputStreamWriter(fop,"UTF-8");
writer.append("输入");
writer.close();
fop.close();
FileInputStream fip=new FileInputStream(f);
InputStreamReader reader=new InputStreamReader(fip,"UTF-8");
StringBuffer sb=new StringBuffer();
while(reader.ready()){
  sb.append((char)reader.read());
}
System.out.println(sb.toString());
reader.close();
fip.close();
```

### 目录

* mkdir() 创建一个文件夹，成功返回true，失败返回false。
* mkdirs() 创建一个文件夹和他所有父文件夹

```java
File d=new File("/tmp/bin");
d.mkdirs();
```