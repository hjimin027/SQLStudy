# NOT NULL Constraint

#### 예시
```sql
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255) NOT NULL,
    Age int
);
```

## NOT NULL & ALTER TABLE
#### SQL Server/MS Access:
```sql
ALTER TABLE Persons
ALTER COLUMN Age int NOT NULL;
```
#### My SQL/Oracle(10G 이전 버전):
```sql
ALTER TABLE Persons
MODIFY COLUMN Age int NOT NULL;
```
#### Oracle 10G 이후:
```sql
ALTER TABLE Persons
MODIFY Age int NOT NULL;
```
