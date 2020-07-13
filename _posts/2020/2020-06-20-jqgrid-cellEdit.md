---
layout:     post
title:       jqgrid 编辑表格
no-post-nav: true
category: js
tags: [js]
excerpt: 编辑表格
---

## jqgrid开启表编辑表格
	 cellsubmit:"clientArray",
	 cellEdit: true,
	 { label: '备注', name: 'remark',  width: 200  , sortable: false,editable : true}

## 当编辑表格之后，直接点击提交按钮，此时没有退出编辑模式，获取的值是input  解决方案如下

```html
定义两个变量 记录 最后一个编辑框，点击保存的时候，关闭闭合框
   var lastrow;  //最后修改行号先定义一个全局变量
    var lastcell; //最后修改列号

beforeEditCell: function (rowid, cellname, v, iRow, iCol) {
                	 lastrow = iRow;  //给全局变量赋值
                     lastcell = iCol;
                },
$('#table_list').jqGrid("saveCell", lastrow, lastcell);  //当前单元格退出编辑模
```

## 编辑的时候，每次都要选中值修改。如何默认选中单元格的值

```html
修改jqgrid源码：

在editCell : function (iRow,iCol, ed)方法里面

window.setTimeout(function () { $(elc).focus();},0);这句后面加下面这句话就可以：

$("input",cc).bind("focus",function(){this.select();});
```

## 选中一条记录，去编辑 结果触发点击事件 把选中的记录取消了。解决方案

```html
   onCellSelect : function(rowid, iCol, cellcontent, e) {
                	if(iCol !=18 ){
                		var mId ="#jqg_table_list_"+rowid;
            			if ($(mId).is(":checked")) {
            				 $("#"+rowid).removeClass("ui-state-highlight");
            				 $(mId).prop("checked", false);
            			} else {
            				 $("#"+rowid).addClass("ui-state-highlight");
            				 $(mId).prop("checked", true);
            			}
                	}
        		},
思路：编辑模式只能使用onCellSelect事件 不能使用onSelectRow 所以选中单元格的时候，把复选框勾上。
如果是编辑列，就不触发勾选
```

## 编辑状态，勾选是代码触发的，所以获取要用其他模式

```html
$("#" + id).jqGrid("getGridParam", "selarrrow");
此方法无法获取到勾选的行，需要使用下面的方法

var rows =[];
$("#table_list input:checkbox").each(function(){
if($(this).is(":checked")){
var id = $(this).attr('id');
rows.push(id.substring(15,id.length)); 
}
});
    	

```

