## Mysql表基本数据类型
整数类型：BIT、BOOL、TINY INT、SMALL INT、MEDIUM INT、 INT、 BIG INT

浮点数类型：FLOAT、DOUBLE、DECIMAL

字符串类型：CHAR、VARCHAR、TINY TEXT、TEXT、MEDIUM TEXT、LONGTEXT、TINY BLOB、BLOB、MEDIUM BLOB、LONG BLOB

日期类型：Date、DateTime、TimeStamp、Time、Year

其他数据类型：BINARY、VARBINARY、ENUM、SET、Geometry、Point、MultiPoint、LineString、MultiLineString、Polygon、GeometryCollection等

## 用sql语句创建表
```
create table tbname(id int auto_increment primary key);
```
## 插入数据
```
insert into tbname(id) value(1);
```
## 删除表
```
truncate 和delete只删除数据， drop则删除整个表（结构和数据）
```
## 修改表
```
/*修改列名*/
ALTER TABLE testalter_tbl CHANGE old new type;
/*修改数据*/
update tbname set name='zhangsan' where id=1;
/*删除列*/
alter table tbname drop column_name;
/*删除行*/
delete from tbname where id = 1;
/*新建列*/
alter table tbname add column_name,data_type
/*新建行*/
insert into tbname(id) value(1);
```


## 作业三

```
/*创建表*/
create table courses(id int auto_increment primary key,student varchar(16),class varchar(16));
/*插入数据*/
insert into courses(student,class) values('A','Math');
insert into courses(student,class) values('B','English');
insert into courses(student,class) values('C','Math');
insert into courses(student,class) values('D','Biology');
insert into courses(student,class) values('E','Math');
insert into courses(student,class) values('F','Computer');
insert into courses(student,class) values('G','Math');
insert into courses(student,class) values('H','Math');
insert into courses(student,class) values('I','Math');
insert into courses(student,class) values('A','Math');
/*查询结果*/
SELECT class,count(DISTINCT student,class) as counts from courses GROUP BY class HAVING counts >= 5;
```

## 作业四
```
/*创建表*/
create table salary(id int auto_increment primary key,name varchar(16),sex varchar(16),salary int);
/*插入数据*/
insert into salary(name,sex,salary) values('A','m',2500);
insert into salary(name,sex,salary) values('B','f',1500);
insert into salary(name,sex,salary) values('C','m',5500);
insert into salary(name,sex,salary) values('D','f',500);
/*查询结果*/
update salary set Sex = case Sex when 'f' then 'm' when 'm' then 'f' end;
```


## MySQL别名
MySQL支持两种别名，称为列别名和表别名
```
SELECT
id,
COUNT(o.name) [as] total	#列别名
FROM
customers [as] c	INNER JOIN orders [as] o #表别名
```
## INNER JOIN
INNER JOIN子句将一个表中的行与其他表中的行进行匹配，并允许从两个表中查询包含列的行记录
```
SELECT column_list
FROM t1
INNER JOIN t2 ON join_condition1
INNER JOIN t3 ON join_condition2
...
WHERE where_conditions;
```

## LEFT JOIN
左连接LEFT JOIN的含义就是求两个表的交集外加左表剩下的数据。依旧从笛卡尔积的角度讲，就是先从笛卡尔积中挑出ON子句条件成立的记录
```
SELECT * FROM t1 LEFT JOIN t2 ON t1.typeId=t2.id;

```
## CROSS JOIN
笛卡尔积就是将A表的每一条记录与B表的每一条记录强行拼在一起。所以，如果A表有n条记录，B表有m条记录，笛卡尔积产生的结果就会产生n*m条记录
```
SELECT * FROM
    T1
        CROSS JOIN
    T2
WHERE
    T1.id = T2.id;
```
## UNION
union查询就是把2条或者多条sql语句的查询结果，合并成一个结果集
```
SELECT id,num FROM num_a UNION SELECT id, num FROM num_b
```
## 自连接
然连接就是USING子句的简化版，它找出两个表中相同的列作为连接条件进行连接
```
select a.ename ,a.empno ,b.ename ,b.empno   from emp a,emp b where a.mgr = b.empno; 
```

## 用法场景
[参考文档](https://www.cnblogs.com/gzh0815/archive/2018/10/18/9808829.html)
> 内连接（INNER JOIN）：当两个表中都存在匹配时，才返回行。

> 左连接（LEFT JOIN）：返回左表中的所有行，即使右表中没有匹配的行。

> 右连接（RIGHT JOIN）：返回右表中的所有行，即使左表中没有匹配的行

> 全连接（FULL JOIN）：只要某一个表存在匹配，就返回行。

> 笛卡尔连接（CARTESIAN JOIN）：返回两个或者更多的表中记录集的笛卡尔积。

> CROSS JOIN 子句从连接的表返回行的笛卡儿乘积

> 自然连接：在连接条件中使用等于(=)运算符比较被连接列的列值，但它使用选择列表指出查询结果集合中所包括的列，并删除连接表中的重复列。

## 作业五
```
SELECt firstname,lastname,city,state FROM person INNER JOIN address on person.PersonId = address.PersonId

```

## 作业六
```
DELETE FROM email WHERE email.ID in (
SELECT id from( SELECT max(id) as id FROM email as e GROUP BY e.Email HAVING count(e.Email) > 1) as a)
```