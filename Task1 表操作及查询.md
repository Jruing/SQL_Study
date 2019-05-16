## Mysql�������������
�������ͣ�BIT��BOOL��TINY INT��SMALL INT��MEDIUM INT�� INT�� BIG INT

���������ͣ�FLOAT��DOUBLE��DECIMAL

�ַ������ͣ�CHAR��VARCHAR��TINY TEXT��TEXT��MEDIUM TEXT��LONGTEXT��TINY BLOB��BLOB��MEDIUM BLOB��LONG BLOB

�������ͣ�Date��DateTime��TimeStamp��Time��Year

�����������ͣ�BINARY��VARBINARY��ENUM��SET��Geometry��Point��MultiPoint��LineString��MultiLineString��Polygon��GeometryCollection��

## ��sql��䴴����
```
create table tbname(id int auto_increment primary key);
```
## ��������
```
insert into tbname(id) value(1);
```
## ɾ����
```
truncate ��deleteֻɾ�����ݣ� drop��ɾ���������ṹ�����ݣ�
```
## �޸ı�
```
/*�޸�����*/
ALTER TABLE testalter_tbl CHANGE old new type;
/*�޸�����*/
update tbname set name='zhangsan' where id=1;
/*ɾ����*/
alter table tbname drop column_name;
/*ɾ����*/
delete from tbname where id = 1;
/*�½���*/
alter table tbname add column_name,data_type
/*�½���*/
insert into tbname(id) value(1);
```


## ��ҵ��

```
/*������*/
create table courses(id int auto_increment primary key,student varchar(16),class varchar(16));
/*��������*/
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
/*��ѯ���*/
SELECT class,count(DISTINCT student,class) as counts from courses GROUP BY class HAVING counts >= 5;
```

## ��ҵ��
```
/*������*/
create table salary(id int auto_increment primary key,name varchar(16),sex varchar(16),salary int);
/*��������*/
insert into salary(name,sex,salary) values('A','m',2500);
insert into salary(name,sex,salary) values('B','f',1500);
insert into salary(name,sex,salary) values('C','m',5500);
insert into salary(name,sex,salary) values('D','f',500);
/*��ѯ���*/
update salary set Sex = case Sex when 'f' then 'm' when 'm' then 'f' end;
```


## MySQL����
MySQL֧�����ֱ�������Ϊ�б����ͱ����
```
SELECT
id,
COUNT(o.name) [as] total	#�б���
FROM
customers [as] c	INNER JOIN orders [as] o #�����
```
## INNER JOIN
INNER JOIN�Ӿ佫һ�����е������������е��н���ƥ�䣬��������������в�ѯ�����е��м�¼
```
SELECT column_list
FROM t1
INNER JOIN t2 ON join_condition1
INNER JOIN t3 ON join_condition2
...
WHERE where_conditions;
```

## LEFT JOIN
������LEFT JOIN�ĺ��������������Ľ���������ʣ�µ����ݡ����ɴӵѿ������ĽǶȽ��������ȴӵѿ�����������ON�Ӿ����������ļ�¼
```
SELECT * FROM t1 LEFT JOIN t2 ON t1.typeId=t2.id;

```
## CROSS JOIN
�ѿ��������ǽ�A���ÿһ����¼��B���ÿһ����¼ǿ��ƴ��һ�����ԣ����A����n����¼��B����m����¼���ѿ����������Ľ���ͻ����n*m����¼
```
SELECT * FROM
    T1
        CROSS JOIN
    T2
WHERE
    T1.id = T2.id;
```
## UNION
union��ѯ���ǰ�2�����߶���sql���Ĳ�ѯ������ϲ���һ�������
```
SELECT id,num FROM num_a UNION SELECT id, num FROM num_b
```
## ������
Ȼ���Ӿ���USING�Ӿ�ļ򻯰棬���ҳ�����������ͬ������Ϊ����������������
```
select a.ename ,a.empno ,b.ename ,b.empno   from emp a,emp b where a.mgr = b.empno; 
```

## �÷�����
[�ο��ĵ�](https://www.cnblogs.com/gzh0815/archive/2018/10/18/9808829.html)
> �����ӣ�INNER JOIN�������������ж�����ƥ��ʱ���ŷ����С�

> �����ӣ�LEFT JOIN������������е������У���ʹ�ұ���û��ƥ����С�

> �����ӣ�RIGHT JOIN���������ұ��е������У���ʹ�����û��ƥ�����

> ȫ���ӣ�FULL JOIN����ֻҪĳһ�������ƥ�䣬�ͷ����С�

> �ѿ������ӣ�CARTESIAN JOIN���������������߸���ı��м�¼���ĵѿ�������

> CROSS JOIN �Ӿ�����ӵı����еĵѿ����˻�

> ��Ȼ���ӣ�������������ʹ�õ���(=)������Ƚϱ������е���ֵ������ʹ��ѡ���б�ָ����ѯ������������������У���ɾ�����ӱ��е��ظ��С�

## ��ҵ��
```
SELECt firstname,lastname,city,state FROM person INNER JOIN address on person.PersonId = address.PersonId

```

## ��ҵ��
```
DELETE FROM email WHERE email.ID in (
SELECT id from( SELECT max(id) as id FROM email as e GROUP BY e.Email HAVING count(e.Email) > 1) as a)
```