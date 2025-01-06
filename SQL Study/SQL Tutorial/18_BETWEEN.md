# BETWEEN
주어진 범위 내에서 값을 선택. 값은 숫자, 텍스트 혹은 날짜

포괄적 → 시작, 끝 값이 포함됨

## Syntax
```sql
SELECT col_name(s)
FROM table_name
WHERE col_name BETWEEN value1 AND value2;
```

## 예시
#### BETWEEN & IN
```sql
-- 가격이 10에서 20 사이이고, CategoryID가 1이나 2, 3 중 하나인 모든 product --
SELECT * FROM Products
WHERE Price BETWEEN 10 AND 20
AND CategoryID IN (1,2,3);
```

#### BETWEEN 텍스트
```sql
-- 이름이, 알파벳순으로, Carnarvon Tigers와 Mozzarella di Giovanni 사이인 모든 product --
SELECT * FROM Products
WHERE ProductName BETWEEN 'Carnarvon Tigers' AND 'Mozzarella di Giovanni'
ORDER BY ProductName;
```

#### BETWEEN 날짜
```sql
SELECT * FROM Orders
WHERE OrderDate BETWEEN #07/01/1996# AND #07/31/1996#;
```
