---
title: linux服务器配置全局命令
date: 2018-02-11
categories: 
- 服务端
tags: 
- 服务端
- 运维
- linux
---

### 一、原因
因为我们要在linux服务器使用一些全局命令，比如npm,cnpm,node等等，所以在配置全局命令的时候遇到了一些障碍，主要还是对linux操作不熟悉。
### 二、开始操作
- 首先，我们在linux系统安装了某个命令，不会像一些windows安装软件似的直接给配置好了全局命令，所以，我们需要手动进行配置。linux服务器的全局命令配置的目录是在
```
/usr/local/bin
```
- 然后我们需要找到我们之前将文件安装到哪里了，比如我安装了cnpm
```
npm install -g cnpm --registry=https://registry.npm.taobao.org
```
但是我不知道真正装到哪里了
我们可以使用命令
```
find / -name 'cnpm'
```
命令的含义是在 /根目录下 查找名字为 'cnpm'的文件
![查找文件](查找文件.png)
其中，在bin目录下的就是我们想要的文件地址（这里我用的是
```
/app/nodejs/lib/node_modules/cnpm/bin/cnpm
 ```
不知道直接选
```
/app/nodejs/bin/cnpm
```
能不能行，下次试试）
- 接下来我们就可以配置全局了，这里用的是软链接
```
ln -s /app/nodejs/lib/node_modules/cnpm/bin/cnpm  /usr/local/bin/cnpm
```
- 最后我们可以去 /usr/local/bin目录下看一看
![查看目录](查看目录.png)
目录中已经有cnpm文件了。

### 三、验证结果
再查看下cnpm是否全局安装成功
![cnpm版本](cnpm版本.png)
ok，大功告成，这样就可以在linux服务器开心的用cnpm了。其他文件的配置也是一样的，这里只是拿cnpm举例而已，如果有不同的地方，大家可以留言告知，一起学习。



