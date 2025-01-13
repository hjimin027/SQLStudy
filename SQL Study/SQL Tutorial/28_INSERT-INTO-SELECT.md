# INSERT INTO SELECT
한 테이블에서 데이터를 복사해 다른 테이블에 삽입

소스 테이블(원본 테이블)과 타겟 테이블의 데이터 타입이 일치해야 함

타겟 테이블의 기존 데이터는 영향 받지 않음

## Syntax
```sql
-- 모든 열을 붙여넣기 --
INSERT INTO table2
SELECT * FROM table1
WHERE condition;
```
```sql
-- 일부 열을 붙여넣기 ``
INSERT INTO table2(col1, col2, ...)
SELECT col1, col2, ...
FROM table1
WHERE condition;
```

## 예시
```sql
-- Suppliers 테이블의 German suppliers만 Customers 테이블에 붙여넣기 --
INSERT INTO Customers (CustomerName, City, Country)
SELECT SupplierName, City, Country FROM Suppliers
WHERE Country='Germany';
```
