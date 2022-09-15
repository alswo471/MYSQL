# 관계연산(relation operation)

- 관계형 데이터 모델에서 릴레이션을 조작하기 위한 연산
- 관계형 데이터베이스 언어의 명세 형식이나 내부 처리 과정과 밀접한 연관성이 있음
* 관계 연산의 대표적인 2 가지 표현 방법
  - 관계 대수(relational algebra) : 사용자가 필요로 하는 데이터 흭득 절차 연산들이 적용 순서로 명세
  - 관계 해석(relational calculus) : 사용자가 필요한 데이터가 무엇인지 연산들이 최종 결과 명세

<br>

### 관계 대수와 관계 해석

- 둘 다 기능이나 표현력은 동등함
- 관계 대수나 관계 해석은 형식 언어로서 둘 다 상용 DBMS 가 직접 지원하지는 않으므로
실제 사용할 수 있는 데이터 언어는 아님
- SQL 언어의 작성 방법이나 내부 처리 방식의 이론적 기반을 제공

<img width="593" alt="image" src="https://user-images.githubusercontent.com/92145785/190327276-e7d0de83-9255-4673-9d7f-683d61f6c7ab.png">

<br>

### 관계 대수 (relational algebra)

* 릴레이션을 내부적으로 처리하기 위한 연산 (operation) 들의 집합
  - 코드가 정의
  - 관계형 데이터 모델의 이론적 언어로써 SQL 데이터베이스 언어의 이론적 토대 제공

* 릴레이션에 적용되는 여러 연산들을 포함
  - 모든 연산의 적용 대상도 릴레이션이고 연산 결과 또한 릴레이션
  - 한 개 이상의 입력 릴레이션으로부터 하나의 새로운 결과 릴레이션을 생성

<br>

#### 관계 대수 연산의 종류

  <img width="494" alt="image" src="https://user-images.githubusercontent.com/92145785/190327765-84424667-eef2-489c-adb9-5283d2395625.png">


### 집합 연산 (set operation)

- 릴레이션을 투플 집합 또는 속성 집합으로 간주 이를 처리하는 연산 그룹
- 일반적인 수학 집합 연산과 의미, 기능이 같다.

#### 집합 연산의 종류

<img width="767" alt="image" src="https://user-images.githubusercontent.com/92145785/190328053-5494d09f-26c0-48e6-ab12-104f9b078fcc.png">

<br>

### 차집합 (difference)

- 수학의 차집합과 같은 개념

- 두 릴레이션 R1 과 R2 의 차집합 R1 - R2 가 반환하는 것은 첫 번째 릴레이션 R1 에는 속하
지만 두 번째 릴레이션 R2 에는 속하지 않는 투플로만 구성된 릴레이션

<img width="598" alt="image" src="https://user-images.githubusercontent.com/92145785/190328153-61cbf570-1166-477b-b943-181da28a7389.png">

### 카티션 프로덕트 (cartesian product)

- 두 릴레이션의 모든 투플을 수평으로 결합하는 연산

- 두 릴레이션 R1 과 R2 의 카티션 프로덕트 R1 × R2 가 반환하는 것은 첫 번째 릴레이션
R1 의 각 투플에 대해 두 번째 릴레이션 R2 의 모든 투플을 반복하여 앞뒤로 연결한 릴레이션 즉 , R1 과 R2 투플들의 모든 조합으로 구성된 결과 릴레
이션을 반환

-두 릴레이션의 기계적인 조합을 만들기 때문에 그 자체보다는 추가적으로 다른 관계
대수 연산을 조합할 때 유용함

<img width="505" alt="image" src="https://user-images.githubusercontent.com/92145785/190328409-0517d149-1292-4fc7-946d-be01cc0e8489.png">

<br>

#### 집합 연산 종류 & 연산적용 개념

<img width="575" alt="image" src="https://user-images.githubusercontent.com/92145785/190328500-1d39261a-d3b6-4133-a8ae-7344845162b5.png">

#### 집합 연산의 적용 결과 (차수 / 카디널리티의 변화)

<img width="779" alt="image" src="https://user-images.githubusercontent.com/92145785/190328609-fc734bf4-5ebb-4d38-a72e-1aa055338260.png">

<br>

### 관계 연산 (relation operation)

- 릴레이션의 구조적 특성에 기반을 둔 연산을 포함

- 관계형 데이터 모델을 위해 고안된 연산들

<img width="791" alt="image" src="https://user-images.githubusercontent.com/92145785/190328731-fff9a3d7-32d6-4d72-aa1a-3ca11b3415d4.png">


<br>

#### 셀렉트(select)

* 릴레이션에서 특정 투플을 추출하는 연산
  - 연산자는 'σ'( 시그마 , sigma) 를 사용
  - 단항 연산 (unary operation)

- 셀렉트 연산 σ 선택 조건식 (R) 이 반환하는 것은 릴레이션 R 의 투플 중에서 명세된 ‘선택 조
건식 ’을 만족하는 투플로만 구성된 릴레이션

- 릴레이션을 수평 분할하는 효과

<img width="554" alt="image" src="https://user-images.githubusercontent.com/92145785/190329099-6970099d-bbc8-4b5c-afcb-fb3285306af5.png">

#### 연산 ex)

<img width="359" alt="image" src="https://user-images.githubusercontent.com/92145785/190329517-4b79ec1e-3257-4598-9b6a-76d9d53bd953.png">

<br>

### 프로젝트 (project)

* 릴레이션에서 특정 속성을 추출하는 연산
  - 연산자는 Π 파이 , 를 사용
  - 단항 연산

- 프로젝트 연산 Π 속성 리스트 ( 가 반환하는 것은 릴레이션 R 에 속한 속성 중에서 ‘속성 리
스트’에 명세된 속성으로만 구성된 릴레이션

- 릴레이션을 수직 분할하는 효과

<img width="560" alt="image" src="https://user-images.githubusercontent.com/92145785/190331885-ac274e4c-6d47-4326-b770-6609313e82be.png">

#### 연산 ex)
<img width="367" alt="image" src="https://user-images.githubusercontent.com/92145785/190331939-4e2d79fc-7b78-4542-bebd-da13e320e867.png">


