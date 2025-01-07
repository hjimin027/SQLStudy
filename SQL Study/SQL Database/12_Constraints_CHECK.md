# CHECK

열에 삽입할 수 있는 값의 범위를 제한할 때 사용

`CHECK`을 정의하면 행의 다른 열에 있는 값을 기반으로 특정 열의 값을 제한할 수 있다.

## CREATE TABLE에서의 CHECK
Persons 테이블을 생성할 때 Age열에 제약조건을 생성하고자 한다. 이 제약조건은 사람의 나이가 18세 이상이어야 한다는 것을 보장한다.
#### MySQL:
```sql
CREATE TABLE Persons (
    ID is NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    CHECK (Age >= 18)
);
```
#### SQL Server/Oracle/MS Access:
```sql
CREATE TABLE Persons (
    ID is NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int CHECK (Age >= 18)
);
```
### 여러 개 열
```sql
CREATE TABLE Persons (
    ID is NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    City varchar(255),
    CHECK CHK_Person CHECK (Age>=18 AND City='Sandes')
);
```

## ALTER TABLE에서의 CHECK
```sql
-- 테이블이 이미 생성된 상태에서 "Age"열에 제약조건 생성 --
ALTER TABLE Persons
ADD CHECK (Age>=18);
```
### 여러 열
```sql
ALTER TABLE Persons
ADD CHECK (Age>=18 AND City='Sandnes');
```

## CHECK 삭제
#### MySQL:
```sql
ALTER TABLE Persons
DROP CHECK CHK_PersonAge;
```
#### SQL Server/Oracle/MS Access:
```sql
ALTER TABLE Persons
DROP CONSTRAINT CHK_PersonAge;
```
