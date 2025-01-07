# DEFAULT

열의 기본값을 설정

다른 값이 지정되지 않는 경우, 기본값이 모든 새로운 레코드에 추가됨

## CREATE TABLE에서 DEFAULT
```sql
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    City varchar(255) DEFAULT 'Sandnes'
);
```
DEFAULT 제약조건은 GETDATE()와 같은 함수를 사용하여 시스템 값을 삽입하는 데 사용할 수도 있다.
```SQL
CREATE TABLE Orders (
    ID int NOT NULL,
    OrderNumber int NOT NULL,
    OrderDate date DEFAULT GETDATE()
);
```

## ALTER TABLE에서의 DEFAULT
SQL 종류마다 다름
#### MySQL
```SQL
ALTER TABLE Persons
ALTER City SET DEFAULT 'Sandnes';
```
#### SQL Server
```SQL
ALTER TABLE Persons
ADD CONSTRAINT df_City
DEFAULT 'Sandnes' FOR City;
```
#### MS Access
```SQL
ALTER TABLE Persons
ALTER COLUMN City SET DEFAULT 'Sandnes';
```
#### Oracle
```SQL
ALTER TABLE Persons
MODIFY City DEFAULT 'Sandnes';
```

## DEFAULT 삭제
#### MySQL
```sql
ALTER TABLE Persons
ALTER City DROP DEFAULT;
```
#### SQL Server/Oracle/MS Access
```sql
ALTER TABLE Persons
ALTER COLUMN City DROP DEFAULT;
```
