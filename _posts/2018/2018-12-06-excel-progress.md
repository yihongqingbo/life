---
layout:     post
title:      java导入excel数据 前端展示进度的功能
no-post-nav: true
category: java
tags: [java]
excerpt: 只谈谈思路	
---
java 读取excel ，每读取一行message++,将message放到session里面
js定时器 ajax从session中获取message ,前端进度条展示进度
导入结束后，将message session置空
