#移动重构需注意事项及常见问题解决方案

	移动重构需注意事项及常见问题解决方案
    │  
    ├── meta标签
    │   
    ├── Retina屏幕 图片怎么处理
    │
    ├── 高性能 CSS3 动画
    │
    ├── 移动设计用户体验
    │
    ├── 布局
    │
    └── 性能



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


## 高性能 CSS3 动画

### 1、如使用3D变形来开启GPU加速
	-webkit-transform: translate3d(0, 0, 0); 
	-moz-transform: translate3d(0, 0, 0); 
	-ms-transform: translate3d(0, 0, 0); 
	transform: translate3d(0, 0, 0); 

如动画过程有闪烁（通常发生在动画开始的时候），可以尝试下面的Hack：

	-webkit-backface-visibility: hidden; 
	-moz-backface-visibility: hidden; 
	-ms-backface-visibility: hidden; 
	backface-visibility: hidden;  
	-webkit-perspective: 1000; 
	-moz-perspective: 1000; 
	-ms-perspective: 1000; 
	perspective: 1000;  	

如下面一个元素通过translate3d右移500px的动画流畅度会明显优于使用left属性：
	
	.ball-1 { 
	    transition: -webkit-transform .5s ease; 
	    -webkit-transform:     translate3d(0, 0, 0);
	}
	.ball-1.slidein{
	    -webkit-transform: translate3d(500px, 0, 0); 
	} 
	.ball-2 {
	    transition: left .5s ease; left：0; 
	}
	.ball-2.slidein { left：500px; 
	}

注：3D变形会消耗更多的内存与功耗，应确实有性能问题时才去使用它，兼在权衡

### 2、尽可能少的使用box-shadows与gradients
> box-shadows与gradients往往都是页面的性能杀手，尤其是在一个元素同时都使用了它们，所以拥抱扁平化设计吧。

### 3、尽可能的让动画元素不在文档流中，以减少重排
	
	position: fixed; position: absolute; 

### 4、优化 DOM layout 性能
	
	// 触发两次 layout 
	var newWidth = aDiv.offsetWidth + 10; 
	// Read 
	aDiv.style.width = newWidth + 'px'; 
	// Write 
	var newHeight = aDiv.offsetHeight + 10; 
	// Read 
	aDiv.style.height = newHeight + 'px'; 
	// Write 


	// 只触发一次 layout 
	var newWidth = aDiv.offsetWidth + 10; 
	// Read 
	var newHeight = aDiv.offsetHeight + 10; 
	// Read
	aDiv.style.width = newWidth + 'px'; 
	// Write 
	aDiv.style.height = newHeight + 'px'; // Write

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
