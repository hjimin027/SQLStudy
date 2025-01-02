# TOP / LIMIT / FETCH FIRST or ROWNUM

## SELECT TOP
반환할 레코드 수 지정

예
```sql
SELECT TOP 3 * FROM Customers;
```
TOP 3 대신 TOP 50 PERCENT 등 변형 가능

**다만, 모든 데이터베이스 시스템이 SELECT TOP을 지원하지는 않음**
* MySQL: `LIMIT`
* Oracle: `FETCH FIRST n ROWS ONLY`, `ROWNUM <= n`

## `ORDER BY` 키워드 추가
SQL Server, MS Access
```sql
SELECT TOP 3 * FROM Customers
ORDER BY CustomerName DESC;
```
MySQL
```sql
SELECT * FROM Customers
ORDER BY CustomerName DESC
LIMIT 3;
```
Oracle
```sql
SELECT * FROM Customers
ORDER BY CustomerName DESC
FETCH FIRST 3 ROWS ONLY;
```
