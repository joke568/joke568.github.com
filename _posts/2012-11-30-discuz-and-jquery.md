---
layout: post
title: '解决jquery和discuz的兼容问题'
---
discuz不支持jquery，看其他的使用discuz程序的网站是这样解决的。
在head中引入jquery的库文件。

```javascript
	<script src="jquery1.8.js" type="text/javascript"></script>
	<script type="text/javascript">
	 var jQ = jQuery.noConflict();
	</script>
```

