---
title: node.js环境及npm深入
date: 2017-12-11
categories: 
- 前端
tags: 
- 前端
- web
- node
---

### 一、node.js REPL环境
- cmd命令里输入node  进入node.js REPL环境，可以做一些运算等
![运算](运算.png)
- 命令
ctrl + c     退出当前终端
ctrl + c     按下两次   退出Node REPL
ctrl + d     退出Node REPL
向上/向下键    查看输入的历史命令
tab键   列出当前命令
.help    列出使用评论
.break   退出多行表达式
.clear    退出多行表达式
.save filename   保存当前的Node REPL会话到指定文件
.load filename   载入当前Node REPL会话的文件内容

### 二、包管理器npm详解
-  npm命令
npm -v     【查看npm版本】
npm  install npm -g    【升级npm（全局安装）】
npm  install  第三方包名  -g     【全局安装包】
npm  uninstall  第三方包名  -g      【全局卸载包】
npm  search  第三方包名        【查找包】
npm  help   【npm帮助】
