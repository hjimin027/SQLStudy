# GROUP BY
동일한 값을 가진 행들을 summary row로 그룹화. (예. 각 국가의 고객 수를 구해라)

Aggregate Function와 함께 자주 사용된다. COUNT(), MIN(), MAX(), SUM(), AVG()

## Syntax
```sql
SELECT col_name(s)
FROM table_name
WHERE condition
GROUP BY col_name(s)
ORDER BY col_name(s);
```

## 예시
#### `GROUP BY`
```sql
-- 각 국가의 customer 수를 나열 --
SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country;
```

```sql
-- 각 국가의 customer 수를 내림차순으로 나열 --
SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country
ORDER BY COUNT(CustomerID) DESC;
```

#### GROUP BY & JOIN
```sql
-- 각 shippers이 보낸 orders 수 나열 --
SELECT Shippers.ShipperName, COUNT(Orders.OrderID) AS NumberOfOrders
FROM Orders
LEFT JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID
GROUP BY ShipperName;
```
