---
title: kloxo不能登录ftp解决方法
layout: post
---
查看21端口是否开启

{% highlight linux %}
netstat -an | grep LISTEN
{% endhighlight %}

正常情况下我们可以看到常用端口诸如7777、7778、80、53、21、22等等都是开启的。

如果21端口都没有开启，我们仅需修改下pureftp配置即可。

编辑/etc/xinetd.d/pureftp文件，修改或者替换为下面的内容：

{% highlight linux %}
service ftp
{
disable = no
socket_type     = stream
wait            = no
user            = root
server          = /usr/sbin/pure-ftpd
server_args     = -A -c5000 -C8 -D -fftp  -H -I15 -lpuredb:/etc/pure-ftpd/pureftpd.pdb -lunix -L2000:8 -m4 -s -p30000:50000 -U133:022 -u100 -Oclf:/var/log/kloxo/pureftpd.log -g/var/run/pure-ftpd.pid -k99 -Z -Y 1
groups          = yes
flags           = REUSE
}  
{% endhighlight %}

重启一下ftp

{% highlight linux %}
service xinetd restart
{% endhighlight %}
