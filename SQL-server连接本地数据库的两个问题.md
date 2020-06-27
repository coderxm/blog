---
title: SQL server连接本地数据库的两个问题
date: 2020-05-23 05:46:14
author: coder小码
tags: SQLserver
categories: SQL
keywords: [SQLserver,数据库]
toc: true
---
#### SQL Server连接本地数据库时的异常
 作者：coder小码

---
最近想学点SQL server,几个月前下过，可中间电脑换过机名，重装过系统(电脑不是键盘一下没反应就是鼠标没反应)，充分暴露出windows的不稳定。这告诉我们：要早点和windows离婚吧，换一个漂亮又好用点的linux系统(关键是免费开源)，如果有钱可以跟风mac。哈哈！所以呢，系统里的环境变量全部没了，除了操作系统本身的变量外。经验告诉我们：换系统就是换血，把C盘的除系统外的渣渣都清除了，还好是其他盘的东西还在，不过又得手动配置她们的变量了。。。

---
#####  01 SQL SERVER初探
初入SQL SERVER的可能不知道有两种版本分类的SQL SERVER，那现在就普及一下。第一种是MSSQL SERVER,全称是Microsoft SQL Sever，开发版，目前的大型网站一般使用Oracle或者MSSQL，JSP.PHP.ASP都可以。一般是企业级的商务网站使用的。全功能SQL数据库服务器，从2017版开始，横跨任何平台，完全免费。第二种是Express ，商业免费，有对应的限制一般都用这个。是SQL SERVER的简洁版，可以这样说。

 但开始我也不懂啊，也没人叫我怎么玩哈，所以最近发现SQL不见了，就急忙下个SQL server2019最新版的玩一下。不行的是下载了6个多G，连带管理工具一起下(都是开热点的流量啊！啊啊！)，N久后，才下完！然后安装！！！N久。

起初是发现从前的2017版的没有了，主要是SSMS没有，SSMS是SQL SERVER Management Studio,SQL SERVER管理工具，用来管理数据库的，而我们下的是SQL SERVER的一个下载工具罢了。没SSMS还是玩不起来。

---
##### 02  第一个问题：配置管理器无法连接到 WMI 提供程序
 这个**问题**我记住你了，化成灰我都认得你！！
 
 ![配置管理器异常](https://img-blog.csdnimg.cn/20200521170345860.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)弄了我一整晚，网上都查遍了，每个有效的方法。现在给大家清楚讲一遍，按上面的说，WMI,（Windows Management Instrumentation 即windows 管理规范）是一项核
心的 Windows 管理技术；**用户可以使用 WMI 管理本地和远程计算机**。简单点，就是管本地和远程计算机的一个东西。有点内味了！！也就是说要这个服务来帮助SQL配置管理器管理计算机的，那怎么管呢？

有两种解决方法：要么是没权限，弄权限；要么是服务器真的不能访问了，解决服务器。很明显，连自己的本地的机子，还说无法访问，那就是没权限啦。查查了半天，说要弄一个NETWORK SERVICE的权限，也弄了没反应，估计还不够吧！之后又有其他办法，说进如："C:\Program Files (x86)\Microsoft SQL Server"里面，我的是这样的，里面是90‘100’120‘的数字文件夹(跟系统打交道的)，不是真正的SQL SERVER文件夹(有界面的那个)。

其中有一个shared文件夹里有150\Shared\sqlmgmproviderxpsp2up.mof这个文件。
![sql~mof](https://img-blog.csdnimg.cn/2020052117542694.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

我的是150/，可能不一样。之后在命令行输入：

> mofcomp "C:\Program Files(x86)\Microsoft
> SQLServer\150\Shared\sqlmgmproviderxpsp2up.mof"

结果：
![将本地数据放到SQL储存库中](https://img-blog.csdnimg.cn/20200521173114764.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
将本地数据放到SQL储存库中了，就表示能访问到。那mof是个什么东西呢！

![mof](https://img-blog.csdnimg.cn/20200521173617862.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

 反正就是微软瞎造的东西，跟配置有关。不管了！可以正常打开配置管理器，但是里面项目为空，啥也看不到呀！正常是这样的：

![正常](https://img-blog.csdnimg.cn/20200521174143779.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

但是右边什么也没有，而且，SSMS还是连不上本地的数据库实例。

---
##### 第二个问题：系统找不到指定的文件
GUI是这样的：
![系统找不到指定的文件](https://img-blog.csdnimg.cn/20200521174341368.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
本来是输入个本机名字就行了，可就是死活连不上。SSMS: 想玩我？没门！这个时候，还是用的2017的SQL配置管理器，2019的SQLEXPRESS，连2019的配置管理器都没有，当然弄不了了。那之前的努力都白搭，花了我N久弄完！

其实挺简单的，一步解决上面两个问题，还能使用最新的2019SQL SERVER。对啦，就是重新安装，不用开浏览器上什么官网，直接follow me。哈哈！

找到SQL SERBER的安装目录，就是那个有安装的SQL server2019：

---
 D盘文件夹：
 ![SQL文件](https://img-blog.csdnimg.cn/20200521180118799.PNG#pic_center)

sqlserver文件夹里是这样的：

![新的本地实例MSSQL1.5](https://img-blog.csdnimg.cn/20200521181435401.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

之后一路默认安装：

![SQL 安装中心](https://img-blog.csdnimg.cn/20200521180336817.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

---
安装期间会同时实例化本地的数据库，以windows管理员的身份管理，完成后就能看到开始菜单里有2019配置管理器了：

![开始菜单](https://img-blog.csdnimg.cn/20200521180652720.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

sercice服务里也会有SQL服务，之前是没有的，即使解决了第一个问题后。估计这就是第二个问题没解决的原因吧！没SQL server服务，就没得玩喽！



![SQLsever服务](https://img-blog.csdnimg.cn/20200521180951615.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

---
所以最后献上玩美结果：

![连上了本地](https://img-blog.csdnimg.cn/20200521181319650.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

哈哈，如果要用Network service权限解决的话请参考[另一篇](https://blog.csdn.net/qq_17532383/article/details/45542605?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522159005588419724811810680%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fblog.%2522%257D&request_id=159005588419724811810680&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~blog~first_rank_v2~rank_v25-7-45542605.nonecase&utm_term=sql%E6%97%A0%E6%B3%95WMI)
最后祝大家玩的愉快！！

---
最后附上：[小码csdn](https://blog.csdn.net/Gobullin)
[博客园](https://www.cnblogs.com/coderma)
微信公众号：小码之光
  
 ![小码之光](https://img-blog.csdnimg.cn/20200427213721746.jpg#pic_center)


---
