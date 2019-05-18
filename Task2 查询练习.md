

## 作业七
```
SELECT a.Department,max(a.Salary) as Salary FROM (
SELECT d.Name as Department,e.Name as Employee,e.Salary as Salary FROM department as d Inner JOIN employee as e on d.Id=e.department_Id 
) as a GROUP BY a.Department
```

## 作业八
```
SELECT id,student FROM
(
SELECT id-1 AS id, student FROM seat WHERE MOD(id,2)=0
UNION
SELECT id+1 AS id, student FROM seat WHERE MOD(id,2)=1
AND id!=(SELECT COUNT(*) FROM seat)
UNION
SELECT id, student FROM seat where mod(id,2)=1
AND id=(SELECT COUNT(*) FROM seat)
) seat ORDER BY id;

```


## 作业九
```
SELECT s.Score as Score,(SELECT COUNT(distinct ss.Score) from Scores as ss where ss.Score >= s.Score) as Ranks FROM  Scores as s ORDER by Score desc;

```