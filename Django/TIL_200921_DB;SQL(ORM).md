## 09 / 21 DB : SQL(ORM)



### Relationship fields

> 모델 간 관계를 나타내는 필드

- Many to one(1:N / 일대다) : `ForeignKey()`

  ​	`Field()`라고 따로 명시되어 있지 않음.

  ​	**외래 키**라고도 함.

- Many to Many(M:N / 다대다) : `ManyToManyField()`

- One to One(1:1 / 일대일) : `OneToOneField()`

#### Foreign Key

> 외래 키는 *참조하는 테이블에서 1개의 키(속성 또는 속성의 집합*)에 해당하고, *참조하는 측의 관계 변수는 참조되는 측의 테이블의 키*를 의미함.

- 참조하는 테이블의 속성의 행 1개의 값은 참조되는 측 테이블의 행 값과 대응된다.
- <u>하나의 테이블이 여러 개의 외래 키를 포함할 수 있음.</u>

![image-20201010142148220](TIL_200921_DB;SQL(ORM).assets/image-20201010142148220.png)

> **참조 무결성의 원칙**
>
> 참조 무결성의 원칙을 어기지 않는 범위 내에서 참조할 수 있는 값에 제한되는 것은 없음(id, content, title 등 가능하지만 주로 겹치지 않을 수 있는 값을 선택)

#### ManyToOneField()

### ### 🟥 Intro
SQLite : RDBMS의 데이터를 다루기 위해 사용하는 언어로 `DML`, `DDL` 두 종류를 사용한다.
- DML(Data Manipulation Language) : 데이터의 추가, 삭제, 갱신, 조회 시에 사용.
	- 예시 : `INSERT`, `DELETE`, `UPDATE`, `SELECT` 
- DDL(Data Definition Language) : 데이터의 테이블 등을 생성, 변경, 제거할 때에 사용. 
	- 예시 :`CREATE`,`ALTER`,`DROP`

> RDBMS(Relational Database Management System)
> : 데이터의 구성이 행(row)으로 구성된 테이블이며 각 행은 열(column)의 데이터로 이루어져 있다. 

### ### 🟧 실행 방법
SQL 홈페이지에서 각자 컴퓨터 사양에 맞는 버전을 설치하자.
나는 Visual Studio Code 2019 버전을 사용하므로 이 프로그램에 맞추어 글을 쓰겠당. 터미널에서 `sqlite3`을 입력하면 sqlite가 실행된다.
```
# sqlite3 실행
$ sqlite3
# 종료
$ .quit
```
Visual Studio Code에서는 Sqlite3 확장 프로그램(Extensions)을 제공하므로 다운로드받으면 사용이 가능하다!
### ### 🟨 DB 생성 및 Table 생성/삭제
> 데이터의 생성 및 조회가 가능하다는 점에서 CRUD의 **C**, **R**과 유사하다.

#### ① DB 생성
```
sqlite3 DB파일이름지정.sqlite3
sqlite> .databases
sqlite> .mode csv
sqlite> .import csv파일이름.csv tbl이름01
```
```
sqlite> .mode csv
sqlite> .import hellodb.csv exm01
sqlite> SELECT * FROM exm01 ;
1,"길동","홍",600,"충청도",010-2424-1232
```
CSV : Comma Seperated Value로 `comma(,)`로 값들이 구분된다는 뜻이다.

#### 📍 추가 사항 : 출력 결과에 변화를 주자
_출력 결과가 더 깔끔했으면 좋겠다!_ 한다면
```
sqlite> .headers on
sqlite> .mode column
sqlite> SELECT * FROM exm01 ;
id  first_name  last_name  age  country  phone
--  ----------  ---------  ---  -------  -------------
1   길동          홍          600  충청도      010-2424-1232
```
`.headers on`
`.mode column`

#### ② Table 생성
```
sqlite> CREATE TABLE 테이블이름(
		데이터 내의 column 값들,
        구분은 comma로 한다,
        명령어 종료는 semicolon으로);
# 생성된 table 목록을 조회(전부 보여줌)
sqlite > .table
```
SQL문의 종료는 `;`로 인식하므로 마지막에 `;`가 없으면 종료되지 않는 것에 주의!
#### ③ Table 삭제
```
sqlite > DROP TABLE 삭제할테이블이름 ;
```
```
sqlite> .tables
exm01  ppls
sqlite> DROP TABLE exm01 ;
sqlite> .tables
ppls
sqlite>
```
#### 📍  추가사항 - Schema 조회

> Schema / 스키마 : 데이터베이스의 구조와 제약 조건을 정의하는 것 - 형식 정의

```
sqlite> .schema 테이블이름
```
위의 코드를 쓰고 실행하면 해당 테이블의 데이터 구조 형태가 출력된다.
```
sqlite> CREATE TABLE ppls (
   ...> id INTEGER PRIMARY KEY,
   ...> name TEXT );
sqlite> .tables
exm01  ppls
sqlite> .schema ppls
CREATE TABLE ppls (
id INTEGER PRIMARY KEY,
name TEXT );
````

[wikidocs-DB](https://wikidocs.net/12452)
[wally-wally님의 github](https://github.com/wally-wally/TIL/blob/master/05_DB/%5BSSAFY%5DDB_%231.md)