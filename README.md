# `머신러닝 & 딥러닝 프로젝트`
- 개요: 머신러닝과 딥러닝으로 예측하는 프로젝트입니다.
- 기간: 2023-03-29 ~ 2023-04-05

## `주제: 당뇨병 예측`

## `팀 소개`

팀장
신주용 : 팀장, 전처리, 모델링코드구현, 발표자료준비

팀원
김주환 : 모델링코드도움, 발표자료준비
이도원 : EDA, 모델링, 발표
박은영 : EDA, 데이터시각화, 발표자료준비
허우영 : EDA, 데이터시각화, 발표
진광환 : EDA, 데이터시각화, 모델링코드구현

## `프로젝트 단계`

1. Column 값 확인
2. 시각화 및 EDA
3. 머신러닝 예측
4. 딥러닝 예측
5. 후기

## `1. Column 값 확인`

| 칼럼명 | 요소1 | 요소2 |  |  |  | 의미 |
| --- | --- | --- | --- | --- | --- | --- |
| Age |  |  |  |  |  | 나이 |
| Sex | 0 = 여성 | 1 = 남성 |  |  |  | 성별 |
| HighChol | 0 = no | 1 = yes |  |  |  | 콜레스테롤 수치가 높은지? |
| CholCheck | 0 = no | 1 = yes |  |  |  | 5년동안 콜레스테롤 수치를 체크 했는지 |
| BMI |  |  |  |  |  | 저체중 18.5미만 <br> 정상 18.5 ~ 24.9 <br> 과체중 25 ~ 29.9 <br> 비만 30~ |
| Smoker | 0 = no | 1 = yes |  |  |  | 평생 핀 담배 수가 100개비 이상 |
| PhysActivity | 0 = no | 1 = yes |  |  |  | physical activity in past 30 days - not including job <br> 30일 내에 운동을 했는지 여부 |
| Fruits | 0 = no | 1 = yes |  |  |  | 하루에 과일을 한번이상 먹는지 |
| Veggies | 0 = no | 1 = yes |  |  |  | 하루에 채소를 한번이상 먹는지 |
| HvyAlcoholConsump | 0 = no | 1 = yes |  |  |  | 한 주에 일정 횟수 이상 음주여부 <br> 남자: 14번이상 <br> 여자:7번 이상 |
| GenHlth | 1 = excellent | 2 = very good | 3 = good | 4 = fair  | 5 = poor | Would you say that in general your health is:평소 자신의 건강상태에 대한 답변 |
| MentHlth | scale = 1~30 |  |  |  |  | days of poor mental health scale 1-30 days : 정신건강이 안좋은 날 수 |
| PhysHlth | scale 1-30 |  |  |  |  | physical illness or injury days in past 30 days scale 1-30 : 지난 30일 내 물리적 질환/부상일수 |
| DiffWalk | 0 = no | 1 = yes |  |  |  | Do you have serious difficulty walking or climbing stairs? : 걷기나 계단오르기에 어려움이 있는지 |
| Stroke | 0 = no | 1 = yes |  |  |  | you ever had a stroke. : 뇌졸증 걸린적이 있는지 |
| HighBP | 0 = no  | 1 = yes |  |  |  | 혈압이 높은지 |
| Diabetes | 0 = no | 1 = yes |  |  |  | 당뇨병인지 |
| HeartDiseaseorAttack | 0 = no | 1 = yes |  |  |  | coronary heart disease (CHD) or myocardial infarction (MI) : 코로나 심장질환 유무 or 심근경색 유뮤 |

## `2. 시각화 및 EDA`

- 각 건강 관련 지표들과 당뇨병의 상관관계를 시각화 하고 분석
- 시각화는 matplotlib, seaborn 사용

## `3. 머신러닝 예측`

### 전처리

1. Age 열 삭제(이유는 삭제 했을때 성능이 약간 더 좋게 나왔다.)
2. train test 8:2
3. numerical => standardscaler 적용
4. PCA 적용(모든 열에 적용해서 새로운 값을 생성해봄 - 실험적)

### 모델 학습 및 평가

- GBM
- AdaBoost
- Bagging
- RandomForest
- SupportVectorMachine
- LogisticRegression
- XGBoost
- LightGBM
- 모든 모델에 Kfold n_split=5 적용
- 결과는 모든 모델이 약 70% 확률을 넘겼고 가장 높은 모델은 LogisticRegression 약 73%

## `4. 딥러닝 예측`

- 사용한 인공신경망 모델은 Dense
- Pipeline사용 (StandardScaler, One-Hot Encoding 사용)
- Kernel Initializer 는 He Normal 사용
- Batch Normalization 적용
- Activation 는 ELU 사용
- Output_layer 직전 Hidden_layer 에 Drop Out 0.5 적용
- 결과는 정확도 약 75%

## `5. 후기`

- 많은 머신러닝과 딥러닝 모델을 사용해 봤지만, 어떤 특정모델의 성능이 특별히 크게 나오거나 하지 않았다. 데이터에 따라서 성능 차이가 크게 난다고 추론할 수 있었다.
- 사용된 데이터는 Kaggle 데이터인데 너무 과하게 정제되어있는 데이터였다(거의 모든 Column이 정확한 수치로 표시되지 않고, 0과 1 값으로 분류되어있었다.). 그래서 오히려 성능이 떨어졌다고 판단되었다.
