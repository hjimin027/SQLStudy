# AND 연산자
`WHERE`에서 하나 이상 사용 가능

## Syntax
```sql
SELECT col1, col2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...;
```
모든 조건이 참이어야 함!

## AND와 OR 결합
괄호 사용에 주의해야 함! 다른 의미가 되어 다른 결과가 나올 수 있음

```sql
SELECT * FROM Customers
WHERE Country='Spain' AND (CustomerName LIKE 'G%' OR CustomerName LIKE 'R%');
```
↑ Spain에서 왔으며, G나 R로 이름이 시작하는 모든 고객

```sql
SELECT * FROM Customers
WHERE Country='Spain' AND CustomerName LIKE 'G%' OR CustomerName LIKE 'R%';
```
↑ Spain에서 왔으며 G로 시작하거나, R로 시작하는 모든 고객


# OR 연산자
`WHERE`에서 하나 이상 사용 가능

## Syntax
```sql
SELECT col1, col2, ...
FROM table_name
WHERE condition1 OR condition2 OR condition3 ...;
```
조건 중 아무거나(하나 이상) 


# NOT 연산자
반대의 결과

## Syntax
```sql
SELECT co1, col2, ...
FROM table_name
WHERE NOT condition;
```

## 예시
#### NOT LIKE
'A'로 시작하지 않는 고객들
```sql
SELECT * FROM Customers
WHERE CustomerName NOT LIKE 'A%';
```
#### NOT BETWEEN
customerID가 10에서 60 사이가 아닌 고객들
```sql
SELECT * FROM Customers
WHERE CustomerID NOT BETWEEN 10 AND 60;
```
#### NOT IN
Paris나 London에서 오지 않은 고객들
```sql
SELECT * FROM Customers
WHERE City NOT IN ('Paris', 'London');
```
