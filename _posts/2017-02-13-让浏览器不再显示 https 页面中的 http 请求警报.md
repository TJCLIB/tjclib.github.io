---
layout:     post
title:      让浏览器不再显示 https 页面中的 http 请求警报             
subtitle:  
date:       2017-02-13
author:     凩茻MUMU
header-img: img/post-bg-js-module.jpg  
catalog: true   
tags:                           
    - https
    - http
    - 错误警报
---

# 让浏览器不再显示 https 页面中的 http 请求警报           
HTTPS 是 HTTP over Secure Socket Layer，以安全为目标的 HTTP 通道，所以在 HTTPS 承载的页面上不允许出现 http 请求，一旦出现就是提示或报错           
HTTPS改造之后，我们可以在很多页面中看到如下警报：           

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/4697920-0937b3f8e457dc27.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
很多运营对 https 没有技术概念，在填入的数据中不免出现 http 的资源，体系庞大，出现疏忽和漏洞也是不可避免的。           
## CSP设置upgrade-insecure-requests           
好在 W3C 工作组考虑到了我们升级 HTTPS 的艰难，在 2015 年 4 月份就出了一个 Upgrade Insecure Requests 的[草案](http://www.w3.org/TR/mixed-content/)，他的作用就是让浏览器自动升级请求。在我们服务器的响应头中加入：           
` header("Content-Security-Policy: upgrade-insecure-requests");`            
我们的页面是 https 的，而这个页面中包含了大量的 http 资源（图片、iframe等），页面一旦发现存在上述响应头，会在加载 http 资源时自动替换成 https 请求。可以查看 google 提供的一个 [demo](https://googlechrome.github.io/samples/csp-upgrade-insecure-requests/index.html)：           

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/4697920-b6338ffac2ad5b25.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
如果我们不方便在服务器/Nginx 上操作，也可以在页面中加入 meta 头：           
` <meta http-equiv="Content-Security-Policy" content="upgrade-insecure-requests" />`            

目前支持这个设置的还只有 chrome 43.0，不过我相信，CSP 将成为未来 web 前端安全大力关注和使用的内容。而 upgrade-insecure-requests           
 草案也会很快进入 RFC 模式。           
从 W3C 工作组给出的 [example](http://www.w3.org/TR/upgrade-insecure-requests/#examples)，可以看出，这个设置不会对外域的 a 链接做处理，所以可以放心使用。           
