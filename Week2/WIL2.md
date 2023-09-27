# 인공지능 Week2

## 목차

1. Computer Vision Applications
2. Semantic Segmentation
3. Object Detection
4. Introduction to Pytorch
5. Pytorch Basics
6. PyTorch 프로젝트 구조 이해하기
7. AutoGrad & Optimizer
8. Pytorch Dataset
9. Model Save
10. Transfer Learning

Semantic Segmentation (의미 분할)은 컴퓨터 비전 분야에서 사용되는 이미지 처리 기술 중 하나로, 이미지를 픽셀 단위로 분류하는 작업입니다. 이 작업에서 각 픽셀은 해당하는 객체 또는 클래스로 분류됩니다. 다시 말해, 이미지의 각 픽셀은 어떤 객체나 물체의 일부인지, 어떤 클래스에 속하는지를 결정하는 것이 Semantic Segmentation의 목적입니다.

Semantic Segmentation의 주요 특징은 다음과 같습니다:

1. **픽셀 수준의 분류**: 이미지를 픽셀 단위로 분류하기 때문에 객체나 물체의 경계나 모양을 정확하게 인식할 수 있습니다.
2. **객체 인식**: 이미지 내의 다양한 객체나 클래스를 식별하여 각 픽셀에 해당 객체 또는 클래스 레이블을 할당합니다. 예를 들어, 도로, 차량, 보행자 등의 클래스를 식별할 수 있습니다.
3. **비지도 학습 대신 지도 학습**: Semantic Segmentation은 주로 지도 학습(Supervised Learning) 방식으로 수행됩니다. 학습 데이터에는 입력 이미지와 해당 이미지의 정확한 픽셀별 레이블이 포함되어 있어야 합니다.
4. **응용 분야**: Semantic Segmentation은 자율 주행 자동차, 의료 영상 분석, 자연 언어 처리, 로봇 비전 등 다양한 응용 분야에서 사용됩니다. 예를 들어, 자율 주행 자동차는 도로 상의 객체를 정확하게 식별하고 분할하여 안전 운전을 위한 정보를 추출합니다.

이 Semantic Segmentation 기술은 고급 비전 기술의 핵심 요소 중 하나이며, 이미지와 비디오 데이터에서 의미 있는 정보를 추출하는 데 중요한 역할을 합니다.

FCN(Fully Convolutional Network)은 CNN(Convolutional Neural Network)의 한 변형 형태로, 주로 Semantic Segmentation과 같은 픽셀 수준의 작업을 수행하기 위해 설계되었습니다. FCN과 기본 CNN의 주요 차이점과 FCN의 특징은 다음과 같습니다:

**1. 구조 차이:**

- **CNN**: CNN은 주로 분류(Classification)나 객체 검출(Object Detection)과 같은 고정된 크기의 입력 이미지에 대한 작업을 수행하는 데 사용됩니다. 일반적으로 완전 연결 레이어(Fully Connected Layer)로 마무리되어 클래스 점수를 출력합니다.
- **FCN**: FCN은 CNN 아키텍처를 확장하여 고정된 크기가 아닌 임의 크기의 입력 이미지에 대한 픽셀 수준의 분할 작업을 수행할 수 있도록 설계되었습니다. FCN은 합성곱 연산과 업샘플링(Deconvolution 또는 Transposed Convolution)을 사용하여 입력 이미지와 동일한 크기의 분할 맵을 생성합니다.

**2. 출력 형식:**

- **CNN**: CNN은 주로 분류 작업에서 클래스 점수를 출력하며, 이를 사용하여 입력 이미지에 대한 하나의 레이블 또는 객체 검출 결과를 얻습니다.
- **FCN**: FCN은 입력 이미지와 동일한 크기의 분할 맵(Segmentation Map)을 출력합니다. 각 픽셀에는 해당 픽셀이 어떤 클래스에 속하는지를 나타내는 클래스 점수가 포함되어 있습니다.

**3. 활용 분야:**

- **CNN**: CNN은 주로 이미지 분류, 객체 검출 등과 같이 입력 이미지에 대한 전체적인 정보를 제공하는 작업에 사용됩니다.
- **FCN**: FCN은 주로 Semantic Segmentation과 같이 입력 이미지를 픽셀 수준에서 세분화하고 객체 레이블을 할당하는 작업에 사용됩니다.

**FCN의 특징:**

1. **End-to-End Segmentation**: FCN은 입력 이미지로부터 출력 분할 맵까지 모든 과정을 엔드 투 엔드로 처리합니다. 이는 이미지 분할 작업을 간단하게 구현할 수 있도록 도와줍니다.
2. **업샘플링**: FCN은 업샘플링 레이어를 사용하여 분할 맵의 크기를 입력 이미지와 동일한 크기로 확장합니다. 이를 통해 픽셀 수준의 정확한 분할을 수행할 수 있습니다.
3. **Skip Connections**: FCN은 다양한 스케일의 정보를 통합하기 위해 스킵 연결을 사용합니다. 이러한 스킵 연결은 작은 객체나 객체의 경계를 잘 분할하는 데 도움을 줍니다.
4. **전이 학습**: 미리 학습된 CNN 모델을 기반으로 FCN 모델을 초기화하고 전이 학습을 수행하여 작은 데이터셋에서도 강력한 성능을 달성할 수 있습니다.

FCN은 Semantic Segmentation과 같이 객체의 경계를 정확하게 분할하고 객체의 위치 및 형태를 보다 정확하게 파악하는 데 사용되며, 컴퓨터 비전 분야에서 중요한 응용 분야 중 하나입니다.

Pytorch를 통해 딥러닝의 기초를 배워보고 프로젝트의 구조 및 연결관계에 대해 입문하는 계기가 됨.