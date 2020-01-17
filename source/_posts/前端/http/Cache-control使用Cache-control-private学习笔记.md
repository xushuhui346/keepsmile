---
title: Cache-control使用Cache-control-private学习笔记
date: 2019-08-12
categories: 
- 前端
tags: 
- 前端
- web
- http
---

>网页缓存由 HTTP消息头中的**Cache-control**控制，常见取值有private、no-cache、max-age、must- revalidate等，默认为private

其作用根据不同的重新浏览方式，分为以下几种情况：
#### （1）打开新窗口
值为private、no-cache、must-revalidate，那么打开新窗口访问时都会重新访问服务器。
而如果指定了max-age值，那么在此值内的时间里就不会重新访问服务器，例如：
Cache-control: max-age=5(表示当访问此网页后的5秒内再次访问不会去服务器)

#### （2）在地址栏回车
值为private或must-revalidate则只有第一次访问时会访问服务器，以后就不再访问。
值为no-cache，那么每次都会访问。
值为max-age，则在过期之前不会重复访问。

#### （3）按后退按扭
值为private、must-revalidate、max-age，则不会重访问，
值为no-cache，则每次都重复访问

#### （4）按刷新按扭
无论为何值，都会重复访问
Cache-control值为“no-cache”时，访问此页面不会在Internet临时文章夹留下页面备份。
另外，通过指定“Expires”值也会影响到缓存。例如，指定Expires值为一个早已过去的时间，那么访问此网时若重复在地址栏按回车，那么每次都会重复访问： Expires: Fri, 31 Dec 1999 16:00:00 GMT
比如：禁止页面在IE中缓存
http响应消息头部设置：
```
CacheControl = no-cache
Pragma=no-cache
Expires = -1
```
Expires是个好东东，如果服务器上的网页经常变化，就把它设置为-1，表示立即过期。如果一个网页每天凌晨1点更新，可以把Expires设置为第二天的凌晨1点。
当HTTP1.1服务器指定 CacheControl = no-cache时，浏览器就不会缓存该网页。

旧式 HTTP 1.0 服务器不能使用 Cache-Control 标题。

所以为了向后兼容 HTTP 1.0 服务器，IE使用Pragma:no-cache 标题对 HTTP 提供特殊支持。
如果客户端通过安全连接 (https://)/与服务器通讯，且服务器在响应中返回 Pragma:no-cache 标题，
则 Internet Explorer不会缓存此响应。注意：Pragma:no-cache 仅当在安全连接中使用时才防止缓存，如果在非安全页中使用，处理方式与 Expires:-1相同，该页将被缓存，但被标记为立即过期。

header常用指令
header分为三部分：
- 第一部分为HTTP协议的版本(HTTP-Version)；
- 第二部分为状态代码(Status)；
- 第三部分为原因短语(Reason-Phrase)。
```
<?php
// fix 404 pages:   用这个header指令来解决URL重写产生的404 header
header('HTTP/1.1 200 OK');  

// set 404 header:   页面没找到
header('HTTP/1.1 404 Not Found');  

// 页面被永久删除，可以告诉搜索引擎更新它们的urls
// set Moved Permanently header (good for redrictions)  
// use with location header  
header('HTTP/1.1 301 Moved Permanently');  
// 访问受限
header('HTTP/1.1 403 Forbidden');
// 服务器错误
header('HTTP/1.1 500 Internal Server Error');

// 重定向到一个新的位置
// redirect to a new location:  
header('Location: http://www.jb51.net);  

延迟一段时间后重定向
// redrict with delay:  
header('Refresh: 10; url=http://www.sina.com.cn');  
print 'You will be redirected in 10 seconds';  

// 覆盖 X-Powered-By value
// override X-Powered-By: PHP:  
header('X-Powered-By: PHP/4.4.0');  
header('X-Powered-By: Brain/0.6b');  

// 内容语言 (en = English)
// content language (en = English)  
header('Content-language: en');  

//最后修改时间 (在缓存的时候可以用到)
// last modified (good for caching)  
$time = time() - 60; // or filemtime($fn), etc  
header('Last-Modified: '.gmdate('D, d M Y H:i:s', $time).' GMT');  

// 告诉浏览器要获取的内容还没有更新
// header for telling the browser that the content  
// did not get changed  
header('HTTP/1.1 304 Not Modified');  

// 设置内容的长度 (缓存的时候可以用到):
// set content length (good for caching):  
header('Content-Length: 1234');  

// 用来下载文件:
// Headers for an download:  
header('Content-Type: application/octet-stream');  
header('Content-Disposition: attachment; filename="example.zip"');  
header('Content-Transfer-Encoding: binary');  

// 禁止缓存当前文档:
// load the file to send:readfile('example.zip');  
// Disable caching of the current document:  
header('Cache-Control: no-cache, no-store, max-age=0, must-revalidate');  
header('Expires: Mon, 26 Jul 1997 05:00:00 GMT');    
// 设置内容类型:
// Date in the pastheader('Pragma: no-cache');  
// set content type:  
header('Content-Type: text/html; charset=iso-8859-1');  
header('Content-Type: text/html; charset=utf-8');  
header('Content-Type: text/plain');  

// plain text file  
header('Content-Type: image/jpeg');    

// JPG picture  
header('Content-Type: application/zip');    

// ZIP file  
header('Content-Type: application/pdf');    

// PDF file  
header('Content-Type: audio/mpeg');    

// Audio MPEG (MP3,...) file  
header('Content-Type: application/x-shockwave-flash');    

// 显示登录对话框，可以用来进行HTTP认证
// Flash animation// show sign in box  
header('HTTP/1.1 401 Unauthorized');  
header('WWW-Authenticate: Basic realm="Top Secret"');  
print 'Text that will be displayed if the user hits cancel or ';  
print 'enters wrong login data';
?>
```
现在表单的填写，我们可以用AJAX对用户随时进行验证，进行友好的提示，但是在用户没有留意AJAX友好提示,提交了错误的表单，跳回原页，而填写的信息却全部丢失了。
要支持页面回跳，有以下的办法：
1.使用**session_cache_limiter**方法： session_cache_limiter('private,must-revalidate');但是要值得注意的是 session_cache_limiter()方法要写在session_start()方法之前才有用;
2.用header来设置控制缓存的方法： **header('Cache-control:private,must-revalidate')**;
