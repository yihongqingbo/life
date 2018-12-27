---
layout:     post
title:      spring-boot中controller，service，serviceImpl，dao，xml的理解
no-post-nav: true
category: bigData
tags: [bigData]
excerpt: spring-boot 后台结构
---
# spring-booth后台约定俗成的几个文件作用
![](/assets/images/2018/20181227_1.png)
一个接口一个实现类的情况下，@Service 不用起名字
一个接口多个实现类的情况下,@Service("name") 需要起名字
service 使用标注@Qualifier("name") 选择实现类

# spring Boot1.5X升级到2.0指南
SpringBoot升级参考资料：[spring-boot升级](https://blog.csdn.net/vqhgWJl9EUB/article/details/81187359)




