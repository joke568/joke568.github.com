---
layout: post
title: '解决帖子内容页用户组图片丢失'
---
后台添加了一个用户组,应用后在帖子的内容页看到了这种情况,用户名的背景没有了。

![](/images/2012-12-04-discuz-pic.png)

解决方法:

在discuz的模板文件里找到了这个viewthread_user.htm文件,这个是帖子页左侧的页面找到以下代码
	<h3 id="<!--{if $post['groupid'] == 1}-->groupida<!--{elseif $post['groupid']>=2 && $post['groupid']<=3 }-->groupidb<!--{elseif $post['groupid']<=15 && $post['groupid'] >=9 }-->groupidc<!--{elseif $post['groupid'] == 20 }-->groupidd<!--{elseif $post['groupid'] == 22 }-->groupide<!--{elseif $post['groupid'] == 23 }-->groupidf<!--{elseif $post['groupid'] == 25 }-->groupidg<!--{elseif $post['groupid'] == 5 }-->groupidh<!--{elseif $post['groupid'] == 6 }-->groupidj<!--{elseif $post['groupid'] == 7 }-->groupidk<!--{elseif $post['groupid'] == 4 }-->groupidl<!--{elseif $post['groupid'] == 28 }-->groupidc<!--{/if}-->"

这个是判断用户组的权限的，如果达到这个权限就显示对于的id，直接在后面补充一个判断。
	<!--{elseif $post['groupid'] == 16 }-->groupidc
其中groupidc是一个样式，就是名称的背景。




