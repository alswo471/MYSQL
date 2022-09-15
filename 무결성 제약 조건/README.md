# 무결성 제약 조건 (integrity constraint)

* 관계형 데이터 모델에서 릴레이션 안의 모든 데이터들을 의미적으로 흠 없이 항상 정확
하고 완전한 상태로 유지하기 위해 적용해야할 제약 사항

* 데이터 무결성 (data integrity)
  - 데이터의 일관성과 정확성에 손상이 없도록 유지되는 특성

<br>

### 개체 무결성 제약 조건 (entity integrity)

- 기본키로 지정한 모든 속성은 널 값을 가질 수 없고 릴레이션 안에서 중복되지 않는 유일
한 값을 가져야 한다는 제약 사항

- 기본키 제약 조건 (primary key)

- 개체의 유일성을 선언하는 제약 조건

- DBMS 에게 기본키를 선언함으로써 즉시 적용됨

<br>

### 참조 무결성 제약 조건 (referential integrity

- 외래키로 지정한 속성은 참조하는 릴레이션의 기본키 속성 값과 일치하는 값이나 널 값
만을 가져야 한다는 제약 사항

- 외래키 제약 조건 (foreign key)

- 개체의 참조 관계를 선언하는 제약 조건

- DBMS 에게 외래키를 선언함으로써 즉시 적용됨

- 의미적으로 연관된 두 릴레이션 튜플 사이의 일관성 유지를 위해 사용함

<img width="602" alt="image" src="https://user-images.githubusercontent.com/92145785/190325212-7e719b52-60ae-4716-8f7b-cbb4af66d812.png">

* 개체 무결성 제약 조건

- 기본키는 개체 식별자 (entity identifier) 의 역할

* 참조 무결성 제약 조건
  - 외래키는 개체 참조자 (entity referer) 의 역할

 <br>
 
### 도메인 무결성 제약 조건 (domain integrity constraint)

- 튜플의 모든 속성 값이 각 속성의 도메인에 속한 값만을 취해야 한다는 제약 사항

* SQL 의 CREATE TABLE 명령문 작성 시
  - 각 열의 타입 , NULL/NOT (널 값 허용 여부 ), DEFAULT ( 기본 값 ), CHECK (값 범
  위 체크 조건 ) 등의 키워드 설정을 통해 DBMS 에게 지시
  
  <br>
  
### 유일성 제약 조건 (uniqueness

* 모든 키 속성 값이 서로 중복되지 않고 유일해야 한다는 제약 사항

* 대체키와 밀접한 연관성이 있으며 키 제약 조건 (key constraint) 이라고도 함

* SQL 의 CREATE TABLE 명령문 작성 시
-UNIQUE( 유일 조건 ) 키워드 설정을 통해 DBMS 에게 지시


<img width="876" alt="image" src="https://user-images.githubusercontent.com/92145785/190325978-d9b94ec1-d467-4ed9-b765-a03e8285cbcc.png">


