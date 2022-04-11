---
layout: post
title: "鼠标右键增加sublime打开"
subtitle: "" 
date: 2022-02-20 12:43:44
author: "muzhi"
header-img: "img/in-post/post-edit-with-sublime.png"
header-mask: 0.4
tags:
  - normal
---

新建文件

```sh
Windows Registry Editor Version 5.00
[HKEY_CLASSES_ROOT\*\shell\SublimeText]
@="Edit with Sublime"
"Icon"="D:\\Program Files\\Sublime Text\\sublime_text.exe,0"
[HKEY_CLASSES_ROOT\*\shell\SublimeText\command]
@="D:\\Program Files\\Sublime Text\\sublime_text.exe %1"
[HKEY_CLASSES_ROOT\Directory\shell\SublimeText]
@="Edit with Sublime"
"Icon"="D:\\Program Files\\Sublime Text\\sublime_text.exe,0"
[HKEY_CLASSES_ROOT\Directory\shell\SublimeText\command]
@="D:\\Program Files\\Sublime Text\\sublime_text.exe %1"

````

命名为`Edit_with_Sublime.reg`，双击运行即可。
