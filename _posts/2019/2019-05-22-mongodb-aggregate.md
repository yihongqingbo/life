---
layout:     post
title:      mongodb聚合
no-post-nav: true
category: bigData
tags: [bigData]
excerpt: mongodb
---
## 插入数据 string和double两种类型
```js
db.getCollection('test_water').insert({deviceId:"110",num:50.5});
db.getCollection('test_water').insert({deviceId:"110",num:20.5});
db.getCollection('test_water').insert({deviceId:"110",num:30.5});
db.getCollection('test_water').insert({deviceId:"120",num:"50.5"});
db.getCollection('test_water').insert({deviceId:"120",num:"20.5"});
db.getCollection('test_water').insert({deviceId:"120",num:"30.5"});
```
效果图：
![](/assets/images/2019/20190522_1.png)

## 聚合查询
```js
db.getCollection('test_water').aggregate([{$group:{_id:"$deviceId",sum_num:{$sum:"$num"},avg_num:{$avg:"$num"},
max_num:{$max:"$num"},min_num:{$min:"$num"},first_num:{$first:"$num"},last_num:{$last:"$num"}}}]);
```
效果图：字符类型的聚合查不到sum和avg
![](/assets/images/2019/20190522_2.png)

## 数据类型转换 string转为double类型
[Mongodb的类型转换](https://www.cnblogs.com/pyspark/p/8817692.html)
```js
db.getCollection('test_water').find().forEach( function (x) {
  x.num = parseInt(x.num);
  db.getCollection('test_water').save(x);
});
```
## 聚合查询 效果图：
![](/assets/images/2019/20190522_3.png)


