---
title: IDEA报错稀有问题
date: 2020-06-26 18:36:18
author: coderxm
tags: 
      - IDEA 
      - 语法
categories: 问题
keywords: [IDEA,语法错误]
comments: false
toc: true
---
### **IDEA报错稀有语法问题**

------

> Error:java: Compilation failed: internal java compiler error;
> 
> Error:java需要";"
![报错](https://img-blog.csdnimg.cn/20200626115209953.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

这种报错不知道大家见过没有，可能一般人不会出现这种编译错误。实际上它的错误是红色的那个"Erroe:java:需要";" ",但是仔细检查正在编辑的代码，一点语法错误都没有，IDEA也没说哪里出问题了。于是又陷入了长久以来的僵局——百度！

------

### 百度的结果

结果说是jdk版本没配置好，我信了，又屁颠屁颠的改版本，原来是jdk8呀，现在也是。步骤如下：

![module](https://img-blog.csdnimg.cn/20200626115249713.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
![project](https://img-blog.csdnimg.cn/20200626115312144.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
![java compiler](https://img-blog.csdnimg.cn/20200626115342760.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

------

##### 百度结果的特点就是，搜出来一大堆相类似的东西，而你要的却是另外一个东西
所以我放弃百度的搜索，改用经典的eclipse进行编辑，在导入文件夹时，没运行就发现了语法错误，然而eclipse给我报错是这样的：

![eclipse报错](https://img-blog.csdnimg.cn/20200626115425299.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

很清楚的给我错的地方！但是反过来看，IDEA自称最智能的编辑器，有时候还是像智障编辑器，eclipse虽然皮肤不好看，但是依旧经典。ok，我回到IDEA智障编辑器里了，这里的问题应该就不难弄懂了，还是过不去的语法问题，出错在另一个文件里。

![修改错误](https://img-blog.csdnimg.cn/20200626115516956.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
改回来之后就行了，就能运行程序了。

------

### 总结：
IDEA报错有时让人摸不着头脑，还告诉你错在何处，接着错上加错，虚度光阴，罪恶之极！总结下来的原因就是，像IDEA编辑文件都是以项目文件进行编辑的，如果一个文件出语法错误，另一个文件(整个项目源码文件)都会受牵连，就会编译不过去。尽管这样，IDEA还是不告诉哪里有语法错误，建议在实际项目用eclipse进行编辑。管他香不香，用的舒服就好！

----
更多问题关注我的公众号：小码之光，**文章将在公众号首发**！
最后附上：
[小码CSDN](https://blog.csdn.net/Gobullin)
[博客园](https://www.cnblogs.com/coderma/)
微信公众号：小码之光
![小码之光](https://img-blog.csdnimg.cn/20200626115852678.jpg#pic_center)
  
 
