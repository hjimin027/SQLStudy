# HAVING
`WHERE`문 안에는 aggregate function을 사용할 수 없다. Aggregate Function을 조건으로 사용하기 위해 `HAVING` 사용

(Aggregate Function이 `WHERE` 이후에 개발됨)

Aggregate Function → `GROUP BY`와 함께 사용

## Syntax
```sql
SELECT col_name(s)
FROM table_name
WHERE condition
GROUP BY col_name(s)
HAVING condition
ORDER BY col_name(s);
```

## 예시
```sql
-- 각 국가의 customer 수 나열. 단, 5명 이상인 국가만 포함 --
SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country
HAVING COUNT(CustomerID) > 5;
```

```sql
-- 10개 이상의 order를 등록한 employee 나열 --
SELECT Employees.LastName, COUNT(Orders.OrderID) AS NumberOfOrders
FROM (Orders
      INNER JOIN Employees ON Orders.EmployeeID = Employees.EmployeeID)
GROUP BY LastName
HAVING COUNT(Orders.OrderID) > 10;
```
