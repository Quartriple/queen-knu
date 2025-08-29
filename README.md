## Project Queen Knu
An NLP model to convert Japanese song lyrics into 'Singable Pronunciation' in Korean.

### 🇰🇷 프로젝트 개요

본 프로젝트는 일본어 가사를 한국어 발음으로 변환하는 자연어 처리(NLP) 모델을 개발하는 것을 목표로 합니다. 특히, 단순히 텍스트를 변환하는 것을 넘어 노래의 멜로디와 운율에 맞춰 따라 부를 수 있는 '**'노래 가능한 발음(Singable Pronunciation)'**'을 제공하는 데 중점을 둡니다. 이 작업은 일반적인 번역이나 텍스트 음성 변환(TTS)과는 달리, 가사의 비정형적 특성과 음악적 제약 조건을 모두 고려해야 하는 복잡한 과제입니다.

### 🇺🇸 Project Overview

This project aims to develop a Natural Language Processing (NLP) model to convert Japanese song lyrics into phonetic Korean, with a special focus on creating **'Singable Pronunciation'** that matches the rhythm and flow of the original songs. This is a more advanced task than simple translation or Text-to-Speech (TTS) conversion, as it requires an understanding of musical constraints and the non-lexical characteristics of lyrics.

### 🇰🇷 기술적 접근법

일본어의 복잡한 언어학적 난제들을 해결하기 위해 최신 딥러닝 기술을 활용할 것입니다.

* **모델 아키텍처**: Grapheme-to-Phoneme(G2P) 작업에 가장 뛰어난 성능을 보이는 **트랜스포머(Transformer) 기반의 Seq2Seq 모델**을 채택합니다.
* **데이터 전략**: 프로젝트의 성공은 양질의 '일본어 가사-한국어 발음' 병렬 데이터셋 구축에 달려 있습니다. 가사의 독특한 특성(비어휘적 소리, 불규칙 구조 등)을 처리하기 위해 숙련된 전문가의 수동 전사 및 정렬 작업이 필수적입니다.
* **입력 특징**: '노래 가능한 발음'이라는 핵심 요구사항을 충족시키기 위해, 원문 철자 외에 각 라인의 **음절 수 정보를 `<SYL>` 토큰 형태로 모델 입력에 포함**시킬 것입니다. 이 방법은 노래의 운율을 학습하는 데 효과적인 것으로 입증되었습니다.

### 🇺🇸 Technical Approach

Our approach leverages modern deep learning techniques to address the complex linguistic challenges of Japanese.

* **Model Architecture**: We will use a **Transformer-based Seq2Seq model**, which is the leading architecture for Grapheme-to-Phoneme (G2P) tasks.
* **Data Strategy**: The project's success is highly dependent on building a high-quality, parallel dataset of Japanese lyrics and their corresponding Korean phonetic transcriptions. This will involve extensive manual transcription and alignment by a skilled expert to handle unique lyric characteristics such as non-lexical sounds and irregular structures.
* **Feature Engineering**: To ensure 'singable' output, we will include syllable count information as a special **`<SYL>` token** in the model's input. This helps the model learn to produce outputs with a syllable count similar to the original lyrics, a method proven effective in similar projects.

### 🇰🇷 파일 구조 (File System Structure)

  * `data/`: 원본 가사와 최종 병렬 데이터셋을 포함한 모든 데이터 파일을 저장합니다.
  * `src/`: 데이터 전처리, 모델 훈련 및 추론을 위한 모든 소스 코드를 담습니다.
  * `experiments/`: 상세한 실험 일지 및 결과를 기록하는 디렉터리입니다.
  * `models/`: 훈련된 모델 체크포인트를 저장합니다.
  * `notebooks/`: 탐색적 데이터 분석 및 프로토타입 개발을 위한 주피터 노트북 파일들을 보관합니다.

### 🇰🇷 프로젝트 로드맵 (Roadmap)

### **1단계: 기반 다지기 및 기술 탐색 (Feasibility Study)**

* **목표**: 일본어 가사의 언어학적 난제를 구체적으로 이해하고, 기존 G2P 기술의 한계를 파악합니다.
* **실행 과제**:
    * **환경 설정**: Python, PyTorch/TensorFlow, Hugging Face `transformers` 등 핵심 라이브러리를 설치합니다.
    * **데이터 샘플링**: 프로젝트의 핵심인 '원문 가사 - 한국어 발음' 병렬 데이터를 소규모(예: 10~20곡)로 수작업으로 구축합니다. 이 과정에서 '노래 가능한 발음'의 정의 기준을 마련합니다.
    * **프로토타입 개발**: Mecab과 같은 기존 일본어 처리 라이브러리를 활용하여, 한자를 히라가나로 변환한 후 한국어 발음으로 치환하는 **규칙 기반 모델**을 개발합니다. 이를 통해 MVP의 실현 가능성을 검증합니다.

### **2단계: 데이터셋 구축 및 모델 MVP 개발 (Data & Model Foundation)**

* **목표**: 딥러닝 모델 학습에 필요한 양질의 '일본어 가사-한국어 발음' 병렬 데이터셋을 구축하고, 트랜스포머 기반의 Seq2Seq 모델을 훈련합니다.
* **실행 과제**:
    * **데이터 수집**: Genius와 같은 웹사이트의 API나 웹 스크래핑을 통해 대규모의 원문 가사 텍스트를 수집하는 파이프라인을 구축합니다.
    * **데이터 정제 및 음역**: 수집된 가사를 수작업 또는 반자동화된 방식으로 한국어 발음으로 음역합니다. 가사의 비정형적 특성(비어휘적 소리, 불규칙 구조 등)을 처리하고, 각 라인의 음절 수를 `<SYL>` 토큰 형태로 추가합니다.
    * **모델 구현**: Hugging Face `transformers` 라이브러리를 활용하여 일본어 음절(또는 단어) 시퀀스를 한국어 음절 시퀀스로 변환하는 트랜스포머 기반의 Seq2Seq 모델을 개발합니다.

### **3단계: 모델 고도화 및 성능 평가 (Refinement & Evaluation)**

* **목표**: 모델의 예측 정확도를 높이고, '노래 가능한 발음'이라는 핵심 요구사항을 충족시키기 위한 평가 체계를 수립합니다.
* **실행 과제**:
    * **모델 튜닝**: 학습률(Learning Rate), 배치 크기(Batch Size) 등 하이퍼파라미터를 최적화하여 모델 성능을 극대화합니다.
    * **데이터 보강**: 모델이 자주 틀리는 한자 발음이나 불규칙 발음 단어들을 식별하고, 해당 데이터셋을 보강하여 모델을 재훈련합니다.
    * **평가 파이프라인 구축**: **단어 오류율(WER)** 및 **음소 오류율(PER)**을 자동으로 측정하는 스크립트를 작성합니다. 또한, '노래 가능성'을 평가하기 위한 인간 평가(Human Evaluation) 기준을 명확히 수립하고, 평가를 위한 간단한 인터페이스를 구축합니다.

### **4단계: 데모 개발 및 최종 지식 공유 (Demo & Knowledge Sharing)**

* **목표**: 최종 모델을 활용한 사용자 경험(UX) 중심의 데모를 개발하고, 프로젝트의 모든 지식을 집대성하여 외부에 공유합니다.
* **실행 과제**:
    * **모델 배포**: 훈련된 모델을 REST API 형태로 배포하여 웹 데모와 연동합니다.
    * **프론트엔드 개발**: 사용자가 일본어 가사를 입력하면 한국어 발음으로 변환된 결과를 보여주는 간단한 웹 인터페이스를 구축합니다.
    * **종합 보고서 작성**: 프로젝트의 배경, 방법론, 결과, 한계점 및 미래 연구 방향을 포함하는 **기술 보고서**를 작성합니다.

### 🇰🇷 참고 자료 (References)

1.  가사 음원 스트리밍 서비스를 위한 영어 및 일본어 가사 한글 발음 전사 모델 개발 보고서
2.  A Survey of Grapheme-to-Phoneme Conversion Methods - MDPI, 8월 28, 2025에 액세스, https://www.mdpi.com/2076-3417/14/24/11790
3.  G2P Shrinks Speech Models - Hugging Face, 8월 28, 2025에 액세스, https://huggingface.co/blog/hexgrad/g2p
4.  Grapheme-to-Phoneme Conversion with Convolutional Neural Networks - MDPI, 8월 28, 2025에 액세스, https://www.mdpi.com/2076-3417/9/6/1143
5.  [NLP] Seq2Seq, Transformer, Bert 흐름과 정리 - 삶은 확률의 구름 - 티스토리, 8월 28, 2025에 액세스, https://ebbnflow.tistory.com/316
6.  Fast, Not Fancy: Rethinking G2P with Rich Data and Rule-Based Models - arXiv, 8월 28, 2025에 액세스, https://arxiv.org/html/2505.12973v1
7.  K-pop Lyric Translation: Dataset, Analysis, and ... - ACL Anthology, 8월 28, 2025에 액세스, https://aclanthology.org/2024.lrec-main.872v1.pdf
8.  Grapheme-to-Phoneme Conversion (G2P) - Deepgram, 8월 28, 2025에 액세스, https://deepgram.com/ai-glossary/grapheme-to-phoneme-conversion-g2p
9.  [Paper Review] DATA DRIVEN GRAPHEME-TO-PHONEME REPRESENTATIONS FOR A LEXICON-FREETEXT-TO-SPEECH - Scrutinizer, 8월 28, 2025에 액세스, https://welcome-be.tistory.com/43

### License
* **MIT**
