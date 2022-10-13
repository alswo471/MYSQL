### CRATE TABLE 문

~~~sql
create table 학생21
(학번 char(4) not null,
이름 varchar(20) not null,
주소 varchar(50) null default '미정',
학년 int not null,
나이 int null,
성별 char(1) not null,
휴대폰번호 char(13) null,
소속학과 varchar(20) null,
primary key (학번),
unique (휴대폰번호));
~~~

~~~sql
create table 과목21
(과목번호 char(4) not null primary key,
이름 varchar(20) not null,
강의실 char(5) not null,
개설학과 varchar(20) not null,
시수 int not null);
~~~

~~~sql
create table 수강21
(학번 char(6) not null,
과목번호 char(4) not null,
신청날짜 date not null,
중간성적 int null default 0,
기말성적 int null default 0,
평가학점 char(1) null,
primary key(학번, 과목번호),
foreign key(학번) references 학생21(학번),
foreign key(과목번호) references 과목21(과목번호));
~~~

### foreign 제약조건으로 인한 오류 떄문에 제약 조건 맞추는 코드
~~~sql
select * from 학생21;
select * from 수강21;
insert into 학생21 select * from 학생;
insert into 수강21 select * from 수강;
insert into 과목21 select * from 과목;

delete from 수강21 where 과목번호='c002' && 학번='s004';

alter table 수강21 add foreign key(학번) references 학생21(학번);
alter table 수강21 add foreign key(과목번호) references 과목21(과목번호);
~~~

### ALTER 문


~~~sql
alter table 학생21
add 등록날짜 datetime not null default '2019-12-30';
~~~

~~~sql
-- 취미열을 입력 null 기본값 로봇조립으로 지정
alter table 학생21
add 취미 varchar(50) null default '로봇조립';
~~~

### DROP문

~~~sql
alter table 학생21
drop column 등록날짜;
~~~

~~~sql
alter table 학생21
drop column 취미;
~~~


~~~sql
-- 봉사활동 점수 50을 적용시키시오.
alter table 학생21
add 봉사활동점수 int not null default 50;
~~~


~~~sql
-- 소속학과가 컴퓨터인 학생들은 10점 감점하시오.
update 학생21 set 봉사활동점수 = 봉사활동점수 - 10 where 소속학과 = "컴퓨터";
~~~


~~~sql
-- 성씨가 '이'씨 사람들에게 학년을 1씩 증가시키시오.
update 학생21 set 학년 = 학년 + 1 where 이름 like "이%";
~~~

### CREATE USER문


~~~sql
create user 'user41'@'127.1.1.1' identified by '1111';
create user 'user42'@'localhost' identified by '2222';
create user 'user43'@'192.182.10.2' identified by '3333';
create user 'user44'@'%' identified by '4444';
~~~

* 생성된 사용자 계정 정보 확인

~~~sql
select host. user from mysql.user;
~~~

