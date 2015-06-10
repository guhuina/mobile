#移动端项目常用代码


## CSS 
> Reset and Set the basic CSS for mobile phones.

### 去除ios a标签被点击时产生的半透明灰色背景 

	-webkit-tap-highlight-color:rgba(255,0,0,0);
	
### Android4.0下版本兼容写法
> Android4.0下不识别该-webkit-transform-3d，使用它可做Android4.0下版本兼容

	@media all and (-webkit-transform-3d){
		.css{}
	}

### 防止横竖屏切换时文本自动缩放

	body{-webkit-text-size-adjust:none;}


### 横屏、竖屏的样式判断

	@media all and (orientation : landscape) { /*这是匹配横屏的状态，横屏时的css代码*/
		body { 
		 
		} 
	} 
	@media all and (orientation : portrait){ /*这是匹配竖屏的状态，竖屏时的css代码*/
		body { 
			background-color: #00ff00; 
		} 
	} 

## HTML

> HTML5 module for mobile phones.

### 设置 viewpoint
> 当我们在 Safari 中打开一个网站时，默认情况下浏览器会对网页进行缩放显示，目的是让 PC 页面能够完全展示在小屏幕设备中，而这种缩放功能会严重影响专为移动设备屏幕尺寸设计的 WebApp 的体验，所以需要通过以下代码来关闭缩放：	
	

	<meta name = "viewport" content = "user-scalable=no, width=device-width">

* user-scalable – 用户是否可以手动缩放；
* width – 定义viewport宽度(默认为980像素) ，例子中值为device-width是指设置为设备显示宽度；
* height – viewport的高度；
* initial-scale – 初始的缩放比例 (范围从 0 到10)；
* minimum-scale – 允许用户缩放到的最小比例；
* maximum-scale – 允许用户缩放到的最大比例；

### 设置主屏幕(Spring Board)启动图标：
> Safari 浏览器有一个“添加到主屏幕”的功能，用户可以像保存书签一样把一个网站添加到主屏幕，下次用户直接点击主屏幕上的图标就能进入网站。
	
	<link rel="apple-touch-icon" href="icon.png" />

#### 因为 iOS 分辨率，所以 icon.png 图片的尺寸也各不相同，我们可以通过sizes属性来分别定义，iOS 系统会自动获取向匹配的图片：
	
	<!--默认为 57x57 像素-->
	<link rel="apple-touch-icon" href="touch-icon-iphone.png" />
	<!--iPad 1 72x72 像素-->
	<link rel="apple-touch-icon" sizes="72x72" href="touch-icon-ipad.png" />
	<!--iPhone 4 114x114 像素-->
	<link rel="apple-touch-icon" sizes="114x114" href="touch-icon-iphone4.png" />
		
### 全屏显示 WebApp，隐藏 safari 导航栏以及工具栏：
> 当我们点击主屏图标打开浏览器进入 WebApp 时，默认情况下 Safari 还是会显示顶部导航栏以及底部工具栏，但这不是我们想要的结果，它们不仅不美观还减少了显示面积，所以可以用以下代码隐藏它们，让 WebApp 像原生应用一样全屏显示：

	<meta name="apple-mobile-web-app-capable" content="yes" />
	
### 屏蔽iPhone下的拨号链接
	
	<meta name="format-detection" content="telephone=no"/>
	
### 链接拨号和发短讯

	<a href="tel:12345654321">打电话给我</a>
	<a href="sms:12345654321">发短信</a>

## 在线调试

### [Android with Chrme](https://developer.chrome.com/devtools/docs/remote-debugging)

