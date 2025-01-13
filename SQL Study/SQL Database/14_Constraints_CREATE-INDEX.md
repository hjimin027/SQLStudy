# CREATE INDEX

인덱스 생성 → 데이터를 더 빠르게 탐색. 사용자는 인덱스를 볼 수 없으며, 인덱스는 검색이나 쿼리 속도를 높이는 데에만 사용됨.

참고:  
인덱스가 있는 테이블을 업데이트하는 데는 없는 테이블보다 더 오래 걸림(인덱스도 업데이트해야 하기 때문)  
따라서, 자주 검색을 사용하는 열에만 인덱스를 생성하는 것이 좋음

## Syntax
#### CREATE INDEX
```sql
CREATE INDEX index_name
ON table_name (col1, col2, ...);
```
#### CREATE UNIQUE INDEX
```SQL
CREATE UNIQUE INDEX index_name
ON table_name (col1, col2, ...);
```
참고:  
인덱스를 생성하는 구문은 데이터베이스마다 다름. 따로 확인해야 함!

## 예시
```sql
-- Persons 테이블의 LastName열에 "idx_lastname"이라는 이름의 인덱스 생성 --
CREATE INDEX idx_lastname
ON Persons (LastName);
```
```sql
-- 열의 조합에 인덱스 생성 - 괄호 안에 쉼표로 구분하여 열 이름 나열 --
CREATE INDEX idx_pname
ON Persons (LastName, FirstName);
```

## INDEX 삭제
`DROP INDEX` 사용. SQL마다 다름
#### MySQL
```sql
ALTER TABLE table_name
DROP INDEX index_name;
```
#### SQL Server
```sql
DROP INDEX table_name.index_name;
```
#### DB2/Oracle
```sql
DROP INDEX index_name;
```
#### MS Access
```sql
DROP INDEX index_name ON table_name;
```
