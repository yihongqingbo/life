---
layout:     post
title:      golang并发和通道
no-post-nav: true
category: golang
tags: [golang]
excerpt: goroutine channel
---
## 单个goroutine的创建
goroutine是轻量级的线程，与java线程相比，创建成本和开销都很小
在函数或者方法前面加上关键字go,即创建了一个并发运行的新goruotine
```GOLang

	func HelloWorld(){
		fmt.Println("hello goroutine")
	}
	func main(){
		go HelloWorld() //开启一个新的并发运行
		time.Sleep(1*time.Seconds)// 等待新线程运行完，再往下执行
		fmt.Println("主函数结束")
	}

```

如果主函数不休眠，HelloWorld()函数还没结束，主函数就结束了，那么HelloWorld()也就暴力结束了。
主函数休息多长时间合适呢？显然让主函数休眠不合理。等待新的并发程序运行，这就需要通道了channel
## 通道(channel)
通道可以让一个goroutine发送特定的值到灵感一个goroutine的通信机制，
通道是阻塞的，有输入有输出 不然就阻塞。垃圾回收机制会自动回收channel
```GOLang
	var done chan bool
	func HelloWorld(){
		fmt.Println("hello goroutine")
		done <- true
	}
	func main(){
		done = make(chan bool)
		go HelloWorld() //开启一个新的并发运行
		<- done
	}

```
