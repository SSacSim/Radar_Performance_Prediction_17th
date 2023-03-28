## Radar_Performance_Prediction_17th

대회 URL: https://dacon.io/competitions/official/235927/overview/description

주최/주관 : LG AI Research / 데이콘

진행 기간 : 2022.08.06 ~ 2022.08.26

대회설명:
  * 자율주행 차량에 중요한 역할을 하는 Radar의 성능을 미리 예측할 수 있는 AI 모델 개발(Multioutput Regression)

대회 목표:
  * Radar 장비의 상태를 의미하는 56개 feature 이용하여 총 14가지 성능을 예측하는 모델 개발
  * Normalized RMSE(NRMSE) 평가지표를 이용하고, 14개 중 특정 target에 가중치를 두어 모델 성능 평가 및 모델 성능 개선

대회 결과 :
  * 파생변수 생성, 데이터 증량(SMOTE)과 모델 앙상블을 사용하여 예측 모델 개발
  * 대회 최종 17등 달성
 * * *
 ## 대회 진행 환경 & 역할
 프로젝트 진행 환경 : Google Colab
 
 팀구성 : 3명
 
 역할 :
  * 데이터 분석
    * feature별 데이터 분포 파악
    * 파생변수 생성
    * SMOTE를 이용한 데이터 증량
  * 모델 개발
    * AutoML을 사용하여 좋은 성능을 내는 모델 선별
    * optuna를 이용하여 각 모델 하이퍼 파라미터 튜닝
    * 다양한 앙상블 방법 적용 (weighted sum, mean, stacking)
* * *
## 진행 상세 과정
1.데이터 분석
  * IQR기법으로 이상치 제거 시도했으나, 대회 Task가 불량 예측을 하는 것이고 도메인 지식도 전무한 상태기에 수행하지 않음.
  * 유일값 변수 & 특정 변수 삭제
  
2.파생 변수 생성
  * feature명을 기준으로 간단한 사칙연산을 통해 많은 파생변수 생성 
  
  (ex) 스크류 회전수 대 삽입 깊이, 안테나 사이 최소,최대 거리 …
  
3.모델링
  * AutoML을 통해 가장 성능이 높은 모델 3가지 선별(Extra Tree, CatBoost, LGBM)
  * weighted sum 앙상블을 이용하여 최종 결과물 산출
  
4.성능 향상 방법
  * SMOTE를 이용하 전체 데이터 수 25% 증량
    * 매우 큰 값을 가지는 데이터 셋을 기존 데이터 수 * 1.25만큼 생성
    * 기존 데이터는 0, 인위적으로 만든 데이터는 1로 구분하여 SMOTE진행
  * Optuna를 이용하여 각 모델 하이퍼 파라미터 튜닝
