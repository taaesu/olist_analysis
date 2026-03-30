## 첫 구매 경험이 재구매 행동에 미치는 영향 분석

&#x20; 

### 핵심 결과

\- 배송 지연 고객의 재구매율은 정상 배송 대비 약 17% 낮게 나타났으나, 절대적인 차이는 크지 않음

\- 낮은 리뷰 점수를 받은 고객군에서 오히려 더 빠른 재구매가 나타나며, 리뷰 점수만으로 재구매 행동을 설명하기 어려움을 확인

&#x20; 

### 인사이트

초기 구매 경험은 재구매 행동과 일정 부분 관련이 있으나, 단일 지표만으로 재구매를 설명하기에는 한계가 있음

&#x20; 

### 분석 방법

\- SQL을 활용한 고객 단위 분석 테이블 구축

\- 재구매 및 배송 지연 기준 정의

\- Python(pandas)을 활용한 재구매율 및 시점 분석

\- 배송 경험 및 리뷰 점수 기준 그룹 비교 분석

\- 분석 결과 해석 및 인사이트 도출

&#x20; 

### 분석 질문

\- 첫 주문 배송 지연이 재구매율에 영향을 미치는가?

\- 첫 주문 리뷰 점수가 재구매 행동에 영향을 미치는가?

&#x20; 

### 데이터

\- Olist E-commerce Dataset (Kaggle)

\- 약 10만 건 주문 / 9개 테이블

\- orders, customers, order\_reviews 3개의 테이블 사용

&#x20; 

### Deliverables

\- 메인 분석: 02\_first\_purchase\_repurchase.ipynb

\- EDA: 01\_eda\_exploration.ipynb

&#x20; 

### Tech Stack

SQL (SQLite) | Python (pandas, matplotlib, seaborn) | Jupyter Notebook

