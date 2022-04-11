---
layout: post
title: "Windows 10 为软件设置快捷键"
subtitle: "" 
date: 2020-07-04 10:40:07
author: "muzhi"
header-style: text
tags:
  - Windows
---

电脑里面有一个绿色截图软件，双击就会触发截屏，但是没有快捷键，在快捷方式中设置的快捷键也不生效。这样的情况有以下几个解决方法：

1、任务栏：把软件拖动到任务栏，任务栏会自动分配快捷键，`win + 数字`，查看软件在第几个，把数字改成几即可；

2、在`C:\Users\用户名\AppData\Roaming\Microsoft\Windows\Start Menu\Programs`目录下创建软件的快捷方式，在此快捷方式右键属性设置快捷键即可生效。