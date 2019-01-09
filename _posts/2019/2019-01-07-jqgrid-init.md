---
layout:     post
title:      jqGrid 初始化参数
no-post-nav: true
category: web
tags: [web]
excerpt: font css 
---

## jqGrid初始化参数
1. 鼠标滚动分页 scroll: 1
2. 底部显示统计信息 footerrow : true,userDataOnFooter : true,
3. 显示总记录数  viewrecords: true
4. 实现２行表头脚本 $("#list2").jqGrid('setGroupHeaders', {});

```js
function pageInit(){
    //创建jqGrid组件
    jQuery("#list2").jqGrid(
        {
            scroll: 1,//创建一个动态滚动的表格 作用：实现滚动鼠标加载数据
            url : 'data/JSONData.json',//组件创建完成之后请求数据的url
            datatype : "json",//请求数据返回的类型。可选json,xml,txt
            colNames : [ 'Inv No', 'Client', 'Date', '最大压力(Mpa)', '最小压力(Mpa)','最大流量(m/h)', '最小流量(m/h)' ],//jqGrid的列显示名字
            colModel : [ //jqGrid每一列的配置信息。包括名字，索引，宽度,对齐方式.....
                {name : 'id',index : 'id',width : 55 ,hidden:true},
                {name : 'name',index : 'name asc, invdate',width : 100,align : "center"},
                {name : 'invdate',index : 'invdate',width : 90,align : "center"},
                {name : 'amount',index : 'amount',width : 80,align : "center"},
                {name : 'tax',index : 'tax',width : 80,align : "center"},
                {name : 'total',index : 'total',width : 80,align : "center"},
                {name : 'note',index : 'note',width : 150,sortable : false}
            ],
            rowNum:10,//在grid上显示记录条数，这个参数是要被传递到后台
            mtype : "post",//向后台请求数据的ajax的类型。可选post,get
            gridview: true, //构造一行数据后添加到grid中，如果设为true则是将整个表格的数据都构造完成后再添加到grid中
          //  rownumbers: true,//是否显示序号
          //  rownumWidth: 40,//序号宽度
            pager : '#pager2',//表格页脚的占位符(一般是div)的id
            viewrecords: true,//显示总记录数
            footerrow : true,//在底部显示一列 用来显示统计数据
            userDataOnFooter : true,//把userData放到底部 用来显示统计数据
            ondblClickRow:function(row) {//双击事件
                var rowData = $('#list2').jqGrid('getRowData', row);
                alert(rowData.name);
            },
            altRows : true ,//画线的粗细
            grouping:false, //开启分组
            groupingView : {
                groupField : ['name'] //按字段分组
            },
            caption : "历史分析"//表格的标题名字

        });
        //实现２行表头脚本
		$("#list2").jqGrid('setGroupHeaders', {
			useColSpanStyle: true,
			groupHeaders:[
				{startColumnName:'name', numberOfColumns:2, titleText: '站点信息'},
				{startColumnName:'amount', numberOfColumns: 2, titleText: '压力'},
				{startColumnName:'total', numberOfColumns: 2, titleText: '流量'},
			]
		})

}
```





