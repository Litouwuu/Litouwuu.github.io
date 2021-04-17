---
title: 使用hexo部署blog
date: 2020-05-27 11:17:12
categories:
- hexo 网站部署
tags:
- hexo
---

本文为刚开始建立网站时所写。由于边写边干，有明显的逻辑不清。主要目的在于记录和方便回看。

# 1. 从git安装到部署hexo

根据知乎[直上云霄](https://www.zhihu.com/people/fang-ze-hua-56)的回答：[hexo超完整的搭建教程，让你拥有一个专属个人博客](https://zhuanlan.zhihu.com/p/44213627)进行部署。参考了customize之前的内容，未设置个人域名。`（该文章中还有关于git分支进行多终端工作的部分，在更换电脑后会用到）`

搭建时主要内容包括：

- 安装git、node.js、hexo
- GitHub创建个人仓库
- 生成SSH添加至GitHub
- 将hexo部署至GitHub
- 设置个人域名
- 发布文章

该回答还有关于hexo的基本配置，更换主题，实现多终端工作和添加各种功能，包括搜索的SEO，阅读量统计，访问量统计和评论系统等的内容，以后仍需参考。

<!--more-->

# 2. 主题设置等

参考[吴润](https://www.zhihu.com/people/wurun)的回答：[GitHub+ Hexo搭建个人网站详细教程](https://zhuanlan.zhihu.com/p/26625249)，同样也很详细。

# 3. 参考hexo官方文件

[点击这里](https://hexo.io/zh-cn/)。内容包括安装、使用方法、命令、主题等。

# 4. 添加分类及标签

是针对主题的config设置，参考回答：[Hexo使用攻略-添加分类及标签](https://www.jianshu.com/p/e17711e44e00)。

# 5. 更多个性化设置

主要参考文章[hexo的Next主题详细配置](http://www.360doc.com/content/19/0418/20/22888630_829741117.shtml)。

使用到的内容包括：

1. 头像设置 Sidebar Avatar
2. 添加搜索功能
3. 添加阅读全文按钮
4. 设置文章字体的颜色、大小、居中（使用html语法）

## 5.1 取消网站自带的文章目录编号

主题配置文件——toc——number改成false

## 5.2 字数统计和阅读时长功能

- 安装插件

`npm install hexo-symbols-count-time --save`

- 修改**站点**配置文件

```symbols_count_time:
 #文章内是否显示
  symbols: true
  time: true
 #网页底部是否显示
  total_symbols: true
  total_time: true
```

- 修改**主题**配置文件

```symbols_count_time:
  separated_meta: true
  #文章中的显示是否显示文字（本文字数|阅读时长） 
  item_text_post: true
  #网页底部的显示是否显示文字（站点总字数|站点阅读时长） 
  item_text_total: false
  #Average Word Length (chars count in word)
  awl: 4
  #Words Per Minute
  wpm: 275
```

## 5.3 Next主题颜色

[详细教程](https://www.jianshu.com/p/ad0d867a8cb6)。主要是不喜欢目录中，选中部分变成了红色。

`hexo/themes/next/source/css/_variables/base.styl`找到Colors

```php
// colors for use across theme.
// --------------------------------------------------
  $whitesmoke   = #f5f5f5
  $gainsboro    = #eee  //这个是边栏头像外框的颜色，
  $gray-lighter = #ddd  //文章中插入图片边框颜色
  $grey-light   = #ccc  //文章之间分割线、下划线颜色
  $grey         = #bbb  //页面选中圆点颜色
  $grey-dark    = #999
  $grey-dim     = #666 //侧边栏目录字体颜色
  $black-light  = #555 //修改文章字体颜色
  $black-dim    = #333
  $black-deep   = #495a80  //修改主题的颜色，这里我已经改成老蓝色了。
  $red          = #ff2a2a
  $blue-bright  = #87daff
  $blue         = #0684bd
  $blue-deep    = #262a30
  $orange       = #F39D01 //浏览文章时，目录选中的颜色
```

