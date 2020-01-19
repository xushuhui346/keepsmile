---
title: winscp链接远程centos服务器：拒绝访问
date: 2018-03-08
categories: 
- 服务端
tags: 
- 服务端
- 运维
- centos
- winscp
---

查了很多资料，最后这个方式解决了，sudo重置root账户的密码
```
sudo passwd root //用sudo修改root帐户
```
Password: //输入密码
Enter new UNIX password: //提示输入新的root帐户密码
Retype new UNIX password:  //再输入一次确认密码

修改成功之后你就可以使用root账号了

有时直接用root账号还是无法登陆远程终端，这时还需要修改ssh配置文件：

/etc/ssh/sshd_config 修改该配置文件：

```
# Authentication:
LoginGraceTime 120
PermitRootLogin without-password
StrictModes yes
```
将 PermitRootLogin without-password  修改为 PermitRootLogin yes，如下：
```
# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes
```
可以成功登陆了。
