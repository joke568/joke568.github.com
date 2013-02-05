----
title: '让代码高亮的方法'
layout: post
---
没有写几篇博客，前面写的偶尔会贴出代码，代码都不是很多，今天发了一篇关于tab切换的代码有点长，一直都想知道这个jekyll是怎么设置代码高亮的，上网搜索了一下首选要引入这个样式highlight.css，然后在_config.yml里要设置pygments: true，在写文章的时候要需要代码高亮的时候写入这个:

	{% highlight language %}代码{% endhighlight %}

这样代码就高亮了！
