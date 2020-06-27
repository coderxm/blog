---
title: c++对象？看看这个
date: 2020-04-28 21:39:25
author: 小码
tags: 
     - c++
     - 面向对象
categories: c/c++
keywords: [对象,c++]
toc: true
---
###  深入理解c++面向对象几大特性
---
 - 类
 - 继承
 - 重载
 - 多态
 - 数据抽象
 - 数据封装
 - 抽象类及实例化

---

![思维图](https://img-blog.csdnimg.cn/20200427194118832.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

---

#### 01 类

类是 C++ 的核心特性，通常被称为用户定义的类型。也就是说，它和其他基本类型一样(浅显的这么说)，都是type。类定义是以关键字 class 开头，后跟类的名称。由类可以生成对象，这里，对象可以理解为变量，一种特殊类型的变量，相当于c语言中的struct结构体类型变量。

---

#### 02 类成员函数
类的成员函数是指那些把定义和原型写在类定义内部的函数，就像类定义中的其他变量一样。也可以在类的外部使用范围解析运算符 :: 定义该函数

![范围解析](https://img-blog.csdnimg.cn/20200427195444481.PNG#pic_center)

需要强调一点，在 :: 运算符之前必须使用类名，调用成员函数是在对象上使用点运算符（.）。

---

#### 03 类访问修饰符
访问限制是通过在类主体内部对各个区域标记 public、private、protected 来指定的。关键字 public、private、protected 称为访问修饰符。

公有成员在程序中类的外部是可访问的(public)，即可以通过(对象.成员)或内部的public调用函数访问。

 私有成员(private)则不同，那只能通过类内部的调用函数访问或修改，这时的内部public函数相当于链接类内外的桥梁，而不能用(对象.成员)去访问了，即便是继承了的子类(派生类)也不能这样调用私有成员。除了protected。

 保护成员(protected)像私有成员一样，不能直接访问，需要使用内部函数，但区别就体现在继承的子类上，子类则可以直接通过(对象.成员)调用成员。

![protected](https://img-blog.csdnimg.cn/20200427202735199.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

---

#### 04 析构与构造函数

类的构造函数是一种特殊的函数，在创建一个新的对象时调用。类的析构函数也是一种特殊的函数，在删除所创建的对象时调用。构造函数的名称与类的名称是完全相同的，并且不会返回任何类型，也不会返回 void。构造函数可用于为某些成员变量设置初始值。类的析构函数是类的一种特殊的成员函数，它会在每次删除所创建的对象时执行。

析构函数的名称与类的名称是完全相同的，只是在前面加了个波浪号（~）作为前缀，它不会返回任何值，也不能带有任何参数。析构函数有助于在跳出程序（比如关闭文件、释放内存等）前释放资源。

下面的实例有助于更好地理解析构函数的概念：

![构造函数](https://img-blog.csdnimg.cn/20200427203150275.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

---


#####  拷贝构造函数：
拷贝构造函数，是一种特殊的构造函数，它在创建对象时，是使用同一类中之前创建的对象来初始化新创建的对象。

![拷贝构造函数](https://img-blog.csdnimg.cn/20200427203553626.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
#### 05 友元函数

类的友元函数是定义在类外部，但有权访问类的所有私有（private）成员和保护（protected）成员。尽管友元函数的原型有在类的定义中出现过，但是友元函数并不是成员函数。友元可以是一个函数，该函数被称为友元函数；友元也可以是一个类，该类被称为友元类，在这种情况下，整个类及其所有成员都是友元。如果要声明函数为一个类的友元，需要在类定义中该函数原型前使用关键字 friend。

![友元函数](https://img-blog.csdnimg.cn/20200427203814283.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
注意：友元函数不是类成员函数，但有很厉害的通行证，能访问所以成员，同时也不能被子类继承，要访问不能用(对象.函数)。

---

#### 06 内联函数
 通过内联函数，编译器试图在调用函数的地方扩展函数体中的代码。内联函数是通常与类一起使用。如果一个函数是内联的，那么在编译时，编译器会把该函数的代码副本放置在每个调用该函数的地方。如果想把一个函数定义为内联函数，则需要在函数名前面放置关键字 inline，在调用函数之前需要对函数进行定义。如果已定义的函数多于一行，编译器会忽略 inline 限定符。引入内联函数的目的是为了解决程序中函数调用的效率问题，这么说吧，程序在编译器编译的时候，编译器将程序中出现的内联函数的调用表达式用内联函数的函数体进行替换，而对于其他的函数，都是在运行时候才被替代。这其实就是个空间代价换时间的i节省。所以内联函数一般都是1-5行的小函数。在使用内联函数时要留神：

    1.在内联函数内不允许使用循环语句和开关语句；
    2.内联函数的定义必须出现在内联函数第一次调用之前；


---

#### 07 this指针
每一个对象都能通过 this 指针来访问自己的地址。this 指针是所有成员函数的隐含参数。因此，在成员函数内部，它可以用来指向调用对象。

this 指针是所有成员函数的隐含参数，即this已经事先定义好了，不用再声明了。友元函数没有 this 指针，因为友元不是类的成员。只有成员函数才有 this 指针。用法与c中结构体类似，指向对象。

---

#### 08 指向类的指针
指向类的指针方式如同指向结构的指针。实际上，类可以看成是一个带有函数的结构。访问指向类的指针的成员，需要使用成员访问运算符 ->，就像访问指向结构的指针一样。与所有的指针一样，必须在使用指针之前，对指针进行初始化。

---

#### 09 静态成员

使用 static 关键字来把类成员定义为静态的。当我们声明类的成员为静态时，这意味着无论创建多少个类的对象，静态成员都只有一个副本。静态成员在类的所有对象中是共享的。如果不存在其他的初始化语句，在创建第一个对象时，所有的静态数据都会被初始化为零。我们不能把静态成员的初始化放置在类的定义中，但是可以在类的外部通过使用范围解析运算符 :: 来重新声明静态变量从而对它进行初始化。

![静态成员函数](https://img-blog.csdnimg.cn/20200427210152476.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

 ---

#### 10 继承
创建一个类时，不需要重新编写新的数据成员和成员函数，只需指定新建的类继承了一个已有的类的成员即可。这个已有的类称为基类，新建的类称为派生类。
 如：
class 继承类: 访问修饰符 基类；

---
#### 11 多继承
多继承即一个子类可以有多个父类，它继承了多个父类的特性。

C++ 类可以从多个类继承成员，语法如下：

class <派生类名>:<继承方式1><基类名1>,<继承方式2><基类名2>,…
{
<派生类类体>
};

---

#### 12 函数重载
在同一个作用域内，可以声明几个功能类似的同名函数，但是这些同名函数的形式参数（指参数的个数、类型或者顺序）必须不同。不能仅通过返回类型的不同来重载函数。

![重载](https://img-blog.csdnimg.cn/2020042721070710.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)![重载](https://img-blog.csdnimg.cn/20200427210731932.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

---

#### 13 运算符重载
重载的运算符是带有特殊名称的函数，函数名是由关键字 operator 和其后要重载的运算符符号构成的。与其他函数一样，重载运算符有一个返回类型和一个参数列表。成员运算符重载：

Box operator+(const Box&);

声明加法运算符用于把两个 Box 对象相加，返回最终的 Box 对象。大多数的重载运算符可被定义为普通的非成员函数或者被定义为类成员函数。如果我们定义上面的函数为类的非成员函数，那么我们需要为每次操作传递两个参数，那这样子类也不能继承，如下所示：

Box operator+(const Box&, const Box&);

![重载函数](https://img-blog.csdnimg.cn/20200427211346583.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
###### 重载决策：
上面的print()函数用了3次，仔细看都是不一样类型的参数，接下来在主函数main里调用了3次，所以内部有一个重载决策机制判断输入的参数类型该定义哪一个函数后调用。


---

#### 14 多态
就是多种形态。当类之间存在层次结构，并且类之间是通过继承关联时，就会用到多态。C++ 多态意味着调用成员函数(即使成员函数名相同)时，会根据调用函数的对象的类型(意味着在基类上产生了不同的派生类)来执行不同的函数。

![多态](https://img-blog.csdnimg.cn/20200427212119939.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)


---

#### 15 数据抽象与封装

数据抽象是指，只向外界提供关键信息，并隐藏其后台的实现细节，即只表现必要的信息而不呈现细节。数据抽象是一种依赖于接口和实现分离的编程（设计）技术。C++ 类为数据抽象提供了可能。它们向外界提供了大量用于操作对象数据的公共方法，也就是说，外界实际上并不清楚类的内部实现。使用类来定义我们自己的抽象数据类型（ADT），可以使用类 iostream 的 cout 对象来输出数据到标准输出，而不需要知道如何实现。说简单点就是要用到接口之类的，从而来方便调用操作数据。

数据封装是一种把数据和操作数据的函数捆绑在一起的机制，数据抽象是一种仅向用户暴露接口而把具体的实现细节隐藏起来的机制。C++ 通过创建类来支持封装和数据隐藏（public、protected、private）。

---

#### 16 抽象类

C++ 接口是使用抽象类来实现的，如果类中至少有一个函数被声明为纯虚函数，则这个类就是抽象类。纯虚函数是通过在声明中使用 "= 0" 来指定的，如下所示：
class Box
{
   public:
      // 纯虚函数
      virtual double getVolume() = 0;
   private:
      double length;      // 长度
      double breadth;     // 宽度
      double height;      // 高度
};

设计抽象类（通常称为 ABC）的目的，是为了给其他类提供一个可以继承的适当的基类。抽象类不能被用于实例化对象，它只能作为接口使用。如果试图实例化一个抽象类的对象，会导致编译错误。

因此，如果一个 ABC 的子类需要被实例化，则必须实现每个虚函数，这也意味着 C++ 支持使用 ABC 声明接口。如果没有在派生类中重写纯虚函数，就尝试实例化该类的对象，会导致编译错误。可用于实例化对象的类被称为具体类。

![抽象类](https://img-blog.csdnimg.cn/20200427212858552.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
说白了，这术语本质上就是个接口，以供调用。这些人说的这么高大上，最后把大家都弄晕了。好了以上就是给大家一个柳暗花明，希望有帮助在学习c++的路上！


![哈哈](https://img-blog.csdnimg.cn/20200427213257990.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
 最后附上：[小码csdn](https://blog.csdn.net/Gobullin)
 微信公众号：小码之光
 ![小码之光](https://img-blog.csdnimg.cn/20200427213721746.jpg#pic_center)





