---
layout:     post
title:      mongodb备份恢复导入导出
no-post-nav: true
category: bigData
tags: [bigData]
excerpt: mongodb
---
## 说明
mongodump,mongorestore,mongoexport 这些命令如果在cmd下不识别，就需要切换到monogdb安装的bin目录下运行。
备份和恢复是对整体数据库操作的。如果需要在原来的数据库中追加数据，就需要使用导入 

## 备份
```js
mongodump -h dbhost -d dbname -o dbdirectory
例如
mongodump -h 10.10.0.132 -d test -o D:/data
```
## 恢复
```js
恢复
mongorestore -h dbhost -d dbname --dir dbdirectory
例如 
mongorestore -h 10.12.42.112 -d test --dir d:/data/test
```

## 导出
```js
mongoexport -h dbhost -d dbname -c collectionname -f collectionKey -o dbdirectory
例如
mongoexport -h 127.0.0.1 -d test -c test_water -o D:\data\test_water.json
```

## 导入
```js
mongoimport -h IP --port 端口  -d 数据库 -c 表名  --upsert --drop 文件名
例如
mongoimport -h 127.0.0.1 --port 27017  -d test -c test_water --upsert --file D:\data\test_water.json
```



