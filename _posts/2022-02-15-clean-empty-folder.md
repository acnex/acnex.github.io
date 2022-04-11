---
layout: post
title: "清理空文件夹"
subtitle: "" 
date: 2020-08-13 10:43:47
author: "muzhi"
header-style: text
tags:
  - Windows
---

这一段用来清理空文件夹的脚本

## 环境

操作系统：Windows

## 步骤

新建文本文件，粘贴以下文本，另存为所有，文件名为 xxx.cmd，双击运行即可。

```shell
@echo off

Cd /d %~dp0

If not "%1" == "" cd /d %1

Echo Current directory: %cd%


For /f "delims=" %%a in ('dir . /b /ad /s ^|sort ' ) do rd /q "%%a" 2>nul
Pause
```