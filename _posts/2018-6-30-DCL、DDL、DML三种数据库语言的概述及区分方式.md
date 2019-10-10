---
layout: post
title: DCL、DDL、DML三种数据库语言的概述及区分方式
description: 基础知识
author: "WarMj"
categories: databases
tags: [databases,mysql,oracle]
image: 
---

|语言|概述|语句|
|:-------|:--------|:------|:------|
|DCL（Data Control Language 数据控制语言）|控制数据库对象的权限，这些操作的确定使数据更加的安全。<br>操作对象：数据库用户|Grant：允许对象的创建者给某用户或某组或所有用户（PUBLIC）某些特定的权限。<br>Revoke：可以废除某用户或某组或所有用户访问权限。<br><br>Rollback：回滚。<br><br>Commit：提交。|
|DDL（Data Definition Language 数据定义语言）|用于操作对象和对象的属性，这种对象包括数据库本身，以及数据库对象，如表、视图等等，DDL对这些对象和属性的管理和定义具体表现在Create、Drop和Alter上。特别注意：DDL操作的“对象”的概念，”对象“包括对象及对象的属性，而且对象最小也比记录大个层次。以表举例：Create创建数据表，Alter可以更改该表的字段，Drop可以删除这个表，从这里我们可以看到，DDL所站的高度，不会对具体的数据进行操作<br>操作对象：对象和对象的属性|Create：可以创建数据库和数据库的一些对象<br><br>Create：可以创建数据库和数据库的一些对象<br><br>Alter：修改数据表结构、定义及属性<br><br>Truncate：清除表格中的所有记录|
|DML（Data Manipulation Language 数据操控语言）|用于操作数据库对象中包含的数据，也就是说操作的单位是记录<br>操作对象：具体数据|Select：查询表内的数据记录<br><br>Insert：向数据表张插入一条记录<br><br>Update：用于修改已存在表中的记录的内容<br><br>Delete：删除数据表中的一条或多条记录，也可以删除数据表中的所有记录<br><br>Order By：排序|
#区分方式
1. DDL不需要提交，不能回滚，立即生效
2. DML需要提交（commit），可以回滚（rollback）
