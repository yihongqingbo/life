---
layout:     post
title:     golang 常用方法
no-post-nav: true
category: golang
tags: [golang]
excerpt: golang 常用方法
---
## 字符长度 要用rune方法
```GOlang
aa := "店舗名（カナ）"
fmt.Println(len([]rune(aa))
```
## 切割空字符串 长度是一
```go
	storeFields := strings.Split("", ",")
	for i, v := range storeFields {
		if i == 0 && v == "" {
			fmt.Println("空")
		}
		fmt.Println(i, v)
	}
```

## 遍历排序数组

```go
	assistArray := make([]string, 0)
	assistArray = append(assistArray, "M000115ALP")
	assistArray = append(assistArray, "M000119UPI")
	assistArray = append(assistArray, "M000115WXP")
	assistArray = append(assistArray, "M000115UPI")

	for i, key := range assistArray {
	fmt.Println(i,key)
	}
	sort.Sort(sort.StringSlice(assistArray))
	for _, key := range assistArray {
		fmt.Println(key)
	}
```
