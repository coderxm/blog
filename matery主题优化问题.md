---
title: matery主题优化问题
date: 2020-04-09 20:32:23
author: 码里奥
tags: 
    - 优化
    - bug问题
categories: 网站运维
keywords: [hexo,matery,优化,bug问题]
toc: true
---
# matery主题优化时解析出bug

 - matery是个好的主题这个我就不详细地说了，但是优化也难
 - 越好的主题、越丰富的主题，插件越多，配置越多，就容易出错
 - 最要命的是这种静态网页的部署还要用最原始的方法进行，先在命令行生成静态文件，然后发送给要命的github
 - 总之bug数不胜数，大部分出错的原因基本都一致，无非就是在yml文件里乱弄出的bug
 - 但是我优化主题时碰上了难得的bug，就分享给大家，省的大家走弯路
 
 ## page.*.ForEach is not a function后接一大片路径

![page bug](https://img-blog.csdnimg.cn/20200409184120112.JPG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
这里的*就是图中的categorioes,我叫他page bug。就光看那么多行根本摸不着头脑，想着是肯定是配置出了问题，于是就打开配置文件查看。其实这个问题很少见，一般都不是config配置文件的问题。弄了半天，谁也没想到是页面文件categorioes里的index.md文件有问题。我的配置如下：
![index.md配置](https://img-blog.csdnimg.cn/2020040918524995.JPG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
一般都很少进入里面配置什么的，但是为了优化主题，让它更好看，就进入里面瞎搞乱改，网上也没什么指导如何优化配置的好文章，所以自然会遇到稀奇bug。上面的配置就出错了，出在categorioes的属性的配置，用这个主题，categories文件(需要事先new一个才有)好像不准添加属性，换成小写c也不行，之后做了如下更改。

![删除属性后](https://img-blog.csdnimg.cn/20200409190637167.JPG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
去掉那个C后，那个bug就没了，一切顺畅生成页面。四不四很无语，就这个鬼东西弄了一整天，不是说，就是这个静态页面配置太苛刻了，用md和yml去写，缩进不对都是要出错的。这给广大怀着博客梦的IT客破了一大盆冷水，太难了！![🆗](https://img-blog.csdnimg.cn/20200409202700413.JPG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)

我还试了在其他页面文件中的md文件里设置categories属性，结果都🆗。。。

![tags文件里md文件配置了没问题](https://img-blog.csdnimg.cn/20200409191736240.JPG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
tags文件里md文件配置了没问题,我是说categorioes属性，图片里没有，配置tags属性也没事(没打双引号都没事)。

```
那到底是什么样的优化造成的魔王级的bug呢？
```
hexo主题本来就不会自带页面的配置优化，需要自己弄，就matery来说吧，除了归档页面，其他的页面都不会出现和用这个主题的人一样相似布局，所以接下来就告诉大家怎么弄。
```
就是在index.md文件里配置，只需添加如下几行：
在categories里：type: 'categories'
				layout: 'categories'		(注意：后空格)
其他类推
```
这样在各个页面就有自己配置了，如下

![配置了friendst页面](https://img-blog.csdnimg.cn/20200409195433492.JPG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
这是弄好了友链页面后的效果，能看到基本上是有个排版了。但框框内却出现了乱码，很巧的是出现乱码的地方都是汉字该出现的地方。所以大家应该知道了，又是编码的问题。这次我们还用notepad++更改编码友链的josn格式,如果没有notepad++或不知道如何更改编码格式，请参考[批处理文件编码出错](https://blog.csdn.net/Gobullin/article/details/105349236)原来友链的josn的编码格式为Ansi,我们需要utf-8格式。欧克，行了，如下：![乱码解决](https://img-blog.csdnimg.cn/20200409200717571.JPG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
### 谈谈hexo

hexo这样的博客虽然用了很流行的框架，但部署起来还是很费劲，就是用上去很费劲，powerful的博客框架还是太少了，什么都追求免费服务，哪有这么样的好事，这就导致了开发出优质的框架的人太少了。现在大牛的程序员都快是古董，做个IT技术更倾向于商业化，应用型。以上就是分享，另附[个人博客](https://www.maliaoblog.cn)




