---
layout:     post
title:       mybatis-plus
no-post-nav: true
category: web
tags: [web]
excerpt: pom maven err solve
---

## 表的映射
@TableName("tableName")
## 主键标识
@TableId
## 字段映射
@TableFile("name")

## BaseMapper.insert()
根据雪花算法自动填充id。实体Id类型必须是Long

## 数据库表中不对应的字段

@TableFiled(exist=fasle)

## eclipse中new一个对象,前面的补齐代码是哪个快捷键

shift+alt+L

