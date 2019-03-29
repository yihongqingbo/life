---
layout:     post
title:      spring-boot-@RequestParam
no-post-nav: true
category: bigData
tags: [bigData]
excerpt: java private reflect
---

## 使用场景
ajax post get向后台传递参数，spring-boot可以使用 @RequestParam @PathVariable @RequestBody接收

## @PathVariable
通过@PathVariable，例如/blogs/1

## @RequestParam
通过@RequestParam，例如blogs?blogId=1

## @RequestBody
@RequestBody主要用来接收前端传递给后端的json字符串中的数据的(请求体中的数据的);
GET方式无请求体，所以使用@RequestBody接收数据时，前端不能使用GET方式提交数据，而是用POST方式进行提交。




