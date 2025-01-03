# SUM()
숫자형 열의 총 합을 반환
## Syntax
```sql
SELECT SUM(column_name)
FROM table_name
WHERE condition
```

## 예시
#### WHERE 추가
```sql
-- Return the sum of the Quantity field for the product with ProductID 11 --
SELECT SUM(Quantity)
FROM OrderDetails
WHERE ProductId = 11;
```
#### Alias 사용
`AS`키워드 사용
```sql
-- 요약된 열의 이름을 "total"로 설정하라 --
SELECT SUM(Quantity) AS total
FROM OrderDetails;
```
#### SUM() & GROUP BY
```sql
-- OrderDetails 테이블에서, 각 OrderID에 따른 Quantity 반환 --
SELECT OrderID, SUM(Quantity) AS [Total Quantity]
FROM OrderDetails
GROUP BY OrderID;
```

## SUM() & Expression
OrderDetails 테이블의 각 product이 10$라고 가정하면, 총 수입은 각 quantity에 10을 곱해서 구할 수 있다.
```sql
SELECT SUM(Quantity * 10)
FROM OrderDetails;
```

또, 10$ 대신, OrderDetails 테이블과 Products 테이블을 `JOIN`하여, 실제 총 금액을 구할 수 있다.
```sql
SELECT SUM(Price * Quantity)
FROM OrderDetails
LEFT JOIN Products ON OrderDetails.ProductID = Products.ProductID;
```
