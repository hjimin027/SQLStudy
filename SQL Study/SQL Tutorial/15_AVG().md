# AVG()
숫자형 열의 평균값을 반환. NULL값은 무시된다.

## Syntax
```sql
SELECT AVG(column_name)
FROM table_name
WHERE condition;
```

## 평균보다 높은
sub query에 `AVG()` 사용
```sql
SELECT *
FROM Products
WHERE price > (SELECT AVG(price) FROM Products);
```

## 예시
#### WHERE
```sql
-- category 1인 products의 평균 가격 반환 --
SELECT AVG(Price)
FROM Products
WHERE CategoryID = 1;
```
#### Alias 사용
```sql
-- 평균값 열의 이름을 "average price"로 설정 --
SELECT AVG(Price) AS [average price]
FROM Products;
```
#### AVG() & GROUP BY
```sql
-- 각 카테고리의 평균가격 반환 --
SELECT AVG(Price) AS AveragePrice, CategoryID
FROM Products
GROUP BY CategoryID;
```
