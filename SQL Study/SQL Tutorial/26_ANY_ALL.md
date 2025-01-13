# ANY & ALL
단일 열 값을 여러 다른 값과 비교할 수 있다.

* * *

# ANY
* boolean값을 결과로 반환
* subquery의 아무 값이나 조건을 충족하면 TRUE

## ANY Syntax
```sql
SELECT col_name(s)
FROM table_name
WHERE col_name operator ANY
  (SELECT col_name
   FROM table_name
   WHERE condition);
```
operator는 표준 비교 연산자(=, <>, !=, >, >=, <, <=)이어야 함

* * *

# ALL
* boolean값을 결과로 반환
* subquery의 모든 값이 조건을 충족하면 TRUE
* `SELECT`, `WHERE`와 `HAVING`과 함께 자주 사용됨

## ALL Syntax
```sql
SELECT ALL col_name(s)
FROM table_name
WHERE condition;
```
```sql
-- WHERE/HAVING과 함께 사용 --
SELECT col_name(s)
FROM table_name
WHERE col_name operator ALL
  (SELECT col_name
   FROM table_name
   WHERE condition);
```
operator는 표준 비교 연산자(=, <>, !=, >, >=, <, <=)이어야 함
