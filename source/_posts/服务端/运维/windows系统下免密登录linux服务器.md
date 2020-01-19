---
title: windows系统下免密登录linux服务器
date: 2018-02-18
categories: 
- 服务端
tags: 
- 服务端
- 运维
- linux
- 免密登录
---

首先声明，本文是在借鉴其他文章，并实践成功后编写的，在文中会有相关引用的链接。大家也可以参考相关文章[Windows 下通过 cmder 远程连接 Linux 服务器](https://www.jianshu.com/p/96918eeda4ca) （注：此文章中有代码在实际操作时有问题，导致报错，笔者会在下文中描述）。
### 一、文章操作指引
>1. 需要先在 Windows 系统中安装 [cmder](https://cmder.net/)（点击蓝色字符下载安装），并通过  [Tools - Windows系统下的命令行工具Cmder](https://www.cnblogs.com/anliven/p/7945165.html)这篇文章对cmder进行配置。
>2. 文中用 "<xxx>" 表示的字符需要替换为自己机器中真实的名称
>3. 以 "$ " 开头的命令代表需要在命令行工具中输入，输入时不需要带上 "$ " 字符。
### 二、前言
SSH 为 [Secure Shell](https://links.jianshu.com/go?to=https%3A%2F%2Fbaike.baidu.com%2Fitem%2FSecure%2520Shell) 的缩写，由 IETF 的网络小组（Network Working Group）所制定；SSH 为建立在应用层基础上的安全协议。SSH 是目前较可靠，专为[远程登录](https://links.jianshu.com/go?to=https%3A%2F%2Fbaike.baidu.com%2Fitem%2F%25E8%25BF%259C%25E7%25A8%258B%25E7%2599%25BB%25E5%25BD%2595%2F1071998)会话和其他网络服务提供安全性的协议。利用 SSH 协议可以有效防止远程管理过程中的信息泄露问题。

SSH 目前提供两种级别的安全验证

*   基于口令的安全验证
*   基于秘钥的安全认证（不需要在网络上传输口令，相对来说更加安全）

### 三、开始操作吧
#### 1.引子：首先，我们先用账号密码的方式登录服务器
通过 SSH 口令方式连接：
- 打开 cmder
- 输入以下命令按回车确认
```
$ ssh <用户名>@<服务器ip地址>
```
- 根据给出的提示输入用户密码，按回车确认
- 登录成功

#### 2.接下来进入正题：通过 SSH 密钥方式连接（实现免密登录）
请先检查本机目录 C:\Users\<用户名>\.ssh 下是否有 id_rsa 和 id_rsa.pub 两个文件，如果有直接上传公钥 id_rsa.pub 到 Linux 服务器（步骤2）即可，无需再生成密钥对
- 步骤1 、在本机生成 SSH 密钥对
(1)打开 cmder
(2)输入以下命令按回车确认
```
$ ssh-keygen -t rsa
```
(3)弹出密钥保存位置提示后，继续按回车（密钥对将生成到默认位置 C:\Users\<用户名>\.ssh\）
(4)弹出输入密码提示后，继续按回车（此时不设置密钥对验证密码）
(5)弹出确认密码提示后，继续按回车
(6)检查本机目录 C:\Users\<用户名>\.ssh\ 下存在 id_rsa 和 id_rsa.pub 两个文件
(7)密钥对生成完毕
- 步骤2、上传公钥到 Linux 服务器
(1)通过方式一连接到 Linux 服务器
(2)在远程服务器上输入以下命令
```
$ mkdir ~/.ssh && touch ~/.ssh/authorized_keys
$ chmod 700 ~/.ssh && chmod 600 ~/.ssh/authorized_keys
```
(3)在本机输入命令
```
$ scp C:/Users/<用户名>/.ssh/id_rsa.pub <用户名>@<服务器ip地址>:~/.ssh/authorized_keys
```
或者
```
$ scp ~/.ssh/id_rsa.pub <用户名>@<服务器ip地址>:~/.ssh/authorized_keys
```
注：上面说的操作报错，就是这里，参考的文章中ssh公钥的目录用的\，导致一直报错找不到文件，网上查了半天，没有合理的解释，用/就没有问题了。windows系统默认的\。。。
(4)输入密码后，按回车确认
(5)上传成功后输入以下命令即可成功连接服务器
```
$ ssh <用户名>@<服务器ip地址>
```
(6)配置 config 文件简化登录输入
```
$ vim C:\Users\<用户名>\.ssh\config
```
输入以下内容：
```
Host <自定义服务名称>
  HostName <服务器ip地址>
  User <用户名>
  PubkeyAuthentication yes
```
config 文件创建好后，直接输入以下命令登录服务器
```
$ ssh <自定义服务名称>
```
好了，大功告成。**注：记得没有<>哦！！！**







