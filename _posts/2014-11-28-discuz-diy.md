---
layout: post
title: 'discuz幻灯片模块'
---
这种用的是discuz自带的幻灯片，样式和模板写在一起，直接就可以用了。用到的素材直接下载下来就可以了

1，幻灯带小图切换

![](/images/20141128.jpg)

```html
<style type="text/css" media="screen">
.viewFlash { position: relative; width: 100%; height: 290px; margin-bottom: 10px; overflow: hidden; }	
.slideshow { clear: both; }
.flashImgUl { height: 290px; }
.flashImgUl li { float: left; width: 100%; height: 290px; }
.slideshow li { position: relative; overflow: hidden; }
.bgContent { position: absolute; z-index: 10; bottom: 0; left: 0; width: 700px; height: 65px; background: #777; border-top: 1px #999 solid; filter: alpha (opacity=70); opacity: 0.7; }
.flashTxtUl { position: absolute; z-index: 11; left: 20px; bottom: 40px; width: 660px; height: 20px; line-height: 20px; font-weight: bold; font-size: 14px; color: #F60; overflow: hidden; }
.flashTxtUl a { color: #FFFCFA; }
.flashBtn { position: absolute; z-index: 12; left: 20px; bottom: 7px; height: 27px; }
.flashBtn a { float: left; width: 42px; height: 23px; margin-right: 7px; display: inline-block; opacity: 0.7; filter: alpha(opacity=70); border: 2px solid #323232; }
.flashBtn a:hover, .flashBtn a.on { border-color: #f60; }
.flashBtn a img { width: 42px; height: 23px; }
.flashBtn2 { position: absolute; z-index: 15; right: 20px; bottom: 7px; width: 80px; height: 27px; }
.flashBtn2 a { position: relative; float: left; width: 40px; height: 27px; overflow: hidden; text-indent: -9999px; background-image: url("./template/20141126/images/dhd.png"); cursor: pointer; }
.flashBtn2 a.btn_1 { background-position: 0 -23px; }
.flashBtn2 a.btn_1:hover { background-position: 0 -51px; }
.flashBtn2 a.btn_2 { background-position:  -40px -23px; margin-left: -1px; }
.flashBtn2 a.btn_2:hover { background-position: -40px -51px; }
<style type="text/css" media="screen">
.viewFlash { position: relative; width: 100%; height: 290px; margin-bottom: 10px; overflow: hidden; }	
.slideshow { clear: both; }
.flashImgUl { height: 290px; }
.flashImgUl li { float: left; width: 100%; height: 290px; }
.slideshow li { position: relative; overflow: hidden; }
.bgContent { position: absolute; z-index: 10; bottom: 0; left: 0; width: 700px; height: 65px; background: #777; border-top: 1px #999 solid; filter: alpha (opacity=70); opacity: 0.7; }
.flashTxtUl { position: absolute; z-index: 11; left: 20px; bottom: 40px; width: 660px; height: 20px; line-height: 20px; font-weight: bold; font-size: 14px; color: #F60; overflow: hidden; }
.flashTxtUl a { color: #FFFCFA; }
.flashBtn { position: absolute; z-index: 12; left: 20px; bottom: 7px; height: 27px; }
.flashBtn a { float: left; width: 42px; height: 23px; margin-right: 7px; display: inline-block; opacity: 0.7; filter: alpha(opacity=70); border: 2px solid #323232; }
.flashBtn a:hover, .flashBtn a.on { border-color: #f60; }
.flashBtn a img { width: 42px; height: 23px; }
.flashBtn2 { position: absolute; z-index: 15; right: 20px; bottom: 7px; width: 80px; height: 27px; }
.flashBtn2 a { position: relative; float: left; width: 40px; height: 27px; overflow: hidden; text-indent: -9999px; background-image: url("./template/20141126/images/dhd.png"); cursor: pointer; }
.flashBtn2 a.btn_1 { background-position: 0 -23px; }
.flashBtn2 a.btn_1:hover { background-position: 0 -51px; }
.flashBtn2 a.btn_2 { background-position:  -40px -23px; margin-left: -1px; }
.flashBtn2 a.btn_2:hover { background-position: -40px -51px; }
.bilicen .b0, .bilicen_b0 { border-width: 0px; }
.bilicen .frame, .bilicen_mb0, .bilicen .frame-tab { margin-bottom: 0px; }
</style>
<div class="slidebox viewFlash cl">
	<ul class="slideshow flashImgUl">
		[loop1]
		<li><a href="{url}" title="{title}" target="_blank"><img src="{pic}" width="{picwidth}" height="{pichieght}" alt="{title}"></a></li>
		[/loop1]
	</ul>
	<div class="bgContent"></div>
	<ul class="slideother flashTxtUl">
		[loop2]
		<li><a href="{url}" title="{title}" target="_blank">{title}</a></li>
		[/loop2]
	</ul>
	<div class="slidebar flashBtn" mevent="mouseover">
		[loop3]
		<a href="{url}" title="{title}" target="_blank" class=""><img src="{pic}" alt="{title}"></a>
		[/loop3]
	</div>
	<div class="flashBtn2">
		<a class="slidebarup btn_1" title="上一张" href="javascript:;">上一张</a>
		<a class="slidebardown btn_2" title="下一张" href="javascript:;">下一张</a>
	</div>
</div>
<script type="text/javascript">
runslideshow();
</script>
```

这个是素材，[dhd.png](/files/dhd.png)

注意:./template/20141126/images/这个是图片的路径。图片的缩略图设置大小是700*290

2,图片滚动带左右控制

![](/images/20141128a.jpg)

```html
<style type="text/css" media="screen">
.publicBg { background: #EEE; }	
.channelShow, .hotGame { border-radius: 0 0 5px 5px; }
.channelShow { width: 680px; padding: 10px; _padding: 7px 10px; position: relative; overflow: visible; }
.slideshow { clear: both; }
.channelShow dl { float: left; width: 96px; margin: 0 8px; _margin: 0 8px 0 7px; display: inline; overflow: hidden; }
.channelShow dl dt { position: relative; width: 96px; height: 128px; overflow: hidden; }
.channelShow dl dt span.txt { background: #555; color: #FFF; }
.channelShow dl dt span.txt { position: absolute; left: 0; bottom: 0px; display: block; width: 90px; height: 20px; line-height: 20px; padding: 0 3px; background: #000; color: #FFF; filter: alpha(opacity=70); opacity: 0.7; text-align: center; }
.djdzkBtn i.ico_2 { background-position: 0 -44px; width: 19px; cursor: pointer; }
.djdzkBtn i.ico_3 { background-position: -20px -44px; width: 19px; cursor: pointer; }
.djdzkBtn a, .djdzkBtn i { display: inline-block; width: 17px; height: 17px; background: url(./template/20141126/images/index.png) no-repeat -40px -26px; vertical-align: middle; }
.djdzkBtn { position: absolute; right: 10px; top: -25px; height: 17px; overflow: hidden; }
.channelShow dl dd { width: 100%; line-height: 20px; padding: 5px; text-align: center; }
.channelShow dl dd a { display: block; height: 20px; overflow: hidden; }
.djdzkBtn a { cursor: default; }
.djdzkBtn a.on { background-position: -40px -44px; }
</style>
<div class="slidebox publicBg channelShow cl" slidenum="6" slidestep="6">
	<div class="slideshow">
		[loop]
		<dl class="">
			<dt><a href="{url}" title="{title}" target="_blank"><img alt="{title}" src="{pic}" width="{picwidth}" height="{picheight}"><span class="txt">{title}</span></a></dt>
			<dd><a href="" title="{title}" target="_blank">{title}</a></dd>
		</dl>
		[/loop]
	</div>
	<div class="slidebar djdzkBtn">
		[loop1]
		<em class=""></em>
		[/loop1]
		[order1=6]
		<a class="on" href="javascript:;" title="第1页"></a>
		[/order1]
		[order1=12]
		<a class="" href="javascript:;" title="第2页"></a>
		[/order1]
		[order1=18]
		<a class="" href="javascript:;" title="第3页"></a>
		[/order1]
		<i class="slidebarup ico_2" title="前一页"></i>
		<i class="slidebardown ico_3" title="后一页"></i>
	</div>
</div>
<script type="text/javascript">
runslideshow();
</script>
```
这个是素材，[dhd.png](/files/index.png)

注意:./template/20141126/images/这个是图片的路径。图片的缩略图设置大小是96*128
