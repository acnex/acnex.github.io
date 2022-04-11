---
layout: post
title: 自适应图片排版
date: 2021-06-26 11:06:00
author: 牧之
tags: 
subtitle:   ""
header-style: text
---


### 代码

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width" />
    <title>T</title>
    <style>
        .images-box {
            padding: 0 0vw 2vw 0vw;
            font-size: 0;
            word-spacing: 0;
            letter-spacing: 1vw;
            line-height: 1vw;
        }

        .images-box a {
            display: inline-block;
            height: 30%;
            width: 30%;
            overflow: hidden;
            text-decoration: none;
            -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
        }

        .images-box a:only-child {
            height: initial;
            width: initial;
            max-width: 80%;
        }

        .images-box a:nth-child(1):nth-last-child(2) {
            width: 45%;
            height: 45%;
        }

        .images-box a:nth-child(2):nth-last-child(1) {
            width: 45%;
            height: 45%;
        }

        .images-box a:nth-child(1):nth-last-child(4) {
            height: 45%;
            width: 45%;
        }

        .images-box a:nth-child(2):nth-last-child(3) {
            height: 45%;
            width: 45%;
        }

        .images-box a:nth-child(3):nth-last-child(2) {
            height: 45%;
            width: 45%;
        }

        .images-box a:nth-child(4):nth-last-child(1) {
            height: 45%;
            width: 45%;
        }

        .images-box a img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
    </style>
</head>

<body>

    <div class="images-box">
        <a><img src="./1.jpg"></img></a>
        <a><img src="./1.jpg"></img></a>
        <a><img src="./1.jpg"></img></a>
        ...
    </div>
</body>

</html>
```
### 效果预览

!!!
二张：
<div class="images-box">
<a><img src="https://blog.cseve.com/usr/uploads/2021/06/797910524.jpg"></img></a>
<a><img src="https://blog.cseve.com/usr/uploads/2021/06/3548855972.png"></img></a>

</div>
<hr/>
四张：
<div class="images-box">
<a><img src="https://blog.cseve.com/usr/uploads/2021/06/3806743166.png"></img></a>
<a><img src="https://blog.cseve.com/usr/uploads/2021/06/2347798521.png"></img></a>
<a><img src="https://blog.cseve.com/usr/uploads/2021/06/1093068526.png"></img></a>
<a><img src="https://blog.cseve.com/usr/uploads/2021/06/550817487.png"></img></a>


</div>

<hr/>
六张：
<div class="images-box">
<a><img src="https://blog.cseve.com/usr/uploads/2021/06/3806743166.png"></img></a>
<a><img src="https://blog.cseve.com/usr/uploads/2021/06/2347798521.png"></img></a>
<a><img src="https://blog.cseve.com/usr/uploads/2021/06/1093068526.png"></img></a>
<a><img src="https://blog.cseve.com/usr/uploads/2021/06/550817487.png"></img></a>
<a><img src="https://blog.cseve.com/usr/uploads/2021/06/550817487.png"></img></a>
<a><img src="https://blog.cseve.com/usr/uploads/2021/06/550817487.png"></img></a>
</div>
!!!

### 参考

1. [纯 CSS 自适应九宫格图片格][1]


  [1]: https://blog.truimo.com/AutoImagesBox.html