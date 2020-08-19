---
title: hexo-matery主题优化(二)
date: 2020-08-06 12:11
author: 小码
tags: [matery,博客美化]
categories: 网站运维
keywords: [hexo-matery,博客,美化]
summay: []
toc: true
comments: false
---
### hexo-matery主题优化(二)

#### 目录：

- hexo搜索
- hexo代码高亮
- 消除文章toc目录的那一竖杠杠
- 去掉友链下那不必要的一栏空白
- 最后

前段时间，我好像写过一篇文章讲hexo-matery主题的配置优化，隔了很久，自己都忘了，应该是第一次安装主题的时候。那现在有些一篇关于这样的文章帮助大家继续增强美化自己的博客，因为本人最近也在做这件事，搭博客已经3个月了，选了喜欢的主题，却还是有一点点不满意，虽然创建主题的都是大佬，但是也有瑕疵的地方。更头疼的是，到最后也没人来告诉我们怎么把我们的博客做的漂亮一点，还是要自己来亲手改改，直接弄成博客是自己亲生的一样！到时候也能吹吹！这次不介绍太多，怕一下弄不过来，主要就讲最近接触过的。

#### hexo搜索

如果你已经做了这个搜索可以跳过，没有就一起干！过程非常可乐，呃，是非常简单！前提是使用的是hexo主题，配置了相应的环境。主题最开始弄下来是没有搜索插件的，需要下载，接下来你懂的，用npm包管理工具下载插件(如果不会用，可以搜索相应的文章看看，有需要会专门讲一下npm是何物，不会有同学还没安装好npm吧？不会吧！不会吧！)。进入到当前博客根目录下，在命令行里：

```js
npm i hexo-generator-search -s
```

就这样下好了！同时需要再当前根目录配置文件中添加配置：

```yaml
#search
search:
  path: search.xml
  field: post 
```

#### hexo代码高亮

还是不要用主题里的高亮了，enable就false掉，还是同样的“骚操作”，下一个代码高亮的插件，这里用hexo-prism-matery,相同的手法下载下来后，在根目录下的配置文件里添加：

```yaml
prism_plugin:
  mode: 'preprocess'  # preprocess/realtime
  theme: 'tomorrow'
  line_number: true #default false
  custom_css: #
```

#### 消除文章toc目录的那一竖杠杠

修改前是这样的：

![toc那一杠](https://img-blog.csdnimg.cn/20200806121739895.JPG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
如果你发现文章的toc目录有一条竖杠，不好看，那么就去掉。之前toc目录一直是这样的，我也不想要了。做博客开始的时候发现了，没太在意，终究是影响了美观。现在就要把目录弄得正常点。来到主题目录下，找到source目录，找到lib目录，里面也是一些css和js文件。其中找到tocbot文件夹，打开它的css文件，找到toc-link::before

```css
.toc-link::before{
    background-color:#EEE;content:' ';
    display:inline-block;height:inherit;/*left:0;*/
    margin-top:-1px;
    position:absolute;
    width:0px;   /*之前是2px*/
}
```

里面可能很乱，就一两行代码，找到后将width值改成0就行了。另外解析的文章目录不完整可能是标题有些不支持：

```yaml
# 是否激活文章 TOC 功能，并配置TOC支持选中哪些标题类型，这是全局配置。
# 可以在某篇文章的 Front-matter 中再加上`toc: false`，使该篇文章关闭TOC目录功能
toc:
  enable: true
  heading: h2, h3, h4, h5, h6  #选中除h1以外的标题，之前没有h6
  collapseDepth: 0 # 目录默认展开层级
  showToggleBtn: true # 是否显示切换TOC目录展开收缩的按钮
```

#### 去掉友链下那不必要的一栏空白

修改前：

![空白栏](https://img-blog.csdnimg.cn/20200806121702255.JPG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dvYnVsbGlu,size_16,color_FFFFFF,t_70#pic_center)
这个也简单，不必过于头疼！因为我已经改好了，直接卖就是了，白给不要钱！

```
<div class="card">
   <!--<div class="card-content">
		<%- page.content %>
       </div>-->
 </div>
```

友链下的那栏不必要的空白着实凸显了它的不必要性，所以我们要去掉它。直接把它的代码给注释掉，找到layout文件夹下的friends.ejs文件。hexo引擎渲染该文件生成html文件，变成了友链页面，其中友链的那一片作为一个模块卡片，valine留言板及空白一栏也是，空白的就是什么也没有，很容易发现，注释即可。

#### 最后

以后还会继续更新站点，如果想看总体的效果就访问我的网站吧！最近的美化优化了很多，变化也很大！如果想深入了解就上公众号吧，**小码之光**，加群交流也行。后续会持续跟大家讲博客美化。

---
公众号：小码之光

