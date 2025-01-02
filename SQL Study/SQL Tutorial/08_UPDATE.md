# UPDATE
이미 테이블에 존재하는 레코드 수정

## Syntax
```sql
UPDATE table_name
SET column1=value1, column2=value2, ...
WHERE condition;
```
#### 주의점
`WHERE`문을 이용해서 `UPDATE`의 대상을 반드시 지정해야 함!!

생략 시 테이블의 모든 레코드가 업데이트됨

## 예시
#### UPDATE Table
```sql
UPDATE Customers
SET ContactName='Alfred Schmidt', City='Frankfurt'
WHERE CustomerID=1;
```
#### UPDATE Multiple Records
```sql
UPDATE Customers
SET ContactName='Juan'
WHERE Country='Mexico';
```
**주의!!** Contry='Mexico'인 모든 레코드들의 ContactName이 'Juan'으로 업데이트됨
