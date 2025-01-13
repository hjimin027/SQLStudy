# SQL Injection

SQL Injection(SQL 삽입, SQL 인젝션)은 응용 프로그램 보안 상의 허점을 이용해,
악의적인 SQL문이 실행되게 함으로써 데이터베이스를 비정상적으로 조작하는 코드 인젝션 공격 방법이다.

가장 흔한 웹 해킹 기법 중 하나로, 웹페이지 입력을 통해 SQL문에 악성 코드를 삽입하는 방식으로 이루어진다.

## 웹페이지에서의 SQL
SQL 인젝션은 일반적으로 사용자에게 입력을 요청할 때 발생한다(username/userid 등). 그러나 이름이나 ID 대신 SQL문을 전송하면, 
해당 사실을 알지 못한 채 데이터베이스에서 실행하게 된다.

다음 예시는 변수 txtUserId를 select string에 추가하여 `SELECT`문을 생성하는 방식이다.  
이 변수는 사용자입력(getRequestString)에서 가져온다.
```
txtUserId = getRequestString("UserId");
txtSQL = "SELECT * FROM Users WHERE UserId = " + txtUserId;
```

이 페이지의 나머지 부분은 SQL문에서 사용자 입력을 사용할 때 발생할 수 있는 위험에 대해 설명한다.

## _1=1은 항상 True_ 를 이용한 SQL 인젝션
위의 예시를 다시 봐라. 코드의 본 목적은 주어진 user id로 user를 선택하는 SQL문을 생성하는 거였다.

사용자의 입력을 제한하는 조치가 없다면, 다음과 같이 "교묘하게" _입력_ 할 수 있다:

UserId: [_105 OR 1=1_]

그럼, SQL문은 다음과 같이 된다-
```sql
SELECT * FROM Users WHERE UserId = 105 OR 1=1;
```
`OR 1=1`은 항상 TRUE이므로, 위의 SQL문은 유효하며 Users 테이블에서 모든 행을 반환한다.

해당 SQL문은 다음과 유사하다-
```sql
SELECT UserId, Name, Password FROM Users WHERE UserId = 105 or 1=1;
```

## _""=""는 항상 True_ 를 이용한 SQL 인젝션

다음과 같은 로그인 창이 있다고 하자:

Username: [_John Doe_]  
Password: [_myPass_]
```
uName = getRequestString("username");
uPass = getRequestString("userpassword");

sql = 'SELECT * FROM Users WHERE Name ="' + uName + ' " AND Pass ="' + uPass + '"'
```
```sql
-- Result --
SELECT * FROM Users WHERE Name ="John Doe" AND Pass ="myPass"
```
해커는 Username과 Password 텍스트박스에 `OR ""=""`를 입력하여 데이터베이스에서 사용자 이름과 비밀번호에 접근할 수 있다.

Username: [_" or ""="_]  
Password: [_" or ""="_]

그럼 SQL문은 아래와 같다.
```sql
SELECT * FROM Users WHERE Name ="" or ""="" AND Pass ="" or ""=""
```
`OR ""=""`는 항상 TRUE이므로, 위의 SQL문은 Users 테이블의 모든 행을 반환한다.

## Batched SQL문을 이용한 SQL 인젝션
대부분의 데이터베이스는 batched SQL문을 지원한다.
###### * SQL문의 배치(batch): 두 개 이상의 SQL문들의 그룹, 세미콜론으로 분리됨
###### * 배치(batch): 데이터를 실시간으로 처리하는 게 아니라, 일괄적으로 모아서 한 번에 처리하는 작업

<br>
아래의 SQL문은 Users 테이블에서 모든 행을 반환한 다음, Suppliers 테이블을 삭제할 것이다.

```sql
SELECT * FROM Users; DROP TABLE Suppliers;
```
다음 명령어와
```
txtUserId = getRequestString("UserId");
txtSQL = "SELECT * FROM Users WHERE UserId = " + txtUserId;
```
다음 입력
User id: [_105; DROP TABLE Suppliers_]
SQL문은 다음과 같을 것이다.
```sql
SELECT * FROM Users WHERE UserId = 105; DROP TABLE Suppliers;
```

## 보호 - SQL Parameter 사용
SQL 인젝션에서 웹사이트를 보호하기 위해, SQL parameters를 사용할 수 있다.

```sql
-- ASP.NET Razor Example --
txtUserId = getRequestString("UserId");
txtSQL = "SELECT * FROM Users WHERE UserId = @0";
db.Execute(txtSQL, txtUserId);
```
##### 파라미터는 SQL문에서 @ 기호로 표시된다.
SQL 엔진은 각 파라미터에 해당 열에 대해 적절한지, 파라미터가 실행될 SQL의 일부가 아니라 문자 그대로 처리되는지 확인한다.
```sql
-- 다른 예 --
txtNam = getRequestString("CustomerName");
txtAdd = getRequestString("Address");
txtCit = getRequestString("City");
txtSQL = "INSERT INTO Customers (CustomerName, Address, City) Values(@0, @1, @2)";
db.Execute(txtSQL, txtNam, txtAdd, txtCit);
```
