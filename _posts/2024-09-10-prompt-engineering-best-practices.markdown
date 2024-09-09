---
title: 프롬프트 엔지니어링 베스트 프랙티스
author: luke
date: 2024-09-09
categories: [AI, Prompt Engineering]
tags: [Prompt, LLM]
---

ChatGPT와 같은 대규모 언어 모델(LLM)에서 최적의 결과를 얻기 위한 몇 가지 핵심 규칙과 예시를 번역 [^1].

### 1. 최신 모델 사용하기
최상의 결과를 얻기 위해서는 항상 최신 모델을 사용하는 것이 좋습니다. 새로운 모델일수록 프롬프트 엔지니어링이 더 쉬워집니다.

### 2. 명령어는 프롬프트의 시작 부분에 두고, ### 또는 """로 구분하기
프롬프트의 명령어와 맥락을 명확하게 구분하는 것이 중요합니다. 이를 위해 명령어는 프롬프트의 시작 부분에 위치시키고, 구분자를 사용하여 본문과 구분합니다.

**덜 효과적인 방식 ❌:**
```
Summarize the text below as a bullet point list of the most important points.

{text input here}
```

**효과적인 방식 ✅:**
```
Summarize the text below as a bullet point list of the most important points.

Text: """
{text input here}
"""
```

### 3. 구체적이고 명확하게 작성하기
프롬프트에서 원하는 맥락, 결과, 길이, 형식, 스타일 등을 가능한 한 자세하게 명시해야 합니다.

**덜 효과적인 방식 ❌:**
```
Write a poem about OpenAI.
```

**효과적인 방식 ✅:**
```
Write a short inspiring poem about OpenAI, focusing on the recent DALL-E product launch (DALL-E is a text to image ML model) in the style of a {famous poet}
```

### 4. 원하는 출력 형식을 예시로 제시하기
모델에게 원하는 형식을 명확하게 제시하면 더 일관된 결과를 얻을 수 있습니다.

**덜 효과적인 방식 ❌:**
```
Extract the entities mentioned in the text below. Extract the following 4 entity types: company names, people names, specific topics and themes.

Text: {text}
```

**효과적인 방식 ✅:**
```
Extract the important entities mentioned in the text below. First extract all company names, then extract all people names, then extract specific topics which fit the content and finally extract general overarching themes

Desired format:
Company names: COMMA_SEPARATED_LIST_OF_COMPANY_NAMES
People names: -||-
Specific topics: -||-
General themes: -||-

Text: {text}
```

### 5. zero-shot에서 출발하고, 필요시 few-shot, 마지막으로 fine-tune
프롬프트 엔지니어링에서는 간단한 제로샷(예시 없이) 프롬프트로 시작하고, 몇샷(예시를 제공하는) 접근으로 전환한 뒤, 둘 다 효과가 없을 경우 파인 튜닝을 고려합니다.

**zero-shot 예시 ✅:**
```
Extract keywords from the below text.

Text: {text}

Keywords:
```

**few-shot 예시 ✅:**
```
Extract keywords from the corresponding texts below.

Text 1: Stripe provides APIs that web developers can use to integrate payment processing into their websites and mobile applications.
Keywords 1: Stripe, payment processing, APIs, web developers, websites, mobile applications
##
Text 2: OpenAI has trained cutting-edge language models that are very good at understanding and generating text. Our API provides access to these models and can be used to solve virtually any task that involves processing language.
Keywords 2: OpenAI, language models, text processing, API.
##
Text 3: {text}
Keywords 3:
```

**fine-tuning 예시 ✅:**
Fine-tune: see fine-tune best practices [here](https://platform.openai.com/docs/guides/fine-tuning){:target="_blank}

### 6. 불분명하거나 모호한 설명은 피하기
명확한 설명을 사용해 프롬프트의 효과를 높입니다.

**덜 효과적인 방식 ❌:**
```
The description for this product should be fairly short, a few sentences only, and not too much more.
```

**효과적인 방식 ✅:**
```
Use a 3 to 5 sentence paragraph to describe this product.
```

### 7. 하지 말라는 것보다는 해야 할 일을 설명하기
하지 말아야 할 것을 나열하는 것보다는, 해야 할 일을 명확히 설명하는 것이 더 효과적입니다.

**덜 효과적인 방식 ❌:**
```
The following is a conversation between an Agent and a Customer. DO NOT ASK USERNAME OR PASSWORD. DO NOT REPEAT.

Customer: I can’t log in to my account.
Agent:
```

**효과적인 방식 ✅:**
```
The following is a conversation between an Agent and a Customer. The agent will attempt to diagnose the problem and suggest a solution, whilst refraining from asking any questions related to PII. Instead of asking for PII, such as username or password, refer the user to the help article www.samplewebsite.com/help/faq

Customer: I can’t log in to my account.
Agent:
```

### 8. 코드 생성: "힌트"를 사용해 특정 패턴 유도하기
코드를 작성할 때는 AI가 특정 패턴을 따르도록 힌트를 주는 것이 좋습니다.

**덜 효과적인 방식 ❌:**
```
# Write a simple python function that
# 1. Ask me for a number in mile
# 2. It converts miles to kilometers
```

**효과적인 방식 ✅:**
```
# Write a simple python function that
# 1. Ask me for a number in mile
# 2. It converts miles to kilometers

import
```

## 참고링크
[^1]: [Best practices for prompt engineering with the OpenAI API](https://help.openai.com/en/articles/6654000-best-practices-for-prompt-engineering-with-the-openai-api#h_ad50145be0){:target="_blank"}

