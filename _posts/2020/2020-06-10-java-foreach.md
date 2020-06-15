---
layout:     post
title:       遍历删除
no-post-nav: true
category: java
tags: [java]
excerpt: 遍历删除常见问题
---

## 遍历删除正确方式：倒序操作
		List<String> main = new ArrayList<String>();
		main.add(String.valueOf(5));
		for (int i = 0; i < 10; i++) {
			main.add(String.valueOf(i));
		}
		main.add(String.valueOf(5));
		int len = main.size();
		for(int i=len-1;i>=0;i--){
			String aa = main.get(i);
			if(aa.equals("5")) {
				main.remove(i);
			}
		}
		for (String string : main) {
			System.out.print(string+" ");
		}

结果：0 1 2 3 4 6 7 8 9 

## 错误1：集合长度一直变化

```
List<String> main = new ArrayList<String>();
		main.add(String.valueOf(5));
		for (int i = 0; i < 10; i++) {
			main.add(String.valueOf(i));
		}
		main.add(String.valueOf(5));
		main.add(String.valueOf(5));
		for (int i = 0; i <  main.size(); i++) {
			System.out.print(main.size()+" ");
			String aa = main.get(i);
			if(aa.equals("5")) {
				main.remove(i);
			}
		}
		System.out.println("");
		for (String string : main) {
			System.out.print(string+" ");
		}
```

结果：13 12 12 12 12 12 11 11 11 11 
            0 1 2 3 4 6 7 8 9 5 


## 错误2：集合长度不变，空指针
```
List<String> main = new ArrayList<String>();
		main.add(String.valueOf(5));
		for (int i = 0; i < 10; i++) {
			main.add(String.valueOf(i));
		}
		main.add(String.valueOf(5));
		main.add(String.valueOf(5));
		int len = main.size();
		for (int i = 0; i < len; i++) {
			String aa = main.get(i);
			if(aa.equals("5")) {
				main.remove(i);
			}
		}
		for (String string : main) {
			System.out.print(string+" ");
		}
```

结果： java.lang.IndexOutOfBoundsException

