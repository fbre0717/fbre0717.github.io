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
published: false
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
그림 6을 보면, 지연 시간이 증가할수록 전환율은 감소하는 것을 볼 수 있다. 그렇기 때문에 지연 시간을 감소시키는 다음과 같은 방법을 사용하였다.
1. Model Redundancy : 대규모 트래픽을 처리할 수 있는 모델이 많이 있다.(수량)
2. In-house developed Linear prediction engine : 예측 시간을 짧게 하기 위한 Naive Bayes, Generalized Linear Model, k-NN 등의 모델을 자체적으로 개발했다.
3. Sparse models : 모델의 파라미터가 적을수록 계산이 빨라진다.
4. Precomputation and caching: feature space가 적다면, 모든 예측 값들을 key-value로 저장한다. feature space가 크다면 자주 사용되는 요청을 메모리에 캐시한다.
5. Bulking : 네트워크 부하를 최소화하기 위해 대량의 일을 한 번에 처리한다.
6. Minimum Feature Transformations : 알고리즘을 개선해 소요 시간을 줄일 수 있다.

이러한 기술의 대부분은 다양한 형식의 모델을 배포하고 사용할 수 있는 간단한 인터페이스를 제공하는 머신 러닝 프로덕션 서비스에 의해 구현됩니다. 이 서비스는 예측 지연 시간뿐만 아니라 고가용성, 내결함성, 모니터링 등 모델 배포의 여러 가지 까다로운 측면을 추상화합니다. 이러한 기술은 일반적으로 개별 모델 수준에서 낮은 지연 시간을 달성하는 데 매우 성공적이지만, 빠른 모델을 추가하는 것이 시스템을 망가뜨리는 '마지막 지푸라기'가 되는 경우가 항상 있을 수 있습니다. 이러한 상황을 감지하기 위해 섹션 7.3에 자세히 설명된 방법을 사용합니다. 이 방법은 지연 시간과 모델 자체가 비즈니스 지표에 미치는 영향을 분리하여 하나의 RCT에서 지연 시간을 개선할 필요가 있는지 또는 모델 자체를 개선할 필요가 있는지 결정할 수 있도록 하는 것입니다.

# 6 MONITORING: UNSUPERVISED RED FLAGS
피드백에 대해 다음의 2가지 문제가 있다.
1. Incomplete feedback : 완전한 label을 얻을 수 없다. 예를 들면, '특별요청'을 요청할지를 예측하는 모델을 생각해보자. 이 것은 예약을 할 때만 '특별요청'을 신청할수 있고, label을 받을 수 있기 때문에 예악하지 않은 사람들에 대해서는 label을 할당할 수 없다.
2. Delayed feedback : label을 얻기까지 지연될 수 있다. 리뷰 작성 같은 경우, 몇 주나 몇 달 후에 label을 얻을 수 있다.

?????

결론 : Response Distribution Analysis 는 초기에 결함을 찾을 수 있는 효과적인 방법이다.

# 7 EVALUATION: EXPERIMENT DESIGN SOPHISTICATION PAYS OFF
유의미를 실험 결과를 추출해내는 방법에 대해 소개한다.
트리거 분석과 처리 설계를 결합하여 특정 모델링 및 구현 선택이 비즈니스 지표에 미치는 영향을 분리하는 방법의 예시를 보여준다.

## 7.1 Selective triggering
피험자를 대조군과 치료군으로 나누는데, 모든 치료군이 치료를 받을 수 있는 상황인 것은 아니다. 그렇기 때문에 치료군에 배정되었지만 치료를 받지 않은 피험자는 표본에 노이즈를 추가하여 실험 결과의 정확도를 떨어뜨린다. 그러므로 치료가능한 피험자만 분석하는 트리거 분석을 적용한다.

## 7.2 Model-output dependent triggering
모든 모델 요건이 충족되더라도 처리 기준은 모델 출력에 따라 달라질 수 있습니다. 예를 들어 모델에서 목적지 유연성이 있는 것으로 식별된 사용자에게만 대체 목적지가 있는 블록을 표시할 때 이런 일이 발생합니다. 또한 사용할 수 없는 관련 항목을 가져오는 등 모델 출력에 따라 후속 단계가 실패하거나 성공할 수도 있습니다. 이러한 경우 일부 사용자는 어떤 처리에도 노출되지 않아 관찰된 효과가 다시 한 번 희석될 수 있습니다. 그럼에도 불구하고 대조군에서는 모델 출력을 알 수 없으므로 트리거링 조건을 설정할 수 없으므로 그림 8의 설정을 사용할 수 없습니다.
대조군을 수정하여 모델을 호출하는 것은 권장되지 않습니다. 이 그룹은 실험 설정의 문제를 감지하기 위한 안전망으로도 사용되며, 이러한 경우 문제를 연구하는 동안 모든 트래픽이 대조군으로 전달될 수 있기 때문입니다. 모델 출력에 따른 트리거링을 설정하려면 그림 9와 같이 세 그룹으로 실험을 진행해야 합니다. 대조군 C는 변경 사항에 전혀 노출되지 않고, 두 처리 그룹 T 1과 T 2는 모델을 호출하고 트리거링 기준(예: 출력 > 0)을 확인하지만, T 1에서만 트리거된 사용자가 변경 사항에 노출됩니다. T 2에서는 모델 출력에 관계없이 사용자가 변경 사항에 노출되지 않습니다. 통계 분석은 T 1과 T 2 모두에서 트리거된 피험자만을 사용하여 수행됩니다.

## 7.3 Controlling performance impact
이전 섹션에서 설명한 설정은 사용자 경험에 대한 기능의 인과적 영향(예: 새로운 추천)과 모델 계산으로 인한 속도 저하를 분리하는 방법이기도 합니다. C와 T 1 사이의 메트릭 비교는 성능 저하를 포함하여 새 기능의 전반적인 효과를 측정합니다. 결과가 긍정적이면 현재 구현을 지지하는 것입니다. 그렇지 않더라도 두 가지 비교를 통해 더 많은 것을 배울 수 있습니다. C와 T 2를 사용하면 이러한 변형 간에 기능에 변화가 없기 때문에 속도 저하와 관심 지표에 미치는 영향을 모두 분리하여 측정할 수 있습니다. 반대로 T 1과 T 2는 모델 호출로 인한 동일한 계산 부하를 공유하며 새로운 기능에 대한 노출만 다르기 때문에 모델과 관련된 계산 비용과 관계없이 그 효과를 측정할 수 있습니다. 이 마지막 비교에서 긍정적인 결과는 모델이 지연 시간에 미치는 영향과 무관하게 새로운 기능을 지원합니다. 이 주제에 대한 자세한 내용은 [7]에서 확인할 수 있습니다.

## 7.4 Comparing Models
서로 개선된 모델을 기반으로 치료법을 비교할 때 높은 상관관계가 있는 경우가 많습니다. 간단한 예로, 이진 분류 문제를 고려하고 80%의 정확도를 가진 성공적인 솔루션인 모델 x를 생각해 보겠습니다. 모델 y는 모델 x의 실수 중 절반을 수정하면서 5%의 새로운 실수만 도입하여 이 결과를 개선합니다. 이 두 모델은 최대 15%의 경우에만 일치하지 않습니다. 나머지 (최소) 85%의 사례에서는 제어 또는 치료 중이라고 해서 다른 경험이 발생하지 않으며, 지표의 차이는 모델 출력의 차이로 인해 발생할 수 없으므로 이러한 트래픽은 노이즈만 추가할 뿐입니다. 그림 10은 이전 상황과 매우 유사한 이 상황에 대한 설정을 보여줍니다. 이 경우 트리거 조건은 모델 불일치이며, 이는 두 모델의 출력이 모두 T 1과 T 2에 필요하다는 것을 의미합니다. 대조군은 현재 기준선인 모델 1의 출력을 호출하여 사용하며 안전망으로도 작동합니다. 추가 이득으로, T 1과 T 2 모두 동일한 모델 관련 계산을 수행하여 모델 간의 성능으로 인한 차이를 제거하여 모델 출력 간의 차이가 목표 지표에 미치는 인과적 영향을 분리합니다.

# 8 CONCLUSION
이 글에서는 150개의 성공적인 머신러닝 애플리케이션을 개발하면서 얻은 6가지 교훈을 공유했습니다. 상업적 영향 전달이라는 관점에서 머신러닝 프로젝트의 모든 단계를 다뤘습니다. 모든 교훈은 가설-모델-실험 주기를 개선하는 것에 관한 것입니다:

시맨틱 레이어와 모델 제품군은 가능한 한 많은 주기를 시작하는 데 도움이 되었고, 
오프라인 지표가 비즈니스 이득과 상관관계가 낮다는 사실을 발견한 후 매우 풍부한 반복 차원을 추가하는 문제 구성과 같은 다른 측면에 집중하게 되었으며, 
지연 시간이 상업적 가치가 있다는 사실을 발견한 후 각 모델이 영향력을 발휘할 수 있는 최상의 기회를 제공하기 위해 지연 시간을 낮추는 방법을 구현하고 비즈니스 지표에 미치는 영향을 분리하는 실험 설계 기법을 개발하게 되었죠; 
응답 분포 분석은 배포 직후 모델 문제를 감지하는 능력을 향상시켰으며, 
마지막으로 실험 정교화는 선택의 효과와 가설의 타당성을 빠르고 신뢰할 수 있으며 세밀하게 추정하여 반복 주기를 개선했습니다.

이러한 교훈을 행동으로 옮기기 위해 제품 개발, 사용자 경험, 컴퓨터 과학, 소프트웨어 공학, 인과 추론 등 다양한 분야의 아이디어를 통합했습니다. 가설 중심의 반복과 학제 간 통합은 머신러닝으로 가치를 제공하기 위한 접근 방식의 핵심이며, 이 작업이 다른 머신러닝 실무자에게 지침이 되고 이 주제에 대한 추가 연구를 촉발할 수 있기를 바랍니다.


<!-- 
# ACKNOWLEDGMENTS
저자들은 이 작업에 참조된 모델을 구축한 동료들과 이를 유용한 제품으로 전환한 UX 디자이너, 소프트웨어 개발자, 카피라이터 및 프로젝트 관리자에게 감사의 뜻을 전합니다. -->