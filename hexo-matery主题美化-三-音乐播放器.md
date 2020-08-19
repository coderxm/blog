---
title: hexo-matery主题美化(三)-音乐播放器
date: 2020-08-09 16:39:30
author: 小码
tags: [matery主题,音乐播放器]
categories: 网站运维
keywords: [hexo-matery,音乐播放器]
summay: []
comments: false
toc: true
---
#### hexo-matery主题美化(三)-音乐播放器

##### 配置音乐播放器

要支持音乐播放，在主题的 `_config.yml` 配置文件中激活music配置即可：

```yaml
# Whether to display the musics.
# 是否在首页显示音乐.
music:
  enable: true
  title: 非吸底模式有效
  show: 听听音乐
  autoHide: true    # hide automaticaly
  server: tencent   #require	music platform: netease, tencent, kugou, xiami, baidu
  type: playlist    #require song, playlist, album, search, artist
  id: 7660234225     #require	song id / playlist id / album id / search keyword
  fixed: true       # 开启吸底模式
  autoplay: false   # 是否自动播放
  theme: 'blue'     #歌词的颜色
  loop: 'all'       # 音频循环播放, 可选值: 'all', 'one', 'none'
  order: 'random'   # 音频循环顺序, 可选值: 'list', 'random'
  preload: 'auto'   # 预加载，可选值: 'none', 'metadata', 'auto'
  volume: 0.7       # 默认音量，请注意播放器会记忆用户设置，用户手动设置音量后默认音量即失效
  listFolded: true  # 列表默认折叠
```

> `server`可选：`netease`（网易云音乐），`tencent`（QQ音乐），`kugou`（酷狗音乐），`xiami`（虾米音乐），
>
> `baidu`（百度音乐）。
>
> `type`可选：`song`（歌曲），`playlist`（歌单），`album`（专辑），`search`（搜索关键字），`artist`（歌手）
>
> `id`获取示例: 打开网易云音乐，选择喜欢的歌单，然后点击分享,生成插件外链

这就是歌单的id，文件里默认设置的歌单其实也还不错。如果以后继续添加歌曲，更新了歌单，我亲自试过，`Aplayer`插件也会更新，之前的16首现在加了三首有19首。看了一些人的文章，有的人说不会更新，不知道他有没有试过。对了，如果打开博客播放器插件加载不出来，可能是网速的原因，刷新一下就好，也有可能是没配置好，多看看文章就行。

参考资料：
[弗兰克的猫-hexo-matery主题配置](https://www.cnblogs.com/mfrank/p/12830097.html#autoid-0-4-0)

[new落花-Aplayer插件](https://www.cnblogs.com/fby698/p/12663089.html)