---
title: '使用vim快速格式化css的方法'
layout: post
---
网站的css压缩了，使用vim打开是一行，为了解压缩css最开始使用的是css格式化工具但是有个缺点，每一句都是一行，后来使用vim命令格式化一下，一句是一行使用的代码是这个
	
	%s/}/}\r/g

这样css就格式化正常了。