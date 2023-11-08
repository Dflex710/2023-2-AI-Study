# 인공지능 Week6

1. Introduction to NLP Task
사람말을 컴퓨터가 이해하도록 하는 작업
NLP - NLU(Natural Language Understanding)
           : 컴퓨터가 자연어를 이해
          ex) 감정 분석, 명령어 인식

       - NLG(Natural Language Generation)
           : 컴퓨터가 자연어를 생성
          ex) 논문 요약, 날씨 보고서 생성

NLU를 통해 텍스트의 의미를 파악해, NLG를 통해 텍스트를 생성 (함께 작동) ex)ChatGPT

2. Word Representation
text데이터를 수치적 데이터로 변환하는 가장 쉬운 방법

 

1. 고유한 단어들을 포함하는 어휘사전 구성하기
• ex. "Your bag is really beautiful", "Studying computer is really challenging"
• Vocabulary: {"Your", "bag", "is", "really", "beautiful", "Studying", "computer",
"challenging"}
2.  각 문장을 one-hot vector의 합으로 나타내기
• ex. "Your bag is really beautiful"
• "is" = [0 0 1 0 0 0 0 0]
• "Your" + "bag" + "is" + "really" + "beautiful" = [1 1 1 1 1 0 0 0]

Word Embedding
단어들을 벡터들로 표현하는 기술
단어가 주변 단어와의 관계에 따라 벡터 공간에서 위치

• 서울 - 한국 + 일본 = 도쿄
• 왕 - 왕비 = 남성 - 여성

EX) Word2Vec, GloVe

3. RNN, LSTM, GRU
RNN : Recurrent Neural Networks (순환 신경망)

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%20Week6%200d8f5899cce74f6da015f99cd3000e10/Untitled.png)

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%20Week6%200d8f5899cce74f6da015f99cd3000e10/Untitled%201.png)

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%20Week6%200d8f5899cce74f6da015f99cd3000e10/Untitled%202.png)

RNN 종류

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%20Week6%200d8f5899cce74f6da015f99cd3000e10/Untitled%203.png)

Standard Neural Networks / Image captioning
Sentiment Classification (감정분석) / Machine Translation
Video classification on frame level

RNN 문제점

backpropagation 을 매 step마다 반복하면서 gradient vanishing or exploding 발생
긴 문장에서 앞부분의 정보가 문장 뒷부분에 영향을 주지 못하게 됨 (제대로 학습 X)

해결법

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%20Week6%200d8f5899cce74f6da015f99cd3000e10/Untitled%204.png)

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%20Week6%200d8f5899cce74f6da015f99cd3000e10/Untitled%205.png)

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%20Week6%200d8f5899cce74f6da015f99cd3000e10/Untitled%206.png)

Encoder, Decoder
대부분의 시퀀스 데이터에서는 입력과 출력의 길이가 일정하지 않다.
Seq2seq >> 인코더 + 디코더 구조
인코더의 마지막 히든 스테이트 벡터는 디코더의  첫번째 입력으로 주어지는  히든 스테이트 벡터가 되어야 한다. 
첫 단어의 정보손실은 막는게 불가하다. 문장이 길어질수록 히든 스테이트 벡터를 거치는 횟수가 늘어나기 때문

Attention score

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%20Week6%200d8f5899cce74f6da015f99cd3000e10/Untitled%207.png)

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%20Week6%200d8f5899cce74f6da015f99cd3000e10/Untitled%208.png)

Beam search
Beam search는 시퀀스 예측 작업에서 사용되는 휴리스틱 검색 알고리즘이다.

가장 가능성이 높은 출력 시퀀스를 효과적으로 찾기 위함
• -> 모든 경우 탐색 greedy 접근 방식은 비현실적
• -> 타협을 본게 k개만 보자. 각 step별로 모은 예측 단어중 가장 가능성이 높은 k개만 보는 것. k를 2라고 가정

F-measure
• Reference: "The sun shines brightly in the clear blue sky."
• Predicted: "The moon shines brightly in the clear black sky."

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%20Week6%200d8f5899cce74f6da015f99cd3000e10/Untitled%209.png)

BLEU Score
• Reference: "The sun shines brightly in the clear blue sky."
• Predicted(model 1): "The moon shines brightly in the clear black sky."
• Predicted(model 2): "The clear sky shines brightly in the blue sun."

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%20Week6%200d8f5899cce74f6da015f99cd3000e10/Untitled%2010.png)

![Untitled](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%20Week6%200d8f5899cce74f6da015f99cd3000e10/Untitled%2011.png)

• BLEU Score : Bilingual Evaluation Understudy
• n-gram : 연속적인 n개의 항목(단어, 문자 등)으로 구성된 부분 시퀀스
• BLEU = brevity penalty x {1-gram, 2-gram, 3-gram, 4-gram precision 의 기하평균}
• Reference: "The sun shines brightly in the clear blue sky."
• Predicted: "The moon shines brightly in the clear black sky."
• brevity penalty =#(predict words)
                              #(reference words)