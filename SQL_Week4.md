# SQL_ADVANCED 4주차 정규 과제 

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_4th_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=DMNpkj_bZIs&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=13
https://www.youtube.com/watch?v=BUHj-behLyc&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=14
https://www.youtube.com/watch?v=JrXWxku7ZIM&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=15
-->

**교재 실습 예제 파일은 07_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_4th_TIL

### 5장 테이블과 뷰
#### 01. 테이블 만들기
#### 02. 제약조건으로 테이블을 견고하게
#### 03. SQL 가상의 테이블: 뷰 


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~99    | ✅         |
| 2주차 | p.102~155   | ✅         |
| 3주차 | p.158~213  | ✅         |
| 4주차 | p.216~271 | ✅         |
| 5주차 | p.274~327 | 🍽️         |
| 6주차 | p.330~369 | 🍽️         |
| 7주차 | p.372~407 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. 테이블 만들기 

<!-- 이번 챕터에서 제시된 실습을 흐름에 맞게 진행한 후, 실습 과정이 보일 수 있도록 인증 사진을 2장 이상 제출해 주세요. -->

> <img width="482" height="344" alt="image" src="https://github.com/user-attachments/assets/b163eb0a-9538-48ac-af1a-c91e0791c965" />
> <img width="577" height="278" alt="image" src="https://github.com/user-attachments/assets/d2f7da9f-ed67-4b9a-ac81-9317996f9a05" />
> <img width="823" height="93" alt="image" src="https://github.com/user-attachments/assets/0914813d-79eb-482f-9247-125e8b8f62f1" />
> <img width="616" height="82" alt="image" src="https://github.com/user-attachments/assets/b2eb06e3-5b19-4526-81fe-117f2d1ac4f9" />
> <img width="821" height="208" alt="image" src="https://github.com/user-attachments/assets/2988c5be-d646-4b10-a841-4d57dd706c64" />



## 2. 제약조건으로 테이블을 견고하게 

<!-- 제약조건에 관해 배우게 된 점을 적어주세요. -->

- 데이터의 무결성을 지키기 위한 핵심 장치

- PRIMARY KEY : 각 행 구분
    - 중복 불가
    - NULL 불가
- FOREIGN KEY : 두 테이블을 연결하여 데이터 관계 유지
    - 참조 테이블의 값은 반드시 기준 테이블에 존재해야 함

- 그 외
    - UNIQUE : 중복을 허용하지 않음. 다만 NULL은 허용 가능
    - CHECK : 입력값이 조건에 맞는지 검사
    - DEFAULT : 값을 입력하지 않으면 자동으로 기본값 입력
    - NOT NULL : 반드시 값 입력

- ON UPDATE CASCADE / ON DELETE CASCADE
    - 기준 테이블의 값이 수정되거나 삭제될 때, 참조 테이블의 값도 자동으로 함께 수정/삭제 -> 데이터 불일치 감소

> **확인문제: 다음 보기 중에서 각 문항이 설명하는 것을 고르세요.**

보기는 아래와 같습니다.
```
CHECK / DEFAULT / PRIMAY KEY / UNIQUE / NOT NULL / FOREIGN KEY
```

```
여기에 답과 그 이유를 적어주세요!
1. 입력되는 데이터가 조건에 맞는지 검사하는 기능: CHECK
    이유: 입력값이 지정한 조건을 만족하는지 검사하는 역할
2. 값을 입력하지 않으면 자동으로 들어갈 값: DEFAULT
    이유 : 사용자가 값을 따로 입력하지 않았을 때 자동으로 기본값 배정
3. 빈 값을 입력하는 것을 허용하지 않음: NOT NULL
    이유 : 해당 열에 반드시 값이 있어야 한다는 의미
```

## 3. 가상의 테이블: 뷰 

<!-- 뷰에 관해 배우게 된 점을 적어주세요. -->

- 실제 데이터 직접 저장 X, SELECT 문의 결과를 마치 하나의 테이블처럼 보여주는 데이터베이스 개체 = SELECT 문

- CREATE VIEW : 뷰 생성
- 테이블처럼 SELECT로 조회가능
- 필요한 열만 보여줌 -> 보안에 유리
- 복잡한 JOIN 문을 뷰 생성 -> 이후 단순한 조회만으로 사용 가능
- 복합 뷰는 일반적으로 읽기 전용
- ALTER VIEW/DROP VIEW : 뷰 수정/삭제
- WITH CHECK OPTION : 뷰의 조건에 맞는 데이터만 입력

> **확인문제: 다음은 뷰의 특징입니다. 거리가 먼 것을 하나 고르세요.**

보기는 아래와 같습니다.
```
1️⃣ 뷰에는 테이블의 모든 열을 포함시켜야 합니다.
2️⃣ 뷰는 복잡한 SQL을 단순하게 만드는 효과가 있습니다.
3️⃣ 뷰는 보안에 도움이 됩니다.
4️⃣ 일부 사용자가 테이블에는 접근하지 못하게 하고, 뷰에만 접근하도록 설정할 수 있습니다.
```

```
1️⃣ 뷰에는 테이블의 모든 열을 포함시켜야 합니다.
뷰는 필요한 열만 선택해서 특정 열만 보여줄 수 있음
```


---

# 2️⃣ 실습과제

## 1. 데이터베이스 구축

아래 코드를 MySQL Workbench에 붙여넣은 후,  
**전체 드래그 → 실행 (Ctrl + Shift + Enter)** 하여 데이터베이스를 생성하세요.

```sql
CREATE DATABASE IF NOT EXISTS week4_db;
USE week4_db;
```

## 2. 실습문제

1. 다음 조건을 만족하는 `users` 테이블을 생성하시오.
```
- user_id는 INT이며 **기본키(Primary Key)**로 설정합니다.
- name은 VARCHAR(20)이며 NULL을 허용하지 않습니다.
- email은 VARCHAR(50)이며 중복을 허용하지 않습니다.
- signup_date는 DATE 타입으로 설정합니다.
- grade는 INT이며 기본값(Default)을 1로 설정합니다.
```

2. 다음 조건을 만족하는 orders 테이블을 생성하시오.
```
- order_id는 INT이며 기본키(Primary Key)로 설정합니다.
- user_id는 INT이며 NULL을 허용하지 않습니다.
- amount는 INT이며 0보다 커야 합니다.
- order_date는 DATE 타입으로 설정합니다.
```

3. 다음 조건을 만족하여 데이터를 삽입하시오.
```
- users 테이블에 3명 이상의 데이터를 직접 INSERT 하시오.
- orders 테이블에 3건 이상의 데이터를 직접 INSERT 하시오.
```

4. users와 orders 테이블을 활용하여 다음 컬럼을 보여주는 뷰 user_order_view를 생성하시오.
```
- user_id
- name
- amount
```

5. 생성한 user_order_view를 조회하시오.

## 3. 제출 방법

1. 각 문제의 실행 결과가 보이도록 화면을 캡처합니다.
2. 테이블 생성 결과, 데이터 삽입 결과, 뷰 생성 및 조회 결과가 모두 보이도록 제출합니다.

**1 + 2**
> <img width="868" height="405" alt="image" src="https://github.com/user-attachments/assets/230b4791-6d08-412e-8ee0-239d3b0c3ccd" />
 
**3**
> <img width="795" height="344" alt="image" src="https://github.com/user-attachments/assets/c1ecf009-06c9-457f-af0b-23151e1c58cf" />
> <img width="818" height="343" alt="image" src="https://github.com/user-attachments/assets/c8cc9719-2891-4d83-8472-16ba036dc8a7" />

**4**
> <img width="1292" height="596" alt="image" src="https://github.com/user-attachments/assets/581be1d8-e555-4f4b-b450-258833775c59" />

**5**
> <img width="551" height="197" alt="image" src="https://github.com/user-attachments/assets/1ca77a41-88e8-4e69-b629-3cbdc2d33052" />

### 🎉 수고하셨습니다.







