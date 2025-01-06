# Join
연관된 열을 기준으로, 두 개 이상의 테이블을 결합할 때 사용

#### [예시](https://www.w3schools.com/sql/trysql.asp?filename=trysql_select_join)
```sql
SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate
FROM Orders
INNER JOIN Customers ON Orders.CustomerID=Customers.CustomerID;
```

## 종류
* [(INNER) JOIN](#inner-join): 두 테이블에서 모두 일치하는 값을 가진 레코드 반환
* [LEFT (OUTER) JOIN](#left-join): 왼쪽 테이블의 모든 레코드와, 거기에 매칭되는 오른쪽 테이블의 레코드를 반환
* [RIGHT (OUTER) JOIN](#right-join): 오른쪽 테이블의 모든 레코드와, 거기에 매칭되는 왼쪽 테이블의 레코드를 반환
* [FULL (OUTER) JOIN](): 왼쪽이나 오른쪽 둘 중 하나라도 매칭되는 레코드를 반환

![img_inner_join](https://github.com/user-attachments/assets/409850a9-0ecb-4477-9daa-14d5ba357428)
![img_left_join](https://github.com/user-attachments/assets/956dbba9-4d5d-4c58-898a-7fbf39517499)

![img_right_join](https://github.com/user-attachments/assets/8125d077-0b05-453a-bd90-7b0d10978d07)
![img_full_outer_join](https://github.com/user-attachments/assets/7d0e5150-3ac9-4ebb-b760-45e013ec2f8a)


* * *

# INNER JOIN
두 테이블을 결합하고, null값이 있는 행은 무조건 제외
## Syntax
```sql
SELECT col_name(s)
FROM table1
INNER JOIN table2
ON table1.column_name = table2.column_name;
```
## JOIN과 INNER JOIN
`JOIN`과 `INNER JOIN`은 똑같은 결과를 반환한다.

INNER는 JOIN의 디폴트 타입

## 테이블 3개 JOIN
```sql
SELECT Orders.OrderID, Customers.CustomerName, Shippers.ShipperName
FROM ((Orders
       INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID)
INNER JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID);
```

* * *

# LEFT JOIN
왼쪽 테이블은 그대로, 오른쪽 테이블을 왼쪽 테이블에 맞춤

어떤 데이터베이스에서는 `LEFT OUTER JOIN`이라고 불린다.

## LEFT JOIN Syntax
```sql
SELECT col_name(s)
FROM table1
LEFT JOIN table2
ON table1.col_name = table2.col_name;
```
이 때, table1이 왼쪽 테이블, table2이 오른쪽 테이블이 된다.

![img_left_join](https://github.com/user-attachments/assets/4756e78a-753a-43ff-b9b5-ca2b6ab75013)

#### 예시
```sql
SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID
ORDER BY Customers.CustomerName;
```

* * *

# RIGHT JOIN
오른쪽 테이블은 그대로, 왼쪽 테이블을 왼쪽 테이블에 맞춤

어떤 데이터베이스에서는 `RIGHT OUTER JOIN`이라고 불린다.

## RIGHT JOIN Syntax
```sql
SELECT col_name(s)
FROM table1
RIGHT JOIN table2
ON table1.col_name = table2.col_name;
```
이 때, table1이 왼쪽 테이블, table2이 오른쪽 테이블이 된다.

![img_right_join](https://github.com/user-attachments/assets/d0fcc39b-cc88-4c3a-a945-b193304a2f6e)

#### 예시
```sql
SELECT Orders.OrderID, Employees.LastName, Employees.FirstName
FROM Orders
RIGHT JOIN Employees ON Orders.EmployeeID = Employees.EmployeeID
ORDER BY Orders.OrderID;
```
