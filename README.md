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

  * **1단계: 최소 기능 제품(MVP) 구축**: 히라가나/가타카나 가사를 중심으로 소규모(예: 100개) 데이터셋을 수작업으로 구축하고, 간단한 규칙 기반 모델을 개발하여 실현 가능성을 검증합니다.
  * **2단계: 데이터셋 확장 및 모델 고도화**: 한자(Kanji)와 불규칙 발음을 포함하도록 데이터셋을 확장합니다. 확장된 데이터를 활용해 트랜스포머 기반 모델을 개발하고 미세 조정(fine-tuning)합니다.
  * **3단계: 성능 평가**: WER, PER과 같은 객관적 지표와 인간 평가를 병행하여 모델의 성능과 '노래 가능성'을 종합적으로 평가합니다.

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

### 🇰🇷 라이선스 (License)
* **MIT**
