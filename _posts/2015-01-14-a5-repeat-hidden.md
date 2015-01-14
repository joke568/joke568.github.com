---
layout: post
title: 'A5分类信息回复可见修改'
---
1，.\source\function\function_discuzcode.php

查找

```php
$message = preg_replace("/\[hide\](.*?)\[\/hide\]/is", tpl_hide_reply_hidden(), $message);
```

更改为

```php
$message = preg_replace("/\[hide\]\s*(.*?)\s*\[\/hide\]/is", tpl_hide_reply(), $message);
```

2，.\source\include\post\post_newthread.php

查找

```php
	$params = array(
		'subject' => $subject,
		'message' => $message,
		'typeid' => $typeid,
		'sortid' => $sortid,
		'special' => $special,
	);
```

更改为

```php
	$params = array(
		'subject' => $subject,
		'message' => trim("[hide]".$message."[/hide]"),
		'typeid' => $typeid,
		'sortid' => $sortid,
		'special' => $special,
	);
```

3，.\source\function\function_threadsort.php

查找

```php
	return $threadsortshow;
```

更改为

```php
	if($_G['uid']) {
		$authoronline = C::t('forum_post')->fetch_pid_by_tid_authorid($_G['tid'], $_G['uid']);
	}


	if($authoronline){
		return $threadsortshow;
	}
```

4， .\template\default\forum\viewthread_node_body.htm

查找

```html
		<!--{if $threadsort && $threadsortshow}-->
			<!--{if $threadsortshow['typetemplate']}-->
				$threadsortshow[typetemplate]
			<!--{elseif $threadsortshow['optionlist']}-->
				<div class="typeoption">
					<!--{if $threadsortshow['optionlist'] == 'expire'}-->
						{lang has_expired}
					<!--{else}-->
						<table summary="{lang threadtype_option}" cellpadding="0" cellspacing="0" class="cgtl mbm">
							<caption>$_G[forum][threadsorts][types][$_G[forum_thread][sortid]]</caption>
							<tbody>
								<!--{loop $threadsortshow['optionlist'] $option}-->
									<!--{if $option['type'] != 'info'}-->
										<tr>
											<th>$option[title]:</th>
											<td><!--{if $option['value'] !== ''}-->$option[value] $option[unit]<!--{else}-->-<!--{/if}--></td>
										</tr>
									<!--{/if}-->
								<!--{/loop}-->
							</tbody>
						</table>
					<!--{/if}-->
				</div>
			<!--{/if}-->
		<!--{/if}-->
```

更改为

```html
		<!--{if $threadsort && $threadsortshow}-->
			<!--{if $threadsortshow['optionlist']}-->
				<div class="typeoption">
					<!--{if $threadsortshow['optionlist'] == 'expire'}-->
						{lang has_expired}
					<!--{else}-->
						<table summary="{lang threadtype_option}" cellpadding="0" cellspacing="0" class="cgtl mbm">
							<caption>$_G[forum][threadsorts][types][$_G[forum_thread][sortid]]</caption>
							<tbody>
								<!--{loop $threadsortshow['optionlist'] $option}-->
									<!--{if $option['type'] != 'info'}-->
										<tr>
											<th>$option[title]:</th>
											<td><!--{if $option['value'] !== ''}-->$option[value] $option[unit]<!--{else}-->-<!--{/if}--></td>
										</tr>
									<!--{/if}-->
								<!--{/loop}-->
							</tbody>
						</table>
					<!--{/if}-->
				</div>
			<!--{/if}-->
		<!--{else}-->
			<div class="showhide"><h4>本贴联系方式隐藏,回复后可见</h4></div>	
		<!--{/if}-->
```
