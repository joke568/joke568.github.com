---
layout: post
title: 'discuz开启调试模式'
---
![](/images/2014-11-15.jpg)


1,在./source/function/文件夹下面添加这个文件[function_debug.php](/files/function_debug.rar)(点击文件名下载)

2,修改配置文件，./config/config_global.php 添加

```php
$_config['debug'] = 'debug'; 
```
3,在访问的页面后面输入?debug=debug就可以看到调试模式了。

http://localhost/portal.php?debug=debug
