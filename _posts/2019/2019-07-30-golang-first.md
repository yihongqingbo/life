---
layout:     post
title:      golang入门
no-post-nav: true
category: web
tags: [web]
excerpt: goLang hello world
---
## 认知golang
公司外派，机缘巧合之下，新项目需要使用golang语言开发，就开始学习golang。工作需要加之有java开发基础，学习了解golang还蛮顺利。
java是1996年发布的第一版JDK。GO于2009年推出。java作为后端开发，go也可以做后端开发。有人说java能做的go都能做。10多年的年龄差，go很好的弥补了java的不方便之处。
大有长江后浪推前浪之势。javaweb招聘100多页，而GO招聘只有一页。这也说明GO比较小众。替代java是不可能了，有项目用GO，就说明有它的优势。还是值得学习的


## package
GO文件，包名可以和文件夹名字不同。如文件夹test下新建hello1.go文件，package aa,也可以是 package bb。但最好是对于起来。再建一个文件hello2.go，这两个文件的包名必须一样。
主函数 是 func mian(){} 主函数文件的包名必须是 package main。
```goLang
package main
import (
	"fmt"
)
func main(){
	fmt.Println("hello world ")
}
```

## GoPath路径
项目必须放到D:\GoPath\src\ 下，知道之后，感觉挺方便的



