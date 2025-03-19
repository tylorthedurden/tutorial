# Gen AI 서비스 첫걸음

## 생성 AI란?

- 사용자의 요청에 따라 학습한 데이터를 적절하게 조합하여 합성 데이터를 만들어 내는 기술
- ChatGPT와 같은 Text 생성 모델 기반의 대화형 서비스뿐 아니라 DALLE, Imagen같은 이미지 생성, Kling, Veo와 같은 Video 생성까지 다양한 서비스들이 있음
- 기본적으로 대화형 서비스로 사람에게 작업을 시키는 것과 유사하게 자연어를 사용하여 작업을 요청할 수 있음
  - ChatGPT(Text):
    - 기본 질문: "상대성 이론이 뭐야?"
    - 코드 작성: "Python으로 이진 탐색 알고리즘을 구현해줘"
    - 글쓰기: "인공지능의 윤리적 문제점에 대한 에세이를 작성해줘"
    - 분석 요청: "다음 주식 시장 데이터를 분석하고 트렌드를 설명해줘: [데이터]"
  
  - Imagen(Image):
    - 사실적 이미지: "realistic photo of a cat, wearing cute red boots, standing on foot, smile, 4k resolution, detailed fur texture"
    - 예술적 이미지: "oil painting of a sunset over mountains, impressionist style, vibrant colors, thick brush strokes"
    - 제품 디자인: "3D render of a modern minimalist smartphone, white background, product photography style"
  
  - Veo(Video):
    - 실사 영상: "A man is doing workout at the gym, muscular build, black hair, blushing face, gasping hard, cinematic lighting, 4k quality"
    - 애니메이션: "2D animated character walking through a colorful forest, Studio Ghibli style, soft lighting"
    - 제품 시연: "3D animation of a drone flying through city streets, showing key features, professional camera movements"

## 대표적 Text 기반 서비스 비교표

| 서비스 | 기능 | 가격 | 장점 | 단점 |
|-------|------|------|------|------|
| Perplexity | 실시간 Web Search, Deep Research, Pro, Thinking, Image 생성 제한적 지원 | $20/Month | OpenAI / Anthropic 다양한 AI 모델을 사용할 수 있음, 검색에 강점, SKT 임직원 1년간 Pro 무료 사용, 응답을 다양한 형식 (PDF, Markdown 등) 추출 가능 | 상대적으로 메시지 맥락의 길이가 짧으며 대화가 길어지면 앞의 대화 내용을 빠르게 망각 |
| ChatGPT (OpenAI) | Deep Research, Reasoning, Image 생성, Video 생성 (Sora), 실시간 Web Search, 실시간 음성 지원 | Plus: $20/월 (2024년 말 $22/월로 인상 예정), Pro: $200/월 | 우수한 성능의 모델을 기반으로 우수한 품질의 서비스를 제공(최근 다소 약화), 가장 표준적이고 널리 알려진 서비스로 사용자 저변이 넓고 사용 방법 및 팁에 대한 자료가 풍부함, 음성 모드의 지연에서 최상 (영어 회화 연습 등의 Use case 지원 가능) | 가격이 상대적으로 높은편 (호9), 가격 상한선에서 업계 선두 |
| Claude (Anthropic) | Thinking (Reasoning), MCP기반의 다양한 확장 지원 (검색, 엑셀 편집 등), 음성모드 지원 (실시간 X) | $20/Month | 가장 우수한 성능의 AI 모델을 보유 (코딩에 강점) | Pro 구독 포함 사용량 상한선 (Rate Limit 존재), 잦은 답변 속도 저하 및 장애 발생, 기본적으로 Web Search 미지원 (MCP를 통해 확장 가능) |
| Gemini (Google) | Thinking (Reasoning), Deep Research, 실시간 Web Search, Google Drive / Gmail / Kayak 등 서비스 통합 기능 지원, 실시간 음성 대화 | Standard: 무료, Advanced: $19.99/월 (미국 기준), Business: $20/월/사용자 (1년 약정 시), Enterprise: $30/월/사용자 (1년 약정 시) | Google Drive와의 연동, Advanced 요금에 포함된 Storage 2TB 5인 공유 가능, 검색 및 Fact Check 등을 제공, 1M 토큰의 맥락 길이를 제공 (책한권을 통으로 입력 가능) | 모델 정확도가 다소 떨어짐, 음성 대화에 지연이 다른 경쟁사 대비 큼 |
| Grok3 (x.com) | Thinking (Think 모드), Deep Research (DeepSearch), 실시간 Web 정보 / x.com의 Post를 검색하여 답변, 유희적 목적의 대화 (Unhinged Mode), 실시간 음성 대화 (Voice Mode), 이미지 생성 | 기본 기능 무료 (X 사용자), X Premium+: $40/월 또는 $395/년 (미국 기준), SuperGrok: $30/월 또는 $300/년 | 실시간 X 데이터 접근으로 최신 정보 제공, 200,000개 Nvidia H100 GPU로 구동되는 강력한 연산 능력, 투명한 사고 과정을 보여주는 Think 모드, 코딩, 수학, 과학 분야에서 뛰어난 성능 | 고급 기능은 유료 구독이 필요, X Premium+ 가격이 최근 두 배 가까이 인상됨, 창의적 글쓰기 능력이 다소 부족, 일부 고급 기능은 SuperGrok 구독으로만 이용 가능 |

## Perplexiy 활용 방법 소개

### 기본 팁 (예시)

- AI 학습 메커니즘에 대한 이해 - Causal Language Modeling (다음 토큰 맞춰기)
  - 데이터가 학습 될 때 전체 글에서 앞부분의 품질은 그 뒤에 나올 글의 품질을 크게 좌우함
  - 앞의 글(Prompt)의 품질을 높이면 뒤의 글(답변)의 품질이 올라감
- Magic Pormpt: Verbalize your think or plan prior to give an answer in step-by-step manner / 답변하기 전에 차근차근 생각을 말로 설명하고 답변해
  - Microsoft의 연구진들이 합성 데이터 활용을 위해 사용한 Magic Recipe [1](https://www.microsoft.com/en-us/research/blog/orca-2-teaching-small-language-models-how-to-reason/), [2](https://arxiv.org/pdf/2312.06585.pdf)
- 언어별 성능 차이 - 영어 사용이 유리
  - AI 학습 데이터의 언어 분포에서 영어가 압도적
  - 언어별 성능 차이가 존재하며 영어로 질의하면 한국어 대비 뛰어난 품질의 결과물을 얻을 수 있음
  - 영어 질의 -> 영어 답변 -> 한국어로 번역 요청
- 템플릿 및 Markdown 사용
  - Markdown(마크다운)이란?
    - 개발자들이 문서를 구조화하여 작성하기 위한 Minimal한 서식을 지원하는 Format
    - 형식이 매우 간결하고 키보드 입력(마우스 필요 없이) 테이블 / 링크 / 불릿 / 헤딩 서식을 적용할 수 있음
    - AI 학습에 많이 사용된 서식
      - 특히, Open Source Code의 대부분 문서 작업이 이 Markdown으로 이루어져 있어 서식을 지원하는 형식 중 가장 높은 비중을 가지고 있을 것으로 추정
    - Code Block
      - Markdown의 서식 중 하나로 주로 코드를 보기 좋게 표시하기 위한 목적
      - 이 Code Block의 경우 일반적으로 복붙이 수반되기 때문에 편의 기능으로 복붙 버튼을 제공
  - 템플릿
    - 질의를 구조화하여 여러번 질의해야 될 내용을 한번에 수집할 수 있음
  - 템플릿 준비
    - AI를 활용하여 Template을 만들 수 있음
    - build Markdown template for quick research for AI startup using tables and bullets and put it within code block
    - build Markdown template for quick comparative research for AI startups
  - 예시: Company Overview

    ---

    ```markdown
    # Manus AI

    ## Overview

    |  |  |
    | - | - |
    | HQ/Foundation       |  |
    | Funding             |  |
    | Investors           |  |
    | Key People          |  |

    - ...

    ## Tech & Services

    - ...

    ## Key Competency

    - ...

    ```

    fill out the form based on web search result

    - make sure every contents are grounded by the search result
    - put the result within code block for ease of copy-paste

    Verbalize your think or plan in step-by-step manner prior to give an answer

    ---

### Deep Research 활용

- Deep Research란?
  - LLM이 사용자의 요청을 분석하고 계획을 수립하여 지속적인 연구를 수행
  - Internal
    - ReAct(Reasoning + Action) / CoT (Chain Of Thought)
    - 사용자 요청 분석 및 계획 / 정보 수집 / (정보 이해) / ...
    - 사용자가 정확한 질의를 위해 필요한 Reasoning을 LLM이 대신 수행하고 결과에 대한 1차 평가를 수행하여 결과물이 사용자의 요청에 부합하다고 판단될 때까지 수행하는 방식
  - 장점
    - 질의나 요청이 암시적이고 불분명하더라도 준수한 수준의 답변 결과를 얻을 수 있음
  - 단점
    - 시간이 많이 걸림 (경우에 따라 5 ~ 10분 소요)
  - (시연) Perplexity, Grok 및 Gemini 동일 쿼리에 대한 결과 비교

### Deep Research 고급 (짜깁기 & Query Augmentation)

- Deep Research는 주어진 요청에 대해 깊이 있는 연구를 수행하여 수 페이지 분량의 보고서를 제공하는 특징
- 다만 최종 결과에 정작 필요한 내용이 누락되거나 만족스럽지 못한 결과를 얻을 경우가 있음
- 이런 문제점을 Query를 다듬어서 보완할 수 있음

#### 짜깁기

- Grok / Perplexity에 Deep Search 결과를 하나의 Template으로 병합
- 1M Token 지원 모델
  - Grok3
  - Gemini
- 시연
  - (복수의 AI 서비스에..) Deep Search 요청 및 수집
  - 수집된 결과 복붙하기
  - Template 넣고 채워달라고 요청하기

#### Query Augmentation

- RA Instruction Prompt

  ```markdown
  I am seeking comprehensive research on "LLM Tech Trend". Please conduct an in-depth investigation and provide a detailed report that includes the following:

  A clear overview, including its definition, history, and significance.
  Current trends, developments, or advancements in the field.
  Key stakeholders, experts, organizations, or communities involved.
  Relevant data, statistics, or case studies that highlight its impact or scope.
  Challenges, controversies, or debates surrounding the subject.
  Potential future implications or predictions over the next 5–10 years.
  A curated list of credible sources, including academic papers, articles, books, or reports, for further reading.
  Ensure the information is up-to-date, accurate, and sourced from reputable and authoritative references. Where applicable, include insights from web searches, posts on platforms like X, and any relevant visual data (e.g., charts, graphs, or infographics). If any information is speculative or opinion-based, clearly label it as such. Please present the findings in a well-organized, easy-to-read format suitable for both experts and non-experts.
  ```

- Meta Prompt

  ```markdown
  Given Topic: Omelet, AI Startup에 대한 심층 연구
  I need you to create a customized research prompt for an AI research assistant to conduct in-depth research on topic. The generated prompt should be tailored to the specific nature and characteristics of the topic, ensuring the research approach is appropriate and comprehensive. To create this prompt, follow these steps:

  Analyze the Topic: Determine the category or domain of topic (e.g., scientific, technological, historical, social, economic, political, cultural, etc.) and identify its key characteristics (e.g., is it emerging, well-established, controversial, interdisciplinary, data-driven, theoretical, etc.).
  Define Research Objectives: Based on the topic’s domain and characteristics, define the most relevant research objectives. For example:
  For emerging technologies, emphasize current advancements, future potential, and key players.
  For historical topics, focus on timelines, primary sources, and historiographical debates.
  For social issues, highlight current trends, stakeholder perspectives, and societal impact.
  For scientific topics, prioritize data, experiments, and peer-reviewed studies.
  Identify Key Components: Include components in the prompt that are most relevant to the topic, such as:
  Historical context or timeline (if applicable).
  Current trends, innovations, or developments.
  Key stakeholders, experts, organizations, or communities.
  Data, statistics, case studies, or experiments.
  Challenges, controversies, or ethical considerations.
  Future implications or predictions.
  Recommended sources (e.g., academic papers, industry reports, primary sources, posts on platforms like X, etc.).
  Customize Source Requirements: Specify the types of sources most appropriate for the topic (e.g., peer-reviewed journals for scientific topics, archival documents for historical topics, policy papers for political topics, etc.).
  Adapt Tone and Audience: Ensure the generated prompt specifies a tone and format suitable for the intended audience (e.g., accessible for non-experts, technical for specialists, etc.).
  Incorporate Flexibility: Allow room for the research assistant to include additional relevant insights, such as visual data (charts, graphs, infographics), expert opinions, or speculative analysis (clearly labeled as such).
  Once you have analyzed the topic and determined the appropriate research approach, generate a clear, concise, and well-structured research prompt that the AI research assistant can use to produce a comprehensive report. Ensure the prompt is actionable, specific to the topic, and designed to yield thorough and credible research. Present the generated research prompt as the final output of this request.
  ```

## Claude & MCP 기반 통합 소개 (Optional)

### MCP란?

- Model Context Protocol로 AI Agent에 Tool을 통합하기 위한 표준 기술

참고 사이트: <https://smithery.ai/>

- 시연.1 Claude Desktop에 MCP 설치를 통해 실시간 웹 검색 추가
  - Claude에 MCP 설치 시연
  - Claude에서 웹 검색 사용 시연

- 시연.2 Code Editor (Cusor 활용)
  - Code Editor에 MCP를 설치
  - 검색 및 파일 등 다양한 RAG 기반 Agent Flow 사용
