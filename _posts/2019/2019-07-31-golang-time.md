---
layout:     post
title:      golang包time
no-post-nav: true
category: web
tags: [web]
excerpt: time Duration
---
## 时间点(time)
注意一点 java时间格式化 是 YYY-MM-DD HH:mm:ss
GoLang时间格式化是 2006-01-02 15:04:05 记忆是06年1月2号3点4分5秒

```GOLang

	fmt.Println(time.Now())
	fmt.Println(time.Now().Format("2006-01-02 15:04:05"))
	fmt.Println(time.Now().Format(time.ANSIC))
	tp,_:=time.ParseDuration("1.5s")
	time.Sleep(tp)
	fmt.Println(tp.Truncate(1000),tp.Seconds(),tp.Nanoseconds())

```

## 时间段(Duration)
java没有时间段函数。休眠sleep(3000) 默认单位就是ms
go有时间段。
```GOLang

	tp,_:=time.ParseDuration("1.5s")
	time.Sleep(tp)
	fmt.Println(tp.Truncate(1000),tp.Seconds(),tp.Nanoseconds())

```
