# UNION
두 개 이상의 `SELECT`문 결과집합을 결합하는 데 사용
* `UNION`내의 모든 `SELECT`문은 동일한 수의 열을 가져야 함
* 열에는 비슷한 데이터타입도 가져야 함
* 모든 `SELECT`문의 열들은 동일 순서여야 함

## Syntax
```sql
SELECT col_name(s) FROM table1
UNION
SELECT col_name(s) FROM table2;
```
### UNION ALL Syntax
`UNION`은 디폴트로 고유값만 SELECT한다. 중복값을 허용하려면, `UNION ALL`을 사용해야 한다.
```sql
SELECT col_name(s) FROM table1
UNION ALL
SELECT col_name(s) FROM table2;
```
결과 집합의 열 이름은 주로 첫 번째 SELECT문의 열 이름과 같다.

## 예시
#### UNION
```sql
-- Customers 테이블과 Suppliers 테이블에서 도시(고유값만)를 반환 --
SELECT City FROM Customers
UNION
SELECT City FROM Suppliers
ORDER BY City;
```

#### UNION ALL
```sql
-- Customers 테이블과 Suppliers 테이블에서 도시(중복 허용)를 반환 --
SELECT City FROM Customers
UNION
SELECT City FROM Suppliers
ORDER BY City;
```

#### UNION & WHERE
```sql
-- Customers 테이블과 Suppliers 테이블에서 독일의 도시(고유값만)를 반환 --
SELECT City, Country FROM Customers
WHERE Country='Germany'
UNION
SELECT City, Country FROM Suppliers
WHERE Country='Germany'
ORDER BY City;
```

#### Alias 활용
```sql
SELECT 'Customer' AS Type, ContactName, City, Country
FROM Customers
UNION
SELECT 'Supplier', ContactName, City, Country
FROM Suppliers;
```
contact한 사람이 Customer인지 Supplier인지 구분
