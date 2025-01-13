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
* [FULL (OUTER) JOIN](#full-join): 왼쪽이나 오른쪽 둘 중 하나라도 매칭되는 레코드를 반환
* (+) [Self Join](#self-join): 자기 자신과 join.

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

* * *

# FULL JOIN
왼쪽이나 오른쪽 테이블에 매칭되는 모든 레코드를 반환

`FULL OUTER JOIN`이라고도 쓰임

## FULL JOIN Syntax
```sql
SELECT col_name(s)
FROM table1
FULL JOIN table2
ON table1.col_name = table2.col_name
WHERE condition;
```
![img_full_outer_join](https://github.com/user-attachments/assets/f0c6fcbc-264c-496c-841a-02144b8f5ff2)

#### 예시
```sql
SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
FULL OUTER JOIN Orders ON Customers.CustomerID=Orders.CustomerID
ORDER BY Customers.CustomerName;
```
##### 참고
`FULL JOIN`은 두 테이블에서 매칭되는 모든 레코드를 반환한다. 다른 테이블이 매칭되지 않더라도 반환하기는 마찬가지다. 매칭되지 않는 행이 있으면, 그런 행들도 함께 나열된다(채워지지 않은 값은 NULL값).

* * *

# Self Join
[참고 자료](https://kimsyoung.tistory.com/entry/SELF-JOIN-%E4%B8%8A-%EA%B0%99%EC%9D%80-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%84-%EC%A1%B0%EC%9D%B8%ED%95%98%EA%B8%B0)

[원문](https://learnsql.com/blog/how-to-join-same-table-twice/)


## 왜 하는가?
데이터를 다루다 보면 같은 테이블을 여러 번 join해야 하는 경우가 발생한다.
예를 들어보겠다.
|customerID|firstName|lastName|birthdate|spouseID|
|----------|---------|--------|---------|--------|
|1|John|Mayer|1983-05-12|2|
|2|Mary|Mayer|1990-07-30|1|
|3|Lisa|Ross|1989-04-15|5|
|4|Anna|Timothy|1988-12-26|6|
|5|Tim|Ross|1957-08-15|3|
|6|Donna|Trapp|1967-07-09|4|

spouseID열은 고객의 배우자의 customerID 정보를 담고 있다(*spouse: 배우자). 예를 들어, customerID 1와 2(John, Mary)는 서로의 배우자다.
하지만, 해당 테이블을 보면 고객의 이름과 그 고객의 배우자 아이디는 알 수 있지만, 배우자의 성과 이름은 바로 알 수 없다.

그래서 Customer 테이블에 배우자의 성과 이름을 붙여주고 싶다. 이 때, Self Join을 사용한다.
```sql
SELECT c.customerID, c.firstName, c.lastName, c.birthdate, c.spouseID,
       s.firstName AS spouse_firstName, s.lastName AS spouse_lastName
FROM Customer AS c
INNER JOIN Customer AS s
ON c.spouseID=s.customerID;
```
위의 쿼리문을 실행하면 아래와 같은 결과가 나온다.
|customerID|firstName|lastName|birthdate|spouseID|spouse_firstName|spouse_lastName|
|----------|---------|--------|---------|--------|----------------|---------------|
|1|John|Mayer|1983-05-12|2|Mary|Mayer|
|2|Mary|Mayer|1990-07-30|1|John|Mayer|
|3|Lisa|Ross|1989-04-15|5|Tim|Ross|
|4|Anna|Timothy|1988-12-26|6|Steve|Donell|
|5|Tim|Ross|1957-08-15|3|Lisa|Ross|
|6|Donna|Trapp|1967-07-09|4|Anna|Timothy|

#### 주의점
Self Join은 테이블 이름을 꼭 지정해줘야 한다.

서로 다른 별칭을 줘 서로 다른 테이블 2개를 join하는 것이라고 인식하게 해야 함. 그렇지 않으면, SQL은 특정 데이터를 어떤 테이블에서 가져와야 하는지 모름. 똑같은 테이블을 합치기 때문에 편의상 Self Join이라고 이름을 붙인 것이지, SQL 자체는 Self Join이라는 개념이 존재하지 않음.

## Self Join은 언제 사용하는가?

(자세한 내용은 [참고자료](https://kimsyoung.tistory.com/entry/SELF-JOIN-%E4%B8%8B-%EC%85%80%ED%94%84-%EC%A1%B0%EC%9D%B8%EC%9D%98-%EC%9A%A9%EB%A1%80) 확인)

### 위계성 데이터(Hierarchical Data)를 다룰 때
위의 Customer 테이블도 이에 해당된다. 다른 말로 "나무 구조(tree structure)"라고도 부른다.
### 순차성 데이터
id, content, previous_id, next_id가 주어질 때, Self Join을 통해 순서에 맞는 테이블을 구할 수 있다.
### 한 개의 테이블 안에 관계성이 명시되어야 할 데이터가 여러 개 존재할 때
