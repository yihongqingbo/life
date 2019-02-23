---
layout:     post
title:      Java利用反射访问类的私有属性
no-post-nav: true
category: bigData
tags: [bigData]
excerpt: java private reflect
---

## 使用场景
<p>想象一种场景：JSON数据{"name":"li","age":10}如何填充到java类Person中</p>
<p>想象例外一种情况：java类Person 有属性name1,name2,...name100...,怎么设置属性的每一个值</p>
<p>解决上面的问题，就要用到反射</p>

## 定义一个类Person
```java
public class Person {
		private Long id;
		private String name;
		private Double money;
		private Date createTime;
		public Long getId() {
			return id;
		}
		public void setId(Long id) {
			this.id = id;
		}
		...
}
```
## 使用反射 为类的属性赋值

```java
public static Person  reflectSet(Person person){
		String names[]= {"id","name","money","createTime"};
		Object values[]={10L,"张三",100.50,new Date()};
		try {
			for(int i=0;i<4;i++){
				Field f;
				f = person.getClass().getDeclaredField(names[i]);
				System.out.println("属性类型:"+f.getGenericType().toString());
				f.setAccessible(true);
		        f.set(person, values[i]);
			}
			
		} catch (Exception e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		} 
		return person;
	}
	
```

## 使用反射访问类的私有属性值
```java
public static Person  reflectGet(Person person){
		String names[]= {"id","name","money","createTime"};
		try {
			for(int i=0;i<4;i++){
			 Method m = (Method) person.getClass().getMethod("get" + getMethodName(names[i]));
				
			  Object vala = m.invoke(person);// 调用getter方法获取属性值
			  System.out.println(names[i]+":"+vala);
			}
			
		} catch (Exception e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		} 
		return person;
	}
	
	// 把一个字符串的第一个字母大写
		 private static String getMethodName(String fildeName) throws Exception{
		  byte[] items = fildeName.getBytes();
		  items[0] = (byte) ((char) items[0] - 'a' + 'A');
		  return new String(items);
		 }
```



