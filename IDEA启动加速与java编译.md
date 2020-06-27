---
title: IDEA启动加速与java编译
date: 2020-05-06 09:17:56
author: coder小码
tags: 
      - idea
      - java
categories: IDE
keywords: [idea,java]
toc: true
---
#### IJ IDEA启动加速与java编译

1.**启动加速** 
2.**java编译**


---

##### 01 启动加速

![tips](https://img-blog.csdnimg.cn/20200504113321417.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
忽然有一天IDEA说：你打开它“有点慢”，然后说：consider reducing the num of folder under antivirus protection. 这很有效！

 可能用IDEA的伙伴都会遇到这样的问题，这只是一个提示。那他说这很有效，到底个怎么有效呢？*consider reducing the num of folder under antivirus protection* 意思翻译过来 就是：考虑在病毒防护中排除启动器打开的文件。那具体咋弄？先看看官方解释：
 ![jetbrain](https://img-blog.csdnimg.cn/20200504114120578.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70)
再翻译一下：

> 某些防病毒软件可能会干扰IDE的构建过程，从而导致构建的运行速度大大降低。 在IDE中运行构建时，会在计算机上创建许多类文件。
> 如果您的防病毒软件启用了实时扫描，则防病毒软件可以在每次创建文件时强制停止构建过程，而防病毒软件会扫描该文件。
> 
> 如果您使用的是Windows Defender，则IDE会自动检查您是否启用了实时扫描，以及是否将扫描配置为处理IDE写入大量文件的目录。
> 
> IDE提供了一种可能性，可以从自动扫描中排除那些目录（此功能在2019.2+ IDE版本中可用）。
> 
> 如果您希望手动执行必要的配置，则可以按照以下步骤进行：
> 
>      点击开始按钮
> 
>      输入“ Windows安全性”
> 
>      点击“病毒和威胁防护”
> 
>      点击“病毒和威胁防护设置”下的“管理设置”
> 
>      如果需要，请向下滚动，然后单击“添加或删除排除项”
> 
>      对于通知中显示的每个文件夹，请按+按钮，从菜单中选择“文件夹”，然后选择该文件夹。



 官方都非常详细地解释了一番，打开IDEA慢的原因受到电脑自带的杀毒软件的影响，使IDEA不能构建文件。


---

##### 02 java编译
有些刚玩IDEA的小伙伴在创建java文件后不知如何编译，大家都知道点击RUN编译运行就可以了，但那是编译带运行输出结果，如果是没有主函数main()呢，只是想编译呢？

 接下来我们介绍三种编译方式：

>  Compile、Make和Build的区别

 
针对开发工具，一般都有Compile、Make和Build三个菜单项，完成的功能的都差不多，但是又有区别。编译，是将源代码转换为可执行代码的过程。编译需要指定源文件和编译输出的文件路径（输出目录）。Java的编译会将java编译为class 文件，将非java的文件（一般成为资源文件、比如图片、xml、txt、poperties等文件）原封不动的复制到编译输出目录，并保持源文件夹的目 录层次关系。
 
在Java的集成开发环境中，比如Eclipse、IDEA中，有常常有三种与编译相关的选项**Compile、Make、Build**三个选项。这三个选项最基本的功能都是完成编译过程。但又有很大的区别：

> 1、Compile：只编译选定的目标，不管之前是否已经编译过。
  
> 2、Make：编译选定的目标，但是Make只编译上次编译变化过的文件，减少重复劳动，节省时间。（具体怎么检查未变化，这个就不用考虑了，IDE自己内部会搞定这些的）

> 3、Build：是对整个工程进行彻底的重新编译，而不管是否已经编译过。Build过程往往会生成发布包，这个具体要看对IDE的配置了，Build在实际中应用很少，因为开发时候基本上不用，发布生产时候一般都用ANT等工具来发布。Build因为要全部编译，还要执行打包等额外工 作，因此时间较长。

 

![编译](https://img-blog.csdnimg.cn/20200504115100594.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
·
---
··················································END························································

以后编译不用迷迷糊糊的去编译啦！对于IEAD的启动Tips，有些人可能会厌烦，但作为一款风靡全球的智能开发软件，还是对新入门的小鸟有很大帮助的，用习惯了，就想说：“**真香**！”

---
 最后写作不易：关注我吧(小码之光)
[博客](https://www.maliaoblog.cn)：www.maliaoblog.cn
![小码之光](https://img-blog.csdnimg.cn/20200504120421301.jpg#pic_center)


----
