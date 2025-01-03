# COUNT()
지정 기준에 맞는 행의 수 반환

## Syntax
```sql
SELECT COUNT(column_name)
FROM table_name
WHERE condition;
```

## 열 지정
열 이름을 지정할 경우, NULL 값은 계산되지 않는다.

## `WHERE`절 추가
```sql
-- Price이 20보다 큰 제품 --
SELECT COUNT(ProductID)
FROM Products
WHERE Price > 20;
```

## 중복 무시
`DISTINCT`키워드 사용
```sql
SELECT COUNT(DISTINCT Price)
FROM Products;
```

## Alias(별칭) 사용
`AS` 키워드 사용
```sql
SELECT COUNT(*) AS [Number of records]
FROM Products
```

## GROUP BY와 사용
```sql
SELECT COUNT(*) AS [Number of records], CategoryID
FROM Products
GROUP BY CategoryID;
```
