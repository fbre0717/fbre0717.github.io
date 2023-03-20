---
# multilingual page pair id, this must pair with translations of this page. (This name must be unique)
lng_pair: Paper_Critiques01
title: 150 Successful Machine Learning Models:6 Lessons Learned at Booking.com

# post specific
# if not specified, .name will be used from _data/owner/[language].yml
# author: Mr. Green's Workshop
# multiple category is not supported
category: 논문
# multiple tag entries are possible
tags: [논문, 머신러닝]
# thumbnail image for post
img: ""
# disable comments on this page
#comments_disable: true

# publish date
# date: "`r format(Sys.Date())`"  => 오류
date: 2023-03-20 16:20:00 +0900

# seo
# if not specified, date will be used.
#meta_modify_date: 2022-02-10 08:11:06 +0900
# check the meta_common_description in _data/owner/[language].yml
#meta_description: ""

# optional
# please use the "image_viewer_on" below to enable image viewer for individual pages or posts (_posts/ or [language]/_posts folders).
# image viewer can be enabled or disabled for all posts using the "image_viewer_posts: true" setting in _data/conf/main.yml.
#image_viewer_on: true
# please use the "image_lazy_loader_on" below to enable image lazy loader for individual pages or posts (_posts/ or [language]/_posts folders).
# image lazy loader can be enabled or disabled for all posts using the "image_lazy_loader_posts: true" setting in _data/conf/main.yml.
#image_lazy_loader_on: true
# exclude from on site search
#on_site_search_exclude: true
# exclude from search engines
#search_engine_exclude: true
# to disable this page, simply set published: false or delete this file
#published: false
---

<!-- outline-start -->

[150 Successful Machine Learning Models:6 Lessons Learned at Booking.com](https://dl.acm.org/doi/abs/10.1145/3292500.3330744)

<!-- outline-end -->
논문을 읽고 제가 이해한 것을 바탕으로 정리한 것입니다. 잘못 이해한 부분이 있을 수 있습니다.

# ABSTRACT
머신러닝을 Booking.com에 적용을 시켰다. 최근 자료들은 머신러닝의 알고리즘에 중점을 두고 있고, 상업적으로 어떤 영향을 미치는지는 많이 발표되지 않았다. 이 논문을 통해 우리가 머신러닝을 적용하여 150가지의 성공적인 상품을 만들면서 얻은 교훈에 대해 설명한다. 주요 결론은 다른 분야와 통합된 반복적인 가설 중심 프로세스(iterative, hypothesis driven process, intergrated with other disciplines)가 기본이 되었다는 것이다.

# 1.INTRODUCTION
Booking.com과 같은 숙박 시스템은 다음의 몇가지 근본적인 문제가 있었다.
1. 노래와 영화는 다르게, 추천해준 숙소를 도중에 취소할 수가 없다.
2. 기존의 숙소 검색 조건에는 목적지, 날짜, 숙박 인원 뿐, 정보가 적기 때문에 좋은 추천을 하기 어려웠다.
3. 목적지, 날짜, 객실 수 등 복잡한 차원을 구성해야 한다.
4. 숙박시설의 공급이 유동적이다.
5. 사람들은 숙소를 자주 방문하지 않기 때문에 그 사이에 선호도가 변할 수도 있는 등 지속적으로 콜드 스타트 문제가 발생한다.(콜드 스타트란 제품을 추천하려고 해도 신규 고객의 경우 자료가 없어서 취향에 대한 분석이 어려운 상황을 말한다.)
6. 숙소에는 설명, 사진, 리뷰, 평점 등 다양한 정보들로 인해 결정을 내리기 어렵다.

기여한 목록
- 상용 제품에서 머신러닝이 미치는 영향에 대한 대규모 연구
- 머신러닝 프로젝트의 교훈 모음
- 각 단계에서 필요한 기술

# 2.INCEPTION: MACHINE LEARNING AS A SWISS KNIFE FOR PRODUCT DEVELOPMENT
여기서 SWISS KNIFE는 스위스 군용 칼처럼 다용도 칼을 의미한다.
특정 분야에 매우 잘 맞는 모델을 설계하면 그 분야에 대해서는 강한 영향을 줄 수 있다. 하지만 그것보다는 광범위에 걸쳐 사용가능한 모델을 설계하는 것이 훨씬 더 효과적이다.

# 2.1 Model Families
## 2.1.1 Traveller Preference Models
사용자가 유연성이 많은지 적은지를 판단한다. 예를들어 날짜에 대해 유연성이 크다면, 예약가능한 여러 날짜들을 보여준다. 그렇지 않다면, 고객이 원하는 정확한 날짜만 보여주게된다.
## 2.1.2 Traveller Context Models
사용자의 여행 모델에 대하여 판단한다. 예를들면 가족 단위의 여행을 한다던가, 여러 도시를 옮겨다니며 여행을 할 수 있다. 이런 여행 자체에 대해서 Context라고 하며, 이것을 예측하는 것은 중요하다. 숙소 검색 첫 단계에서부터 자녀의 수를 입력하게 되면 아이들의 출입을 금지하는 숙소는 검색하지 않게되어 사용자의 부정적인 경험을 줄일 수 있다.
## 2.1.3 Item Space Navigation Models
사용자가 정보를 찾을 때 사용하는 스크롤이나 클릭, 정렬 등의 행위 등을 기록하여 사용자의 취향을 빠르게 고려하여 더 좋은 결과를 보여준다.
## 2.1.4 User Interface Optimization Models
인터페이스도 사용자의 행동에 큰 영향을 미치기 때문에, 최적의 사용자 인터페이스를 결정한다.
## 2.1.5 Content Curation
현재 사용자가 수집할 수 있는 정보가 상당히 방대하기 때문에 이러한 정보들을 요약해준다.
## 2.1.6 Content Augmentation
수집한 다양한 데이터를 바탕으로 그것을 분석하여 추가적인 정보를 제공한다. 예를 들면 당일 기준 가장 저렴한 숙소를 알려주거나, 가격 동향 그래프를 제공해준다.

# 2.2 All model families can provide value
Content Curation을 제외한 나머지 모든 model들은 모두 유의미한 성과를 거두었다.
추가적으로, 어떤 모델은 다른 여러 모델의 개발에 도움이 되어 반복적인 성과를 거두었다.

# 3 MODELING: OFFLINE MODEL PERFORMANCE IS JUST A HEALTH CHECK
Health Check : 서버나 네트워크가 정상인 상태인지 여부를 확인하는 것
Online Model : 지속적인 데이터 추가에 따라, model도 지속적으로 추가 학습을 시켜주는 방법
Offline Model : 한 번 데이터를 학습하고 추가적인 학습없이 사용되는 model, 추가적인 학습을 위해서는 모든 데이터를 다시 학습시켜야한다. 

Pearson Correlation Coefficient(피어슨 상관계수) : 두 변수 사이의 선형 관계가 있는지 나타내는 지표
Spearman Correlation Coefficient(스피어먼 상관계수) : 두 변수 사이의 단조 관계(monotonic relation)가 있는지 나타내는 지표
Pearson과 Spearman 모두 1에 가까우면 양의 관계, -1에 가까우면 음의 관계, 0에 가까우면 상관관계가 없다고 판단한다.

그림 4는 기존의 성공적인 model과 새로운 model을 비교하였고, x축은 성능을, y축은 성과를 나타낸다. 그림 4를 보면 성능과 성과는 상관관계가 없다는 것을 육안으로 확인할 수 있고, 실제로 Pearson Correlation Coefficient는 -0.1, Spearman Correlation Coefficient는 -0.18로 유의미한 상관관계가 없다는 것을 보여주었다. 즉 모델의 성능 향상은 가치 창출과 관계가 없을 수 있다는 것이다.

이러한 원인은 다음과 같은 것으로 추정된다.
1. 모델의 성능이 이미 포화되어 가치 향상의 한계에 마주쳤다.
2. 세그먼트 포화 : 즉 고객의 성향에 따라 그룹을 세그먼트화(분리) 하고, 맞는 모델을 적용하는 것을 끝냈기 때문에 더이상의 성능향상이 이루어지지 않았다.
3. 불쾌한 골짜기 : 모델이 점점 좋아지면서 사용자를 더 예측을 잘하게되며, 일부 사용자는 이에 대해 불안감을 느낄 수 있다.
4. 프록시 과도최적화 : 프록시, 즉 상관관계는 있지만 직접적으로 비즈니스에 영향을 주지 않는 변수에 대해 과도하게 성능을 올려서 문제가 생길 수 있다.(위와 같이 이해했다.) 
예를 들면 클릭은 구매와 상관관계가 있기 때문에 클릭율이 높은 모델을 구축한다. 그러나 성능이 좋아질수록 클릭 유도만 하고 구매를 하지 않을 수 있다, 상세한 예시로는 사용자가 보고있는 호텔과 비슷한 호텔을 보여주어 클릭 유도를 한 뒤, 두 호텔을 비교하느라 구매를 하지 않는 경우가 생길 수 있다.

이렇듯 오프라인 모델은 단순히 헬스체크에 그치지 않는다. 그러므로 최소한의 모델을 통해 빠르게 반복적인 테스트를 하는 것으로 방향을 바꾸었다.

# 4 MODELING: BEFORE SOLVING A PROBLEM, DESIGN IT
모델을 학습할 때, 구체적인 목표를 설정하는 것이 좋다. 예를 들면, 날짜 유연성에 대해 학습하려고 할 때, 날짜 유연성에 대한 정의에 따라 다양한 모델이 있을 수 있다. 머신러닝 문제들을 다음의 조건으로 나눌 수 있다.
1. 학습 난이도
2. 데이터와 개념 일치 : 예를 들면 사용자에게 질문을 하고 답을 예측하는 모델을 구성한다. 이렇게 하면 훨씬 더 개념에 가까운 모델을 구성할 수 있지만, 응답자의 데이터만 학습하므로 선택 편향이 발생하기 쉽다.
3. 선택 편향 : 관측 공간에서, 타겟 변수를 계산할 수 있는 관측과 그렇지 않은 관측으로 분류하면 선택 편향을 쉽게 판단할 수 있다. 이것은 보정이 필요하다.
- 이해가 조금 더 필요한 부분
모델을 향상시킬 수도 있지만, 문제 자체를 다르게 해석할 수도 있다. 예를 들면, 숙박 기간을 회귀가 아닌 다중 분류 문제로 바꿀 수 있고, 클릭 데이터 기반의 선호도 평가 모델을 리뷰 데이터 자연어 처리 문제로 생각할 수 있다. 이렇게 다양하게 문제를 변화시키는 것은 비즈니스적으로 매우 효과적인 방법이다.

# 5 DEPLOYMENT: TIME IS MONEY
