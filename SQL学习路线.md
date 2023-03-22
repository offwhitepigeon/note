SQL	学习路线

1.mySQL基本命令语句

cmd 连接mysql   mysql -u root -p

mySQL

查询某表格

```sql
SELECT * FROM <TABLE_NAME>;
#限制条件
SELECT * FROM <T_N> WHERE <condition> AND <condition>;
#NOT AND OR 按层级减弱
#<>可以用来判断不等
#LIKE 可以用来判断相似（匹配）
SELECT <COL_NAME,...> ~~;
#从指定列查询
SELECT <COL_NAME RENAME,...> ~~;
#将列名字替换为rename
SELECT * FROM <> ORDER BY <COL_NAME>;
#按照col排序 默认ASG 使用DESC倒序，接colname后
#相同的col值再在COLNAME后加<，colname>
#ORDER BY behind where
SELECT ... LIMIT <INT1> OFFSET <INT2>;
#分页输出 从int2开始，最多获取int1条数据
#可以简写成LIMIT INT1,INT2

SELECT COUNT(*) FROM table_nams;
#查询表格有多少记录
SELECT COUNT(*) ANS_name ~;
#由于返回的是一个表格一行一列，可以赋予列名
#可搭配WHERE条件使用
/*SQL内置函数还有
	SUM 某列和 列需为数值
	AVG 平均值 列需为数值
	MAX 最大值 
	MIN 最小值
*/

 SELECT COUNT(*) <name> FROM <> GROUP BY <col_name2>;
#按照colname2对from进行分组聚合
SELECT <col_name1>, COUNT(*) <name> ~~;
#分组聚合返回colname1 和name的表格
SELECT <col-name1,col_name2> ~~ BY <name1,name2>;
#获得在两个条件下均满足的结果,多重聚合

SELECT 
	<name1>.<col_name1> rename1,
	<name2>.<col_name2> rename2
FROM <table_name1> <name1>,<table_name2> <name2>;
#多表查询

SELECT * FROM <table_name> t_name
INNER JOIN <table_name_2> t_name_2
ON t.col_name = t2.col_name;
#内连接查询，ON连接两个表的对应字段（同处）
SELECT ~~
RIGHT OUTER JOIN <table_name> t_name
ON ~;
#外连接查询，内连接返回两张表都存在的数据
#外连接根据关键字RIGHT LEFT FULL分别获取左表、有表、全表存在的数据
#所以，确定主表，也就是左表非常关键！！！

```

修改数据

```sql
INSERT INTO <table_name>(col_name1,col_name2)
VALUES (value1,value2)，(value1,value2)
#插入数据，可多条

UPDATE <table_name>
SET <col_name1>=value1,... 
WHERE <col_name> = value;
#修改数据，可多条
#SET 后可跟表达式
#实际中，总是先用SELECT语句查询WHERE条件筛选的是否准确，然后再调用UPDATE更新

DELETE FROM <table_name>
WHERE ...;
#删除数据
#实际中，总是先用SELECT语句查询WHERE条件筛选的是否准确，然后再调用DELETE删除

```



mySQL语法

```sql
SHOW DATABASES;#查询数据库
CREATE DATABASE <DATABASE_name>;#创建数据库
DROP DATABASE <DATABASE_name>;#删除数据库
USE <DATABASE_name>;#进入某数据库

SHOW TABLES;#查询表
DESC <table_name>;#查询表结构
SHOW CREATE TABLE <table_name>;#查询创建表语句
CREATE TABLE <table_name>;#创建表
DROP TABLE <table_name>;#删除表

ALTER TABLE <table_name> ADD COLUMN <col_name> VARCHAR(10) NOT NULL;#创建列
ALTER TABLE <table_name> CHANGE COLUMN <col_name> <col_name> <name> VARCHAR(20) NOT NULL;#修改列
ALTER TABLE <table_name> DROP COLUMN <col_name>day;#删除列

```

常见问题

1.排序问题
