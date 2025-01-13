# ALTER TABLE
테이블을 추가, 삭제, 혹은 열을 수정

또, 다양한 제약 조건을 추가하거나 삭제하기도 한다.

## 열 추가(ADD)
```SQL
ALTER TABLE table_name
ADD column_name datatype;
```
##### 예시
```sql
ALTER TABLE Customers
ADD Email varchar(255);
```

## 열 삭제(DROP)
```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```
##### 예시
```sql
ALTER TABLE Customers
DROP COLUMN Email;
```

## 열 이름 변경(RENAME)
```sql
ALTER TABLE table_name
RENAME COLUMN old_name to new_name;
```
SQL Server에서는 다음과 같은 방법도 있다:
```sql
EXEC sp_rename 'table_name.old_name', 'new_name', 'COLUMN';
```

## 데이터타입 변경/수정
데이터베이스 종류마다 다르다.

#### SQL Server/MS Access:
```sql
ALTER TABLE table_name
ALTER COLUMN column_name datatype;
```
#### My SQL/Oracle(10G 버전 이전):
```sql
ALTER TABLE table_name
MODIFY COLUMN column_name datatype;
```
#### Oracle 10G 이후
```sql
ALTER TABLE table_name
MODIFY column_name datatype;
```
