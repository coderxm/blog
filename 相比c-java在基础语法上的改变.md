---
title: '相比c++,java在基础语法上的改变'
date: 2020-05-28 10:23:55
author: coder小码
tags: 
      - java
categories: java
keywords: [java,c++]
toc: true
---
此篇给Java初学者的一点参考，算是入门吧，对有c/c++基础的同学来说，更是帮助他们尽快理解Java更深层次(面向对象，集合，泛型，多线程与并发)的强力剂，如有缺漏敬请补正！转载需注明出处！

##### 文章目录：

1. 运行机制
2. 基本数据与特殊类型
3. 字符集与数值表达
4. 文档注释
5. 连字符+与输出
6. switch语句
8. foreach循环
8. 数组类型

------

#### 01 Java运行机制

在运行机制上，Java不同于任何一门语言，Java编写好的源代码文件并不是经过编译后就能立马执行的。不像c/c++一样，编译后就是.exe了，双击就可以运行，但是Java有它巧妙的地方。先说明一下，任何的编程语言的源码都需要经过编译变成二进制代码，才能被执行，无论c/c++还是Java。在Windows上把c/c++源码经过gCC/g++编译后能运行，但在Linux或其他平台，要有相应的源码编译器为源码进行编译，也就是说，想要在其他平台上运行，得把c/c++源码在编译一遍才能运行。看起来也还行的样子，不就是在编译一次嘛！有多大麻烦呢？对程序员来说不算是什么难事，但对用户来说就是难事，或者说，用起来就是个麻烦事。谁还会辛辛苦苦又编译一次源码，然后让它在机子上跑，万一出问题还得重来！

起初Java就是为解决这个问题而设计出来的，最早是被sun公司用于嵌入式的设备开发，理念是“write once,run anywhere!”，设计出来后并不很火，那时候c++本身就可以跨平台，所以也没Java什么事儿了。但是之后发现真的可以做到 “  run anywhere ” , 并且由于网页端互联网浪潮的掀起，Java在web上大显身手，这才有了今天的Java，然而sun公司在09年被Oracle收购，之后江湖上再也没了sun公司的身影。那Java又是怎么解决跨平台的问题呢?

先要了解Java文件，源码文件以.java为后缀，经过编译后不直接生成可执行文件，而是生成.class字节码文件(16进制)，这个文件不是让平台的操作系统读的，是让JVM (java virtual machine)java虚拟机读的，平台上的虚拟机识别后会相应生成能让机子跑起来的二进制文件，就能执行了。其中的原理比较复杂，就不过多陈述啦！

那有人就不快乐啦：就这？

当然不是，继续讲。想简单跑一个"hello 妹纸！"需要咋做啊？

首先上[Oracle的官网]，下载jdk1.8版本，就是常说的Java8。jdk(java development kits大概就这样)，顾名思义：Java开发包，有SE(standard     environment)   ,  EE (enterprise environment),ME(micro environment),即标准版，企业版，微型版。我们要学的是SE，到了工作岗位，可能就要EE了，ME现在基本少的接触，就不用学了，毕竟jdk都14了！里面大致分为javac编译器，运行器java.exe，JRE(java runtime environment) java 运行环境，java基础类库，和其他支持。其中JRE里面有JVM(负责解释字节码)，和其他环境支持。如果在windows上编译"coder小 码.java "源文件，就变成"coder小码.class",想要在另一台装linux的机子上运行，只需要在这台机子上装JRE就行了，JVM解释"coder小码.class"文件后执行它就行了。

------

#### 02 基本与特殊数据类型

Java相较于原始的c语言，多出了两个基本数据类型，byte字节(1个字节)，和boolean布尔(true/false)基本类型,总共8种；其他为引用(reference)类型，多出了String字符串类型，Array数组类型，null类型(唯一值null)，等等。原来的char字符类型变成了两个字节，可以支持中文字符，一个char,一个汉字。

保留字(目前未使用但以后会使用):const ; goto也是关键字。

直接量：true,false,null.虽然不是关键字，但依然不能用来做标识符。

标识符：增加了$标识开头(中英字母，下划线)，同样不能数字打头，其后才能接任意字符，中日英皆可。

------

#### 03 字符集与数值表达

上面大家可能就有点疑问了，咋就这么越来越开放了！中日字符都来了！没错，Java换了字符支持，使用unicode字符集，几乎支持所有字符，改变了以往编程语言只支持英文标识符的情况，现在读取一个char就相当于读取了一个汉字了。unicode就是这么杠！

数值表达：Java在整数上又动手动脚的，增加了对二进制整数的表达，比如。

```
int binary = 0b10000001;
```

上面为一个负数，需要换算成原码为-128。另外为防止程序员出意外看走眼，还可以写成：

```
int binary  = 0b1000_0001;
```

用下划线可以分隔整型和浮点型。

------

#### 04 文档注释

注释除了以前常用的单多行注释，Java还增加了文档注释。Java为开发者提供了大量的基础类，同时也提供了[API帮助文档](https://www.oracle.com/technetwork/java/javase/downoads/)，介绍各个API、方法、包、类的使用方法，原型。如果编写很大的Java程序，可以利用javadoc工具将源码的文档注释提取出来变成API文档，例：

```
/**两个*
*Description
*<h1>javadoc</h1>
*Copyright 2009
*@author coder小码
*@version 1.0
*/
```

可以在类，方法，public\protected变量前加注释。进入目录，终端输入：

```
javadoc -d D://coder/ -windowtitle API文档 -author -version *.java
```

上面的命令用于生成Java文档，-d 存放目录 ，-windowtitle 窗口标题，-author -version,加上作者和版本信息，从当前目录下所有Java源文件中提取注释。之后就生成了和官方一样专业的API文档了！

------

#### 05 连字符‘+’与输出

和c++一样，Java也有连字符，可以将字符串拼接到一起，但同时又能做算术运算，这就涉及到了运算符的重载和基本数据类型的装拆箱了。

```
String coder = "小码"+"coder";
String coder2 = "coder小码"+321；
System.out.println(coder);
System.out.println(coder2);
```

输出为：“小码coder”,“coder小码321”。

将+看作是一个方法，既可以把数字作为参数，又可以把字符做参数，而方法名却没有变，算是隐式的重载一个“+”方法。

##### 输入输出：

Java里主要有3种输出方式，或者说方法吧！上面的算一种：println(变量),即直接输出变量值，还带换行！第二种：printf("%s",string),这种再熟悉不过了，需要搭配格式符输出；第三种：print(变量)，同样直接输出值，只不过不带换行！以上都在lang包的System类下的out方法，返回PrintStream输出流类下的println()方法。

------

#### 06 switch语句

Java7增强了switch语句,原来从switch(expression)，表达式只能是byte , short , int , char四种，后来增加了枚举类型enum和String类型，但是不能为true/false布尔型 。相比c/c++的switch语句，多了byte,char(可以是单个中文字符)。需要注意的是：可以是String类型，而不是StringBuffer或StringBuilder字符串类型，即使都是字符串类型。

```
String coder = "coder小码";
switch (coder){
	case "点赞":
		System.out.println(coder);
		break;
	case "收藏":
		System.out.println(coder);
		break;
	case "coder小码":
		System.out.println(coder);
		break;
	default:
		System.out.println(coder);
}
```

------

#### 07 foreach循环

foreach循环是从Java5之后开始加入的，python语法里也有foreach循环，使用它进行遍历操作非常方便。那方便在哪呢？

- 无需获得要遍历对象的长度，即不需要知道数组或集合多大
- 无需根据索引(下标)访问数组或集合(collection)的元素

foreach语法如下：

```
for(元素类型 循环变量: 数组或集合){
	//要执行的代码块
	System.out.println(循环变量);
}
```

从上面看出，foreach的循环将数组或集合中的元素临时赋值给了循环变量，后逐个输出，并没有改变数组的元素，即foreach虽好，但不能改变数组或集合的内容 或值。如果在循环内给循环变量进行赋值，同样不能改变其内容，反而将想要获得的数组的元素修改替换了。

------

#### 08  数组类型

在Java里数组类型有很大变化，以前在c/c++里，数组名就相当于一个指针，指向数组内存首地址。在Java中不是没有指针，只是指针这种概念被弱化了，很少提到，反而多出了引用这种类型，而数组就属于引用类型。

##### 数组的定义有两种方式：

```
int[] coder;
或int coder[];
```

很明显，在引入引用的概念并支持unicode字符集后，选择第一种方式才符合Java的语法，不是说第二种就错了，而是第二种可读性太差，很容易看成是定义了一个int类型的以“coder[]”为变量名的数据，而第一种方式，int[]本身就是一种引用类型，而coder就是一个妥妥的引用变量。

##### 数组的初始化的3种方式：

```
第一种：coder = new int[] {3,2,1};
第二种：coder = new int[3];
第三种：int[] coder = {3,2,1};
```

经典又常用的三种初始化方式，先说前两种吧。前两种都是在已经定义了数组的情况下进行初始化的，我们将第一种称做静态初始化，即初始化的时候就把元素值填了进去，这个时候数组就定了，长度不再改变。而第二种则可以称动态初始化，只是初始化他的长度，并没有赋值。第三种是第一种的简化，即把数组定义和静态初始化两步合一步。以上就是数组的诞生过程，可能有小伙伴会发牢骚：弄一个数组都这么麻烦，还没c/c++效率高呢！的确，c/c++是效率高，但上面之所以要带一个关键字new，其实是为了给数组分配一个内存并初始化赋值，尽管定义了一个数组变量，但只是引用变量而已，没有真正的存数据的内存，起到的也只是一个指向内存的作用，真正有内存是new一个给它。

------
最后附上：
[github](https://GitHub.com/coderxm/)
[博客园](https://www.cnblogs.com/coderma)
微信公众号：小码之光
  
 ![小码之光](https://img-blog.csdnimg.cn/20200427213721746.jpg#pic_center)


