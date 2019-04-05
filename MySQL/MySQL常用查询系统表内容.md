一、表操作：
1.查看表结构相关信息：
	1）desc 表名；这种方式查询到的信息有：字段名称、数据类型、是否为空、哪个是key、默认为啥、额外字段（缺点：居然没有注释信息）
	2）show create table 表名；这种方式查到的是你建表的时候的语句，这个对程序员最友好
	3）select*from information_schema.columns where table_schema = '数据库名' and table_name = '表名'；这个查询的虽然全面（字段有table_name,table_comment,column_name,column_comment等），但是语句太长，不好
2.删除表：
	1）drop table if exists 表名；最常用


二、表内数据操作：
1.清空表内数据：truncate table 表名；