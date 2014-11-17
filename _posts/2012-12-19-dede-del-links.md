---
layout: post
title: '去除dede默认的友情连接'
---
这个是从网上看到的

	找到dedecms5.7根目录下的 include/taglib/flinktype.lib.php，flinktype.lib.php这个文件,用记事本打开。

	找到以下代码：

	$dedecms = false; 
		$dedecms->id = 999; 
		$dedecms->typename = '织梦链'; 
		if($type == 'dedecms') $row[] = $dedecms; 


	直接将其删除即可，然后保存。

	最后到dedecms5.7后台重新生成下，再到网站首页看下，此时“织梦链”已经去掉了

