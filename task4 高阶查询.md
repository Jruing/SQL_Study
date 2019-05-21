## 项目十
```
SELECT T.Request_at Day, round(sum(	if (T.Status like 'cancelled_%',1,0))/count(*),2) 'Cancellation Rate' FROM Trips T,Users WHERE T.Client_Id = Users.Users_Id AND (T.Request_at Between '2013-10-01' AND '2013-10-03') AND Users.Banned = 'No' GROUP BY T.Request_at;
```

## 项目十一
```
SELECT d.Name Department, e1.Name Employee,  e1.Salary  FROM Employee e1, Employee e2, Department d WHERE e1.DepartmentID = e2.DepartmentID AND e2.Salary >= e1.Salary AND E1.DepartmentID = d.ID GROUP BY e1.Name  HAVING COUNT(DISTINCT e2.Salary) <= 3 ORDER BY d.Name, e1.Salary DESC;
```

## 项目十二
```
SELECT t1.Score, (SELECT COUNT(Score) FROM score WHERE Score > t1.Score) + 1 AS 'Rank' FROM score t1 ORDER BY t1.Score DESC
```
