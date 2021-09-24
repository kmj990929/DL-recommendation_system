# 추천시스템 평가하기 - RMSE

-실제 예측과 결과를 보면서 데이터적으로 분석해보는 과정도 중요함

## RMSE (Root Mean Square Error)
$RMSE = \sqrt {{1\over n} \displaystyle\sum_{i=1}^{n}{(y_i - \hat{y_i})^2}}$
- Scale-dependent
    - 같은 0.01의 에러값도 어떤 y_pred와 y_actual을 사용했느냐에 따라 다른 의미를 갖는다.
- 평점 예측 문제에 많이 사용
- 제곱을 하여 더 큰 오차를 만들고, 제곱근으로 원래 scale의 의미있는 숫자로 돌아감