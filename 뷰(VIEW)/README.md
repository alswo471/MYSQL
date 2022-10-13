# 뷰 

### 뷰의 개념

* 실제 데이터를 저장하지 않는 가상 테이블 (virtual table)
* 데이터베이스를 바라보는 창문 (window)
* 뷰에 대해 사용자가 질의를 요청할 때 비로소 DBMS 는 뷰 정의를 참조하여 질의를 수행
하고 그 결과를 사용자에게 반환
* 주로 기반 테이블로부터 정의되지만 또 다른 뷰를 기반으로도 정의될 수도 있음

<img width="653" alt="image" src="https://user-images.githubusercontent.com/92145785/195530938-9e22510b-90a1-4592-875f-7651557ad2bd.png">

### 뷰의 장점

* 편의성 : 복잡한 질의문 작성이 쉽고 간단해진다
* 보안성 : 데이터 보안 유지가 쉽다
* 재사용성 : 반복되는 질의문 작성에 효율적이다
* 독립성 : 스키마 변경에도 뷰 질의문은 변경할 필요가 없다

### 뷰 생성

* CREATE VIEW 명령문의 형식

~~~
CREATE VIEW 뷰_이름 [ (열_리스트) ]
AS SELECT_검색문

* 3학년 혹은 4학년 학생의 학생이름, 나이, 성, 학년으로 구성된 뷰를 'V1_고학년학생' 이라는 이름으로 생성하시오

~~~sql
create view v21_고학년학생(학생이름, 나이, 성, 학년)
as select 이름, 나이, 성별, 학년
from 학생21 
where 학년>=3 and 학년<=4;
~~~

* 뷰의 생성 확인

~~~sql
select *
from V1_고학년학생;
~~~

* 각 과목별 과목번호, 강의실, 수강 인원수로 구성된 뷰를 'V2_과목수강현황' 이라는 이름으로 생성하시오

~~~sql
create view V2_과목수강현황(과목번호, 강의실, 수강인원수)
AS select 과목.과목번호, 강의실, COUNT(과목,과목번호)
from 과목 join 수강 on 과목.과목번호 = 수강.과목번호
group by 과목.과목번호; 

select * from V2_과목수강현황;
~~~

* V1_고학년학생' 뷰를 기반으로 여학생만으로 구성된 뷰를 'V3_고학년학생' 이름으로 생성하시오

~~~sql
create view V3_고학년여학생
as select * 
from V1_고학년학생
where 성 = '여'

select * from V3_고학년여학생
~~~

#### 뷰를 통한 데이터 변경
 
* 뷰 검색은 제한 없이 가능한 반면 뷰 변경은 특정한 경우로 한정

* 뷰 변경이 제한되는 이유

> 뷰를 정의하는 SELECT_ 검색문 ’의 조건이 다양하기 때문

> 뷰가 참조하는 기반 테이블을 변경해야 하므로 내부 처리가 어려운 경우는 변경이 허용
되지 않음

<img width="517" alt="image" src="https://user-images.githubusercontent.com/92145785/195532752-480ae33e-8f8d-4093-95c9-61979ba9c182.png">


#### 뷰 삭제

* DROP VIEW 명령문의 형식

~~~
DROP VIEW 뷰_이름;
~~~

* DROP VIEW 적용 예

~~~sql
DROP VIEW V1_고학년학생;

ShOW TABLES;
~~~

