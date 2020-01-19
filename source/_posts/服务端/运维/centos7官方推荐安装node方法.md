---
title: centos7官方推荐安装node方法
date: 2018-02-10
categories: 
- 服务端
tags: 
- 服务端
- 运维
- centos
- node
---

网上查看centos上安装node的方法，就这种最简单，而且默认全局安装，不用软连接了。
```
curl --silent --location https://rpm.nodesource.com/setup_8.x | sudo bash -
```
```
yum -y install nodejs
```
```
sudo yum install gcc-c++ make
```
