# Join
연관된 열을 기준으로, 두 개 이상의 테이블을 결합할 때 사용

#### [예시](https://www.w3schools.com/sql/trysql.asp?filename=trysql_select_join)
```sql
SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate
FROM Orders
INNER JOIN Customers ON Orders.CustomerID=Customers.CustomerID;
```

## 종류
* (INNER) JOIN: 두 테이블에서 모두 일치하는 값을 가진 레코드 반환
* LEFT (OUTER) JOIN: 왼쪽 테이블의 모든 레코드와, 거기에 매칭되는 오른쪽 테이블의 레코드를 반환
* RIGHT (OUTER) JOIN: 오른쪽 테이블의 모든 레코드와, 거기에 매칭되는 왼쪽 테이블의 레코드를 반환
* FULL (OUTER) JOIN: 왼쪽이나 오른쪽 둘 중 하나라도 매칭되는 레코드를 반환

![img_inner_join](https://github.com/user-attachments/assets/409850a9-0ecb-4477-9daa-14d5ba357428)
![img_left_join](https://github.com/user-attachments/assets/956dbba9-4d5d-4c58-898a-7fbf39517499)

![img_right_join](https://github.com/user-attachments/assets/8125d077-0b05-453a-bd90-7b0d10978d07)
![img_full_outer_join](https://github.com/user-attachments/assets/7d0e5150-3ac9-4ebb-b760-45e013ec2f8a)
