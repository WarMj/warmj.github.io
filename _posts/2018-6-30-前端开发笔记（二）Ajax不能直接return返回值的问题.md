---
layout: post
title: Ajax不能直接return返回值的问题
description: 细节问题，非常容易忽略
author: "WarMj"
categories: program
tags: [program,ajax,html,web]
image: 
---

写了一个请求，代码如下

	// 获取json数据
	function getJson(url) {
		var json;
		$.ajax({
					type : 'get',
					async : false,
					url : url,
					dataType : "json",
					data : {
						depId : "DD83B3658A2449FEBEE10C2E5AFBA33C12345"
					},
					success : function(result) {
	//					json = result;
						return result;
					},
					error : function(errorMsg) {
						alert("json数据请求失败");
					}
				});
				console.log("执行到此处");
	//	return json;
	}

发现直接 `return result` 并不能产生作用，于是在底下添加了 `console.log("执行到此处");`调试代码，发现执行了，说明 `return result` 并没有跳出整个函数，只是跳出了当前域，具体原因请看下方讲解。
![cnblogs-幻天芒
](https://upload-images.jianshu.io/upload_images/2864463-4b9e5d698251e955.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>原文链接：https://q.cnblogs.com/q/65549/




