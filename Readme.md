# [머신러닝 스터디 2~4강 정리 9/6]
## 2강_ Image Classification
이미지 -> 3D array(height * width * color channel)
문제점 : 보는 시각에 따라, 조명에 따라, 감춰진 정도에 따라 등등 여러 요인에 따라 다르게 보일 수 있다.

	Nearest Neighbor Classifier (Nonparametric approach)
: 모든 학습용 이미지와 레이블을 메모리상에서 기억, 테스트 이미지를 학습 이미지와 하나하나 비교해보며 가장 비슷한 학습 이미지 label을 test label이라 predict

Test 이미지와 학습 이미지 비교 -> 비교기준 = 거리(hyper parameter), 거리 같으면 같은 이미지
-L1 distance = ∑_p▒〖abs(I_1^p-I_2^p)〗
-L2 distance = ∑_p▒〖sqrt((I_1^p-I_2^p )^2)〗

	K Nearest Neighbor Classifier(kNN) -> test 시간 대비 성능이 안 좋아 안 쓴다.
: k개의 가장 가까운 이미지 찾고 k개의 이미지가 다수결로 vote, 가장 많이 나오는 것으로 해당 test 이미지가 어떤 학습 이미지와 유사한지 판단

Hyper parameter를 계속 바꾸며 Test 데이터 셋에 적용 -> 절대 하면 안된다.
Test data set은 성능 평가용, 학습할 때 절대 사용하면 안됨
hyper parameter 설정을 위해 여러 번의 실험을 해야함 -> Train data의 일부 (20%정도)를 validation set data로 설정하여 해당 hyper parameter에 대해 어느 정도의 성능이 나오는지 판단 후 튜닝
Train data가 적은 경우에는 Cross validation 사용
: Train data set을 n개의 fold로 나누어 n-1개의 fold는 학습 진행, 1개의 fold는 검증. 검증에 사용되지 않은 fold 1개는 검증에 사용 나머지 fold와 그 전 검증에서 사용한 fold는 학습, 이 과정을 반복한다.
