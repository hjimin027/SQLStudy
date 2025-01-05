# LIKE
`WHERE`절 안에서 사용. 특정 패턴 탐지
* % : 0개 이상의 글자
* _ : 1개 이상의 글자

## Syntax
```sql
SELECT col1, col2, ...
FROM table_name
WHERE columnN LIKE pattern;
```

## Wildcard
### _
1개 이상의 글자
```sql
-- Return all customers from a city that starts with 'L' followed by one wildcard character,
   then 'nd' and then two wildcard characters: --
SELECT * FROM Customers
WHERE city LIKE 'L_nd__';
```

### %
0개 이상의 글자
```sql
-- L이라는 글자를 포함한 도시에서 온 customers를 반환 --
SELECT * FROM Customers
WHERE city LIKE '%L%';
```

## 예시
#### ~로 시작하는
```sql
-- 'La'로 시작하는 모든 customer 반환 --
SELECT * FROM Customers
WHERE CustomerName LIKE 'La%';
```
```sql
-- AND이나 OR와 결합 - 'a'나 'b'로 시작하는 모든 customer --
SELECT * FROM Customers
WHERE CustomerName LIKE 'a%' OR CustomerName LIKE 'b%';
```

#### ~로 끝나는
```sql
-- 'a'로 끝나는 모든 customer --
SELECT * FROM Customers
WHERE CustomerName LIKE '%a';
```

#### ~를 포함하는
```sql
-- 'or'를 포함하는 모든 customer --
SELECT * FROM Customers
WHERE CustomerName LIKE '%or%';
```

#### %와 _의 결합
```sql
-- 'a'로 시작하고 적어도 세 글자 이상의 이름을 가진 모든 customer --
SELECT * FROM Customers
WHERE CustomerName LIKE 'a__%';
```
