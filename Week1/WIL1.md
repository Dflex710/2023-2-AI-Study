# Week1

# WIL1
DL Basic

AI, ML, DL

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled.png)

DL: Neural network를 기반으로 한 ML의 하위분야
<Deep Learning Component>

1) Data
다루는 Task에 의존한다.
{Classification, Semantic Segmentation, Object Detection, Pose Estimation}

2) Model
학습하는 Model에 따라 결과값은 상당히 달라진다.
{AlexNet, GoogleLeNet, ResNet, DenseNet, LSTM, AutoEncoder, GAN}

3) Loss function
학습중 알고리즘이 얼마나 잘못되었는지 알려주는 지표
알고리즘이 예측한 값과 실제 정답의 차이를 비교해 학습

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled%201.png)

4) Optimization and Regularization

- Optimization
Gradient Descent Method(경사하강법)
loss function을 빠르고 정확하게 줄이기위한 최적화기법
- Regularization
학습을 방해하여 일반화 성능 up

### <Nonlinear Function>
활성함수로 비선형함수를 사용하는 이유

- 활성함수가 선형함수라면 여러 겹을 쌓아도 하나의 활성함수로 대체 가능
- 신경망의 표현성을 높이기 위해 비선형 연산 사용

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled%202.png)

## <Neural Network>

Function Approzimators that stack affine transformations followed by nonlinear transformations.

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled%203.png)

## <Multi-Layer Perception>

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled%204.png)

# <Generalization>

- 일반화성능
- Generalization Gap = | Test error - Training error |
- Under-fitting vs Over-fitting

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled%205.png)

- CrossValidation (교차검증)
Test data를 학습시 사용하는 것은 cheating
그렇지만 학습이 잘 되고 있는지 확인할 수 있는 지표가 필요 >> valid data

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled%206.png)

- Ensemble

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled%207.png)

- Regularization (학습을 방해)
Early stopping
Parameter norm penalty
Data augmentation
- Noise robustmess
ML에서 robustness? 이상치나 노이즈가 들어와도 크게 흔들리지 않음

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled%208.png)

- Dropout
Train에서만 적용되는 방법
Test에서는 드랍되는 노드 없이 모든 노드가 항상 추론에 참여
- Label smoothing
모델이 너무 확신을 가지지 않도록 도와주는 방법

일반적으로 모델은 예측을 할 때 하나의 클래스에 대해 확률을 1로 예측하고 나머지 클래스에는 0으로 예측 >> 과적합 초래

[0,1,0,0] >> [0.025,0.925,0.025,0.025] (a를 0.1로 설정)

## <Convolutional Neural Networks(CNN)>
합성곱 신경망

- 이미지의 공간정보를 유지하며 학습

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled%209.png)

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled%2010.png)

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled%2011.png)

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled%2012.png)

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled%2013.png)

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled%2014.png)

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled%2015.png)

## <1*1 Convolution>

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled%2016.png)

## <Modern CNN>

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled%2017.png)

1) AlexNet (2012 winner)

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled%2018.png)

2) VGGNet (2014 준 winner)

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled%2019.png)

3) GoogleNet (2014 winner)

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled%2020.png)

4) ResNet (2015 winner)

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled%2021.png)

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled%2022.png)

![Untitled](Week1%20bd5ff5baa37f468ba911fd1e82711d1f/Untitled%2023.png)

5) Summary

- VGG는 3*3 conv 사용
- GoogleNet은 1*1 conv를 사용
- Resnet은 Skip connection을 사용