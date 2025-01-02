# SELECT

## Syntax

```sql
SELECT column1, column2, ...
FROM table_name;
```
* column1, column2, ... : 테이블의 필드명. 여러 개일 경우 쉼표로 구분
* table_name : 데이터를 선택하고 싶은 테이블 명


### Select ALL columns (모든 열 선택)

```sql
SELECT * FROM Customers;
```


# SELECT DISTINCT

해당 열에 중복값이 많은 경우, 고유값만 나열하고 싶을 때 사용.

```SQL
SELECT DISTINCT col1, col2, ...
FROM table_name;
```
<a href="https://www.w3schools.com/sql/trysql.asp?filename=trysql_select_distinct" target="_blank">SELECT DISTINCT 예시(실행)</a>

## Count Distinct
`COUNT` 함수를 사용할 때 `DISTINCT` 키워드를 함께 사용하면, 다른 국가들의 수를 구할 수 있다.
```sql
SELECT COUNT(DISTINCT Country) FROM Customers;
```
