# Aliases(별칭)
* 테이블이나 열에 임시 이름을 지정할 때 사용
* 열 이름의 가독성을 높일 때 사용하기도 함
* 해당 쿼리가 지속되는 동안만 유지
* `AS`키워드를 사용해 생성

## `AS`는 선택 사항이다
`AS`를 생략해도 똑같은 결과가 나온다.
```sql
SELECT CustomerID ID
FROM Customers;
```

## Syntax
열에 사용할 때:
```sql
SELECT col_name AS alias_name
FROM table_name;
```
테이블에 사용할 때:
```sql
SELECT col_name
FROM table_name AS alias_name;
```

## Aliases를 공백문자와 함께 사용하기
별명(alias)를 대괄호[]나 큰따옴표""로 감싸라
```sql
SELECT ProductName AS [My Great Products]
FROM Products;
```
```sql
SELECT ProductName AS "My Great Products"
FROM Products;
```

## 여러 열 연결
```sql
-- 열 (Address, PostalCode, City, Country)를 연결해서 'Address' 열을 만듦 --
SELECT CustomerName, Address + ', ' + PostalCode + ' ' + City + ', ' + Country AS Address
FROM Customers;
```

MySQL에서는 다음과 같이 작성한다.
```sql
SELECT CustomerName, CONCAT(Address, ', ', PostalCode, ' ', City, ', ', Country) AS Address
FROM Customers;
```

Oracle에서는 다음과 같이 작성한다.
```sql
SELECT CustomerName, (Address || ', ' || PostalCode || ' ' || City || ', ' || Country) AS Address
FROM Customers;
```

## 테이블 Alias
쿼리에서 두 개 이상의 테이블을 사용하는 경우, SQL문을 더 짧게 작성할 수 있다.
```sql
SELECT o.OrderID, o.OrderDate, c.CustomerName
FROM Customers AS c, Orders AS o
WHERE c.CustomerName='Around the Horn' AND c.CustomerID=o.CustomerID;
```

#### Aliases는 다음 상황에서 유리하다:
* 쿼리에 두 개 이상의 테이블이 포함되어 있는 경우
* 쿼리에서 함수가 사용되는 경우
* 열 이름이 크거나 가독성이 떨어지는 경우
* 두 개 이상의 열이 결합되는 경우
