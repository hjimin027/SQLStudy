# Stored Procedures 저장 프로시저

저장 프로시저: 코드를 재사용할 수 있도록 준비된 SQL 코드

반복 작성하는 SQL 쿼리가 있으면 저장 프로시저로 만들어서, 필요할 때 호출하면 됨

매개변수를 전달할 수 있음

## Syntax
저장 프로시저 생성
```sql
CREATE PROCEDURE procedure_name
AS
sql_statement
GO;
```
저장 프로시저 실행
```sql
EXEC procedure_name;
```

## 예시
#### 저장 프로시저 예시
```sql
-- Customers 테이블의 모든 레코드를 반환하는 "SelectAllCustomers" 저장 프로시저 생성 --
CREATE PROCEDURE Select AllCustomers
AS
SELECT * FROM Customers
GO;
```
```sql
-- 위의 저장 프로시저 실행 --
EXEC SelectAllCustomers;
```
#### 매개변수 하나를 입력하는 저장 프로시저
```sql
CREATE PROCEDURE SelectAllCustomers @City nvarchar(30)
AS
SELECT * FROM Customers WHERE City = @City
GO;
```
```sql
-- 위의 저장 프로시저 실행 --
EXEC SelectAllCustomers @City = 'London';
```

#### 매개변수 여러 개를 입력하는 저장 프로시저
```sql
CREATE PROCEDURE SelectAllCustomers @City nvarchar(30), @PostalCode nvarchar(10)
AS
SELECT * FROM Customers WHERE City = @City AND PostalCode = @PostalCode
GO;
```
```sql
-- 위의 저장 프로시저 실행 --
EXEC SelectAllCustomers @City = 'London', @PostalCode = 'WA1 1DP';
```
