# ORDER BY

키워드. 결과물을 오름차순(ascending)/내림차순(descending)으로 정렬할 때 사용

## Syntax
```sql
SELECT col1, col2, ...
FROM table_name
ORDER BY col1, col2, ... ASC | DESC;
```

## DESC
`ORDER BY` 키워드는 기본이 오름차순(ascending).

내림차순으로 정렬하려면 `DESC`키워드 사용

```sql
SELECT * FROM Products
ORDER BY Price DESC;
```

##  여러 열로 정렬
```sql
SELECT * FROM Customers
ORDER BY Country, CustomerName;
```
위 예시의 경우, "Country"와 "CustomerName"열을 기준으로 정렬된 "Customers" 테이블을 선택한다.

이는, Country열을 기준으로 정렬되며, Country열의 값이 동일할 경우는 CustomerName열을 기준으로 정렬한다는 것을 의미한다.

## ASC와 DESC 둘 다 사용하기
```sql
SELECT * FROM Customers
ORDER BY Country ASC, CustomerName DESC;
```
