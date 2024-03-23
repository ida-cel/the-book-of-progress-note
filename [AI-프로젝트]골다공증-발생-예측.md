# [AI 프로젝트] 골다공증 발생 예측


## 주제 : 골다공증 위험 예측 모델 성능 비교 

## 요약
골다공증은 '40대부터 ~ 90대' 노년층에서 많이 발생한다는 것을 알 수 있었습니다.
다양한 머신러닝 모델 중  Gradient Boosting Classifier, K-Nearest Neighbors,  Support Vector Classifier, Logistic Regression, MLP Classifier, RandomForestClassifier 를 이용하여 성능을 비교한 결과, 5가지 모델 중 Gradient Boosting Classifier 모델이 91%의 정확도로 가장 높은 예측 성능을 보였습니다.


## 개요
골다공증 발생 요인이 어떤 특성과 상대적으로 높은 상관관계를 가지는지를 알아보고
다양한 머신러닝 모델 Gradient Boosting Classifier, K-Nearest Neighbors,  Support Vector Classifier, Logistic Regression, MLP Classifier,  Decision Tree  별 성능을 비교해보고 가장 적합한 모델이 무엇인지 알아보고자 합니다.


## 예상 진행 순서

### 데이터 분석
1. 데이터 정보 확인

### 데이터 전처리
1. 데이터 정제(Data Cleaning)
    - 누락값(Missing Values) 수정 : 데이터 완전성을 유지 
    - 이상치(Outliers) 수정 : 분석의 정확성 향상
1. Feature Engineering
    - 레이블 인코딩(Encoding) : 범주형 변수를 숫자 형태로 맵핑
    - '나이' 구간화(Binning) 
1. 특성 변형(Data Transformation)
    - 스케일링(Scaling) :  정규화(Normalization)

### 상관관계 시각화
- 특성별 분포 비교 : 히스토그램
- 특성별 골다공증 발생 빈도를 중심으로 상관관계 비교 : 히트맵
- 나이를 구간값에 따라 분류하여 골다공증 발생 분포 비교 : 히트맵

### 모델링
1. 모델별 성능 비교 
- Gradient Boosting Classifier
- K-Nearest Neighbors
- Support Vector Classifier
- Logistic Regression
- MLP Classifier
- Decision Tree 
1. GridSearchCV 최적의 하이퍼파라미터 검색
1. 모델 선택
1. 모델 학습
1. 예측 및 평가
  
## 참고

https://www.kaggle.com/code/theoneandonlyp/90-82-osteoporosis-risk-prediction

https://www.kaggle.com/code/docxian/osteoporosis-risk-prediction


