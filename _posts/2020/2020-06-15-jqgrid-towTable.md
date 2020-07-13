layout:     post
title:       jqgrid 两级表格
no-post-nav: true
category: js
tags: [js]
excerpt: 两级表格
---

## jqgrid多级表格
	let _width = $(window).width() - 44;
	let _height = $(window).height() - 109;
	jQuery("#list").jqGrid(
		{
			url:url,
			datatype : "json",
			height: _height,
			width:_width,
			// autowidth:true,
			shrinkToFit:true,
			multiselect: true,//复选框 
			colModel: [
				{ label: 'id', name: 'id',key:true, width: 100,hidden:true },
				{ label: '名称', name: 'name',  width: 100, sortable: false }
			],
			viewrecords:true,
			hidegrid:false,
			rownumbers: false,  
			rowNum:-1,
			onSelectRow : function(code) {
			},
			subGrid: true,//开启子表格支持 
	        //子表格的id；当子表格展开的时候，在主表格中会创建一个div元素用来容纳子表格，subgrid_id就是这个div的id
	        subGridRowExpanded: function (subgrid_id, row_id) {//子表格容器的id和需要展开子表格的行id
	        	var subgrid_table_id;  
	            subgrid_table_id = subgrid_id + "_t";   // (3)根据subgrid_id定义对应的子表格的table的id  
	            // (5)动态添加子报表的table和pager   
	            $("#" + subgrid_id).html("<table id='"+subgrid_table_id+"' class='scroll'></table>");  
	            // (6)创建jqGrid对象   
	            $("#" + subgrid_table_id).jqGrid({  
	                url:路径,  // (7)子表格数据对应的url，注意传入的contact.id参数  
	                datatype: "json",  
	                colModel: [
	        			{ label: 'id', name: 'id',key:true, width: 100,hidden:true },
	        			{ label: '名称', name: 'name',  width: 150, sortable: false }		
	        		],
	                jsonReader: {   // (8)针对子表格的jsonReader设置  
	                    root:"gridModel",  
	                    records: "record",  
	                    repeatitems : false  
	                },  
	                postData: {"mainId":row_id},//传参
	                prmNames: {search: "search"},  
	                viewrecords: true,  
	                height: "100%",  
	                rowNum:-1,
	           });  
	       },           
			postData: {"mainIds":mainIds}, //传参
			loadui: "disable",
			loadComplete: function (data) {
		
			}
		});