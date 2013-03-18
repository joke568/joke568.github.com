---
title: 'kloxo文件夹不能修改权限'
layout： post
---
vps安装的kloxo，在使用FTP中不能修改文件夹的权限，在kloxo文件管理里修改权限了也没有用，后来上网看到一个解决方法挺不错的。

{% highlight javascript %}

	cd /home
	cd admin
	chown -R admin:users *

{% endhighlight %}

好了，FTP可以上传文件了。
