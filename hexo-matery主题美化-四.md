---
title: hexo-matery主题美化(四)
date: 2020-08-19 08:05:52
author: coderxm
tags: [matery,美化]
categories: 网站运维
keywords: [matery,博客美化]
summay: [matery主题美化]
comments: false
toc: true
---
#### hexo-matery主题美化(四)

#### 目录：

> 前言
>
> 去掉banner的颜色动画
>
> 添加背景壁纸
>
> 修改滑动条
>
> 修改导航栏、页脚及文章卡片标签的颜色
>
> 修改目录样式


##### 前言：

这是最后一篇关于hexo-matery博客美化的文章了，大部分都是前端的东西，所以没啥好讲的，对我来说后端更侧重一点，这些天都没怎么写Java代码了。离前一篇博客美化文章已过去一个星期了，因为我回了趟老家，住了一个星期，心里感觉很复杂。我本身技术并不是很强，每天都要实实在在的学习知识，家里条件不好，以后的路真的难走！加油吧！

##### 一、去掉banner的颜色动画

有的同学可能不喜欢banner的颜色遮罩，特别是在banner图片的颜色和动画颜色一样时，表现不出图片的美观。去掉后放一张高清小姐姐大图，博客访问量一下迅速爆炸！听我的准没错，那如何去掉这个烦人的彩色动画呢？跟着我：在theme主题目录下，找到`matery.css`文件,`ctrl+F`快捷键查找`.bg-cover:after`，注释掉即可。

```css
/* .bg-cover:after {
    -webkit-animation: rainbow 60s infinite;
    animation: rainbow 60s infinite;
} */
```



##### 二、添加背景壁纸

同样在matery.css文件下查找body样式,修改如下：

```css
body {
    /* background-color: #eaeaea; */
    background: linear-gradient(60deg, rgba(255, 165, 150, 0.5) 5%, rgba(0, 228, 255, 0.35) ) 0% 0% /     cover, url("https://x.png"), url("https://x.jpg") 0px 0px;
    background-attachment: fixed;
    margin: 0;
    color: #7F95D1;
}
```

如果不想要图片，去掉即可，比如：

```css
body {
    cursor:url(/cursor.svg),auto;
    background: linear-gradient(60deg, rgba(255, 165, 150, 0.5) 5%, rgba(0, 228, 255, 0.35) );
    margin: 0;
    color: #34495e;
}
```



##### 三、修改滑动条（没试过，好像没用）

说是说修改滑动条，但是不需要太麻烦，在matery.css中添加样式即可：

```css
/* 滚动条 */
::-webkit-scrollbar-thumb {
    background-color: #FF2A68;
    background-image: -webkit-linear-gradient(45deg,rgba(255,255,255,.4) 25%,transparent 25%,transparent 50%,rgba(255,255,255,.4) 50%,rgba(255,255,255,.4) 75%,transparent 75%,transparent);
    border-radius: 3em;
}
::-webkit-scrollbar-track {
    background-color: #ffcacaff;
    border-radius: 3em;
}
::-webkit-scrollbar {
    width: 8px;
    height: 15px;
}
```


##### 四、修改导航栏、页脚及文章卡片标签的颜色

同样的操作，在matery.css中找到`.bg-color`,修改即可：

```css
.bg-color {
    background-image: 
    linear-gradient(to right, #3f1b07 0%, #3f1b07 100%);/*咖啡色*/
}
```


##### 五、修改目录样式（没试过）

在`themes\Matery\layout\_partial\post-detail-toc.ejs`，在这里修改:

```css
.toc-widget {
    width: 345px;
    padding-left: 20px;
    background-color: rgb(255, 255, 255,0.7);
    border-radius: 10px;
    box-shadow: 0 10px 35px 2px rgba(0, 0, 0, .15), 0 5px 15px rgba(0, 0, 0, .07), 0 2px 5px -5px rgba(0, 0, 0, .1) !important;
    }
```
---
公众号：小码之光
[个人站点](https://index.maliaoblog.cn/)  https://index.maliaoblog.cn
