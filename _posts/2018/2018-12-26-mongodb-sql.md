---
layout:     post
title:      mongodb特殊语法
no-post-nav: true
category: bigData
tags: [bigData]
excerpt: mongodb
---
# sql语句支持js语法
for(i=3;i<100;i++)db.imooc_collection.insert({x:i})
# 只更新部分字段$set
db.imooc_collection.update({x:100},{$set:{y:200}})
# update不存在的数据时，可以转新增
db.imooc_collection.update({x:1000},{$set:{y:200}},true)
# 查询
1. 比较操作符 $lt $lte $gt $gte 分别对应 < <= > >=
2. 不等于 $ne





