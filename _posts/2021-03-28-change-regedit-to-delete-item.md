---
layout: post
title: 删除鼠标右键新建文件列表项
date: 2021-03-28 19:21:00
author: 牧之
tags: 
subtitle:   ""
header-style: text
---


## 一、缘起

安装完新软件后，软件会写入注册表一些文件，鼠标右键新建文件列表就会出现好多不常用的文件类型，对于我来说，刚刚安装的 PowerDesigner 软件就会在鼠标右键新建列表写入很多新类型文件，但我不想使用，在我想使用鼠标右键新建一个 word 文档的时候，看到一列长长的文件类型瞬间有种大海捞针的感觉，十分头疼，于是打算“干掉”这群不速之客。

## 二、解决方案

使用快捷键`win` + `r`, 打开运行窗口，输入`regedit`，打开注册表，在`计算机\HKEY_CLASSES_ROOT\`下，会有很多以点开头的目录，这是文件的拓展名。类似下图就是 Microsoft Word 软件的文件拓展名之一`.docx`，目录下的 ShellNew 就是今天的主角了。

![20210328190923018-ShellNew文件夹-江寻博客.png][1]

ShellNew 文件夹的作用就是在鼠标右键的新建列表添加该类型的新建文件。所以我们只需要找到想要删除的文件类型，删除 ShellNew 文件夹即可。比如想要删除这个选项，

![20210328191321713-鼠标右键-新建-要删除-江寻博客.png.png][2]

我们只需要查看这个文件的拓展名，不知道的话可以新建一个文件看一下

![20210328191602621-文件拓展名-江寻博客.png][3]

如果没有的话，你可能需要搜索一下如何显示文件拓展名的相关知识。

接下来，我们在注册表找到它

![20210328191744250-在注册表内-江寻博客.png][4]

我们只需要删除 ShellNew文件夹即可。此时右键新建文件列表已经没有这个选项了。

![20210328191852380-删除完的效果-江寻博客.png][5]

—— End ——


  [1]: https://blog.cseve.com/usr/uploads/2021/03/3277521391.png
  [2]: https://blog.cseve.com/usr/uploads/2021/03/3150981732.png
  [3]: https://blog.cseve.com/usr/uploads/2021/03/364889883.png
  [4]: https://blog.cseve.com/usr/uploads/2021/03/4099150816.png
  [5]: https://blog.cseve.com/usr/uploads/2021/03/2708912878.png