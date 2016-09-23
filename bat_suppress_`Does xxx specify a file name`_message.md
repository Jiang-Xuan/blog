---
title: "bat命令xcopy抑制复制文件的时候的消息"
date: 2016-9-22 17:24:00
tags: ['bat', 'xcopy指令', 'windows']
---

# xcopy拷贝文件夹

今天在学习bat批处理编程的时候接触到了xcopy命令。
我尝试用它来拷贝文件夹，但是可恶的是，每次我拷贝文件夹的时候总是报出一个提示信息：
<pre>Does xxxxxx specify a file name
or directory name on the target
(F = file, D = directory)?</pre> 
既然是复制文件夹，这个参数一直是`D`，这样的一直提示让我选择特别烦。
看了xcopy的帮助信息也没有什么帮助，然后网上搜，中文的有用信息一点儿也没有看到。
最后在StackOverflow上看到了解决办法。
<pre>echo f | xcopy /f /y /h srcfile destfile</pre>
``\h``表示递归复制所有的文件包括文件夹
<strong>先输出选择再执行拷贝命令</strong>
如果你的英文比较好，请查看[英文原文](http://stackoverflow.com/questions/3018289/xcopy-file-rename-suppress-does-xxx-specify-a-file-name-message)