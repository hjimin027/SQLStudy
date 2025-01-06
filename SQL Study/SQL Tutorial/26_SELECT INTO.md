# SELECT INTO
한 테이블의 데이터를 다른 테이블로 복사

## Syntax
```sql
-- 모든 열 복사 --
SELECT *
INTO newtable [IN externaldb]
FROM oldtable
WHERE condition;
```

```sql
-- 일부 열만 복사 --
SELECT col1, col2, ...
INTO newtable [IN externaldb]
FROM oldtable
WHERE condition;
```
새 테이블은 이전 테이블에 정의된 이름과 타입으로 생성될 것이다. `AS`를 사용해 새 열 이름을 만들 수 있다.

## 예시
#### SELECT INTO
```sql
-- Customers 테이블 백업 복사 --
SELECT * INTO CustomersBackup2025
FROM Customers;
```

#### `IN` 사용 → 다른 DB에 있는 테이블에 복사
```sql
-- Customers를 'Backup.mdb'의 CustomersBackup2025애 복사 --
SELECT * INTO CustomersBackup2025 IN 'Backup.mdb'
FROM Customers;
```

#### SELECT INTO & WHERE
```sql
--  German의 customers만 새 테이블에 복사 --
SELECT * INTO CustomersBackup2025
FROM Customers
WHERE Country = 'Germany';
```

#### 새로운 빈 테이블 생성 → 데이터를 반환하지 않는 WHERE절을 추가하면 됨
```sql
SELECT * INTO newtable
FROM oldtable
WHERE 1 = 0;
```
