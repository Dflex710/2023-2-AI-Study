# 인공지능 Week4

개가 두 마리이면 두 개의 값이 나와야 하지만 6마리면 6개의 값이 나와야 한다.
Detecting Multiple Objects
객체 슬라이딩 윈도우 방식 (Sliding Window)
슬라이딩 구역을 설정해 모든 부분에 각각 classification을 진행하는 방식이다.

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%20Week4%20200c90143afd46259c152544b73090f5/Untitled.png)

R-CNN

1. selective search로 ROI(Region of Interest) 뽑기
2.  region size process (224x224로 warping)
3. Compute CNN features
4.  Linear SVM로 classify (Support Vector Machine)

Object Detector를 평가하는 기준
• 각 category별 Average Precision의 평균
• 1) test image를 detector에 넣고 동작시킨다.
• 2) NMS를 가지고 overlapping된 bbox들을 제거한다.
• 3) 각 카테고리별 Average Presion을 계산한다. (Precision vs Recall Curve)

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%20Week4%20200c90143afd46259c152544b73090f5/Untitled%201.png)

2000번의 CNN -> 1번의 CNN
29
• CNN과 Resize의 순서를 바꾸어 속도 개선
• Classification으로 SVM에서 linear classification 사용
• R-CNN
• region 뽑고 warping 하고 ConvNet
• Fast R-CNN
• ConvNet 돌리고 region을 projection하여 해당 feature
map을 뽑아와서 ROI Pooling하여 class와 bbox를 뽑아
냄.
• ConvNet 에서 fc layer 없음 주의

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%20Week4%20200c90143afd46259c152544b73090f5/Untitled%202.png)

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%20Week4%20200c90143afd46259c152544b73090f5/Untitled%203.png)

Region Proposal Network(RPN)의 등장

1. CNN을 통과시켜 feature map 뽑기
2.  Region Proposal Network로 region proposal
3. ROI Pooling을 거쳐 classification와 bbox regression

- 앵커박스 안에 객체를 포함하고 있는지 아닌지를 판단
• Anchor box (앵커박스)
• 다양한 가로세로비율(ex. 1, 0.5, 2), 다양한 크기 조합
• 1x1 binary classification 수행 -> Classification loss (object or not)
• 2(object or not) X 9 (num of anchors) 채널 생성
• 객체를 포함하고 있다면 구체적으로 중심을 찾아 이동하고 resize를 해주는 역할 -> bbox regression loss

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%20Week4%20200c90143afd46259c152544b73090f5/Untitled%204.png)

- 1) CNN을 거치고 나온 feature map을 input으로 받음
• 2) 3x3 conv를 수행하여 intermediate layer 생성
• 3) 1x1 conv를 수행하여 binary classification 수행 ( 2 x 9개의 1x1x512 conv사용)
• 4) 1x1 conv 수행하여 bounding box regression 수행

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%20Week4%20200c90143afd46259c152544b73090f5/Untitled%205.png)

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%20Week4%20200c90143afd46259c152544b73090f5/Untitled%206.png)

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%20Week4%20200c90143afd46259c152544b73090f5/Untitled%207.png)