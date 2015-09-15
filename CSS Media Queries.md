# CSS Media Queries for iPads & iPhones

## iPad Media Queries

### 1、iPad Media Queries (所有版本，包括iPad mini)

	@media only screen and (min-device-width : 768px) and (max-device-width : 1024px)  { 
		/* 样式写在这里 */
	}

### 2、iPad3和iPad4 
> iPad3和iPad4具有Retina屏幕技术，如果你想针对Retina屏幕使用@2x的图像，来区别普通屏幕下的显示，那么使用下面的Media Queries会让你很轻松实现。

	@media only screen and (min-device-width : 768px) and (max-device-width : 1024px)and (-webkit-min-device-pixel-ratio: 2) { 
		/* 样式写在这里 */
	}
	// 区别portrait 和 landscape
	@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) and (orientation : landscape) and (-webkit-min-device-pixel-ratio: 2) { 
		/* 样式写在这里 */
	}

### 3、iPad 1 和 iPad 2 Media Queries

	@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) and (-webkit-min-device-pixel-ratio: 1){ 
		/* 样式写在这里 */
	}



## iPhone Media Queries

### 1、iPhone 5 Media Queries

	@media only screen and (min-device-width : 320px) and (max-device-width : 568px) { 
		/* 样式写在这里 */
	}
	
### 2、iPhone 2G, 3G, 4, 4S Media Queries

	@media only screen and (min-device-width : 320px) and (max-device-width : 480px) { 
		/* 样式写在这里 */
	}

### 3、iPhone 5 Media Queries

	@media only screen and (min-device-width : 320px) and (max-device-width : 568px) { 
		/* 样式写在这里 */
	}

### 4、iPhone 6 Media Queries

	@media only screen and (min-device-width: 375px) and (max-device-width: 667px) {
	    /*iPhone 6 Portrait*/
	}

	@media only screen and (min-device-width: 414px) and (max-device-width: 736px) {
	    /*iPhone 6+ Portrait*/
	}

	@media only screen and (max-device-width: 640px), only screen and (max-device-width: 667px), only screen and (max-width: 480px){
    	/*iPhone 6 and iPhone 6+ portrait and landscape*/
	}


> 来源：http://www.stephen.io/mediaqueries/

