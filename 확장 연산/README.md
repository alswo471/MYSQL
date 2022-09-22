# 확장 연산

#### 기존 관계 대수 연산을 확장하여 추가로 정의

- 자연 조인의 확장된 형태인 세미 조인 연산과 외부 조인 연산
- 합집합의 확장된 형태인 외부 합집합 연산

<br>

#### 확장 관계의 연산의 종류

<img width="900" alt="image" src="https://user-images.githubusercontent.com/92145785/191664502-219b4032-654a-4a4e-9ae5-a5448cf2a762.png">

<br>

#### 세미 조인 

-자연 조인이 변환하는 결과 릴레이션 중에서 한쪽 릴레이션 속성만으로 한정하여 반환하는 제안적 자연 조인 연산

<img width="500" alt="image" src="https://user-images.githubusercontent.com/92145785/191664858-7e7dd90d-5833-497c-a84a-ba29948cc827.png">

- 릴레이션 R1 과 R2 의 세미 조인 R1 R2 는 R2 와의 자연 조인에 참여할 수 있는 R1 의 투
플만을 선택하여 반환

- R2 를 ‘조인 속성’ 으로만 프로젝트한 뒤 , 결과 릴레이션을 R1 에 다시 자연 조인한 결과와
같음

<br>


#### 왼쪽 세미 조인

- 자연 조인 결과 중 왼쪽 릴레이션의 속성만 반환

<img width="700" alt="image" src="https://user-images.githubusercontent.com/92145785/191665043-fb12827d-0336-49b6-88d5-c77e4c208940.png">

<br>

#### 오른쪽 세미 조인

- 자연 조인 결과 중 오른쪽 릴레이션의 속성만 반환

<img width="700" alt="image" src="https://user-images.githubusercontent.com/92145785/191665193-23ac0ef7-2449-4c64-8405-958155ce4ec8.png">

<br>

#### 외부 조인 (outer join)

- 자연 조인 결과에 포함되지 않는 , 조인에 실패한 투플까지 모두 포함하도록 확장한 연산
- 자연 조인의 확장된 형태
- 대응 속성 없이 추가된 투플들은 널 값을 채워서 반환

- 모든 투플을 반환하는 대상 릴레이션의 위치에 따라 분류
- 완전 외부 조인 ⟗
- 왼쪽 외부 조인 ⟕
- 오른쪽 외부 조인 ⟖ )

<br>

#### 완전 외부 조인 (full outer join)

- 왼쪽과 오른쪽 R1, R2 릴레이션의 모든 투플을 빠짐없이 조인 결과에 포함하도록 대응
- 투플이 없는 경우 널 값을 채워서 반환

<img width="700" alt="image" src="https://user-images.githubusercontent.com/92145785/191665493-43d34bd0-7d88-4f20-895b-f2c71eeebec6.png">

<br>

#### 왼쪽 외부 조인 (left outer join)

- 왼쪽 R1 릴레이션의 모든 투플을 빠짐없이 조인 결과에 포함하도록 대응 투플이 없는 경
우 널 값을 채워서 반환

<img width="700" alt="image" src="https://user-images.githubusercontent.com/92145785/191665611-d533d024-a2f9-4d4a-a5ef-38232e4d9942.png">

<br>

#### 오른쪽 외부 조인 (right outer join)

- 오른쪽 R2 릴레이션의 모든 투플을 빠짐없이 조인 결과에 포함하도록 대응 투플이 없는
경우 널 값을 채워서 반환

<img width="700" alt="image" src="https://user-images.githubusercontent.com/92145785/191665659-b3442a32-2ab1-46cf-8454-d3c404f95070.png">

<br>

외부 합집합 (outer union)

- 합병 가능하지 않은 정확히 말하면 부분적으로만 합병 가능한 두 릴레이션의 투플을 합
병

- 대응하는 속성이 없는 경우도 널 값을 채워 모든 투플을 결과 릴레이션에 포함

<img width="700" alt="image" src="https://user-images.githubusercontent.com/92145785/191665778-9456d6f4-1074-4d40-9e4b-7e1b0a15e69d.png">

#### 관계 대수식 작성 예

- 예제 릴리이션

<img width="700" alt="image" src="https://user-images.githubusercontent.com/92145785/191666257-064af8de-345a-41b1-a4be-c4b2c3ce9c05.png">

<br>

- 학생1 릴레이션에 학번이 "s004", 이름이 '이영애', 학년이 2학년 , 성별이 '여' 인 학생을 삽입하세요

<img width="300" alt="image" src="https://user-images.githubusercontent.com/92145785/191666060-b310e24a-44f7-4972-bb22-3f9dbaeb1bbe.png">

<br>

- 학생1 릴레이션에서 이름이 '이승환' 인 학생을 삭제하세요

<img width="500" alt="image" src="https://user-images.githubusercontent.com/92145785/191666084-beb05b28-6cc7-4a3a-89a1-30ec743299d2.png">

<br>

- 학생 1 릴에이션에서 이름이 '김연아' 인 학생의 학년을 3학년으로 수정하세요

<img width="500" alt="image" src="https://user-images.githubusercontent.com/92145785/191666101-4358fdcc-2c39-46f9-913e-313744d9f08e.png">

<br>

- 모든 학생의 이름과 학년을 검색하세요 

<img width="500" alt="image" src="https://user-images.githubusercontent.com/92145785/191666119-0dd0f9fd-832c-4635-bf03-9d40581a8a54.png">

<br>

'137' 강의실에서 강의되는 모든 과목을 수강하는 학생 이름을 

<img width="500" alt="image" src="https://user-images.githubusercontent.com/92145785/191666139-5ac3ace2-9280-430f-b42c-9607c8a230fc.png">

<br>

#### 최적의 관계 대수식을 결정하기 위한 DBMS 내부의 질의 트리 작성과 최적화 과
정

- 다음 질의 요청에 대한 SQL 문장과 관계 대수식을 작성

- 예 ) ‘ 학생이 수강한 과목이름과 평가학점 , 학생의 이름을 검색하시오

<img width="700" alt="image" src="https://user-images.githubusercontent.com/92145785/191667057-337922be-332d-41aa-a100-eb95d632a5e7.png">

<br>

- 전달받은 SQL 질의문에 대해 DBMS 가 내부적으로 생성될 수 있는 후보 관계 대
수식 중의 하나

<img width="400" alt="image" src="https://user-images.githubusercontent.com/92145785/191667184-6253f131-b828-4f50-9b7d-e242b0fd10cf.png">

<br>

#### 질의 트리 (query tree)

- 생성된 후보 관계 대수식은 DBMS 안의 질의 최적화 과정을 위해 질의트리로 변환

- DBMS 의 질의 처리기는 여러 가능한 후보 질의 트리들을 최적에 가까운 트리로 변환해
가며 하나의 질의 실행 계획 (query execution 을 결정

* 질의 최적화 (query optimization) 의 핵심
-연산 순서를 조정함으로써 연산으로 생기는 중간 릴레이션의 크기를 최소화하는 것

<img width="700" alt="image" src="https://user-images.githubusercontent.com/92145785/191667350-2a69409d-4d7a-41a0-bd3c-2d743881be53.png">

#### 질의 트리 최적화 변환 규칙

- AND 연산자로 연결된 셀렉트 연산은 분리하여 개별 셀렉트 연산으로 변환

- 셀렉트 연산은 가능한 한 먼저 실행되도록 질의 트리 아래쪽으로 이동

- 프로젝트 연산도 프로젝트 속성을 분리해서 개별 프로젝트 연산으로 변환한 뒤 , 가능한
한 먼저 실행되도록 질의 트리 아래쪽으로 이동

- 여러 셀렉트 연산중에서는 결과 릴레이션 크기가 가장 작은 것부터 제한적 셀렉트 연산
순으로 질의 트리 최하단으로 이동

- 카티션 프로덕트 연산과 바로 위의 셀렉트 연산은 하나의 조인 연산으로 통합 변환

- OR 연산자로 연결된 조건식은 가능하면 AND 연산자로 연결된 조건식으로 변환







