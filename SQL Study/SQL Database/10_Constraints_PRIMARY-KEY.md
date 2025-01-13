# PRIMARY KEY

Primary Key(기본키): 테이블의 각 레코드를 식별하는 최소 정보

`UNIQUE`인 동시에 `NOT NULL`이어야 함.

테이블은 하나의 기본키만 가질 수 있음. 단, 기본키는 1개 이상의 열로 이루어짐

## CREATE TABLE에서의 PRIMARY KEY
### 하나의 열
#### My SQL:
```sql
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    PRIMARY KEY (ID)
);
```
#### SQL Server/Oracle/MS Access:
```sql
CREATE TABLE Persons (
    ID int NOT NULL PRIMARY KEY,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int
);
```
### 열 여러 개
```sql
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    CONSTRAINT PK_Person PRIMARY KEY (ID,LastName)
);
```
Primary Key는 1개이다—PK_Person

단, 이 값이 두 개의 열로 이루어졌다— ID + LastName


## ALTER TABLE에서의 PRIMARY KEY
### 하나의 열
```SQL
ALTER TABLE Persons
ADD PRIMARY KEY (ID);
```

### 열 여러 개
```sql
ALTER TABLE Persons
ADD CONSTRAINT PK_Person PRIMARY KEY (ID, LastName);
```
`ALTER TABLE`을 사용해 기본 키를 추가하는 경우, 해당 열에 NULL값이 생성되지 않도록 선언해야 한다.

## PRIMARY KEY Constraint 삭제
#### MySQL:
```sql
ALTER TABLE Persons
DROP PRIMARY KEY;
```
#### SQL Server/Oracle/MS Access:
```sql
ALTER TABLE Persons
DROP CONSTRAINT PK_Person;
```
