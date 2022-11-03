## 트리거

- 데이터 변경 등 명세된 이벤트 발생시 감지하여 자동 실행되는 사용자 정의 프로시저

- INSERT, UPDATE, DELETE 명령문의 실행 직전 · 후 자동으로 호출되어 실행

> 트리거를 생성하는 CREATE TRIGGER 명령문의 형식

~~~sql
create trigger 트리거_이름
[before | after] [ insert|update|delete| on 테이블이름 for each row

begin

...
sql 명령문 ;
...

end
~~~

~~~sql
create table 남녀학생총수 (
성별 char(1) not null default ' ',
인원수 int,
primary key(성별));
~~~

<br/>

~~~sql
insert into 남녀학생총수 select '남', count(*) from 학생 where 성별 = '남';
insert into 남녀학생총수 select '여', count(*) from 학생 where 성별 = '여';
~~~

<br/>

* 트리거 생성

~~~sql
delimiter //
create trigger AfterInsertStu1
after insert on 학생 for each row
begin 
if (new.성별 = '남') then
	update 남녀학생총수 set 인원수 = 인원수 + 1 where 성별 = '남';
elseif (new.성별 = '여' ) then
	update 남녀학생총수 set 인원수 = 인원수 + 1 where 성별 = '여';
    end if ;
    end ;
// delimiter ;
~~~

<br/>

- 트리거 실행

~~~sql
insert into 학생
values('s008','최동석','경기 수원', 2 , 26 ,'남','010-8888-6666','컴퓨터');
~~~
