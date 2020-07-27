---
layout:     post
title:       mybatis 常见问题
no-post-nav: true
category: java
tags: [java]
excerpt: sql mybatis
---

## 字符串切割
	<if test="monthId !=null and monthId !='' ">
		and month_id in
	<foreach item="key" collection="monthId.split(',')" open="(" separator="," close=")" >
		#{key}
		</foreach>
	</if>

## list循环

<if test="monthIds !=null and monthIds.length>0">

<foreach  collection="monthIds" index="index" item="key">

#{key}

</foreach>

</if>

## key Entity

```html
@MapKey("id")
Map<Long, Entity>  findByIds(@Param("ids") List<Long>  ids);
```

