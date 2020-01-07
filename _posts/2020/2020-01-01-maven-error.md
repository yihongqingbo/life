---
layout:     post
title:       pom文件常见错误解决方案
no-post-nav: true
category: maven
tags: [maven]
excerpt: pom maven err solve
---

## 

## line 1 :maven configuration problem
```json
添加 配置内容
  <properties>
        <maven-jar-plugin.version>3.0.0</maven-jar-plugin.version>
</properties>
然后 maven --> update project
```

## 缺少jar包，然后硬盘中已存在
```json
Project -->clean
然后 maven --> update project
```

