# 데이터 정의어 

## 데이터 정의어는 테이블의 구조

### CREATE문

~~~html
CREATE TABLE 테이블이름(
	{속성이름 데이터 타입 [NULL | NOT NULL | UNIQUE | DEFAULT 기본 값 | CHECK 체크 조건]}
	[PRIMARY KEY 속성이름(들)]
	[FOREIGN KEY 속성이름 REFERENCES 테이블이름(속성이름)]
	[ON DELETE {CASCADE | SET NULL}]
)
~~~

* NOT NULL 은 NULL 을 허용하지 않는 제약
* UNIQUE 유일한 값에 대한 제약
* DEFAULT 기본값 설정
* CHECK는 값에 대한 조건을 부여할 때 
* PRIMARY KEY는 기본키를 정할 때
* FOREIGN KEY는 외래키를 지정할 때
* ON DELETE는 투플의 삭제시 외래키 속성에 대한 동작(옵션으로는 CASCADE, SET NULL , 명시하지 않으면 RESTRICT(NO ACTION))

~~~html
  CREATE TABLE Student(
  studentid INTEGER,
  studentname VARCHAR(20),
  studentage INTEGER,
  adress VARCHAR(20)
  );
~~~

### 문자 데이터
* CHAR(n) 저장되는 문자의 길이가 n보다 작으면 나머지는 공백으로 채워서 n바이트를 만들어 저장
* VARCHAR(n) 저장되는 문자의 길이만큼만 기억장소를 차지하는 가변형

>CHAR(n)에 저장된 값과 VARCHAR(n)에 저장된 값이 비록 같을지라고 CHAR(n)은 공백을 채운 문자열이기 때문에 동등 비교 시 실패할 수 있다.

### 기본키 지정

* 방법 1

~~~html
CREATE TABLE Student (
  studentid INTEGER, 
  studentname VARCHAR(20),
  studentage INTEGER,
  adress VARCHAR(20),
  PRIMARY KEY(studentid)
    );
~~~

* 방법2

~~~html
CREATE TABLE Student(
  studentid INTEGER PRIMARY KEY,
  studentname VARCHAR(20),
  studentage INTEGER,
  adress VARCHAR(20)
    );
 
~~~

* id 가 없을시 복합키 설정 방법 

~~~html
CREATE TABLE Student(
  studentname VARCHAR(20) NOT NULL, 
  studentage INTEGER, 
  adress VARCHAR(20) UNIQUE,
  PRIMARY KEY ( studentname, studentage)
    );
~~~

~~~html
CREATE TABLE Student(
  studentid INTEGER UNIQUE, //같은 값 존재 X
  studentname VARCHAR(20) NOT NULL, // NULL 가질 수 없음
  studentage INTEGER, DEFAULT 8 CHECK( studentage >= 8), //값이 입력되지 않으면 기본 값 8 이고 최소 8 이상으로 설정한다.
  adress VARCHAR(20),  NOT NULL,
  PRIMARY KEY (studentid)
    );
~~~

 ### 외래키를 생성
 
* 먼저 학교 도서관 테이블 생성

~~~html
CREATE TABLE ShcoolLibrary(
studentid INTEGER,
bookid INTEGER
bookname VARCHAR(20),
publisher VARCHAR(20), //출판사

);
~~~

* 외래키 생성

~~~html
CREATE TABLE ShcoolLibrary(
studentid INTEGER,
bookname VARCHAR(20),
publisher VARCHAR(20),
bookid INTEGER, 
PRIMARY KEY(bookid),
FOREIGN KEY(studentid) REFERENCES student(studentid) ON DELETE CASCADE
);
~~~

>주의 : 참조되는 테이블(부모 릴레이션)이 존재해야 하며 참조되는 테이블의 기본키여야 한다.

* ON DELETE CASCADE 옵션 : 참조되는 student 테이블의 투플(student.studentid=5일 경우라고 가정)이
* 삭제되면 참조하는 ShcoolLibrary 테이블의 해당 투플(ShcoolLibrary.studentid=5)이 연쇄 삭제(CASCADE)된다.




### ALTER문

* ALTER문은 생성된 테이블의 속성과 속성에 관한 제약을 변경하며, 기본키 및 외래키를 변경한다.

~~~html
ALTER TABLE 테이블 이름
	[ADD 속성이름 데이터타입] 
	[DROP COLUMN 속성이름]
	[ALTER COLUMN 속성이름 데이터타입]
	[ALTER COLUMN 속성이름 [NULL | NOT NULL]]
	[ADD PRIMARY KEY(속성이름)]
	[[ADD | DROP] 제약이름]
~~~

* ADD : 속성 추가
* DROP : 속성 제거
* MODIFY : 속성 변경
* ADD <제약이름>, DROP <제약이름> : 제약사항을 추가하거나 삭제

~~~html
CREATE TABLE Student(
  studentid INTEGER,
  studentname VARCHAR(20),
  studentage INTEGER,
  adress VARCHAR(20)
  );
~~~

*Student 테이블에 VARCHAR(13)의 자료형을 가진 isbn을 추가

~~~html
ALTER TABLE Student ADD isbn VARCHAR(13);
~~~

* isbn 의 데이터 타입 INTEGER로 변경

~~~html
ALTER TABLE Student MODIFY isbn INTEGER;
~~~

*  isbn 속성을 삭제

~~~html
ALTER TABLE Student DROP COLUMN isbn;
~~~

### DROP문

* 테이블을 삭제하는 명령어

>주의 DROP문은 테이블의 구조와 데이터를 모두 삭제하므로 사용에 주의해야함

~~~html
DROP TABLE 테이블이름
~~~

~~~html
DROP TABLE Student; 
//Error Code: 3730. Cannot drop table 'student' referenced by a foreign key constraint 'shcoollibrary_ibfk_1' on table 'shcoollibrary'.	0.000 sec
~~~

> 삭제하려는 테이블의 기본키를 다른 테이블에서 참조하고 있다면 삭제가 거절된다. 테이블을 삭제하기 위해서는 참조하고 있는 테이블을 먼저 삭제해야함


~~~html
DROP TABLE ShcoolLibrary;
~~~

* 참조하고 있는 테이블 삭제 후

~~~html
DROP TABLE Student; //삭제완료
~~~

* 컬럼 삭제 

~~~html
ALTER TABLE 테이블명 DROP `컬럼명`;
~~~
