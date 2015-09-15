#移动重构需注意事项及常见问题解决方案

## meta标签
	<!-- 主要的 -->
	<meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no, minimal-ui" />
	<meta name="apple-mobile-web-app-capable" content="yes" />
	<meta name="apple-mobile-web-app-status-bar-style" content="black" />
	<meta name="format-detection"content="telephone=no, email=no" />

	<!-- 启用360浏览器的极速模式(webkit) -->
	<meta name="renderer" content="webkit">

	<!-- 避免IE使用兼容模式 -->
	<meta http-equiv="X-UA-Compatible" content="IE=edge">

	<!-- 针对手持设备优化，主要是针对一些老的不识别viewport的浏览器，比如黑莓 -->
	<meta name="HandheldFriendly" content="true">

	<!-- 微软的老式浏览器 -->
	<meta name="MobileOptimized" content="320">

	<!-- uc强制竖屏 -->
	<meta name="screen-orientation" content="portrait">

	<!-- QQ强制竖屏 -->
	<meta name="x5-orientation" content="portrait">

	<!-- UC强制全屏 -->
	<meta name="full-screen" content="yes">

	<!-- QQ强制全屏 -->
	<meta name="x5-fullscreen" content="true">

	<!-- UC应用模式 -->
	<meta name="browsermode" content="application">

	<!-- QQ应用模式 -->
	<meta name="x5-page-mode" content="app">

	<!-- windows phone 点击无高光 -->
	<meta name="msapplication-tap-highlight" content="no">

## Retina屏幕 图片怎么处理
	
### 1 、使用CSS Media Queries

	@media only screen and (-Webkit-min-device-pixel-ratio: 1.5),
		only screen and (-moz-min-device-pixel-ratio: 1.5),
		only screen and (-o-min-device-pixel-ratio: 3/2),
		only screen and (min-device-pixel-ratio: 1.5) {
		  .icon {
		    background-image: url(example@2x.png);
		    background-size: 100% 100%;
		  }
	}

### 2、使用JavaScript
	
	$(document).ready(function(){
		if (window.devicePixelRatio > 1) {
			var lowresImages = $('img');

			images.each(function(i) {
				var lowres = $(this).attr('src');
				var highres = lowres.replace(".", "@2x.");
				$(this).attr('src', highres);
			});
		}
	});

### 可缩放矢量图形

	svg,icon font

## 移动设计用户体验

* button大小
* 默认最小字体为14px大小
* 提示和显示（又称，逐步展示）


## 布局
* flex布局
* 绝对定位布局


## 性能

* 利用CSS3代替图片（圆角，阴影，渐变填充等）
* DATAURI来代替图片与WEB字体文件
* 可缩放矢量图形(SVG)而不是图片
* Sprites图
* 避免内联iframe

## 在线调试
* [Android with Chrme](https://developer.chrome.com/devtools/docs/remote-debugging)
* [iOS with Safari](http://debugbrowser.com/)
