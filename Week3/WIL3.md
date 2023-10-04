# 인공지능 Week3

image classification
classifier를 정의해보자
부서지기 쉬움
확장성이 뛰어나지 않음

KNN(K-Nearest Neighbor)
simple image classifier
훈련 단계에서는 아무것도 하지 않고 모든 훈련 데이터를 기억
예측 단계에서는 새로운 이미지를 가져와 앞서 훈련단계에서 보았던 데이터중 가장 유사한 이미지를 찾아 그 이미지의 라벨로 예측

다수결로 수렴?
k=1, 3, 5로 이웃을 봄으로써 더 일반화된 성능을 얻는다.

Why K ?
• 색칠된 부분은 test data가 해당된 영역에 놓이게되면 가지게 될 group 의 색깔

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%20Week3%20d75d3ca22c1246d69aa1c9b8e5b1799c/Untitled.png)

- 우리는 이미지를 보지만 컴퓨터는 거대한 픽셀 숫자 그리드를 본다 : semantic gap
• semantic gap 때문에 사진의 각도나 물체의 조명, 포즈, 위치가 달라질때마다 어려움 O
• 디테일한 규칙들을 작성하여 분류 실패
• 대규모 데이터 셋을 기반으로 요약된 context를 학습하는 모델
• KNN알고리즘
• 모든 훈련 데이터 셋을 기억하고 가장 가까운 거리의 이웃을 찾아 라벨링
• 시간 이슈, 이미지의 지각적 유사성 != 픽셀간의 거리 , 차원의 저주

Linear Classification
Summary
• 신경망의 가장 기본적인 구성요소
• 훈련 데이터에 대한 지식을 요약하고 모든 지식을 이러한 가중치에 집어넣었음.
• 가중치 행렬과 이미지 행렬의 계산으로 템플릿과 이미지 픽셀 사이의 유사성에 대한 score를 매기는 방식
• 선형분류기를 하나만 이용하면 템플릿이 하나로만 요약된다는 단점이 있음. => 다양한 블록들을 쌓을 필요

A Loss Function tells how good our current classifier is
• Low Loss = good classifier
• High Loss = bad classifier
• Loss Function = objective Function = Cost Function

L2 Regularization
• 매끄러운 그래프를 원할때 쓰는 정규화
• 특정 요소만의 의존보다는 모든 요소의 전체적인 영향을 원하는 정규화
• L1 Regularization
• 분류기가 복잡하다고 느껴질때 쓰는 정규화
• 가중치값에 0이 많도록 하여 보다 더 단순한 식을 만들어준다.

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%20Week3%20d75d3ca22c1246d69aa1c9b8e5b1799c/Untitled%201.png)

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%20Week3%20d75d3ca22c1246d69aa1c9b8e5b1799c/Untitled%202.png)