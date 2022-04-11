---
layout: post
title: markdown-preview缺少tslib模块解决方案
date: 2021-12-03 23:06:00
author: 牧之
tags: 
  - vim
subtitle:   ""
header-style: text
---


## 环境

- windows 10 1909
- vim-vi improved 8.2 ms-windows 64-bit gui version

## 缘起

安装markdown-preview插件后，使用时无论是使用快捷键还是命令，都没有任何反馈

## 排查

在vim命令行输入`messages`输出以下出错信息( 部分)：

```
......
[vim-node-rpc] rpc error: internal/modules/cjs/loader.js:883
[vim-node-rpc] rpc error: throw err;
[vim-node-rpc] rpc error: ^
[vim-node-rpc] rpc error:
[vim-node-rpc] rpc error: error: cannot find module 'tslib'
[vim-node-rpc] rpc error: require stack:
[vim-node-rpc] rpc error: - /users/dxm/.vim/bundle/markdown-preview.nvim/app/lib/app/index.js
[vim-node-rpc] rpc error: - /users/dxm/.vim/bundle/markdown-preview.nvim/app/index.js
......
```
可以看到是因为缺少tslib模块引起的错误，经查资料得知此模块用途超出我的知识范围qaq，
> tslib是一个开源的程序，能够为触摸屏驱动获得的采样提供诸如滤波、去抖、校准等功能。-百度百科

所以去插件的Github仓库去碰碰运气，终于在一条issue下找到解决方法：

## 解决

在插件目录下执行：

```
npm install
```
![npm-install](https://cloud.cseve.com/index.php/s/FfeeBwRiJaYYqqS/preview)

## 后记

其他操作系统或许可以尝试诸如`yarn install`等操作，当然，还是要根据出错信息
自己排查解决。

## 参考资料

1. https://github.com/iamcco/markdown-preview.nvim/issues/305
2. https://baike.baidu.com/item/tslib/722869?fr=aladdin
