---
title: hexo常用操作以及注意事项
date: 2022-09-03 15:39:53
tags:
- 原创
- hexo
categories: hexo
description: 关于hexo常用操作的记录
---
## 新建文章

> 命令：`hexo new [layout] title`或 `hexo n [layout] title`

创建文章前要先选定模板，在hexo中也叫做布局。hexo支持三种布局（layout）：post(默认)、draft、page。我们先介绍如何使用已有布局，后面还将会介绍如何自定义布局。

在博客目录下输入以下命令时，会默认使用post布局，然后自动在`source\_posts`目录生成一个text1.md文件：

```bash
$ hexo n text1
```

当然你还可以指定布局：

```bash
$ hexo n [layout_name] draft1
```

该命令创建了一个使用特定布局的名为draft1的文章。

打开之前创建的text1.md文件，我们可以看到文章开头包含以下内容：

```yaml
---
title: text1
author: longpi1
tags: hexo
categories: blog
---
```

上面的内容在hexo被称作**Front-matter，实际上就是该文章的一些变量，用于实现一些特定的功能**。比如使`author: longpi1`，那么渲染后的文章中将显示文章作者为`longpi1`。



## 本地调试

启动hexo本地服务器`hexo server` 或 `hexo s`

```
$ hexo s INFO  Start processingINFO  Hexo is running at http://localhost:4000/. Press Ctrl+C to stop.
```

在浏览器输入 http://localhost:4000/ 进行预览，回到Git Bash输入`Ctrl+C`关闭本地服务器退出预览。

指定端口：
`hexo s -p 8080`

自定义 IP
服务器默认运行在 0.0.0.0，您可以覆盖默认的 IP 设置，如下：
`hexo server -i 192.168.1.1`



## 部署

`hexo d` 或 `hexo deploy`
`hexo d -g` 部署之前预先生成静态文件

### 关于部署后原来的CNAME文件被覆盖的问题

解决：CNAME,README,404.html都可以放在Hexo/source文件夹下，`hexo g`生成博客时会被原封不动的拷贝到public文件夹中，部署后自然就到了项目的根目录。