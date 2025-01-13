# AUTO INCREMENT
새로운 레코드가 추가될 때마다 자동으로 값을 증가시킴


`AUTO INCREMENT`(자동 증가)는 레코드가 테이블에 삽입될 때 고유한 숫자가 자동으로 생성되도록 한다.  
이 기능은 주로 새로운 레코드가 삽입될 때마다 자동으로 생성되기를 원하는 기본 키(Primary Key) 필드에 사용된다.

데이터베이스 종류마다 Syntax이 다르다.

## 예시 - Persons 테이블에 "PersonID"를 추가, auto-increment 설정
### MySQL
```sql
CREATE TABLE Persons (
    PersonID int NOT NULL AUTO_INCREMENT,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    PRIMARY KEY (PersonID)
);
```
* `AUTO_INCREMENT` 키워드 사용
* Default: 시작값=1, 새로운 레코드가 추가될 때마다 1씩 증가

시작값을 다른 값으로 설정하려면, 다음과 같이 작성하면 된다:
```SQL
ALTER TABLE Persons AUTO_INCREMENT=100;
```

### SQL Server
```sql
CREATE TABLE Persons (
    PersonID int IDENTITY(1,1) PRIMARY KEY,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int
);
```
* `IDENTITY` 키워드 사용
* Default: 시작값=1, 새로운 레코드가 추가될 때마다 1씩 증가
* 시작값=10, 5씩 증가하도록 설정하려면 `IDENTITY(10, 5)`로 변경

### MS Access
```SQL
CREATE TABLE Persons (
    PersonID AUTOINCREMENT PRIMARY KEY,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int
);
```
* `AUTOINCREMENT` 키워드 사용
* Default: 시작값=1, 새로운 레코드가 추가될 때마다 1씩 증가
* 시작값=10, 5씩 증가하도록 설정하려면 `AUTOINCREMENT(10, 5`로 변경

### Oracle
```SQL
CREATE SEQUENCE seq_person
MINVALUE 1
START WITH 1
INCREMENT BY 1
CACHE 10;
```
* seq_person이라는 시퀀스 객체를 생성하며, 이 시퀀스는 1부터 시작하려 1씩 증가
* 성능을 위해 최대 10개의 값을 캐시 - 메모리에 저장될 시퀀스 값의 수 지정
* Persons 테이블에 새로운 레코드를 삽입하려면, `nextval`함수를 사용해야 함
  - `nextval`함수는 seq_person 시퀀스에서 다음 값을 가져옴
```sql
INSERT INTO Persons (PersonID, FirstName, LastName)
VALUES (seq_person.nextval, 'Lars', 'Monsen');
```
