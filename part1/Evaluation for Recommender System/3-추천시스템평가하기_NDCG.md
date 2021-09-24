# 추천시스템 평가하기 - NDCG

## NDCG (Normalized Discounted Cumulative Gain)
- 기존 정보검색에서 많이 사용했던 지표임 (검색엔진, 영상, 음악 등 컨텐츠 랭킹 추천에서의 주요 평가지표)
- Top-N의 랭킹 리스트를 만들고, 더 관심있거나 관련성 높은 아이템의 포함여부를 평가
- 순위에 가중치를 주고, 단순한 랭킹이 아닌 데이터의 성향을 반영하기 위한 평가 지표
- MAP(Mean Average Precision), Top K Precision/Recall 등 평가방법 보완
    - 추천 또는 정보검색에서 특정 아이템에 biased된 경우
        - 이미 유명한 아이템이 포함되는 경우 등
### 정답 랭킹과 현재 알고리즘이 만든 랭킹 사이의 점수를 누적 비교
- 1에 가까울 수록 좋은 랭킹임
- log를 활용하여, 순위가 낮을 수록 가중치가 감소
- 랭킹문제에서 자주 사용됨
### 수식 설명
$CG_p = \displaystyle\sum_{i=1}^{p}{rel_i}$


$DCG_p = rel_1 + \displaystyle\sum_{i=2}^{p}{rel_i\over log_2{i}} $

$NDCG_p = {DCG_p \over IDCG_p}$
- p = 평가하고자 하는 아이템 개수
- CG = 상위 아이템 p개의 관련성을 합한 cumulative gain
    - rel은 relation의 약자로, T/F나 score값으로 표현 가능
    - 상위 아이템 p개에 대해서 동일한 비중으로 합함 (가중치 없는 개념)
- DCG
    - CG에서 상위 아이템에 가중치를 부여하기 위해 만든 개념으로 이해함
    - 개별 아이템의 관련성에 log normailzation 적용
    - 랭킹에 따라 비중을 discount하여 관련성 계산
        - 즉 하위권에 penalty 부여
- IDCG = Ideal DCG. 전체 p개의 결과 중 가질 수 있는 가장 큰 DCG
- 따라서 현재 알고리즘의 DCG와 IDCG를 비교한 NDCG값으로 평가


## 기타 Evalutaion Matrics
1. Precision @K (Top-K)
    - 관련 여부를 T/F로 평가하여 맞춘 비율 평가
2. Mean Average Precision (MAP)
    - 추천 결과에 대해서, k를 변경해가면서 Precision @K를 구하여 평균
3. Precision/Recall, AUC
    - 정밀도, 재현율
    - 분류 문제에서 자주 사용되는 평가 지표
