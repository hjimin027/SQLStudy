# EXISTS
서브쿼리subquery에서 레코드가 존재하는지 확인(테스트)

레코드가 1개 이상이면 TRUE 반환

## Syntax
```sql
SELECT col_name(s)
FROM table_name
WHERE EXISTS (SELECT col_name
              FROM table_name
              WHERE condition);
```

## 예시
```sql
-- 제품 가격이 20 미만인 suppliers 나열 - 서브쿼리의 레코드가 0개가 아니므로 TRUE 반환 --
SELECT SupplierName
FROM Suppliers
WHERE EXISTS (SELECT ProductName
              FROM Products
              WHERE Products.SupplierID = Suppliers.supplierID AND Price < 20;
```
