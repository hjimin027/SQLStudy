# SQL CASE
조건을 처음 충족하면 해당 명령 실행. 조건을 충족하지 않으면 ELSE문 실행

ELSE문이 존재하지 않으면, NULL 반환

## Syntax
```sql
CASE
	WHEN condition1 THEN result1
	WHEN condition2 THEN result2
	WHEN condition3 THEN result3
	ELSE result
END;
```

## 예시
```sql
-- 조건을 충족하면 값 반환 --
SELECT OrderID, Quantity,
CASE
	WHEN Quantity > 30 THEN 'The quantity is greater than 30'
	WHEN Quantity = 30 THEN 'The quantity is 30'
	ELSE 'The quantity is under 30'
END AS QuantityText
FROM OrderDetails;
```
```sql
-- customers를 City순으로 정렬. City가 NULL이면, Country순으로 정렬
SELECT CustomerName, City, Country
FROM Customers
ORDER BY (CASE
			WHEN City IS NULL THEN Country
			ELSE City
		  END);
```
