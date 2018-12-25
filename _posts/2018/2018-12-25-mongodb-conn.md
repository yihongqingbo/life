---
layout:     post
title:      mongodb远程连接配置
no-post-nav: true
category: bigData
tags: [bigData]
excerpt: mongodb
---
# 创建配置文件mongodb.conf
配置文件内容如下
```shell
bind_ip=0.0.0.0 #任何主机都能够连接
port=27017 #端口
dbpath=/apps/mongodb/dbdata #数据存储地址
logpath=/apps/mongodb/mongodb.log #日志文件的路径
fork=true #后台进程
```
# 使用配置文件 启动mongodb
```shell
cd /apps/mongodb  #切换到mongodb 目录
./bin/mongod -f mongodb.conf #使用mongodb.conf配置文件启动服务
``` 
# 如果开启防火墙，添加某个端口访问操作
修改/etc/sysconfig/iptables文件，添加如下内容:
```shell
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
-A INPUT -p icmp -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -m state --state NEW -m tcp -p tcp --dport 22 -j ACCEPT
-A INPUT -m state --state NEW -m tcp -p tcp --dport 27017 -j ACCEPT
-A INPUT -j REJECT --reject-with icmp-host-prohibited
-A FORWARD -j REJECT --reject-with icmp-host-prohibited
```
#重启防火墙
ervice iptables restart

# 连接mongodb
```shell
cd /apps/mongodb/bin  #切换到bin 目录
./mongod ip:27017
```


