---
layout: post
title: 如何实现鼠标悬停隐藏文字出现
categories: 泰牛程序员笔记
tags: 
- Display
- block
comments: true
---


#### 如何实现鼠标悬停隐藏文字出现
**1.普通导航条**

<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8" />
	<title>鼠标移动到图片文字显示</title>
	<style type="text/css">
	* {margin:0px; padding:0px;}
		
		/***
			设置li为相对定位		
		*/
		.content ul li {
			 float:left;
			 list-style:none;
			 position:relative;
		}
		/***
			设置隐藏文本为绝对定位
			并且把文本隐藏起来	
		*/
		.content li span{
			position:absolute;
			left:0px;
			bottom:2px;
			background:red;
			display:none;
			width:151px;

		}
		/***
			当鼠标移动到图片上，显示隐藏的文本
		*/
		ul li:hover span{
			display:block;
		}
	</style>
</head>
<body>
		<div class="content">
			<ul>
				<li>
					<a href="#"><img src="images/chanpin_img.jpg"></a>
					<span>PHP工程师</span>
				</li>
			</ul>
		</div>
</body>
</html>


#####效果图如下



![悬停显示](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "悬停显示")