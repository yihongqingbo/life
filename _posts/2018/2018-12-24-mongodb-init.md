---
layout:     post
title:      mongodb在lunix上的安装部署
no-post-nav: true
category: bigData
tags: [bigData]
excerpt: mongodb
---
例子：[demo](/assets/files/2018/penguin.html)
# html中图片上画框
这种应用场景很多，工艺图片上添加文字描述。人物图片上画图头像框
原理：图片作为div的背景图片。在div中添加文字或元素
```css
	#img2{
	width:350px;
	height:250px;
	background:url(penguin.png) no-repeat;
	background-size:contain;
	border:solid 1px #000;
	}

	#secondhead{
	width:80px;
	height:80px;
	position:absolute;
	left:150px;
	top:30px;
	border: 1px solid #f00;
	}
``` 
# html中图片的局部放大
这种应用场景有：比较两个图片差异处的时候，进行放大。
原理：图片作为div的背景图片。div的宽高是局部大小的N倍。
根据background-position:x y，设置图片位置的移动。
图片一般需要向右上移动，所以x,y为负数

```css
	#bigimg{
	width:160px;
	height:160px;

	background:url(penguin.png) no-repeat;
	background-position: -300px -60px;
	border:solid 1px #000;
	}
``` 

