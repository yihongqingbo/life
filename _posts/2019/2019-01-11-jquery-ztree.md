---
layout:     post
title:      ztree 常用方法
no-post-nav: true
category: web
tags: [web]
excerpt: jquery ztree 
---
## ztree的初始化方法
```js
	var ztree;
	$.get(url, function(data){
        ztree = $.fn.zTree.init($("#id"), setting, data);
    })
```

## ztree的基础配置
后台的不用组织树结构，数据是List<Entity>的格式就行
通过配置主键字段 父节点字段，跟节点值，节点名称就能正确显示
```js
var setting = {
    data: {
        simpleData: {
            enable: true,
            idKey: "id", //主键
            pIdKey: "parentId",//父节点是哪个字段
            rootPId: 0 // 跟节点值
        },
        key: {
            name:"description" // 节点名称显示json数据中的description
        }
    },
    callback: {
		onClick: function(event, treeId, treeNode){
		//onClick的回调函数
		}
	}
};
```
## ztree节点的选择

```js
	var treeObj = $.fn.zTree.getZTreeObj("id");
    var nodes = treeObj.getSelectedNodes();
	for (var int = 0; int < nodes.length; int++) {
    	console.log(nodes[int].id+"---"+nodes[int].name);
	}
```





