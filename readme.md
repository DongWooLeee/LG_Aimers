- 8_3 코드 두 개는 안보셔도 됩니다(nn basemodel)

- 8_2 : X feature 시각화,cor,vif

- XY_cor : x feature 개별과 y label 개별 cor 시각화

- automl_passnonpass : automl로 학습한 pass nonpass 분류 모델(top 성능 model 선정 + 튜닝 + feature_importance + 오차 행렬)

- pass_nonpass_eda : new feature 60, 61 추가 + x feature 개별과 y label 개별 cor 시각화 + vif 

- 14y_automl : y 개별 14개 회귀 모델

- pass_nonpass_model: y 기준으로 양품/불량품 그루핑 + 각자에 맞춘 모델 학습(양품은 양품에 대해서만 학습, 불량은 전체에 대해 학습,due to too high score(3.0)) + feature importance, without tuning

- vis_y08: y08번 변수 기준으로 Pass/Fail 나눈 뒤, 각 그룹별 x feature boxplot 시각화
