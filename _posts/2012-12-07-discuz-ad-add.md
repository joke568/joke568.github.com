---
layout: post
title: '更改discuz的右下角的弹窗'
---
在discuz的后台文件添加右下角的弹窗文件后前台显示关闭之后再重新刷新就不显示了，后来在discuz的论坛上看到原来是设置了cookie，默认的cookie是86400也就是一天的时间，要修改一下discuz的源文件来更改这个cookie的值，这样弹窗不至于等24小时候才显示。

在discuz的根目录下面找到source\class\adv\adv_cornerbanner.php找到第118行看到这个代码

	 setcookie(\\\'adclose_\'.$adid.\'\\\', 1, 86400);

我设置的是一分钟后显示就把这个86400更改为60，如果你觉得时间还太长可以继续修改这个默认的86400的值到适合的大小为止！


