# MIN(), MAX()
## Syntax
```sql
SELECT MIN(column_name)
FROM table_name
WHERE condition;
```
```sql
SELECT MAX(column_name)
FROM table_name
WHERE condtion;
```

## [열 이름 지정(Alias)](https://www.w3schools.com/sql/trysql.asp?filename=trysql_select_min_as)
```sql
SELECT MIN(Price) AS SmallestPrice
FROM Products;
```

## [GROUP BY와 함께 사용하기](https://www.w3schools.com/sql/trysql.asp?filename=trysql_select_min_groupby)
```sql
SELECT MIN(Price) AS SmallestPrice, CategoryID
FROM Products
GROUP BY CategoryID;
```
