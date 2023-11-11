# 인공지능 Week7

RNN

각 step에 따라 input이 모델 안으로 들어가게 되고, 앞 step에서 나온 hidden state vector가 이후 모델로 다음 input과 함께 들어간다.

RNN은 시퀀스를 앞에서부터 뒤로 가는 한 방향으로만 처리하기때문에 어떤 시점에서의 hidden state는 그 지점 이전의 입력들에 대해서만 정보를 가지고 있다.

Bi-directional (양방향) RNN

한 방향으로만 정보를 처리하는 것이 아니라, 두 개의 RNN을 사용하여 하나는 앞에서부터
뒤로, 다른 하나는 뒤에서부터 앞으로 시퀀스를 처리

Transformer는 자연어 처리 작업에서 기존의 순환 신경망(RNN)이나 장단기 메모리(LSTM) 등의 아키텍처에 비해 효과적인 모델 구조를 제공하는 딥 러닝 아키텍처 중 하나이다. 

Transformer의 주요 특징

1. **Self-Attention Mechanism:**
    - Transformer의 핵심은 self-attention 메커니즘. 각 입력 토큰은 다른 모든 토큰에 대해 얼마나 중요한지를 결정하는 attention 가중치를 가지고 있다. 이를 통해 모델은 문장 내의 임의의 위치 간에 상관 관계를 파악할 수 있다.
2. **Multi-Head Attention:**
    - Self-attention을 여러 개의 헤드로 나눠 각각 계산하고 이를 다시 합치는 Multi-Head Attention이 적용된다. 이를 통해 모델은 여러 다양한 관점에서 정보를 수집할 수 있다.
3. **Positional Encoding:**
    - Transformer는 문장의 단어 순서 정보를 처리하기 위해 positional encoding을 도입했다. 이는 각 입력 토큰에 위치 정보를 주입하여 모델이 단어의 순서를 이해할 수 있도록 한다.
4. **Feedforward Neural Network:**
    - 각 self-attention 레이어 이후에는 피드포워드 신경망이 적용된다. 이를 통해 모델은 각 토큰의 특징을 높은 수준으로 추출할 수 있다.
5. **Layer Normalization and Residual Connections:**
    - 각 서브레이어에서는 레이어 정규화와 잔차 연결이 적용되어 학습을 안정화하고 그래디언트 흐름을 강화한다.
6. **Encoder-Decoder Architecture:**
    - Transformer는 번역과 같은 시퀀스 투 시퀀스 작업을 위해 인코더-디코더 아키텍처를 사용한다. 인코더는 입력 문장을 처리하고, 디코더는 출력 문장을 생성한다.

Transformer는 번역, 요약, 질문 응답 등 다양한 자연어 처리 작업에서 높은 성능을 보이며, 뛰어난 병렬화와 확장성을 제공하는 특징을 가지고 있다.