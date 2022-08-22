- 8_3 코드 두 개는 안보셔도 됩니다(nn basemodel)

- 8_2 : X feature 시각화,cor,vif

- XY_cor : x feature 개별과 y label 개별 cor 시각화

- automl_passnonpass : automl로 학습한 pass nonpass 분류 모델(top 성능 model 선정 + 튜닝 + feature_importance + 오차 행렬)

- pass_nonpass_eda : new feature 60, 61 추가 + x feature 개별과 y label 개별 cor 시각화 + vif 

- 14y_automl : y 개별 14개 회귀 모델

- pass_nonpass_model: y 기준으로 양품/불량품 그루핑 + 각자에 맞춘 모델 학습(양품은 양품에 대해서만 학습, 불량은 전체에 대해 학습,due to too high score(3.0)) + feature importance, without tuning

- vis_y08: y08번 변수 기준으로 Pass/Fail 나눈 뒤, 각 그룹별 x feature boxplot 시각화

- 참조용01, 참고용 with pca, stacking 예시코드, feature selection 파일 참조해서
1.y 타겟 skewness 있으면 로그변환...을 해서
우리가 쓸거는 다 트리계열이니깐
전처리는 저 변환 말고는 딱히 필요는 없었을거구요(이것도 해야하나 싶긴하지만) + 클리핑(일단은 하지 않고 놔두기)
그 분류기를 만드시는 분들(옵티머스)도 있는데 사실 그건 너무 리스크가 크기도 하고 시간도 없구요
2. 러프하게 넣고 하이퍼파라미터 튜닝 후 (모델 세개, xgboost, randomforest, lightgbm --> 얘네 셋이 예전에 서연님이랑 automl 돌렸을떄 가장 비교적 좋게 나오더라구요 )
3.타겟별 최적 feature selection 진행 후 전체데이터로 모델 3개 학습 + 스태킹 모델 학습
4. 스태킹 모델이랑 다른 모델 3개 블렌딩(이거 가중치는 어떻게 주어야할지 잘 모르겠네요 좀 찾아봐야할거같아요) --> 아래 참고
5. 타겟별로 prediction 진행, prediction 결과 합치기
+autosklearn 돌려서 최적의 모델 앙상블 조합 찾기!!
참조: https://medium.com/dlift/%EC%A0%81%EB%8B%B9%ED%95%9C-%EC%A0%95%ED%99%95%EB%8F%84-%EA%B0%80-%EB%B3%B4%EC%9E%A5%EB%90%98%EB%8A%94-%EB%AA%A8%EB%8D%B8%EC%9D%84-%EC%9E%90%EB%8F%99%EC%9C%BC%EB%A1%9C-%EB%A7%8C%EB%93%A4-%EC%88%98%EB%8A%94-%EC%97%86%EC%9D%84%EA%B9%8C-f0da4a6a9607

진행해주시면 될 것 같습니다.

홍인희: 1,2,3,4 타켓별 예측모델
김서연: 5,6,7
이동우 8,9,10,11
김태국 12,13,14
이렇게 해주시고

이후에 합쳐서 내보고
그 상황에서 더 성능 끌어올리려면 인희님 하시던 feature 만들기... 등을 시도해보면 좋을 것 같습니당
