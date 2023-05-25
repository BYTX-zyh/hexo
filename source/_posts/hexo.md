---
title: hexo
date: 2023-05-23 19:15:36
tags:
    - hexo
categories: 博客
---

## 安装 hexo

关于安装详细查看[此处](https://hexo.io/zh-cn/docs/#安装)，需要的依赖包括有：

- Node.js (Node.js 版本需不低于 10.13，建议使用 Node.js 12.0 及以上版本)
- Git

而后使用npm安装hexo即可。

## 建站与站点文件夹概述

安装完成后，使用如下命令创建新的站点：

```shell
$ hexo init <folder>
$ cd <folder>
$ npm install
```

新建站点的目录内容大致如下：
```shell
.
├── _config.landscape.yml
├── _config.next.yml
├── _config.yml
├── db.json
├── node_modules
├── package-lock.json
├── package.json
├── public
├── scaffolds
├── source
├── themes
└── yarn.lock
```

其中`config.yml`为站点配置文件，`_config.next.yml`为主题 next的配置文件，`source`目录下为源文件，而`themes`目录下为博客主题。

## 安装主题

通过搜索关键词 hexo themes或者在[hexo主题](https://hexo.io/themes/)中查看选择合适的主题，并根据其对应的readme文件进行安装与配置。

## 配置

在hexo中，配置文件通常需要两个，分别为*站点*配置文件与*主题*配置文件，站点配置文件一般为`_config.yml`,主题配置文件一般为`_config.themeName.yml`(例如`_config.next.yml`)，且主题配置的优先级高于站点配置。

> 站点配置查看[此处](https://hexo.io/zh-cn/docs/configuration)了解详细信息。


## hexo命令

hexo 通常具有如下一些常用命令。

> 官方文档查看[此处](https://hexo.io/zh-cn/docs/commands)。

```shell
hexo init [folder] # 新建站点
hexo new [layout] <title> # 新建一篇hexo文章
hexo generate / hexo g # 生成静态文件
hexo server / hexo s # 启动hexo服务器
hexo deploy / hexo d # 部署网站
hexo clean # 清除缓存文件
```
