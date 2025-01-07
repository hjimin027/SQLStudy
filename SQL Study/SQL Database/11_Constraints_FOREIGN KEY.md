# FOREIGN KEY (외래 키)

테이블 간 링크를 파괴하는 것을 방지

다른 테이블의 기본 키를 참조

외래 키를 가진 테이블을 child table(자식 테이블), 기본 키를 가진 테이블을 부모 테이블 혹은 참조 테이블이라 부른다.

#### 예를 들어보자.
Persons Table
| PersonID 	| LastName  	| FirstName 	| Age 	|
|----------	|-----------	|-----------	|-----	|
| 1        	| Hansen    	| Ola       	| 30  	|
| 2        	| Svendson  	| Tove      	| 23  	|
| 3        	| Petterson 	| Kari      	| 20  	|

Orders Table
| OrderID 	| OrderNumber 	| PersonID 	|
|---------- |-------------	|----------	|
| 1       	| 77895       	| 3        	|
| 2       	| 44678       	| 3        	|
| 3       	| 22456       	| 2        	|
| 4       	| 24562       	| 1        	|

Persons 테이블과 Orders 테이블에서 둘 다 "PersonID"열을 확인할 수 있다.  
Persons 테이블의 PersonID는 기본키(Primary Key)이다.  
Orders 테이블의 PersonID는 외래키(Foreign Key)이다.

`FOREIGN KEY`는 열에 잘못된 데이터가 삽입되는 것을 방지한다. 외래키는 부모 테이블에 포함된 값 중 하나이어야 하기 때문이다.

## CREATE TABLE에서의 FOREIGN KEY
#### MySQL:
```SQL
CREATE TABLE Orders (
    OrderID int NOT NULL,
    OrderNumber int NOT NULL,
    PersonID int,
    PRIMARY KEY (OrderID),
    FOREIGN KEY (PersonID) REFERENCES Persons(PersonID)
);
```
#### SQL Server, Oracle, MS Access:
```sql
CREATE TABLE Orders (
    OrderID int NOT NULL PRIMARY KEY,
    OrderNumber int NOT NULL,
    PersonID int FOREIGN KEY REFERENCES Persons(PersonID)
);
```
### 외래키의 명명을 허용 FOREIGN KEY (외래 키)

테이블 간 링크를 파괴하는 것을 방지

다른 테이블의 기본 키를 참조

외래 키를 가진 테이블을 child table(자식 테이블), 기본 키를 가진 테이블을 부모 테이블 혹은 참조 테이블이라 부른다.

#### 예를 들어보자.
Persons Table
| PersonID 	| LastName  	| FirstName 	| Age 	|
|----------	|-----------	|-----------	|-----	|
| 1        	| Hansen    	| Ola       	| 30  	|
| 2        	| Svendson  	| Tove      	| 23  	|
| 3        	| Petterson 	| Kari      	| 20  	|

Orders Table
| OrderID 	| OrderNumber 	| PersonID 	|
|---------- |-------------	|----------	|
| 1       	| 77895       	| 3        	|
| 2       	| 44678       	| 3        	|
| 3       	| 22456       	| 2        	|
| 4       	| 24562       	| 1        	|

Persons 테이블과 Orders 테이블에서 둘 다 "PersonID"열을 확인할 수 있다.  
Persons 테이블의 PersonID는 기본키(Primary Key)이다.  
Orders 테이블의 PersonID는 외래키(Foreign Key)이다.

`FOREIGN KEY`는 열에 잘못된 데이터가 삽입되는 것을 방지한다. 외래키는 부모 테이블에 포함된 값 중 하나이어야 하기 때문이다.

## CREATE TABLE에서의 FOREIGN KEY
#### MySQL:
```SQL
CREATE TABLE Orders (
    OrderID int NOT NULL,
    OrderNumber int NOT NULL,
    PersonID int,
    PRIMARY KEY (OrderID),
    FOREIGN KEY (PersonID) REFERENCES Persons(PersonID)
);
```
#### SQL Server, Oracle, MS Access:
```sql
CREATE TABLE Orders (
    OrderID int NOT NULL PRIMARY KEY,
    OrderNumber int NOT NULL,
    PersonID int FOREIGN KEY REFERENCES Persons(PersonID)
);
```
### 외래키에 이름을 지정하고, 여러 열에 대한 외래키 제약조건 정의
```sql
CREATE TABLE Orders (
    OrderID int NOT NULL,
    OrderNumber int NOT NULL,
    PersonID int,
    PRIMARY KEY (OrderID),
    CONSTRAINT FK_PersonOrder FOREIGN KEY (PersonID)
    REFERENCES Persons(PersonID)
);
```

## ALTER TABLE에서의 FOREIGN KEY
```SQL
ALTER TABLE Orders
ADD FOREIGN KEY (PersonID) REFERENCES Persons(PersonID);
```
```sql
ALTER TABLE Orders
ADD CONSTRAINT FK_PersonOrder
FOREIGN KEY (PersonID) REFERENCES Persons(PersonID);
```

## FOREIGN KEY 삭제
#### My SQL:
```SQL
ALTER TABLE Orders
DROP FOREIGN KEY FK_PersonOrder;
```
#### SQL Server/Oracle/MS Access:
```sql
ALTER TABLE Orders
DROP CONSTRAINT FK_PersonOrder;
```
