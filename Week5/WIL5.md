# 인공지능 Week5

1. Semantic Segmentation
Segmentation : 이미지의 픽셀 수준에서 각 픽셀이 어떤 의미를 갖는지 파악하는 task

task introduction
• Instance Segmentation
• 같은 class에 속하더라도 다른 instance면 다르게 분류
• Semantic Segmentation
• 꼭 object가 아니더라도 class가 될 수 있음 (ex. 인도, 차도, 하늘)

FCN의 특징 3가지
• FCN
• 2015년에 CVPR 게재
• 이후 segmentation model들의 baseline
• 1) VGG16을 backbone으로 사용
• 2) VGG 네트워크의 FC Layer인 nn.Linear 부분을
Convolution으로 변경
• 3) Transposed Convolution을 이용해 Pixel Wise
Prediction을 수행

1) VGG16을 backbone으로 사용

- pretrained 된 네트워크를 그대로 사용 가능• AlexNet, VGG, GoogLeNet과 비교 실험중 가장 좋은 성능

2) Fully Connected Layer 대신 Fully Convolution Layer 사용
>>위치 정보를 보존할 수 있다!!

3) Transposed Convolution을 통해서 pixelwise prediction을 진행
Upsampling, Unpooling max pooling

<convolution 연산 복습을 과제를 통해 수행>

FCN 성능 향상 방법
1/32배의 feature map은 너무 coarse 해서 Skip connection을 제안
Pixel Accuacy, Mean IOU, Frequency Weighted IOU

FCN의 한계

1. 객체의 크기가 크거나 작은 경우에 예측을 잘 하지 못하는 문제
2. Object 의 디테일한 모습이 사라지는 문제

DeconvNet
FCN의 한계를 극복
• Encoder와 Decoder 구조 사용
• Unpooling과 Transpose Convolution block을 반복