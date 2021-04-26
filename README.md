# simple_seq2seq-GRU-
RNN의 단점을 보완한 GRU에 대해 알아보기 위해 시작한 간단한 프로젝트
아스키 코드를 데이터 셋으로 사용해 hello를 hola로 번역한다.

# seq2seq?
RNN 기반의 번역 모델.
기계 번역의 새로운 패러다임을 열었다 할 정도로 뛰어난 성능을 보여줬다.

# 특징
시퀀스를 입력받아 또 다른 시권스를 출력한다. -> 문장을 다른 문장으로 번역해주는 모델

# 구조
두 개의 RNN을 이어 붙인 모델.
보통 번역을 한다고하면, 다음과 같은 과정으로 번역이 진행된다.
## 1. 외국어 문장을 읽고 의미를 이해한다.
## 2. 외국어 문장의 의미를 생각하면서 한국어 단어를 문맥에 맞게 적어나간다.
seq2seq에서는 1번을 인코더에게 맡기며 2번을 디코더에 맡긴다.

# 인코더?
원문의 내용을 학습하는 RNN.
원문 속의 모든 단어를 입력받아 문장의 뜻을 내포하는 하나의 고정 크기 텐서를 만든다.
이를 원문의 뜻과 내용을 압축하고 있다고 하여 문맥 벡터(context vector)라고 한다.

# 디코더?
원문 문맥 벡터를 이어받아 번역문 속의 토큰을 차례대로 예상한다.

# 학습 원리
1. 인코더의 문맥 벡터를 디코더에 입력
2. 디코더는 번역문 내 토큰들을 차례대로 예측
3. 디코더가 예상해낸 모든 토큰과 실제 번역문 사이의 오차를 줄여나간다.

# 환경
- python = 3.x
- pytorch = 1.18

# 데이터
## vocab size
- 영문만 다룰 것이기 때문에 영문을 숫자로 표현하는 방식인 아스키 코드로 임베딩을 대신한다.
- 따라서, 아스키 코드는 총 256개의 글자를 표현할 수 있으므로, 사전에 담을 수 있는 토큰 수를 256으로 정의함.

# 목표
- 영어 hello를 hola로 번역하는 아주아주 간단한 기계 번역 모델을 구현한다.
