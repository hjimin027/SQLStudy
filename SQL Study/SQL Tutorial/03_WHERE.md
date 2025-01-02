# WHERE Clause
(*구(Phrase), 절(Clause), 문장(Sentenct))

`WHERE`: 특정 조건을 만족하는 레코드만 추출(필터링)하기 위해 사용

## Syntax

```sql
SELECT col1, col2, ...
FROM table_name
WHERE condition;
```
`WHERE`절은 `SELECT` 뿐만 아니라, `UPDATE`, `DELETE` 등 다른 곳에서도 사용함!

## Text Fields vs. Numeric Fields

* Text Field: 따옴표 필요
* Numeric Field: 따옴표X
```sql
SELECT * FROM Customers
WHERE Country='Mexico';
```
```sql
SELECT * FROM Customers
WHERE CustomerID=1;
```

## WHERE 절에서의 연산자
|연산자|설명|예시|
|-|-|-|
|=| |[실행](https://www.w3schools.com/sql/trysql.asp?filename=trysql_op_to)|
|>| |[실행](https://www.w3schools.com/sql/trysql.asp?filename=trysql_op_greater_than)|
|<| |[실행](https://www.w3schools.com/sql/trysql.asp?filename=trysql_op_less_than)|
|>=| |[실행](https://www.w3schools.com/sql/trysql.asp?filename=trysql_op_greater_than2)|
|<=| |[실행](https://www.w3schools.com/sql/trysql.asp?filename=trysql_less_than2)|
|<>|같지 않음. !=로 사용하는 버전도 있음|[실행](https://www.w3schools.com/sql/trysql.asp?filename=trysql_op_not_equal_to)|
|BETWEEN|특정 범위 내|[실행](https://www.w3schools.com/sql/trysql.asp?filename=trysql_op_between)|
|LIKE|패턴 검색|[실행](https://www.w3schools.com/sql/trysql.asp?filename=trysql_op_like)|
|IN|특정 열에 대한 값으로 지정|[실행](https://www.w3schools.com/sql/trysql.asp?filename=trysql_op_in)|
