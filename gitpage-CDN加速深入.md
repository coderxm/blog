---
title: gitpage CDN加速配置与深入
date: 2020-04-21 12:09:58
author: 小码
tags: 'github page'
categories: 网站运维
keywords: [CDN,github page,aliyun]
toc: true
---
 ### github page cdn加速服务深入了解

 - CDN介绍
 - CDN提供商
 - github page cdn加速服务配置
 - CDN加速服务深入
 
#### CDN介绍
CDN的全称是Content Delivery Network，即内容分发网络。CDN是构建在现有网络基础之上的智能虚拟网络，依靠部署在各地的边缘服务器，通过中心平台的负载均衡、内容分发、调度等功能模块，使用户就近获取所需内容，降低网络拥塞，提高用户访问响应速度和命中率。CDN的关键技术主要有内容存储和分发技术.....

上面是百度的介绍，啰嗦了一大堆，说白了就是让坐在电脑前的用户就近的获取需要的网络资源，而不用跑去访问遥远的服务器了。既然这么好，那就用呗！国内外都有一些这样的CDN服务提供商，但是大家都知道，访问外面的网络很费劲的。国内的一些CDN提供商也有不少，服务也不错，就给大家推荐一下。

#### CDN提供商
###### 阿里云CDN/DCDN全站加速
![阿里云CDN](https://img-blog.csdnimg.cn/20200421103618200.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)阿里云的CDN加速服务应该算是不错了，支持国内外和全球加速，这里选择全站加速会比较好一点。

##### 腾讯云CDN
巨头们总是这么滴强。。。腾讯云内同样提供比较哟西的CDN加速服务，提供商不一样，可能CDN操作的流程会略有不同。
![腾讯CDN](https://img-blog.csdnimg.cn/20200421104213353.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
##### 又拍云CDN
又拍云服务提供商也还行吧，反正试了下没啥效果，这里最好在域名提供商哪里选择CDN服务。
![又拍云CDN](https://img-blog.csdnimg.cn/20200421104446548.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
#### Github page cdn配置
在没有CDN的时候是这样的
![无CDN测速](https://img-blog.csdnimg.cn/20200421104655773.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)火红的大火鸡，非常差的访问去访问github节点。之后我选择阿里云的CDN去加速访问，在这之前可能要准备一个域名来操作啦。

现在我们进入阿里云的CDN，在域名管理处添加要加速的域名，如'www.maliaoblog.cn',这时候会提示没有备案，不用管，继续操作。在源站信息配置上，有三种选择，分别是OSS，域名，IP，如果你还填要加速的域名的话，显然会有重定向的麻烦，所以这里的源站在阿里云帮助文档里就讲了，源站就是github page服务器的域名或IP地址，这里还没有涉及到回源host的设置，大家尽管放心操作。之后在端口处选择443端口（以https协议访问，需要添加Https证书，如SSL的），加速区域选不包含中国大陆的，即海外节点加速，最后点击下一步。

![CDN配置](https://img-blog.csdnimg.cn/20200421110442442.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
到这里基本上就完成了，返回的时候刷新一下，能看到CNAME地址！需要在域名解析到这个CNAME地址。

![CDN运行正常](https://img-blog.csdnimg.cn/20200421111013463.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)只有解析到这个CNAME地址后，过几分钟，阿里云才能进行CDN加速服务。之后以这个加速域名去测速，速度就会提升了。注意，是以这个加速了的域名访问，那访问的就是阿里云帮我们提供的CDN节点，那当然会更快啦。

#### CDN加速服务深入

其实也没有多大的深入，就是在弄明白一个问题：github page还需要自定义域名吗？我们加没加速对博客站点的访问？

##### ping了一下，没加速对github.io的访问
![io还是原样](https://img-blog.csdnimg.cn/20200421112042708.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
github.io为美国的节点，直接访问当然没多快呀，如果ping加速域名的话，会访问阿里美国的CDN的节点，如果要回源的话，访问的请求会从节点发送出去。这就等于加速了从电脑前的客户所在地到节点该段的速度，走的是访问CDN节点的路线。

![流程图](https://img-blog.csdnimg.cn/2020042111291429.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)接着我再以加速域名测速，肯定是红色少了

![鸡儿绿了](https://img-blog.csdnimg.cn/20200421113044946.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
访问请求最终还是要得到最后的服务器的回应，也就是给我们网页资源。为此我又进行了测试。

###### 路由测试
![路由测试](https://img-blog.csdnimg.cn/20200421115105784.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
###### DNS测试
![DNS测试](https://img-blog.csdnimg.cn/202004211152004.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)如果加速域名DNS解析到github.io的话，github.io又有节点，那整个访问就快了。真的是这样的吗？还要不要.io自定义域名呢？page通过产生的github.io就可以访问到博客，自定义域名只是放到另一个展示(published)的地方(site)，那既然我们需要买域名去覆盖，那就要解析一个到github.io的CNAME的记录了。这么多，浏览器可能产生重定向的问题，以至于要不断刷新页面。但可以用一下，至少不要跑老远去DNS解析，输入域名，浏览器就老老实实交出页面啦。
[小码CSDN博客](https://blog.csdn.net/Gobullin)

