# 첫 구매 경험이 고객 재구매 행동에 미치는 영향 분석 (Olist E-commerce Data)
 
## 1. Project Overview

Olist는 다양한 판매자가 입점한 브라질 기반 전자상거래 플랫폼이다.  
플랫폼형 커머스의 특성상 신규 고객 유입뿐 아니라 기존 고객의 재구매는 매출 성장과 서비스 안정성에 중요한 역할을 한다.
특히 첫 구매 경험은 고객의 향후 재구매 행동에 큰 영향을 미칠 수 있다. 

본 프로젝트는 고객의 첫 구매 경험이 이후 재구매 행동에 어떤 영향을 미치는지 데이터를 통해 검증하는 것을 목표로 한다.

## 2. Analysis Questions

1. 첫 주문 배송이 지연된 고객은 재구매를 덜 하는가?
2. 첫 주문 리뷰 점수에 따라 재구매까지 걸린 시간에 차이가 있는가?

## 3. Dataset

- Source: Kaggle – Brazilian E-Commerce Public Dataset by Olist  
- Period: 2016 ~ 2018  
- Size: 약 100,000건 주문, 9개 테이블

본 분석에서는 다음 주요 테이블을 활용하였다.

- orders
- customers
- order_reviews

## 4. Key Definitions

- 고객 단위: 
   - customer_unique_id

- 첫 주문: 
   - 고객별 최초 order_purchase_timestamp

- 재구매:
   - 동일 고객의 주문 수 ≥ 2
   - 첫 주문 이후 60일 이내 추가 주문 발생

- 배송 지연:
   - order_delivered_customer_date > order_estimated_delivery_date

- 분석 대상:
   - order_status = 'delivered'
   - 실제 배송일 정보가 없는 8건 제외

- 리뷰 점수:
   - 주문별 리뷰가 여러 개인 경우 평균값 사용
   - 리뷰가 없는 주문은 NaN 처리

## 5. Analysis Process

1. CSV 데이터를 SQLite 데이터베이스로 통합
2. SQL 기반 고객 단위 분석 테이블 생성
3. Python(pandas)을 활용한 지표 계산
4. 배송 경험 및 리뷰 점수에 따른 재구매 행동 비교
5. 결과 해석 및 비즈니스 시사점 도출
 
## 6. Key Findings

- 첫 주문 배송이 지연된 고객의 60일 이내 재구매율은 정상 배송 고객 대비 약 0.16% 낮게 나타났으며, 이는 상대적으로 약 17% 낮은 수준이다.
-  다만 전체 재구매율이 매우 낮아 배송 개선만으로 재구매율을 크게 개선하기에는 한계가 있을 가능성이 있다.

- 첫 주문 리뷰 점수가 낮은 고객군에서 재구매까지 걸린 시간이 더 짧게 나타났다.
- 이는 첫 주문 경험의 만족도보다는 다른 요인이 재구매 시점에 더 큰 영향을 미칠 가능성이 있다.

## 7. Deliverables

- 메인 분석 노트북:
   - 02_first_purchase_repurchase.ipynb

- 보조 분석 (EDA)  
   - 01_eda_exploration.ipynb

## 8. Tech Stack

- SQL (SQLite)
- Python (pandas, matplotlib, seaborn, scipy)
- Jupyter Notebook

## Additional Analysis (Exploratory)

본 프로젝트 이전 단계에서 Olist 데이터 구조 이해를 위해
주문, 배송, 매출, 리뷰 전반에 대한 탐색적 분석을 수행하였다.

<<<<<<< HEAD
- 배송 지연 분포 및 지역·카테고리별 특성
- 카테고리별 매출 편중 현상
- 리뷰 점수 분포 및 주요 불만 키워드 분석

해당 분석은 메인 프로젝트의 기초 자료로 활용되었다.
=======
   - 주문, 배송, 매출, 리뷰, 지역 등 다방면 분석

4\. 가설 검정

   - t-test를 활용하여 배송 예측 정확도 검증

5\. 시각화

   - 'matplotlib' / 'seaborn' / 'plotly' 활용

6\. 인사이트 도출

   - 각 분석 결과에 기반한 비지니스 시사점 정리



\## 주요 분석 내용 및 인사이트



   ### 배송 분석

   - 가설(H₀) : 실제 배송일과 예상 배송일의 차이는 없다 → 배송 예측 시스템은 정확하다.

   - 대립가설(H₁): 두 값에는 차이가 존재한다 → 배송 예측 시스템에 오차가 있다.

   - 결과 :  p-value < 0.05 → 귀무가설 기각

   - 해석 : 배송 예측 시스템에 통계적으로 유의한 오차 존재

   - 평균 배송 소요: 약 12일

   - IQR 기준(Q3+1.5×IQR)으로 25일 초과 배송을 지연으로 분류

   - 배송 지연은 특정 카테고리(bed\_bath\_table, health\_beauty 등)와 특정 지역(RJ, SP, BA 등)에서 집중적으로 발생

   Business insight :

    → 배송 지연이 집중된 특정 제품군 및 지역을 우선적으로 관리하면 전체 지연율을 빠르게 개선할 수 있음



   ### 제품·매출 분석

   - 제품 카테고리별 매출 상위 10개 비중 : 전체 매출의 63%를 차지

   - 하위 10개 카테고리는 0.09%에 불과함 → 매출 편중 심화

   - 제품 가격과 배송 시간 간의 유의한 상관관계는 없음

   - 2017년 11월 24일 일매출 급등 → 블랙프라이데이로 인한 거래량 상승 효과

   Business insight :

   → 매출 비중이 낮은 카테고리는 상품 경쟁력 부족 또는 노출 부족 가능성이 있어, 프로모션·가격 조정등의 개선 전략이 필요함



   ### 리뷰 분석

   - 리뷰 점수는 4~5점 중심으로 분포

   -  1~2점대 비중은 약 15%

   - 저평가 리뷰의 주요 키워드: “늦게 왔다”, “안 왔다”, “문제 있다”

   - 배송 지연 및 품질 관련 이슈가 낮은 평점의 핵심 요인

   Business insight :

   → 배송 및 물류 개선은 리뷰 점수 상승, 고객 불만 감소, 재구매율 증가 등 고객 경험 전반에 긍정적 효과를 가져올 것으로 기대됨



\## 사용 기술

\- SQL: 데이터 추출 및 가공

\- Python: pandas, seaborn, matplotlib, plotly, scipy

\- Jupyter Notebook / SQLite



\## 결론

본 분석을 통해 배송 지연의 원인(제품군·지역), 매출 구조의 편중, 리뷰 텍스트 기반 고객 불만 요인을 도출하였고,

데이터 기반 의사결정을 위한 인사이트를 도출하는 과정을 경험했습니다.



\## Tableau Dashboard

\- https://public.tableau.com/views/olist_dashboard_17639630074110/OlistDashboard?:language=ko-KR&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link
>>>>>>> c7ffc49bab340cd4484ebf525264b0e0805e870d
