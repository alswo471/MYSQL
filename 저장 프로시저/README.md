## 저장 프로시저 (stored procedure)

- 미리 작성하여 데이터베이스 안에 저장한 SQL 문장들의 묶음

- 독립된 프로그램으로 데이터베이스 안에 하나의 객체로 저장

- 장점 : 최적화된 SQL 문을 미리 데이터베이스에 작성해둘 수 있고 복잡한 SQL 문을 전달
할 필요가 없어 네트워크 부하가 줄어들며 여러 응용 프로그램간의 공유가 가능함

### CREATE PROCEDURE 문

~~~sql 
create procedure 프로시저_이름
begin

...
sql 명령문;
...
end
~~~


* '과목' 테이블에 데이터를 추가(입력 또는 수정)하는 저장 프로시저를 작성하시오.


~~~sql 
delimiter //
create procedure InsertOrUpdateCourse(
in CourseNo varchar(4),
in CourseName varchar(20),
in CourseRoom char(3),
in CourseDept varchar(20),
in CourseCredit int)
begin
declare Count int;
select count(*) into Count from 과목 where 과목번호=CourseNo;
if(Count=0) then
	insert into 과목(과목이름, 이름, 강의실, 개설학과, 시수)
    values(CourseNo, CourseName, CourseRoom, CourseDept, CourseCredit);
    else 
    update 과목
    set 이름 = CourseName, 강의실=CourseRoom, 개설학과=CourseDept, 시수=CourseCredit
    where 과목번호=CourseNo;
  end if;
end //
delimiter ;
~~~

