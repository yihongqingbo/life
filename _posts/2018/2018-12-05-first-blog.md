---
layout:     post
title:      使用Jekyll gitalk搭建博客遇到问题
no-post-nav: true
category: life
tags: [life]
excerpt: 初次尝试搭建博客	
---
# fork一份Jekyll主题之后，博客请求不到js，css
博客是https地址，不能请求http资源。把js,css资源改成本仓库的地址
修改界面是_includes文件下的head.html 、 footer.html、 comments.html 

#博客无法评论 Error:Not Found问题 
在评论组件上方页面提示 Error: Not Found. 一般是由于 repo 填写错误
repo是仓库名称 （用来存放评论的仓库名）

![](https://yihongqingbo.github.io/assets/images/2018/projectNmae.png)
