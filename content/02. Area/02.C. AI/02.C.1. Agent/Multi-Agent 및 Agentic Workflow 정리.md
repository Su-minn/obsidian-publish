---
created_date: 2024-07-14 11:29
tags:
  - AI
  - agent
  - autogen
  - crew
  - solvit
aliases:
---
# Context
- [[EP4. Multi-Agent 시나리오 개요]]를 작성하는 과정에서,
  Multi-agent 및 Agentic Design Pattern에 대해서 정리하였다
요
# Content
## Multi-Agent 분류 (Ver. 24.07.14) by ChatDev(칭화대 Lab)
- Multi-agent system은 현재 **'사람의 외부 지시 하에서 구체적인 목표를 달성하도록 디자인되었는가'** 에 따라 2가지로 분류된다
	- 'specific task goals under external human instructions'
- A) Task-solving-oriented systems
- B) Social-simulation-oriented systems
### A) Task-solving-oriented systems
#### Task-solving-oriented systems 참고 이미지
![[Pasted image 20240714115340.png]]
![[Pasted image 20240714115323.png]]
- Task-solving-oriented systems(과제 해결 중심 다중 에이전트 시스템)은 자율 에이전트(autonomous agents)들이 협력하여 복잡한 문제(complex problems)를 해결하는 시스템이다
#### Task-solving-oriented systems 분야의 최신 연구 분야 (24.07.14)
- 이 분야의 최신 연구는 주로 세 가지 주요 영역에 중점을 둔다
- A-1) 에이전트 간의 의사소통을 촉진하는 것 ([[Multi-Agent 및 Agentic Workflow 정리#A-1) Communication|Communication]])
	- facilitating communication among agents
- A-2) 상호작용을 위한 효과적인 조직 구조를 설계하는 것 ([[Multi-Agent 및 Agentic Workflow 정리#A-2) Organization|Organization]])
	- designing effective organizational structures for interaction
- A-3) 시간이 지남에 따라 에이전트들이 어떻게 함께 발전하는지를 탐구하는 것 ([[Multi-Agent 및 Agentic Workflow 정리#A-3) Evolution|Evolution, Evolvement]])
	- exploring how agents co-evolve over time
### B) Social-simulation-oriented systems ([[Multi-Agent 및 Agentic Workflow 정리#B) Simulation|Simulation]])
#### Social-simulation-oriented systems 참고 이미지
![[Pasted image 20240714115404.png]]
![[Pasted image 20240714115416.png]]
- 사회 시뮬레이션 중심 다중 에이전트 시스템(Social Simulation)은 에이전트들의 사회적 행동을 모델링하고 분석하는 데 중점을 둔다
- 이는 인간의 역학에 대한 통찰을 제공하며, 사회 현상을 분석하거나 예측하는 능력을 향상시킨다
### A-1) Communication
>facilitating agent communication
- Task-solving-oriented systems(과업 지향적 에이전트 통신)은
  일반적으로 프로토콜 설계(protocol design)와
  지식 강화 커뮤니케이션(knowledge-augmented communication)에 중점을 둔다
- 이를 통해 보다 효과적인 정보 상호작용(information interaction)과 합의 도출(consensus building)을 보장한다
#### 출처
- [Chap 1. Communication | ChatDev Ebook](https://thinkwee.top/multiagent_ebook/communication.html)
### A-2) Organization
>organizing agents effectively
### A-3) Evolution
>growing capabilities over time
### B) Simulation
>simulating societal dynamics

## Agent(Agentic) Design Pattern by Andrew Ng
### AI Agent(ic) Workflow
>Andrew Ng(앤드류 응) 교수님이 언급하는 Agentic design pattern
>에이전트 워크플로우는 LLM에 여러 번 프롬프트를 주어,
>단계별로 더 높은 품질의 출력을 만들 수 있는 기회를 제공한다
>
>크게, 4가지의 디자인 패턴이 있다
> (1) Reflection
> (2) Tool Use
> (3) Planning
> (4) Multi-agent Collaboration
- Andrew Ng 교수님은 Agent냐 아니냐에 대한 이분법적인 논쟁은 큰 의미가 없으며,
  Agentic 이라는 형용사로 광범위하게 open하여 바라볼 것을 권장한다
#### Andrew Ng의 AI Agent Workflow 설명
- AI 에이전트 워크플로가 올해 엄청난 AI 발전을 이끌 것이라고 생각합니다.
- 아마도 다음 세대의 기초 모델보다 더 큰 영향을 미칠 것입니다.
- 이는 중요한 트렌드이며, AI 분야에서 일하는 모든 분들이 주목해야 할 점입니다.

- 오늘날 우리는 대부분 LLM을 제로샷(zero-shot) 모드에서 사용하고 있습니다.
- 모델이 작업을 수정하지 않고 마지막 출력 토큰을 하나씩 생성하도록 프롬프트하는 방식입니다.
- 이는 마치 누군가에게 백스페이스 없이 처음부터 끝까지 에세이를 작성하게 하고, 높은 품질의 결과를 기대하는 것과 비슷합니다.
- 이 어려운 과제에서도 LLM은 놀라울 정도로 잘 해내고 있습니다!

- 그러나 에이전트 워크플로우를 사용하면 LLM에게 문서를 여러 번 반복하여 작업하도록 요청할 수 있습니다.
- 예를 들어, 다음과 같은 일련의 단계를 거칠 수 있습니다:
	1. 개요 계획하기
	2. 더 많은 정보를 수집하기 위해 필요한 웹 검색이 있는지 결정하기
	3. 초안 작성하기
	4. 초안을 검토하여 정당화되지 않은 주장이나 불필요한 정보 찾기
	5. 발견된 약점을 고려하여 초안 수정하기 등등.
- 이러한 반복적인 과정은 대부분의 인간 작가들이 좋은 글을 쓰는 데 필수적입니다.
- AI에서도 이런 반복적인 워크플로우는 한 번에 쓰는 것보다 훨씬 더 나은 결과를 냅니다.
- (LLM이 최종 출력을 직접 생성하는 대신, 에이전트 워크플로우는 LLM에 여러 번 프롬프트를 주어 단계별로 더 높은 품질의 출력을 만들 수 있는 기회를 제공합니다.)

- 최근 Devin의 화려한 데모가 소셜 미디어에서 큰 화제를 모았습니다.
- 우리 팀은 코드를 작성하는 AI의 발전을 면밀히 지켜보고 있습니다.
- 우리는 여러 연구팀의 결과를 분석했으며, 특히 널리 사용되는 HumanEval 코딩 벤치마크에서 알고리즘의 성능에 초점을 맞췄습니다.
- 아래 도표에서 우리의 발견을 확인할 수 있습니다.
![[Pasted image 20240714151313.png]]
- GPT-3.5(제로샷)는 48.1%의 정확도를 보였습니다.
- GPT-4(제로샷)는 67.0%로 더 나은 성능을 보입니다.
- 그러나 GPT-3.5에서 GPT-4로의 개선은 반복적인 에이전트 워크플로우를 도입함으로써 얻는 개선에 비하면 미미합니다.
- 실제로 에이전트 루프에 포함된 GPT-3.5는 최대 95.1%의 성능을 달성합니다.

- 오픈소스 에이전트 도구와 에이전트에 관한 학술 문헌이 급증하고 있어, 이는 흥미진진한 시기이기도 하지만 혼란스러운 시기이기도 합니다.
- 이러한 작업을 이해하는 데 도움을 드리고자 에이전트 구축을 위한 설계 패턴을 분류하는 프레임워크를 공유하고자 합니다.
- 제 팀 AI Fund는 이러한 패턴을 많은 애플리케이션에서 성공적으로 사용하고 있으며, 여러분에게도 유용할 것이라 믿습니다.

- **Reflection**: LLM이 자신의 작업을 검토하고 개선 방법을 찾아냅니다.
- **Tool Use**: LLM이 정보를 수집하거나, 행동을 취하거나, 데이터를 처리하는 데 도움을 주는 웹 검색, 코드 실행 등의 도구를 사용합니다.
- **Planning**: LLM이 목표를 달성하기 위해 다단계 계획을 세우고 실행합니다(예: 에세이 개요 작성, 온라인 조사, 초안 작성 등).
- **Multi-agent collaboration**: 여러 AI 에이전트가 함께 작업하여 작업을 나누고 아이디어를 논의하고 토론하여 단일 에이전트보다 더 나은 해결책을 도출합니다.

- 다음 주에는 이러한 디자인 패턴에 대해 더 자세히 설명하고 각 패턴에 대한 추천 읽을거리를 제공하겠습니다.

### Reflection
> Large language models can become more effective agents by reflecting on their own behavior.
> 
> reflection : 비판적 피드백을 제공하는 단계를 자동화하여,
> 모델이 자체 출력을 자동으로 비판하고 응답을 개선하는 디자인 패턴
![[Pasted image 20240714152824.png]]
#### Andrew Ng 교수님 설명 내용
- 지난주에 저는 올해 큰 진전을 이끌 것으로 믿는 AI 에이전트 워크플로우의 네 가지 설계 패턴, 즉 반성(Reflection), 도구 사용(Tool Use), 계획 수립(Planning), 다중 에이전트 협업(Multi-agent Collaboration)에 대해 설명했습니다.
- LLM이 최종 출력을 직접 생성하는 대신, 에이전트 워크플로우는 LLM에 여러 번 프롬프트를 주어 단계별로 더 높은 품질의 출력을 만들 기회를 제공합니다.
- 이번 편지에서는 반성(reflection)에 대해 논의하고자 합니다.
- 구현하기 상대적으로 빠른 이 설계 패턴이 놀라운 성능 향상을 가져오는 것을 보았습니다.

- 여러분은 ChatGPT/Claude/Gemini에 프롬프트를 주고, 만족스럽지 않은 출력을 받은 뒤, LLM이 응답을 개선하도록 비판적인 피드백을 제공하고, 그 후 더 나은 응답을 받는 경험을 해보셨을 것입니다.
- 만약 이 **비판적 피드백을 제공하는 단계를 자동화하여 모델이 자체 출력을 자동으로 비판하고 응답을 개선**하도록 한다면 어떨까요?
- 이것이 반성(reflection)의 핵심입니다.

- LLM에게 코드 작성을 요청하는 작업을 예로 들어보겠습니다.
- 우리는 LLM에게 어떤 작업 X를 수행하기 위한 원하는 코드를 직접 생성하도록 프롬프트할 수 있습니다.
- 그 후, 다음과 같이 자체 출력을 반성하도록 프롬프트할 수 있습니다:

>다음은 작업 X를 위한 코드입니다 : {이전에 생성된 코드}
 이 코드를 정확성, 스타일, 효율성 측면에서 신중하게 검토하고,
 개선할 수 있는 방법에 대한 건설적인 비판을 제공해 주세요.

- 이러한 프롬프트는 LLM이 문제를 발견하고 건설적인 제안을 도출하게 할 수 있습니다.
- 다음으로, (i) {이전에 생성된 코드}와 건설적인 피드백(reflection 결과)을 포함한 문맥을 제공하고,
  (ii) 피드백을 사용하여 코드를 다시 작성하도록 요청할 수 있습니다.
- 이를 통해 더 나은 응답을 얻을 수 있습니다.
- 비판/재작성 과정을 반복하면 추가적인 개선이 이루어질 수 있습니다. 이러한 자기 반성 과정은 LLM이 코드 생성, 텍스트 작성, 질문 답변 등 다양한 작업에서 격차를 발견하고 출력을 개선할 수 있게 합니다.

- 그리고 우리는 LLM에게 자신의 출력을 평가하는 데 도움이 되는 도구를 제공함으로써 자기 반성을 넘어설 수 있습니다.
- 예를 들어, 작성된 코드를 몇 가지 유닛 테스트에 통과시켜 테스트 케이스에서 올바른 결과를 생성하는지 확인하거나, 텍스트 출력을 이중 확인하기 위해 웹을 검색할 수 있습니다.
- 그런 다음 LLM은 발견된 오류를 반성하고 개선 아이디어를 도출할 수 있습니다.

- 더 나아가, 다중 에이전트(multi agent) 프레임워크를 사용하여 반영을 구현할 수 있습니다.
- 저는 좋은 출력을 생성하도록 프롬프트된 에이전트와 첫 번째 에이전트의 출력을 건설적으로 비판하도록 프롬프트된 두 번째 에이전트를 만들어 서로 토론하게 하는 것이 편리하다는 것을 발견했습니다.
- 두 에이전트 간의 토론은 개선된 응답으로 이어집니다.

- 반성(reflection)은 비교적 기본적인 유형의 에이전트 워크플로이지만, 몇 가지 경우에 응용 프로그램의 결과를 크게 개선하는 것을 보고 매우 기뻤습니다.
- 여러분도 자신의 작업에 반영을 시도해 보길 바랍니다.

- 반영에 대해 더 알고 싶다면 다음 논문들을 추천합니다:
	- “Self-Refine: Iterative Refinement with Self-Feedback,” Madaan et al. (2023)
	- “Reflexion: Language Agents with Verbal Reinforcement Learning,” Shinn et al. (2023)
	- “CRITIC: Large Language Models Can Self-Correct with Tool-Interactive Critiquing,” Gou et al. (2024)
#### 원본
- [Agentic Design Patterns Part 2, Reflection | DeepLearning.AI - The BATCH](https://www.deeplearning.ai/the-batch/agentic-design-patterns-part-2-reflection/)
#### 예시
- [translation-agent by Andrew Ng | Github](https://github.com/andrewyng/translation-agent)
### Tool Use
> How large language models can act as agents by taking advantage of external tools for search, code execution, productivity, ad infinitum
> 
> Tool Use : LLM이 정보 수집, 행동 수행, 또는 데이터 조작을 위해 호출할 수 있는 함수를 제공받는
> AI 에이전트 워크플로우의 핵심 디자인 패턴
![[Pasted image 20240714152903.png]]
#### Andrew Ng 교수님 설명 내용
- 도구 사용(Tool Use)은 **LLM이 정보 수집, 행동 수행, 또는 데이터 조작을 위해 호출할 수 있는 함수를 제공받는 AI 에이전트 워크플로우의 핵심 설계 패턴**입니다.
- 여러분은 웹 검색을 수행하거나 코드를 실행할 수 있는 LLM 기반 시스템에 익숙할 수 있습니다.
- 일부 대규모 소비자 대상 LLM은 이미 이러한 기능을 포함하고 있습니다.
- 하지만 도구 사용은 이러한 예시를 훨씬 뛰어넘습니다.

- 온라인 LLM 기반 채팅 시스템에 "리뷰어들에 따르면 가장 좋은 커피 메이커는 무엇인가요?"라고 프롬프트를 주면, 시스템은 웹 검색을 수행하고 하나 이상의 웹 페이지를 다운로드하여 맥락을 얻기로 결정할 수 있습니다.
- 초기에 LLM 개발자들은 사전 훈련된 트랜스포머에만 의존하여 출력 토큰을 생성하는 것은 제한적이며, LLM에 웹 검색 도구를 제공하면 훨씬 더 많은 일을 할 수 있다는 것을 깨달았습니다.
- 이러한 도구를 사용하면 LLM은 미세 조정되거나 프롬프트되어(아마도 few-shot 프롬프팅을 통해) {tool: web-search, query: "커피 메이커 리뷰"}와 같은 특별한 문자열을 생성하여 검색 엔진 호출을 요청합니다. (정확한 문자열 형식은 구현에 따라 다릅니다.)
- 그 후 후처리 단계에서 이러한 문자열을 찾아 관련 매개변수로 웹 검색 함수를 호출하고, 결과를 추가 입력 맥락으로 LLM에 다시 전달하여 추가 처리를 합니다.

- 마찬가지로, "100달러를 연복리 7%로 12년 동안 투자하면 최종적으로 얼마가 되나요?"라고 물으면, LLM은 트랜스포머 네트워크를 사용하여 직접 답변을 생성하려고 하는 대신(이는 올바른 답변을 얻기 어려울 수 있음) 코드 실행 도구를 사용하여 100 * (1+0.07)\*\*12를 계산하는 Python 명령을 실행할 수 있습니다. LLM은 이런 식의 문자열을 생성할 수 있습니다
  : {tool: python-interpreter, code: "100 * (1+0.07)\*\*12"}.

- 하지만 에이전트 워크플로우에서의 도구 사용은 이제 훨씬 더 나아갑니다.
- 개발자들은 다양한 소스(웹, 위키피디아, arXiv 등)를 검색하고, 생산성 도구(이메일 보내기, 캘린더 항목 읽기/쓰기 등)와 인터페이스하며, 이미지를 생성하거나 해석하는 등 다양한 기능을 위해 함수를 사용하고 있습니다.
- 우리는 많은 함수에 대한 자세한 설명을 제공하는 컨텍스트를 사용하여 LLM에 프롬프트를 줄 수 있습니다.
- 이러한 설명에는 함수가 수행하는 작업에 대한 텍스트 설명과 함수가 예상하는 인수에 대한 세부 정보가 포함될 수 있습니다.
- 그리고 우리는 LLM이 작업을 수행하기 위해 자동으로 올바른 함수를 선택할 것으로 기대합니다.
- 더 나아가, LLM이 수백 개의 도구에 접근할 수 있는 시스템이 구축되고 있습니다.
- 이러한 환경에서는 모든 함수를 LLM 컨텍스트에 넣기에는 너무 많을 수 있으므로, 현재 처리 단계에서 가장 관련성 있는 하위 집합을 선택하기 위해 휴리스틱을 사용할 수 있습니다.
- Gorilla 논문에서 설명된 이 기술은 컨텍스트로 포함하기에 텍스트가 너무 많은 경우, 검색 증강 생성(RAG) 시스템이 텍스트의 하위 집합을 선택하기 위한 휴리스틱을 제공하는 방식을 연상시킵니다.
	- (= 검색 증강 생성(RAG) 시스템과 유사)

- LLaVa, GPT-4V, Gemini와 같은 대규모 다중 모달 모델(LMM)이 널리 사용되기 전, LLM의 초기 역사에서 LLM은 이미지를 직접 처리할 수 없었기 때문에 도구 사용에 대한 많은 연구가 컴퓨터 비전 커뮤니티에 의해 수행되었습니다.
- 당시 LLM 기반 시스템이 이미지를 조작할 수 있는 유일한 방법은 객체 인식이나 다른 기능을 수행하는 함수를 호출하는 것이었습니다.
- 그 이후로 도구 사용 관행이 폭발적으로 증가했습니다.
- 작년 중반에 출시된 GPT-4의 함수 호출 기능은 범용 도구 사용을 향한 중요한 단계였습니다.
- 그 이후로 점점 더 많은 LLM이 도구 사용에 능숙하도록 개발되고 있습니다.

- 도구 사용에 대해 더 자세히 알고 싶다면 다음을 추천합니다:
	- Gorilla: Large Language Model Connected with Massive APIs, Patil et al. (2023)
	- MM-REACT: Prompting ChatGPT for Multimodal Reasoning and Action, Yang et al. (2023)
	- Efficient Tool Use with Chain-of-Abstraction Reasoning, Gao et al. (2024)

- 도구 사용(Tool Use)과 지난주에 언급한 성찰(Reflection)은 모두 내 애플리케이션에서 꽤 안정적으로 작동시킬 수 있는 설계 패턴입니다
	- 둘 다 배워볼 만한 가치가 있는 기능입니다.
- 앞으로 계획 및 다중 에이전트 협업 설계 패턴에 대해 설명할 예정입니다.
- 이들은 AI 에이전트가 훨씬 더 많은 작업을 수행할 수 있게 해주지만, 덜 성숙하고 예측하기 어려운 - 그러나 매우 흥미로운 - 기술입니다.

#### 원본
- [Agentic Design Patterns Part 3, Tool Use | DeepLearning.AI - The BATCH](https://www.deeplearning.ai/the-batch/agentic-design-patterns-part-3-tool-use/)
- [Tool Use Tweet by Andrew Ng | X](https://x.com/AndrewYNg/status/1775951610059141147)
	- 동일한 내용의 Tweet
### Planning
>Large language models can drive powerful agents to execute complex tasks if you ask them to plan the steps before they act.
>
>Planning : 더 큰 작업을 수행하기 위해 어떤 순서로 단계를 실행할지 자율적으로 결정하는
>중요한 Agentic 디자인 패턴
![[Pasted image 20240714153141.png]]
#### Andrew Ng 교수님 설명 내용
- 계획(Planning)은 대규모 언어 모델(LLM)을 사용하여 **더 큰 작업을 수행하기 위해 어떤 순서로 단계를 실행할지 자율적으로 결정하는 중요한 에이전트적 AI 설계 패턴**입니다.
- 예를 들어, 에이전트에게 특정 주제에 대해 온라인 조사를 하라고 하면, LLM을 사용하여 목표를 작은 하위 작업으로 나눌 수 있습니다.
- 예를 들어, 특정 하위 주제를 조사하고, 발견한 내용을 종합하고, 보고서를 작성하는 식입니다.
- 많은 사람들이 ChatGPT가 출시된 직후, ChatGPT를 사용해 보고 AI가 할 수 있는 일에 대한 기대를 훨씬 초과하는 것을 보고 놀랐던 "ChatGPT 순간"을 경험했습니다.
- 아직 비슷한 "AI 에이전트적 순간"을 경험하지 못했다면, 곧 경험하게 되길 바랍니다.

- 저는 몇 달 전, 다양한 온라인 검색 도구에 접근할 수 있는 연구 에이전트를 시연할 때 그런 순간을 경험했습니다.
- 이 에이전트를 여러 번 개인적으로 테스트했을 때, 항상 웹 검색 도구를 사용하여 정보를 수집하고 요약을 작성했습니다.
- 그러나 라이브 데모 중에 웹 검색 API가 예상치 못한 속도 제한 오류를 반환했습니다.
- 저는 데모가 공개적으로 실패할 것이라고 생각했고, 다음에 무슨 일이 일어날지 두려웠습니다.
- 놀랍게도, 에이전트는 재빠르게 Wikipedia 검색 도구로 전환하여 웹 검색 대신 Wikipedia를 사용하여 작업을 완료했습니다.
- 이것은 저에게 AI 에이전트적 순간의 놀라움이었습니다.
- 아직 이런 순간을 경험하지 못한 많은 사람들이 앞으로 몇 달 안에 경험하게 될 것이라고 생각합니다.
- 에이전트가 예상치 못한 방식으로 자율적으로 결정을 내리고 성공하는 것을 보는 것은 정말 아름다운 일입니다!
- 많은 작업은 한 단계나 하나의 도구 호출로 완료할 수 없지만, 에이전트는 어떤 단계를 밟을지 결정할 수 있습니다.
- 예를 들어, HuggingGPT 논문에서 단순화된 예를 들면, 소년의 사진을 보고 같은 포즈의 소녀의 그림을 그리도록 에이전트에게 요청하면, 작업은 두 가지 단계로 나눌 수 있습니다:
	- (i) 소년의 사진에서 포즈를 감지하고
	- (ii) 감지된 포즈로 소녀의 그림을 렌더링합니다.
- LLM은 "{tool: pose-detection, input: image.jpg, output: temp1} {tool: pose-to-image, input: temp1, output: final.jpg}"와 같은 문자열을 출력하여 계획을 지정하도록 미세 조정되거나 프롬프트될 수 있습니다.
- 이러한 구조화된 출력은 두 단계를 지정하며, 소프트웨어가 포즈 감지 도구를 호출한 후 포즈-이미지 도구를 호출하여 작업을 완료하도록 트리거합니다. (이 예시는 설명을 위한 것이며, HuggingGPT는 다른 형식을 사용합니다.)
- 물론, 많은 에이전트적 워크플로우는 계획(Planning)이 필요하지 않습니다.
- 예를 들어, 에이전트가 고정된 횟수만큼 출력을 성찰(reflection)하고 개선하도록 할 수 있습니다.
- 이 경우, 에이전트가 취하는 단계의 순서는 고정되고 결정적입니다.
- 그러나 복잡한 작업에서 사전에 작업을 일련의 단계로 나눌 수 없는 경우, 계획은 에이전트가 동적으로 어떤 단계를 밟을지 결정할 수 있게 합니다.

- 한편으로, 계획은 매우 강력한 기능입니다.
- 다른 한편으로는, 결과를 예측하기 어렵게 만듭니다.
- 제 경험상, 성찰(reflection)과 도구 사용(tool use)의 에이전트적 설계 패턴은 신뢰할 수 있게 작동하고 애플리케이션의 성능을 향상시킬 수 있지만, 계획은 덜 성숙한 기술이며 사전에 무엇을 할지 예측하기 어렵습니다.
- 그러나 이 분야는 빠르게 발전하고 있으며, 계획 능력이 빠르게 개선될 것이라고 확신합니다.

- LLM을 사용한 계획에 대해 더 알고 싶다면, 다음을 추천합니다:
	- Chain-of-Thought Prompting Elicits Reasoning in Large Language Models, Wei et al. (2022)
	- HuggingGPT: Solving AI Tasks with ChatGPT and its Friends in Hugging Face, Shen et al. (2023)
	- Understanding the planning of LLM agents: A survey, by Huang et al. (2024)

#### 원본
- [Agentic Design Patterns Part 4, Planning | DeepLearning.AI - The BATCH](https://www.deeplearning.ai/the-batch/agentic-design-patterns-part-4-planning/)
### Multi-agent collaboration
> Prompting an LLM to play different roles for different parts of a complex task summons a team of AI agents that can do the job more effectively.
> 
> Multi-agent collaboration : 복잡한 작업을 소프트웨어 엔지니어, 디자이너, QA(품질 보증) 엔지니어 등 다양한 역할이 수행할 하위 작업으로 나누고, 서로 다른 에이전트가 각각의 하위 작업을 수행하도록 함
![[Pasted image 20240714153436.png]]
#### Andrew Ng 교수님 설명 내용
- 다중 에이전트 협업이 AI 에이전트 설계의 핵심 패턴으로 부상했습니다.
- 소프트웨어 작성과 같은 **복잡한 작업이 주어졌을 때, 다중 에이전트 접근 방식은 이 작업을 소프트웨어 엔지니어, 제품 관리자, 디자이너, QA(품질 보증) 엔지니어 등 다양한 역할이 수행할 하위 작업으로 나누고, 서로 다른 에이전트가 각각의 하위 작업을 수행하도록 합니다.**
- 서로 다른 에이전트는 하나의 LLM(또는 원한다면 여러 LLM)에 다른 작업을 수행하도록 프롬프트를 주어 구축될 수 있습니다.
- 예를 들어, 소프트웨어 엔지니어 에이전트를 만들기 위해 LLM에 "당신은 명확하고 효율적인 코드를 작성하는 전문가입니다. 다음 작업을 수행하는 코드를 작성하세요..."라고 프롬프트를 줄 수 있습니다.

- 동일한 LLM에 여러 번 호출을 하면서 여러 에이전트를 사용하는 프로그래밍 추상화를 적용하는 것이 직관에 반할 수 있습니다.
	- 즉, 같은 LLM을 여러번 호출하면서도 여러 에이전트를 사용하는 프로그래밍 추상을 적용하는 것은 역설적으로 보일 수도 있습니다.

- 이에 대해 몇 가지 이유를 제시하고 싶습니다:

- 1) 효과가 있습니다!
	- 많은 팀들이 이 방법으로 좋은 결과를 얻고 있으며, 결과만큼 중요한 것은 없습니다!
	- 또한, AutoGen 논문에서 인용된 것처럼 에이전트를 여러 개 사용하는 것이 단일 에이전트보다 더 나은 성능을 보여주는 연구 결과도 있습니다.
- 2) 오늘날 일부 LLM이 매우 긴 입력 컨텍스트를 받아들일 수 있지만(예: Gemini 1.5 Pro는 1백만 토큰 수용), 긴 복잡한 입력을 진정으로 이해하는 능력은 아직 혼재되어 있습니다.
	- LLM이 한 번에 한 가지에 집중하도록 프롬프트를 주는 에이전트적 워크플로우는 더 나은 성능을 낼 수 있습니다.
	- LLM에게 소프트웨어 엔지니어 역할을 할 때를 알려줌으로써, 그 하위 작업에서 중요한 것이 무엇인지도 지정할 수 있습니다.
	- 예를 들어, 위의 프롬프트는 확장성이 높고 매우 안전한 코드가 아닌 명확하고 효율적인 코드를 강조했습니다.
	- 전체 작업을 하위 작업으로 분해함으로써 하위 작업을 더 잘 최적화할 수 있습니다.
- 3) 아마도 가장 중요한 점은, 다중 에이전트 설계 패턴이 개발자인 우리에게 복잡한 작업을 하위 작업으로 분해하는 프레임워크를 제공한다는 것입니다.
	- 단일 CPU에서 실행될 코드를 작성할 때, 우리는 종종 프로그램을 여러 프로세스나 스레드로 나눕니다.
	- 이는 웹 브라우저 구현과 같은 작업을 코딩하기 쉬운 하위 작업으로 분해할 수 있게 해주는 유용한 추상화입니다.
	- 저는 다중 에이전트 역할을 통해 생각하는 것이 유용한 추상화라고 생각합니다.

- 많은 회사에서 관리자들은 일상적으로 어떤 역할을 고용할지 결정하고, 대규모 소프트웨어 작성이나 연구 보고서 준비와 같은 복잡한 프로젝트를 어떻게 나누어 다양한 전문성을 가진 직원들에게 할당할지 결정합니다.
- 다중 에이전트 사용은 이와 유사합니다.
- 각 에이전트는 자체 워크플로우를 구현하고, 자체 메모리(에이전트 기술에서 빠르게 발전하는 영역 - 에이전트가 앞으로의 상호작용을 더 잘 수행하기 위해 과거 상호작용을 충분히 기억할 수 있는 방법은?)를 가지며, 다른 에이전트에게 도움을 요청할 수 있습니다. 
- 에이전트 자체도 계획 수립과 도구 사용에 참여할 수 있습니다
-  이는 매우 복잡한 워크플로우로 이어질 수 있는 LLM 호출과 에이전트 간 메시지 전달의 혼란을 초래합니다.

- 사람을 관리하는 것은 어렵지만, 그것은 우리에게 AI 에이전트를 "고용"하고 작업을 할당하는 방법에 대한 정신적 프레임워크(mental model)를 제공하는 충분히 친숙한 아이디어입니다.
- 다행히도 AI 에이전트를 잘못 관리하는 것의 피해는 인간을 잘못 관리하는 것보다 훨씬 적습니다!

- AutoGen, Crew AI, LangGraph와 같은 emerging 프레임워크는 문제에 대한 다중 에이전트 솔루션을 구축하는 풍부한 방법을 제공합니다.
- 재미있는 다중 에이전트 시스템을 사용해보고 싶다면 ChatDev도 확인해보세요.
- 이는 가상 소프트웨어 회사를 운영하는 일련의 에이전트를 구현한 오픈 소스입니다.
- 그들의 GitHub 저장소를 확인하고 직접 저장소를 클론하여 시스템을 실행해보시기를 권장합니다.
- 항상 원하는 결과를 내지 않을 수 있지만, 그 성능에 놀라실 수 있을 것입니다!

- 계획(Planning)과 같은 설계 패턴처럼, 저는 다중 에이전트 협업의 출력 품질을 예측하기 어렵다고 생각합니다.
- 반성(Reflection)과 도구 사용(Tool Use)이라는 더 성숙한 패턴들이 더 신뢰할 만합니다.
- 여러분이 이러한 에이전트 설계 패턴을 즐겁게 사용해보시고 놀라운 결과를 얻으시기를 바랍니다!

- 더 자세히 알고 싶다면 다음을 추천합니다:
	- Communicative Agents for Software Development, Qian et al. (2023) (ChatDev 논문)
	- AutoGen: Enabling Next-Gen LLM Applications via Multi-Agent Conversation, Wu et al. (2023)
	- MetaGPT: Meta Programming for A Multi-Agent Collaborative Framework, Hong et al. (2023)
#### 원본
- [Agentic Design Patterns Part 5, Multi-agent collaboration | DeepLearning.AI - The BATCH](https://www.deeplearning.ai/the-batch/agentic-design-patterns-part-5-multi-agent-collaboration/)

## Multi Agents 구현 예시
### Multi Agents 기반 Opensource
#### Software engineer
- [Devika | Github](https://github.com/stitionai/devika/blob/main/docs/architecture/ARCHITECTURE.md#agents)
	- 여러 agents로 구성되어있음
- [OpenDevin | Github](https://docs.all-hands.dev/modules/usage/architecture)
	- AgentHub를 통해 여러 Agent로 구성되어있음
- [SWE-Agent | Github](https://princeton-nlp.github.io/SWE-agent/reference/agent/)
	- 단일 Agent 기반인지, Multi인지, 자율 설정인지 아직 파악이 안됨
#### Simulation
- 위의 Multi Agents 동향 글 참고하기
### 그 외 다양한 AI Agents List
- [Awesome AI Agents | Github](https://github.com/e2b-dev/awesome-ai-agents)


# 출처 (참고 문헌)
- [Comprehensive Outline of Large Language Model-based Multi-Agent Research by ChatDev](https://thinkwee.top/multiagent_ebook/#more-works)
	- 칭화대의 ChatDev Group에서 publishing한 자료
- Andrew Ng의 X
- [Agentic Design Patterns by Andrew Ng | Deeplearning.AI - The BATCH](https://www.deeplearning.ai/the-batch/how-agents-can-improve-llm-performance/)

# 연결 문서
- [[EP4. Multi-Agent 시나리오 개요]]
	- 위의 분류 중, 직관적이고 핵심적인 내용만 선별하여 반영 예정
- [[다중(멀티) 에이전트(Multi Agent) 구조]]