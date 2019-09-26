---
layout:     post
title:      golang指针符号 * 和 &
no-post-nav: true
category: golang
tags: [golang]
excerpt: 指针符号 * 和 &
---
## 符合 * 和 & 
&符号的意思是对变量取地址， 如：变量a的地址是&a
*符号的意思是对指针取值，如*&a,就是a变量所在地址的值，当然也就是a的值了

## 指针在struct reflect中的应用
```golang
func main() {
	type Son struct {
		name string
	}
	type Father struct {
		N    int
		name string
		son   Son
		son1  *Son
	}
	son := Son{"zhangwei"}
	son1 := Son{"zhangpeng"}

	n := Father{18, "zhangsan", son,&son1}
	nbb := reflect.ValueOf(n.son)
	temp := nbb.FieldByName("name").String()
	fmt.Println(temp)
	
	nbb1 := reflect.ValueOf(*n.son1)
	temp1 := nbb1.FieldByName("name").String()
	fmt.Println(temp1)

}
```

