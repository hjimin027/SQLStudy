# UNIQUE Constraints
해당 열의 모든 값이 각각 달라야 함

`UNIQUE`와 `PRIMARY KEY` 모두 열 혹은 열의 집합에 대한 고유성을 보장한다.

`PRIMARY KEY`는 자동으로 `UNIQUE`를 포함한다.

그러나, `UNIQUE`는 한 테이블에 여러 개 사용 가능하지만, `PRIMARY KEY`는 한 테이블 당 하나만 사용할 수 있다.


## CREATE TABLE에서의 UNIQUE Constraints
### 하나의 열에 UNIQUE
#### SQL Server/Oracle/MS Access:
```sql
CREATE TABLE Persons (
    ID int NOT NULL UNIQUE,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int
);
```
#### My SQL
```sql
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    UNIQUE(ID)
);
```
### 여러 열에 UNIQUE
```sql
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    CONSTRAINT UC_Person UNIQUE (ID, LastName)
);
```


## ALTER TABLE에서의 UNIQUE Constraints
### 하나의 열
```sql
ALTER TABLE Persons
ADD UNIQUE(ID);
```
### 여러 열
```sql
ALTER TABLE Persons
ADD CONSTRAINT UC_Person UNIQUE (ID, LastName);
```

## UNIQUE Constraint 삭제
#### SQL Server/Oracle/MS Access:
```sql
ALTER TABLE Persons
DROP CONSTRAINT UC_Person;
```
#### My SQL:
```sql
ALTER TABLE Persons
DROP INDEX UC_Person;
```
