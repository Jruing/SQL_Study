## Sql是什么，MySQL是什么
Sql是一种特殊目的的编程语言，是一种数据库查询语言。
MySQL是关系型数据库管理系统

## 去重语句
```
SELECT DISTINCT email FROM email; 查询去重后的结果
```
## 前N个结果
```
SELECT email from email LIMIT 0,N; 查询前N个结果
```
##  CASE...END判断语句
```
SELECT CASE 
	WHEN email = 'a@b.com' THEN
		'zhangsan'
	ELSE
		'lisi'
END FROM email;
```
## where
```
符号	描述	备注
=	等于	
<>, !=	不等于	
>	大于	
<	小于	
<=	小于等于	
>=	大于等于	
BETWEEN	在两值之间	>=min&&<=max
NOT BETWEEN	不在两值之间	
IN	在集合中	
NOT IN	不在集合中	
<=>	严格比较两个NULL值是否相等	两个操作码均为NULL时，其所得值为1；而当一个操作码为NULL时，其所得值为0
LIKE	模糊匹配	
REGEXP 或 RLIKE	正则式匹配	
IS NULL	为空	
IS NOT NULL	不为空	

运算符号	作用
NOT 或 !	逻辑非
AND	逻辑与
OR	逻辑或
XOR	逻辑异或

运算符	作用
+	加法
-	减法
*	乘法
/ 或 DIV	除法
% 或 MOD	取余


```


## 分组
```
SELECT email from email GROUP BY email; 分组
SELECT email,COUNT(*) as count from email GROUP BY email HAVING count>1;
```

## 排序
```
SELECT * from email ORDER BY email ASC;  正序
SELECT * from email ORDER BY email DESC; 倒序
```

## 函数
```
https://www.runoob.com/mysql/mysql-functions.html 
```

## SQL注释

```
/* 查询表中数据 */
select * from email;
```



## 作业一

```
SELECT email,COUNT(*) as count from email GROUP BY email HAVING count>1;

```

email | count 
---|---
a@b.com| 2

## 作业二
```
SELECT * FROM world WHERE area > 3000000 or population > 25000000 AND gdp > 20000000;
```

name | continent |area | population |gdp
---|---|---|---|---
Afghanistan	|Asia|	652230|	25500100|	20343000
Algeria|	Africa	|2381741|	37100000|	188681000