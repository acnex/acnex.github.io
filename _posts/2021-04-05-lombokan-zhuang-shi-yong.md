---
layout: post
title: lombok 安装使用
date: 2021-04-05 12:04:00
author: 牧之
tags: 
  - Java
  - Maven
subtitle:   ""
header-style: text
---


## lombok 简介

> Lombok 是Java语言编程中可以使用的一种工具，它可用来帮助开发人员减少编写一些可以机械完成的代码，尤其是对于简单的 Java 对象（POJO）。它通过注解实现这一目的。

比如：

```java
public class Mountain{
    private String name;
    private double longitude;
    private String country;
}
```

要生成这个对象的 get、set方法，有参构造、无参构造器等，都可以通过简单的注解实现。

```java
@Data // 只添加这一个注解
public class Mountain{
    private String name;
    private double longitude;
    private String country;
}
```

只添加`@Data`这一个注解，就可以自动生成该类的get、set、equals方法等

当然，也有`@AllArgsConstructor,@NoArgsConstructor,@Getter,@Setter`等注解。

## 使用方法

1、安装 IDEA 的 lombok plugin 插件

插件安装：`File-Settings-Plugs-Browse repositories...`搜索安装即可

> 可能由于我的 IDEA 版本较旧，安装时搜索不到这个插件，可以到网上下载后安装
>
> 地址：https://plugins.jetbrains.com/plugin/6317-lombok/versions

2、引入maven依赖

```xml
<!--lombok-->
<dependency>
  <groupId>org.projectlombok</groupId>
  <artifactId>lombok</artifactId>
  <version>1.18.6</version>
  <scope>provided</scope>
</dependency>
```

3、在需要添加相关方法的类上加相关注解

---End---