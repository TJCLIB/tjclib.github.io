---
layout:     post
title:      使用Sublime Text 3 编辑写作Markdown文件
subtitle:   Sublime写Markdown
date:       2017-02-18
author:     Airmole
header-img: img/post-bg-unix-linux.jpg
catalog: true
tags:
    - Sublime
    - Markdown
    - 编辑
---

# 使用Sublime Text 3 编辑写作Markdown文件

回顾 [Markdown新手指南](https://mumu0934.github.io/2017/02/10/Markdown%E6%96%B0%E6%89%8B%E6%8C%87%E5%8D%97/) 了解最基础常用的语法规则

Sublime Text 3 是我第一次正式的接触的文本编辑器，之前也无意中接触过Notepad++和UltraEdit,但是那个时候什么都不懂，可以说完全不知道是用来干什么的。第一次接触到Sublime Text 3 好像是在初中毕业的时候，在百度云看HTML教程，那个讲师提到的，发现确实很方便，很好用，效率比较高。最近，也越来越觉得强大。
通过安装插件可以实现Sublime Text 3 对 Markdown 文档的预览和转换功能。

## 安装Package Control

安装包控制扩展可以方便地为Sublime Text 3添加拓展。

打开st，按下组合键Control + `(如果安装了QQ输入法这个快捷键好像会冲突），出现控制台，输入

```
import urllib2,os; pf='Package Control.sublime-package'; ipp = sublime.installed_packages_path(); os.makedirs( ipp ) if not os.path.exists(ipp) else None; urllib2.install_opener( urllib2.build_opener( urllib2.ProxyHandler( ))); open( os.path.join( ipp, pf), 'wb' ).write( urllib2.urlopen( 'http://sublime.wbond.net/' +pf.replace( ' ','%20' )).read()); print( 'Please restart Sublime Text to finish installation')
```

当看到代码最后一行提示的时候说明安装成功，此时重启Sublime Text 3，可在Preferences -> Package Settings看到Package Control。

## 安装markdown preview

按下键Ctrl+Shift+p调出命令面板，找到Package Control: install Pakage这一项。搜索markdown preview，点击安装。

## 关于编辑

按Ctrl + N 新建一个文档

按Ctrl + Shift + P

使用Markdown语法编辑文档

语法高亮，输入ssm 后回车(Set Syntax: Markdown)

## 关于使用

编辑过程中按下Ctrl+Shift+P：


![Paste_Image.png](http://upload-images.jianshu.io/upload_images/4697920-4ebf82838364c4aa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


Markdown Preview:Copy to Clipboard     #复制到粘贴板

Markdown Preview:Preview in Browser     #在浏览器中预览

Markdown Preview:Save to HTML      #保存为HTML

Markdown Preview:Open markdown Cheat sheet     #打开快捷指南(大概差不多这个意思)

Build With:Markdown     #使用Markdown建立(事实证明这个没什么用，因为毕竟Markdown是用来写文档的，不是编程语言。)

Markdown Preview:Export HTML in Sublime Text       #输出为HTML并在Sublime Text 中打开。

Set Syntax开头的最后这两项是设置语法的。不知道那个Multi Markdown是个啥。应该跟Markdown差不多,稍微高级一点吧，以后有空再看。

preview inbrowser据称是实时的，但是实践上还是需要在Sublime Text 3保存，然后浏览器刷新才能看到新的效果，好在markdown写得多的话也不需要每敲一行看一次效果。

## 打印成PDF

将markdown转换为pdf应该有很多种方法的。可直接用谷歌浏览器虚拟打印功能生成。

利用Markdown Preview的Preview in Browser功能可以在浏览器上看到html效果。在页面右键->打印->另存为pdf->调节页边距即可将pdf文件下载下来。


参考链接：

- [sublime text 2(3)下的Markdown写作](http://www.cnblogs.com/jadeboy/p/4165449.html)

