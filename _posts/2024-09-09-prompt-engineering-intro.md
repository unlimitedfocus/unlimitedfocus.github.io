---
title: 프롬프트 엔지니어링
author: luke
date: 2024-09-09
categories: [AI, Prompt Engineering]
tags: [Prompt, LLM]
---

## 프롬프트란?

프롬프트는 대규모 언어 모델(LLM)과 같은 AI에 입력하는 질문이나 지시로, ChatGPT처럼 다양한 작업을 요청할 때 사용됩니다.


## 프롬프트 엔지니어링

프롬프트 엔지니어링은 프롬프트를 지속적으로 조정하고 개선하여 AI의 출력을 원하는 방향으로 유도하는 기술입니다. 이를 통해 AI의 성능을 극대화할 수 있으며, 사용자는 업무 자동화, 콘텐츠 생성 등 다양한 분야에서 AI를 효과적으로 활용할 수 있습니다.

저는 작년부터 여러 도서나 아티클을 참고해 여러 LLM을 '그냥' 사용해왔지만, 최근 강수진님의 [유튜브 영상](https://youtu.be/GlvOHXJT_gI?si=lgd4uCAYJ9ZFfo1V){:target="_blank"}을 보니 '잘' 사용하는 것과 '그냥' 사용하는 것의 차이를 조금 알 것 같습니다.

어떻게보면  사진 촬영에 비유할 수 있을 것 같습니다. 같은 카메라와 피사체를 사용하더라도, 구도, 조명, 셔터 스피드에 따라 결과물이 천차만별 달라지듯이, LLM도 프롬프트 구성을 어떻게 하느냐에 따라 할수 있는것과 결과가 크게 달라지는것 같습니다.


## [프롬프트의 구성요소](https://www.promptingguide.ai/introduction/elements){:target="_blank"}

프롬프트를 구성하는 주요 요소는 다음과 같습니다.
1. 지시(Instruction): 모델이 수행할 특정 작업이나 지시
2. 문맥(Context): 더 나은 응답을 위한 외부정보나 배경
3. 입력데이터(Input Data): 응답 받고자 하는 입력이나 정보
4. 출력지시자(Output Indicator): 출력물의 유형이나 형식


## [프롬프트 작성가이드](https://learn.deeplearning.ai/courses/chatgpt-prompt-eng/){:target="_blank"}

1. 원칙1: 명확하고 구체적인 지시를 작성
- 전략1. 구분 기호를 사용하여 Input 구조화
- 전략2. 구조화된 출력을 요청 (Json, HTML)
- 전략3. 모델이 조건을 충족하는지 확인 요구
- 전략4. 예시를 제공 (Few-shot prompting)

2. 원칙2: 모델에게 생각할 시간을 주기
- 전략1. 테스크를 완수하기 위한 구체적인 단계를 제공
- 전략2. 모델이 판단을 내리기 전에 자신만의 해결책을 차도록 지시

---

## [프롬프트 테크닉](https://www.promptingguide.ai/kr/techniques)

LLM(대형 언어 모델)을 효과적으로 활용하기 위한 프롬프트 엔지니어링은 다양한 기법을 통해 모델의 성능을 극대화할 수 있습니다. 이번 글에서는 각 프롬프트 엔지니어링 테크닉을 설명하고, 이를 활용하여 어떻게 더 나은 결과를 얻을 수 있는지 알아보겠습니다.

### 1. Zero-shot Prompting
**Zero-shot prompting**은 사전 학습된 모델이 추가적인 학습이나 예시 없이 새로운 데이터를 처리할 수 있도록 하는 기법입니다. 모델은 주어진 질문이나 명령에 대해 직접적인 답을 생성하며, 추가적인 예시는 제공되지 않습니다.

- **사용 예**: "고양이가 영어로 뭐야?"라는 질문을 하면, 모델은 바로 "cat"이라는 답을 제공할 수 있습니다.

### 2. One-shot Prompting
**One-shot prompting**은 단 하나의 예시나 입력 데이터를 제공하여 모델이 더 나은 응답을 생성하도록 하는 기법입니다. 한정된 정보로도 모델의 성능을 높일 수 있는 방법입니다.

- **사용 예**: "Translate 'Hello' into Spanish: Hola. Translate 'Goodbye' into Spanish:"라고 입력하여 한 가지 예시만으로 번역 작업을 유도할 수 있습니다.

### 3. Few-shot Prompting
**Few-shot prompting**은 작은 수의 예시(보통 2~5개)를 제공하여 모델이 문제 해결 방식을 학습하게 하는 기법입니다. 예시가 적지만, 이를 통해 모델의 성능을 향상시킬 수 있습니다.

- **사용 예**: "Translate 'Hello' into Spanish: Hola. Translate 'Goodbye' into Spanish: Adiós."

### 4. Chain-of-Thought Prompting
**Chain-of-Thought (CoT) prompting**은 여러 단계를 거친 추론 과정을 통해 모델이 복잡한 문제를 해결하도록 유도하는 기법입니다. 이 방식은 특히 논리적 추론이나 수학 문제에서 효과적입니다.

- **사용 예**: "34 + 47을 계산하려면, 먼저 30 + 40 = 70을 구하고, 그다음 4 + 7 = 11을 구해 합하면 81이 됩니다."

### 5. Self-Consistency
**Self-consistency**는 여러 번의 추론 경로를 생성한 후 가장 자주 등장하는 결과를 선택하는 방식입니다. 이는 응답의 일관성을 높이는 데 효과적입니다.

- **사용 예**: 같은 문제에 대해 여러 답변을 얻고, 그중 가장 많이 등장한 답변을 최종 답으로 채택.

### 6. Generate Knowledge Prompting
**Generate knowledge prompting**은 먼저 관련 지식을 생성한 후 이를 기반으로 문제를 해결하는 방식입니다. 이는 복잡한 개념이나 깊이 있는 설명이 필요할 때 유용합니다.

- **사용 예**: "양자역학에 대해 설명해줘. 이제 이 지식을 바탕으로 초전도를 설명해줘."

### 7. Prompt Chaining
**Prompt chaining**은 여러 개의 프롬프트를 연속적으로 사용하여 복잡한 문제를 단계적으로 해결하는 기법입니다. 각 단계의 결과가 다음 프롬프트의 입력으로 사용됩니다.

- **사용 예**: 첫 번째 프롬프트에서 데이터를 요약한 후, 그 요약을 바탕으로 분석을 진행.

### 8. Tree of Thoughts
**Tree of Thoughts (ToT)**는 여러 가지 사고 과정이나 선택지를 트리 구조로 펼치며 문제를 해결하는 방식입니다. 다양한 경로를 탐색한 후 최적의 경로를 선택합니다.

- **사용 예**: 다양한 해결 방안을 나열하고, 각각의 장단점을 비교해 최적의 결정을 내리는 구조.

### 9. Retrieval Augmented Generation (RAG)
**Retrieval Augmented Generation (RAG)**은 모델이 외부 데이터를 검색하고 그 데이터를 기반으로 답변을 생성하도록 하는 기법입니다. 모델이 사전 학습된 데이터 외에 실시간 정보를 사용할 수 있습니다.

- **사용 예**: "최근 뉴스를 검색하고 그 내용을 요약해줘."

### 10. Automatic Reasoning and Tool-use
**Automatic reasoning and tool-use**는 모델이 계산기나 API 같은 외부 도구를 사용하여 복잡한 계산이나 데이터 처리 작업을 수행할 수 있도록 하는 기법입니다.

- **사용 예**: "256의 제곱근을 계산해줘."

### 11. Automatic Prompt Engineer
**Automatic prompt engineering**은 모델이 스스로 최적의 프롬프트를 생성하거나 수정하는 방식입니다. 모델이 학습을 통해 프롬프트의 효과성을 스스로 개선합니다.

- **사용 예**: 모델이 스스로 프롬프트를 조정하여 더 나은 성능을 발휘.

### 12. Active-Prompt
**Active-prompting**은 모델이 추가 정보를 요청하거나 명확한 질문을 통해 사용자의 입력을 유도하는 방식입니다.

- **사용 예**: "어떤 종류의 주식 분석을 원하시나요?"와 같이 추가 정보를 요청하는 프롬프트.

### 13. Directional Stimulus Prompting
**Directional Stimulus Prompting**은 모델에게 특정 방향성을 제시하여 원하는 종류의 응답을 얻는 방식입니다.

- **사용 예**: "18세기 유럽 철학의 맥락에서 칸트의 사상에 대해 설명해줘."

### 14. Program-Aided Language Models (PALM)
**PALM**은 프로그래밍 논리와 언어 모델의 출력을 결합하여 문제 해결 능력을 높이는 방식입니다. 프로그래밍을 통한 논리적 추론을 강화할 수 있습니다.

- **사용 예**: 모델이 파이썬 코드를 생성하고 실행하여 문제 해결.

### 15. ReAct
**ReAct**는 모델이 추론 과정에서 논리적 사고와 행동을 결합하는 기법으로, 문제 해결 중 외부 정보를 활용할 수 있습니다.

- **사용 예**: 모델이 논리적 사고를 하며 계산기를 이용해 문제를 해결.

### 16. Reflexion
**Reflexion**은 모델이 스스로 답변을 재검토하고 개선하는 방식입니다. 자가 수정 기법으로, 모델이 답변을 반복적으로 개선합니다.

- **사용 예**: 모델이 자신의 초기 답변을 검토하고 오류를 수정.

### 17. Multimodal Chain-of-Thought (CoT)
**Multimodal CoT**는 텍스트뿐만 아니라 이미지, 비디오 등 다양한 매체를 사용하여 복합적인 사고 과정을 수행하는 기법입니다.

- **사용 예**: 모델이 이미지를 분석하고 그 내용을 텍스트로 설명.

### 18. Graph Prompting
**Graph prompting**은 그래프 기반 구조를 활용하여 관계를 이해하고 더 복잡한 추론을 수행하는 기법입니다.

- **사용 예**: 지식 그래프를 구축하여 인물 간의 관계를 설명.

### 19. Meta-Prompting
**Meta-prompting**은 모델이 스스로 자신의 프롬프트를 생성하거나 수정하는 방식입니다. 이를 통해 더 나은 성과를 얻기 위해 프롬프트를 동적으로 변경할 수 있습니다.

- **사용 예**: "어떤 정보가 필요하면 스스로 추가 질문을 만들어."

---


## 참고링크
- [Prompt Engineering Guide](https://www.promptingguide.ai/){:target="_blank"}
- [ChatGPT Prompt Engineering for Developers](https://learn.deeplearning.ai/courses/chatgpt-prompt-eng/){:target="_blank"}


