---
layout:     post
title:      前端好用的方法
no-post-nav: true
category: web
tags: [web]
excerpt: js css 好用方法分享
---

## isNaN(x)
js 检验其参数是否是 非数字值，null ,"", 10.5 均为true。表单检验数字类型的 很好用
```js
function validateEntity(entity){
	var flag = true;
	var message =[];
	
	if(isNaN(entity.monney)){
		flag=false
		message.push("金额必须是数字");
	}
	if(isNaN(entity.age)){
		flag=false
		message.push("年龄必须是数字");
	}
	
	if(!flag){
		return message.join("<br>"); 
	}else{
		return null;
	}
	
}
```
## css伪元素 :after :before  常结合 content使用
```css
        h5:before{
            content: "我在内容前";
        }
        h5:after{
            content: "我在元素后";
        }
	
<h5> 我是元素h5 </h5>
```
效果为： 我在内容前 我是元素h5 我在元素后

##  css3 视口高度 vh
<p>通常我们要设置div高度为浏览器可视高度，而height:100% 是无效的。需要js设置元素高度为浏览器的可视高度 div.height =$(window).height()。</p>
<p>缺点很明显：div的样式 需要js去控制</p>
<p>height:97vh 高度等于视口高度的97%。因为 html body div 是有内边距 边框 的原因，如果设置div为100vh，出现滚动条。所以设置成97vh就行了
</p>
<p>如果是<div style="height:97vh"><div style="height:100vh"></div></div>;里面的div会比外面的div高。因为vh是视口单位。所以我们应该这样写：
<div style="height:97vh"><div style="height:100%"></div></div>,里面的div就用百分百就行</p>


