---
title: java语言介绍
date: 2019-08-01
categories: 
- 服务端
tags: 
- 服务端
- java
---

### 1 Java的起源
Oak --> Java
### 2 Java的发展
Java1.0
Java2.0  JavaSE：java平台标准版  JavaME：微型版   JavaEE：企业版
sun公司
oracle公司
### 3 Java的特性
面向对象
可移植性  JVM实现了可移植性
健壮性
分布式
多线程：线程可以理解为轻量的进程。
### 4 Java的工作方式
java源文件（.java格式结尾）-----经过java编译器编译----字节码（.class格式结尾）------>被类装载器装载到Java虚拟机（JVM）---- 被JVM解释给操作系统-----操作系统来执行。
### 5 Java开发系统的构成
- 1.Java虚拟机（JVM）：指令集、寄存器、堆栈、垃圾处理器、方法区域组成。
三种区域：局部变量区域、执行环境区域、操作数区域。
- 2.类库：标准类库（官方提供的，我们可以直接使用类库中的类）、开发者自己的类
- 3.包：本质上是文件夹的形式，用于组织项目文件。
- 4.JRE：Java Runtime Environment，java运行环境
- 5.JDK：Java Development Kit，Java开发套件。  Eclipse

### 6 Java技术的应用
JavaME：目前市场份额很小，ios / android
JavaSE：标准版，用于桌面软件的编程。
JavaEE：为企业级开发提供一整套的解决方案。
### 7 Java跨平台性
常见平台  windowsOs   Unix   Unix-like(linux,Android,ios等)   Mac Os
跨平台：同一份代码可以在多个平台中运行
跨平台原理：每个平台一个配套的虚拟机（JVM）