---
layout:     post
title:     http thread
no-post-nav: true
category: golang
tags: [golang]
excerpt: http请求和线程
---
## 想想一个问题场景

一个车间能最多能注册1万台设备。多个用户同时注册设备，数量可能超过1万。

解决思路：车间表添加一个字段plan(此次请求要添加的设备数量)，当用户发送请求到后台时(创建N个设备)。设置数据库表值 plan = plan+ N。当前车间下设备数量为num。 if num+plan >1万{设置表值plan = plan- N}else{

添加N个设备之后，设置表值plan = plan- N}

## 模拟http请求，观察多个请求的关系

两个浏览器同时访问一个地址请求
```golang
package main

import (
	"fmt"
	"net/http"
	"time"
)
func IndexHandle(w http.ResponseWriter,r *http.Request){
	if r.RequestURI == "/favicon.ico"{
		return
	}
	fmt.Println("request begin time ：",time.Now().Format("2006-01-02 03:04:05"))
	tp,_ :=time.ParseDuration("5s")
	time.Sleep(tp)
	fmt.Println("request end time：",time.Now().Format("2006-01-02 03:04:05"))
	fmt.Fprint(w,"hello world ")
}

func main() {
	http.HandleFunc("/",IndexHandle)
	_ = http.ListenAndServe("127.0.0.1:8080", nil)
}

```
执行结果 如下，说明：每个请求启用个线程，相互之间不阻塞
```json
API server listening at: 127.0.0.1:54773
request begin time ： 2019-09-30 10:40:55
request begin time ： 2019-09-30 10:40:57
request end time： 2019-09-30 10:41:00
request end time： 2019-09-30 10:41:02
```
