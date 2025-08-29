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

### 🇰🇷 개발 로드맵 (Roadmap)

#### **Phase 1: 기술 탐색 및 핵심 기능 검증 (The Discovery & MVP Phase)**
이 단계의 목표는 프로젝트의 기초를 다지는 것입니다. G2P 기술의 원리와 일본어 음운론적 특징을 학습하고, 규칙 기반의 최소 기능 제품(MVP)을 구축하여 핵심 기능의 실현 가능성을 검증합니다.

* **기초 지식 학습**: Grapheme-to-Phoneme(G2P) 기술의 원리, 규칙 기반 및 딥러닝 모델의 차이점을 파악합니다. 또한, 한자(Kanji)의 복수 발음(음독/훈독), 장음, 촉음 등 일본어 발음의 고유한 난제를 깊이 이해합니다.
* **데이터 수집 및 전처리**: 웹 스크래핑을 통해 히라가나와 가타카나 가사 원문 데이터를 100곡 이상 수집합니다. 이 데이터는 가사의 비정형적 구조와 비어휘적 소리(예: "yeah")를 처리하는 수작업 정렬의 토대가 됩니다.
* **MVP 구현**: 일본어 발음 규칙과 오픈 소스 라이브러리를 활용하여 히라가나/가타카나를 한국어 발음으로 변환하는 간단한 규칙 기반 모델을 개발하고, 핵심 기능의 동작 여부를 확인합니다.

#### **Phase 2: 데이터셋 확장 및 모델 고도화 (The Scaling & Refinement Phase)**
이 단계의 목표는 프로젝트의 규모를 확장하고, 복잡한 언어적 난제를 해결하기 위한 딥러닝 모델을 개발하는 것입니다.

* **대규모 데이터셋 구축**: 한자가 포함된 가사를 포함하여 1,000곡 이상의 원문 데이터를 추가로 수집하고, 수동 검수 과정을 거쳐 '원문-한국어 발음' 병렬 데이터셋을 구축합니다.
* **모델 개발**: 가사 음역에 가장 적합한 **트랜스포머(Transformer) 기반의 Seq2Seq 모델**을 채택하고 구현합니다.
* **'노래 가능한 발음' 학습**: 모델 입력에 각 라인의 **음절 수 정보를 `<SYL>` 토큰 형태로 추가**하여, 노래의 운율을 고려한 발음 표기 생성을 유도합니다.

#### **Phase 3: 성능 평가 및 모델 최적화 (The Evaluation & Optimization Phase)**
이 단계의 목표는 개발된 모델의 성능을 객관적, 주관적으로 평가하고, 실제 사용성을 높이기 위한 지속적인 개선 프로세스를 수립하는 것입니다.

* **객관적 성능 평가**: G2P 모델의 표준 평가 지표인 **단어 오류율(WER)**과 **음소 오류율(PER)**을 사용하여 모델의 정확도를 정량적으로 측정합니다.
* **주관적 성능 평가**: WER과 PER로는 측정할 수 없는 '노래 가능성'을 평가하기 위해, 인간 평가자 그룹을 통한 주관적 평가를 수행합니다.
* **반복적 개선**: 평가 결과를 바탕으로 모델의 예측 오류가 빈번한 단어(고유명사, 불규칙 발음)를 식별하고, 해당 데이터셋을 보강하여 모델을 재훈련함으로써 성능을 지속적으로 향상시킵니다.

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
