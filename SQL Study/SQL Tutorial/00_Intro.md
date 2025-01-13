출처: w3schools

# 목차
### 기본
1. [기본 syntax](01_Syntax.md) - 핵심 sql 명령들
2. [`SELECT`](02_SELECT.md) - `SELECT`, `SELECT DISTINCT`
3. [특정 조건 - `WHERE`](03_WHERE.md)
4. [정렬](04_ORDER-BY.md) - `ORDER BY`, `ASC`/`DESC`
5. [`AND/OR/NOT`](05_AND_OR_NOT.md) - `WHERE`문에서 사용

### 레코드
6. [새로운 레코드 삽입](06_INSERT-INTO.md) - `INSERT INTO`─`VALUES`
7. [NULL](07_NULL.md) - NULL 확인: `IS NULL`. 비교연산자(=, >, <>) 사용 불가능
8. [레코드 수정](08_UPDATE.md) - `UPDATE`─`SET`





# SQL Intro

## SQL은 무엇인가?
* SQL = Structured Query Language
* 데이터베이스 액세스 및 조작

## SQL은...
SQL은 ANSI/ISO standard이지만, 버전마다 다름

그러나, 최소한의 주요 명령어는 모두 비슷한 방식으로 지원함
> 예: SELECT, UPDATE, DELETE, INSERT, WHERE

## SQL을 웹사이트에 적용하기 위해서는
* RDBMS database program (예: MS Access, SQL Server, MySQL)
* server-side scripting language 사용 (예: PHP, ASP)
* 원하는 데이터를 얻기 위해 SQL 사용
* 페이지를 구성할 HTML/CSS

...이 필요하다.


## RDBMS
RDBMS = Relational Database Management System

RDBMS의 데이터는 Table이라는 데이터베이스 객체에 저장됨

테이블: 관련 데이터 항목의 모음. 행과 열로 구성됨
