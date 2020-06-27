---
title: java equals()函数与‘=='
date: 2020-05-09 07:26:20
author: coder小码
tags: 
     - java
     - equals
categories: java
keywords: [java]
toc: true
---
### java equals()函数与‘==’
---
> 谈到java的字符串比较函数equals(),就不得不说它真真的用途啦！虽然只是java里面一个简单的知识点，还是有必要扯扯它，因为有许多学习java的小伙伴在比较字符串上纠结与equals()和‘==’的选择。


---
#### equals()函数
函数原型：

> public boolean equals(Object anObject)

![equals()](https://img-blog.csdnimg.cn/20200509203330784.PNG#pic_center)

函数用来比较**字符串内容**的相等，可以是字符串的变量String a = "coder小码",字符串对象String a = new String("coder小码")之间或和同类型的字符串比较，只要是String就行。返回值是布尔值，true \ false,与类型是String或String对象没有关系，只要字符串内容一致，就返回true,否则false。

######   字符对象比较
![字符对象的比较](https://img-blog.csdnimg.cn/20200509204232153.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
###### 字符对象与字符String比较

![字符对象与字符String比较](https://img-blog.csdnimg.cn/20200509204448284.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
###### 字符String之间比较

![字符String之间比较](https://img-blog.csdnimg.cn/20200509204724918.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

----
#### ‘==’关系运算符的运用

在编写代码的过程中我们经常用到‘==’ 运算符，那 它实质比较的是什么呢？其实也不很高深莫测，实质上是在比较引用指向的内存地址的，只要指向的内存地址相同，即可判断为true。

说到这里可能会有疑惑了，难道还比内存不成？咋回事啊？咱们先看看几个小例子：


###### 对象间的比较
![对象间的比较](https://img-blog.csdnimg.cn/20200509205936508.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
###### 字符间的比较
![字符间的比较](https://img-blog.csdnimg.cn/20200509210051416.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

###### 字符与字符对象的比较

![字符与字符对象的比较](https://img-blog.csdnimg.cn/20200509210147114.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

###### 整型间比较
![整型间比较](https://img-blog.csdnimg.cn/20200509210230950.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

---
#### 总结
以上代码例子可以说明equals()只是用来比较字符串内容的，不涉及字符串值的地址，而‘==’用法就广泛一点，还能用来比较整形(不止整形和字符)，但实质上是比较是不是来自同一个地址，是就返回true，否则false。好啦，以上就是今天的内容，欢迎在下面留言哦！每一点都是知识的积累，希望学习躺赢，学习愉快！

---
最后：
[博客CSDN](https://blog.csdn.net/Gobullin)：coder小码
公众号‘**小码之光**’：
![小码之光](https://img-blog.csdnimg.cn/20200509211320148.jpg#pic_center)



---
