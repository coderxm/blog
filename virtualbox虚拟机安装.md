---
title: virtualbox虚拟机安装
date: 2020-04-25 12:43:02
author: 小码
tags: 
    - ubantu
    - virtualbox虚拟机
categories: linux
keywords: [ubantu,linux,virtualbox,虚拟机]
toc: true
---
#### 用虚拟机virtualbox安装ubantu桌面系统

 - 下载ubantu镜像
 - 下载安装虚拟机
 - 新建一个虚拟电脑Linux01
 - 安装ubantu镜像
 - （网络设置）
 
---
##### 01 下载ubantu镜像
要想在虚拟机里玩ubantu，就要先准备好该系统的iso镜像文件，那么我们就直接到了官网去了

![官网](https://img-blog.csdnimg.cn/20200425111147300.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
可是我们点击下载后速度又慢了，比github还慢，原因就不说了。所以当然有更快的方法啦！不一定非要去国外的官网下载，国内的各大高校和巨头都有镜像站提供免费的镜像下载，这里就给大家推荐一番。

###### [阿里云开发者社区镜像站](https://developer.aliyun.com/mirror/)

![阿里镜像站](https://img-blog.csdnimg.cn/20200425111743145.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
第一个就是ubantu,这里可以下server或desktop都可以，反正又快又免费！哈哈

###### [浙大镜像站](http://mirrors.zju.edu.cn/)
 
 为什么选择浙江大学的镜像站呢？国内有很多这样的镜像站啊。。。。当然是快啦，相比较其他大学的站点，算是比较好了。

![浙大镜像站](https://img-blog.csdnimg.cn/20200425112624418.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

 我是在阿里云下的，起初弄不清server和desktop版，就先下了server版，结果就是疑惑了半天，也没出现漂亮的界面。
 ![命令行](https://img-blog.csdnimg.cn/20200425112906835.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
 

---

##### 02 安装oracle virtualbox虚拟机

这个就有点难下了，我没在镜像站里找，在网盘下的。(VMware需要许可证)这里大家可以搜一搜，分享[VM](https://pan.baidu.com/s/13mubMuemzTbLApTyxJXQVQ)

提取码：vz1h

下载好安装包后，打开就行了

![安装完成](https://img-blog.csdnimg.cn/20200425115703159.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

---
##### 03 新建虚拟电脑Linux01

点击新建，选择要安装的系统，之后就是一路默认。

![新建](https://img-blog.csdnimg.cn/20200425120535645.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
 内存最好配置在2G以上

![内存](https://img-blog.csdnimg.cn/20200425120650265.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

---
##### 04 安装ubantu镜像
虽然已经有一个虚拟电脑了(其实就是占用宿主机的磁盘空间)，这个时候只有硬件上的支持，还没有系统文件的调用。所以咋们进入启动Vbox界面的设置项

![设置](https://img-blog.csdnimg.cn/20200425121253258.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

红色箭头那点击进入，再点击注册项，即可从宿主机文件里选择下载好的ubantu镜像文件

![注册](https://img-blog.csdnimg.cn/20200425121517698.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
ok,配置好后，再启动虚拟电脑，就进入ubantu系统安装界面了，而不是命令行。

![ubantu界面](https://img-blog.csdnimg.cn/2020042512174573.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
```
 接下来就是安装了 
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200425122022310.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
 这里可以选择试用或者安装ubantu，安装后启动就直接进入虚拟电脑工作界面了。
 

![ubantu](https://img-blog.csdnimg.cn/20200425122834737.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
 界面还是很漂亮的，不过virtualbox是小型机，界面不能全屏，如果可能还是选VMware虚拟机吧，试过，感觉就是香！哈哈！

---
##### 05 网络设置
 
 这里就不过多讲了，建好后可以配置网络，有自己的cdn节点。推荐[程序羊](https://www.bilibili.com/video/BV1bA411b7vs)


---
附：[小码csdn](https://blog.csdn.net/Gobullin)


















