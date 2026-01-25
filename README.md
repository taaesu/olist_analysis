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

- 배송 지연 분포 및 지역·카테고리별 특성
- 카테고리별 매출 편중 현상
- 리뷰 점수 분포 및 주요 불만 키워드 분석

해당 분석은 메인 프로젝트의 기초 자료로 활용되었다.