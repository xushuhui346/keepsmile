---
title: java开发环境搭建
date: 2019-08-08
categories: 
- 服务端
tags: 
- 服务端
- java
---

# 简单开发环境
#### 1 安装JDK  
我的路径：  例如 C:\Program File\Java\jdk1.7.0_67\
#### 2 配置JDK环境变量
（系统变量）
JAVA_HOME  jdk安装路径  C:\Program File\Java\jdk1.7.0_67\
PATH       %JAVA_HOME%\bin
CLASSPATH  .
#### 3 验证环境搭建成功
命令行  输入java  javac  java -version  没报错，环境就搭建成功了

# 集成开发环境
#### 1 IDE 集成开发环境
常见IDE  Eclipse/NetBean/IDEA/MyEclipse等
#### 2 Eclipse 开源的，用java编写的
#### 3 集成开发环境的好处
- 不需要手动编译了（javac）
- Eclipse默认在保存源文件时编译
- 默认把class放在bin目录（源码src目录）
- 不需要手动执行了（java）
- 右键-run java application即可
- 代码提示等
