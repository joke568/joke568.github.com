---
layout: post
title: 'discuz的认证显示设置'
---
今天需要修改一下帖子的内容页在左侧的用户信息里判断是否认证，如果认证了显示指定的认证，没有认证则不显示。修改后的效果如下。

![](/images/2012-12-15-discuz-change-verify.png)

添加的代码如下:

			<!--{if $_G['setting']['verify']}-->
				<!--{loop $_G['setting']['verify'] $vid $verify}-->
						<!--{if $verify['available'] && $post['verify'.$vid] == 1 && $vid == 2}-->
						<li><strong>认证:</strong><span>$verify[title]</span></li>
        				<!--{/if}-->
    			<!--{/loop}-->
			<!--{/if}-->

其中$vid==2是显示认证的ID，可以根据需求进行更改。
