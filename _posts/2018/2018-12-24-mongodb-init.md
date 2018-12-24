---
layout:     post
title:      mongodb在lunix上的安装部署
no-post-nav: true
category: bigData
tags: [bigData]
excerpt: mongodb
---
# 下载安装包
下载地址：[mongodb](https://www.mongodb.com/download-center/community)

# 解压 拷贝到指定目录
```shell
tar -zxvf mongodb-linux-x86_64-3.0.6.tgz                           # 解压
mv  mongodb-linux-x86_64-3.0.6/ /apps/mongodb                 # 将解压包拷贝到指定目录
``` 
# 创建数据存储文件夹和日志文件
需要创建mongoDB的数据存储目录 ，日志文件
```shell
mkdir dbdata
touch mongodb.log
``` 
![](https://yihongqingbo.github.io/assets/images/2018/20181224_1.png)
# 启动数据库服务器
```shell
cd /apps/mongodb/bin  #切换到bin 目录
./mongod -dbpath=/apps/mongodb/dbdata -logpath=/apps/mongodb/mongodb.log -logappend -port=27017 -fork
``` 
常用的启动参数：
   --dbpath：指定存储数据的文件夹
   --logpath：指定日志存储文件
   --logappend：日志以增加方式产生
   --port指定端口，如果不写的话，默认是27017
   --fork代表后台运行
启动成功的界面（加了后台启动参数fork）
![](https://yihongqingbo.github.io/assets/images/2018/20181224_2.png)
# 停止mongodb
```shell
./mongod -shutdown -dbpath=/apps/mongodb/dbdata
```
![](https://yihongqingbo.github.io/assets/images/2018/20181224_3.png)
# 连接mongodb
进入mongodb命令行
```shell
cd /apps/mongodb/bin  #切换到bin 目录
./mongod
```
也可以通过mongoVUE这个可视化工具连接
下载地址：[mongoVUE](https://www.newasp.net/soft/396162.html)

