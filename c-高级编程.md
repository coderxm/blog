---
title: c++高级编程
date: 2020-05-01 08:26:55
author: 小码
tags: c++
categories: c/c++
keywords: [c++,后端]
toc: true
---
#### c++高级编程介绍

   学c++确实是件痛苦的事，这水平得一步步抬上去，实话说学校教的也不好，就更痛苦了，还要学这学那，对技术没半点提升。最近就在学这个，没得方向，只好自己归纳了。嘤！嘤！
   ![嘤嘤](https://img-blog.csdnimg.cn/20200429165631459.jpg#pic_center)


---
##### 目录
 - 预处理
 - 模板
 - 命名空间
 - 文件和流
 - 动态内存分配
 - 异常处理
 - 信号处理
 - 多线程
 - web编程
---
![知识图](https://img-blog.csdnimg.cn/20200429190054196.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)


---
##### 01 预处理

###### 预处理指令
预处理器是一些指令，指示编译器在实际编译之前所需完成的预处理。所有的预处理器指令都是以井号（#）开头，和C语言一样，也不是c++语句。C++ 还支持很多预处理指令，比如 #include、#define、#if、#else、#line 等。

**define 预处理**

#define 预处理指令用于创建符号常量。该符号常量通常称为宏，指令的一般形式是：

```
#define 宏 替代文本 
```
这里的宏可以当成常量，书本上一般都大写。但不是非得大写，可以小写，只是在以后的学习上有一个好习惯。其他的宏就不一一介绍了。

**预定义宏**

![预定义宏](https://img-blog.csdnimg.cn/20200429170234837.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

**#运算符**

 和 ## 预处理运算符在 C++ 和 ANSI/ISO C 中都是可用的。# 运算符会把替换文本令牌转换为用引号引起来的字符串。
 ![#](https://img-blog.csdnimg.cn/20200429170741843.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70)
 **条件编译**
 有几个指令可以用来有选择地对部分程序源代码进行编译。这个过程被称为条件编译。条件预处理器的结构与 if 选择结构很像。
![条件编译](https://img-blog.csdnimg.cn/20200429171048730.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70)

---
##### 02 模板
模板是c++一个很重要的概念，模板是泛型编程的基础，泛型编程即以一种独立于任何特定类型的方式编写代码。

上面是c++自己说的，讲的这么高尚，都把自己讲糊涂了！简单去讲，模板可以理解为一种基本模样，可以用来创建函数或者类，或者别的，只是还不到变量的类型。需要注意的是模板可不是类，也就是没有特定的类型啦！

**函数模板**

![函数模板](https://img-blog.csdnimg.cn/20200429172124168.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)图中的T是无特定类型，整个用法有点像函数重载一样，至少重载需要定义不同的同名函数，参数输入也要不一样，有了模板，代码量就减少了，套模板就是。当输入的是整型时，则T为整形进行运算，其余类似。关于刚才的重载和inline内联可参考上次的文章：[c++面向对象吗？不懂看这个](https://blog.csdn.net/gobullin/article/details/105798076)


**类模板**

在这里，type 是占位符类型名称，可以在类被实例化的时候进行指定。可以使用一个逗号分隔的列表来定义多个泛型数据类型。
![类模板](https://img-blog.csdnimg.cn/20200429173329417.PNG#pic_center)

![类模板](https://img-blog.csdnimg.cn/20200429173646951.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
以上就是几个常见的模板，如果真要一个类型去归纳的话，c++给了一个高大上的名字：**泛型**，一个宽泛的类型。。。。


---

##### 03 命名空间
在c++中，一个名为 xyz() 的函数，在另一个可用的库中也存在一个相同的函数 xyz()。这样，编译器就无法判断您所使用的是哪一个 xyz() 函数。因此，引入了命名空间这个概念，它可作为附加信息来区分不同库中相同名称的函数、类、变量等。使用了命名空间即定义了上下文。本质上，命名空间就是定义了一个**范围**。
![图解](https://img-blog.csdnimg.cn/20200429174417484.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
**特定命名**：

![命名namespace](https://img-blog.csdnimg.cn/20200429174452299.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)然而，以上命名空间的函数前，都加了空间名，我们可以用using指令省去，即using namespace 空间名 就可以省去了，例：

using namespace std;

cout << '小码之光' <<endl;
 而不是std::cout/endl

**嵌套命名**

![嵌套命名](https://img-blog.csdnimg.cn/20200429175303338.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

---
##### 04 文件和流
C++ 中另一个标准库 fstream，它定义了三个新的数据类型：
![文件io](https://img-blog.csdnimg.cn/20200429175459819.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
以上三个理解：
ofstream:out-file-stream写文件;
ifstream:in-file-stream读文件;
fstream:file-stream读写;

![读写模式](https://img-blog.csdnimg.cn/20200429180035780.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
在从文件读取信息或者向文件写入信息之前，必须先打开文件。ofstream 和 fstream 对象都可以用来打开文件进行写操作，即需要**先创建文件对象**，如果只需要打开文件进行读操作，则使用 ifstream 对象。和c里的文件读取一样，c++也有打开模式。不过有点不同。

下面是 open() 函数的标准语法，open() 函数是 fstream、ifstream 和 ofstream 对象的一个成员。

void open（文件名, ios::打开模式);

![例](https://img-blog.csdnimg.cn/20200429180141903.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
当 C++ 程序终止时，它会自动关闭刷新所有流，释放所有分配的内存，并关闭所有打开的文件。但程序员应该养成一个好习惯，在程序终止前关闭所有打开的文件。

close() 函数是 fstream、ifstream 和 ofstream 对象的一个成员。


---

##### 05 动态内存
**关键字**new\delete
堆是程序中未使用的内存，在程序运行时可用于动态分配内存。使用new 运算符为给定类型的变量在运行时分配堆内的内存，这会返回所分配的空间地址。如果您不再需要动态分配的内存空间，可以使用 delete 运算符，删除之前由 new 运算符分配的内存。

**数组**
![动态分配](https://img-blog.csdnimg.cn/20200429181216147.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)**对象**

![对象分配](https://img-blog.csdnimg.cn/20200429181424810.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)


---
##### 06 异常处理
异常是程序在执行期间产生的问题。C++ 异常是指在程序运行时发生的特殊情况，比如尝试除以零的操作。

异常提供了一种转移程序控制权的方式。C++ 异常处理涉及到三个关键字：try、catch、throw。
··································································································
   throw: 当问题出现时，程序会抛出一个异常。这是通过使用 throw 关键字来完成的。
   catch: 在您想要处理问题的地方，通过异常处理程序捕获异常。catch 关键字用于捕	获异常。
    try: try 块中的代码标识将被激活的特定异常。它后面通常跟着一个或多个 catch 块。
····································································································

![异常处理](https://img-blog.csdnimg.cn/20200429181940957.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
![捕获异常](https://img-blog.csdnimg.cn/20200429182015771.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
C++ 提供了一系列标准的异常，定义在 <exception> 中，我们可以在程序中使用这些标准的异常。它们是以父子类层次结构组织起来的，如下所示：
![异常说明](https://img-blog.csdnimg.cn/20200429182113676.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
**自定义异常**

![自定义](https://img-blog.csdnimg.cn/2020042918221952.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)


---

##### 07 信号处理
信号是由操作系统传给进程的中断，会提早终止一个程序。不是我们一般意义上的信号。这些信号是定义在 C++ 头文件csignal 。

![信号](https://img-blog.csdnimg.cn/20200429182634851.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)C++ 信号处理库csignal提供了 signal 函数，用来捕获突发事件。
**signal函数**

![signal](https://img-blog.csdnimg.cn/20200429182924504.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
**raise函数**

![raise](https://img-blog.csdnimg.cn/20200429183036845.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

---

##### 08 多线程
在高级语言编程里，总是会听到多线程，一些大厂面试也会提到多线程，那多线程有多厉害多神秘呢？

这里又要扯上专业课了，多线程是多任务处理的一种特殊形式，多任务处理允许让电脑同时运行两个或两个以上的程序。一般情况下，两种类型的多任务处理：基于进程和基于线程。

    基于进程的多任务处理是程序的并发执行。
    基于线程的多任务处理是同一程序的片段的并发执行。

多线程程序包含可以同时运行的两个或多个部分。这样的程序中的每个部分称为一个线程，每个线程定义了一个单独的执行路径。通俗的说就是，计算机干活时候，将以一个进程为单位，处理一个要执行的程序，比如要打开的QQ，但不能一股脑把它干了，还有别的程序要运行呢。所以进程在内存上是间隔的，运行一个程序，计算机把很大的可执行文件分成若干部分去执行，每一部分以线程(都这么叫)的形式执行，这样就有了多线程处理。

**创建线程**：
	#include <pthread.h>
	pthread_create (thread, attr, start_routine, arg) ；

![参数](https://img-blog.csdnimg.cn/20200429184556582.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
**终止线程**

使用下面的程序，我们可以用它来终止一个 POSIX 线程：

#include <pthread.h>
pthread_exit (status) ；

在这里，pthread_exit 用于显式地退出一个线程。通常情况下，pthread_exit() 函数是在线程完成工作后无需继续存在时被调用。如果 main() 是在它所创建的线程之前结束，并通过 pthread_exit() 退出，那么其他线程将继续执行。否则，它们将在 main() 结束时自动被终止

**线程连接与分离**

![线程连接分离](https://img-blog.csdnimg.cn/20200429185150937.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)![lianjie](https://img-blog.csdnimg.cn/20200429185212778.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
··············································································································
![c11](https://img-blog.csdnimg.cn/20200429185308444.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

---

##### 09 web编程
 除了线程难以外，web编程学起来也很费劲，对初学者一点也不友好。所以在这里就不做过多累赘了。要学的太多了！就简单介绍一下公共网关接口（CGI），公共网关接口（CGI）是一套标准，定义了信息是如何在 Web 服务器和客户端脚本之间进行交换的，是一种用于外部网关程序与信息服务器（如 HTTP 服务器）对接的接口标准。如果要深入学习就寻找相关的书籍资料吧！(进公众号也行，问小码要哦，尽量帮你弄到， 写作不易，客官赏一个！)
![拽](https://img-blog.csdnimg.cn/2020042919130999.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

---
更多尽在微信公众号小码之光

博客：www.maliaoblog.cn
 推荐：
    《Essential C++ 中文版》
    《C++ Primer Plus 第6版中文版》
    《C++ Primer中文版（第5版）》


··················································END·························································

 微信公众号	：小码之光（免费资料等你拿哦，文章公众号首发！二维码7天有效）
 [项目资料](https://mp.weixin.qq.com/s/C-IDOjM245by-U_mBzPV2Q)

 ![公众号](https://img-blog.csdnimg.cn/20200429190944279.jpg#pic_center)



