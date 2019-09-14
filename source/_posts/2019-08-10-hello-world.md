---
title: Hello World 
author: vear
avatar: https://cdn.jsdelivr.net/gh/vearvip/cdn@v0.0.12/img/avatar/avatar.webp
authorLink: /
authorAbout: vear
authorDesc: 唯二
categories: 技术
date: 2019-08-10 12:00:01
comments: true
keywords: Sakura
description: 你好世界
photos: https://cdn.jsdelivr.net/gh/vearvip/cdn@v0.0.12/img/article/古建筑少女.webp
---

# Hello World
## 你好世界

 初次见面，你好，`hexo`。采用上古模板语法`ejs`，其实蛮不喜欢/习惯的，奈何架不住`hexo`生成的静态网页可以直接部署到**git pages**上，可以省钱啊，其次`hexo`又有很多优质主题，只能说**真香**！

 见过了`vue`的`template`语法，`react`的`jsx`语法，难免吐槽一番，对这种学生时代学习`nodejs`时，连老师都鄙视的语法实在提不起兴趣。`ejs`模板渲染可能是沿袭了`jsp`和`php`的习惯吧，真的是又丑又难以阅读，还不如用[art-template](https://github.com/aui/art-template)，明显可读性更高一点，写起来也像`angular`和`vue`。

> 贴一段art的模板代码

```html
<!--layout.art-->
<!doctype html>
<html>
<head>
    <meta charset="utf-8">
    <title>{{block 'title'}}My Site{{/block}}</title>

    {{block 'head'}}
    <link rel="stylesheet" href="main.css">
    {{/block}}
</head>
<body>
    {{block 'content'}}{{/block}}
</body>
</html>

```
