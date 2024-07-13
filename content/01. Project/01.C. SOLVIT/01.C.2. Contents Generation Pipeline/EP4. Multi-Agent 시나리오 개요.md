---
created_date: 2024-07-13 20:28
tags:
  - solvit
  - crew
aliases:
---
# Content
## 반영하고자하는 관점
### A) 스토리텔링 구조 관점
#### 1) Problem-Solution 구조를 명확하게한다
- 1-1) multi-agent가 왜 적합한 solution이 될 수 있는지 납득이 되어야한다
	- 기존 LLM -> Agent 흐름을 소개하고 우리의 이전 agent 영상도 언급한다
	- Agent의 한계와 multi-agent 등장을 소개한다
- 1-2) 실제 의미있게 사용되는 사례를 보여주어야한다
	- 단일 Agent과 Multi-Agent 간 비교를 하며 확실한 개선을 보여준다
##### 근거 reference
- AI Jason의 영상
	- Build AI agent workforce - Multi agent framework with MetaGPT & chatDev
	- AI agent manages community 24/7 - Build Agent workforce ep#1
- Maya Akim의 영상
	- How I Made AI Assistants Do My Work For Me: CrewAI
#### 2) solution 소개 시, 단계적으로 제시한다
- 1단계 : Hands-on (quick-show(small-wow))
- --> 2단계 : shallow-dive each components (이론에 대한 쉬운 설명(초심자에게도 성취감 제공))
- ----> 3단계 : Show solvit's real use case (실 적용 예시 보여주기)
##### 근거 reference
- AI Jason의 영상
	- Build AI agent workforce - Multi agent framework with MetaGPT & chatDev
- Maya Akim의 영상
	- How I Made AI Assistants Do My Work For Me: CrewAI
#### 3) 인트로 마지막에 영상의 목적과, 이 영상을 끝까지 보았을 때의 benefit(insight)을 말한다
> optional로 다소 공식적인 느낌이 있어 필수는 아니라고 봄
##### 근거 reference
- Maya Akim의 영상
	- 이 비디오에서는 복잡하고 까다로운 문제를 해결하기 위해 자신만의 스마트 AI 에이전트 팀을 구성하는 방법을 보여드리겠습니다. 또한 이메일이나 Reddit 대화와 같은 실제 데이터에 접근할 수 있게 함으로써 이들을 더욱 지능적으로 만드는 방법도 시연하겠습니다. 마지막으로, 로컬에서 모델을 실행함으로써 회사에 수수료를 지불하거나 개인 정보를 노출하는 것을 피하는 방법을 설명하겠습니다. **로컬 모델과 관련해서는 실제로 몇 가지 놀라운 발견을 했는데, 이에 대해서는 나중에 조금 이야기하겠습니다.**

#### 추가적인 스토리텔링 레퍼런스
- [2024 AI 키워드, Agentic Workflow | brunch](https://brunch.co.kr/@beingcognitive/17)

### B) 톤앤매너 관점
#### 1) 가급적 비유를 많이 사용하고, 쉽게 풀어서 설명한다
- 결국 대중성은, 쉽고 직관적이어야한다 (너무 어려우면 내용과 무관하게, So what이 될 수 있음)
##### 근거 reference
- 단순 기능 소개지만 깔끔하게 소개했을 때의 임팩트 예시
	- [챗GPT 제대로 쓰고 내 능력 미친듯이 끌어올리기 | 커리어해커 알렉스](https://www.youtube.com/watch?v=Qilv5SJmzKI)
- 적당히 익숙하면서, 적당한 새로움을 넣는 것이 최적일 수도 있다
- 조회수 차원에서 최적을 의미한 것이고, 우리의 BM 입장에서는 조회수를 희생하더라도 더 전문적이어야함
#### 2) 역설적이게도, 듣고 이해하기는 쉬우나 내용은 다소 어려워야한다 (shallow-challenge)
- curiosity와 tension 유도를 위해, 새로운 개념이나 프레임워크를 명확하고 간결하게 구조적으로 제시
	- ex 1) Agent 설명
		- Agent란? : 계획 -> 우선순위 -> 실행
		- Agent의 구성요소 소개 : 언어모델((LLM) + 메모리 + 도구)
	- ex 2) 개념의 대비 : 파인 튜닝 Vs. 놀리지 베이스
	- ex 3) Multi-agent 사례
		- Andrew Ng이 언급한, Agentic Design Patterns 대표 프레임워크 제시
			- 이 또한 P-S 구조로 설명
				- (P) : "자율성이 너무 높아 어떻게 여러 agent 구성을 해야할지 막막할 수 있다"
				- "여러 시행착오를 거친 후 효과적이라고 알려진 내용을 소개드릴테니, 처음 사용하시는 분들은 이를 참고하시면 많은 시간을 세이브하실 수 있을 것."
				- (S) : "AI 대가인 Andrew Ng이 언급한 Design Patterns을 소개하겠다"
		- Reflection, Tool Use, Plannig, Multi-agent Collaboration

## 시나리오 개요
### Intro : 사람들의 상황에 대한 공감과 이로부터의 문제제기
- 많은 분들이 다양한 방식으로 언어 모델, ChatGPT, Claude와 같은 SaaS, 혹은 노코드(make)와 함께 Agent를 결합하는 등 AI를 사용하고 있다.
- 응답에 대한 대답을 받는 ChatGPT와 같은 서비스를 사용하셨거나, 단일 API 호출을 통한 답변을 받아오신 분들은, 이와 유사한 문제를 경험하셨을 것이다.
- (아래 KeyPoints의 problem 제시) 

- 오늘은 하나의 LLM 혹은 단일 Agent를 사용하면서
  (1) 성능 및 일관성에 대한 아쉬움 (2) 워크 플로우 상 아쉬움을 느꼈던 분들께 이를 개선할 수 있는 Multi Agents 접근을 제시하고자한다.
- 이 영상에서는 Multi Agent가 왜 나왔고 어떤 부분에서 강점이 있는지, 어떻게하면 잘 쓸 수 있는지를 먼저알려드리고, 실제 저희 워크플로우에 통합하는 과정을 보여드릴테니 끝까지 봐주시면 감사하겠다.
#### Key Points
- 1) ChatGPT를 사용하며, 계속 다시 알려줘 or '이러한 부분을 추가해서' 다시 말해줘 (problem 제시)
	- 편집을 통한 화면으로 보여주어도 되고, 말로 언급해도 됨
	- 이후, reflection solution 과 매칭 됨
- 2) ChatGPT(or Claude)를 사용하며, workflow가 분절되는 예시 (problem 제시)
	- 나온 결과물을 다시 형식을 변형한 이후에 다른 곳에 붙여넣거나, 복사해서 다른 곳에 전송하는 예시
	- 이후, multi agent collaboration을 통한 E2E Workflow 구현 solution과 연결 됨
#### Intro Reference
##### SOLVIT 파인튜닝 영상의 공감과 문제제기
- 많은 분들이 자신이 일하고 있는 분야에서 GPT를 사용하고 싶어합니다.
- 의학이나 법학처럼 굉장히 도메인 지식이 많이 필요한 분야에 일하는 사람들도 이 GPT 같은 언어 모델을 어떻게 하면 더 잘 활용할 수 있을지 고민을 하는 분위기가 많이 느껴지곤 합니다.
- 그런데 일반적으로 이미 지금 OpenAI가 서비스를 하고 있는 이 GPT를 그대로 사용했을 때 굉장히 좋은 결과를 얻지는 못할 겁니다
##### Maya Akim의 CrewAI 영상의 공감과 문제제기
- 당신은 논란의 여지가 있는 구매를 하기 직전에 이런 경험을 해본 적이 있나요?
- 구매 버튼을 클릭하려는 순간, 갑자기 예상치 못한 생각이 떠오릅니다. "잠깐, 이거 약간 콩 치즈처럼 생기지 않았나?" "아니, 아니, 아니, 절대 아니야. 이건 정말 아름다워. 카녜 웨스트도 좋아하잖아. 그는 항상 이걸 착용하고 다니니까." "하지만 내가 카녜가 좋아하는 것을 좋아한다면, 그게 정말 좋은 건가?" "진정해야 해. 모든 게 괜찮아. 이걸 사는 건 나를 선구자로 만들어 주는 거야, 트렌드 세터로."
- "이 구멍들은 환기를 위해 존재하는 걸까?" "좋아, 잠깐 쉬어야겠어. 이 모든 생각에서 벗어나기 위해 급히 프링글스로 스트레스를 풀어야겠어." "잠깐, 이게 정말 건강에 좋지 않은 걸까?"

- 방금 목격한 이 내면의 대화는 **'빠르게 생각하기, 느리게 생각하기'(Thinking Fast and Slow)의 저자 대니얼 카너먼이 말하는 '시스템 2 사고'** 입니다.
- 이는 의식적이고 신중한 사고 유형으로, 의도적인 노력과 시간이 필요합니다.
- 이와 반대되는 것이 '시스템 1' 또는 '빠른 사고'입니다. 시스템 1은 무의식적이고 자동적입니다.
- 예를 들어, 군중 속에서 익숙한 얼굴을 쉽게 알아보는 것과 같습니다.

- 그런데 왜 AI 보조에 관한 비디오에서 이런 이야기를 하고 있을까요?
- 이를 이해하려면 **OpenAI의 훌륭한 엔지니어인 Andrej Karpathy**가 올린 놀라운 YouTube 비디오를 언급해야 합니다. 그 비디오에서 Andrej는 현재 모든 대규모 언어 모델들이 오직 시스템 1 사고만 가능하다고 설명합니다. 이들은 스테로이드를 맞은 자동 예측 기능과 같습니다. 현재의 LLM 중 어느 것도 요청을 처리하는 데 40분을 소요하고, 문제를 다양한 각도에서 생각한 뒤 복잡한 문제에 대해 매우 합리적인 해결책을 제시할 수 없습니다.
- 우리가 AI에게 궁극적으로 원하는 것은 바로 이 합리적이거나 시스템 2와 같은 사고입니다.



- 1) Why multi-agent? (Problem)과 Solution 구조
	- multi-agent가 어떠한 문제를 해결해주는 기술인지
	- 기존 단일 agent 간략 소개와, 단일 agent의 한계를 소개
	- 이를 극복하기 위한 multi-agent가 등장 소개
- 2) 현재 multi-agent system 현황
	- ChatDev, MetaGPT로 부터 유명해지기 시작했으며, 요즘은 아래의 기술들이 많이 사용되는 것으로 파악 됨
	- a) LangChain 기반의 LangGraph
	- b) CrewAI
		- 특징 : 좀 더 쉽게 구축 가능
	- c) AutoGen
		- MS에서 만든 오픈소스로, 에이전트간 계층 구조 등 세부 조정하기에 좋음
		- GUI 형태의 AutoGen Studio도 있으니,
		  코드에 익숙하지 않은 분들도 찾아보시면 노코드 형태로 시도해보실 수 있을 것

- 3) 우리가 사용할 AutoGen(or CrewAI), 실제 적용할 예시
	- use case 확정 필요
	- AI outfit 포함할지 말지도 고민
		- 참고) [AI Outfit 시나리오 | Notion](https://www.notion.so/janghoo/AI-virtual-tryon-EP01-EP02-8e17eef29371412ebba5706f613017db?pvs=4)
- 4) 우리의 상황에 대한 문제와 해결 적용 방식 구체화하여 단계별 설명
- 5) 실제 구현 데모

##### 커리어해커 알렉스의 ChatGPT 활용법 영상의 본인 소개와 영상 베네핏 언급
- 여러분 ChatGPT 어디까지 써보셨나요?
- 저부터 말씀드리자면 저는 지금 실리콘밸리에서 시니어 개발자로 일을 하고 있고 챗지피티가 출시되자마자 미친듯이 쓰기 시작하면서 정말 별걸 다 해봤는데 앱도 만들어보고 개발도 시켜보고 일상적인 대화에서도 많이 활용하거든요.
- 그렇게 1년 동안 어떻게 하면 더 이걸 잘 쓸 수 있는지 연구를 되게 많이 해 봤는데 그 결과 챗지피티를 남들보다 꽤 잘 쓰고 있다고 생각을 해요.
- 이 스킬이 나중에 가서는 엄청 큰 경쟁력이 될 것 같은데 숨겨진 기능들을 통해서 잘 쓸 수 있는 방법 세 가지 오늘 여러분께 알려 드릴게요.
- 안녕하세요 커리어해커 알렉스입니다 오늘은 사람들이 잘 모르는 ChatGPT 350% 활용하는 방법 말씀드려 볼게요.

##### AI Jason 디스코드 봇 영상 인트로 : 영상 목적과 문제제기
- 저는 실제 AI 직원들을 구축하는 방법에 대한 일련의 비디오를 만들 것입니다.
- 여러분 덕분에 제 유튜브 채널이 급성장했지만, 매일 많은 이메일과 디스코드, 텔레그램, 트위터에서의 메시지, 그리고 새로운 구매와 비디오 편집 작업까지 처리해야 합니다.
- 그래서 일부 작업을 다른 사람들에게 아웃소싱할지 고민하기 시작했습니다.
- 하지만 AI 자율 에이전트에 관한 몇 가지 비디오를 만들면서, 왜 AI 직원들을 만들어서 이 작업들을 대신 처리하게 하지 않을까 생각하게 되었습니다.
- 그래서 저는 제가 필요로 하는 다양한 역할과 작업을 수행할 디지털 AI 직원을 만들기 위한 비디오 시리즈를 시작할 것입니다.


---

### 1) Multi-agent의 등장 (Why Multi-agent? & What is Multi-agent?)
- 사실 여러분만 느낀 한계가 아니고, 저를 포함한 수많은 다른 분들도 같은 어려움을 느껴왔다.
- 이에, 처음 단순한 LLM에서, 이를 극복하기위해 Agent 개념이 나왔고,
  이 단일 Agent를 더 잘 쓰고자하는 발전(ReAct, CoT, ToT 등)이 많이 있어왔다.
- 그 이후로 오늘 소개하고자하는 Multi-agent 라는 개념까지 등장하게 되었다.
	- cf) 만약 단일 Agent를 처음 접하시는 분이 있으시다면, 이 영상(Research Agent)을 참고하셔도 도움이 되실 것 같다

- 등장 배경
	- 단일 Agent에 대한 연구와 발전이 있어왔고 ReAct, CoT와 같은 접근이 생기며 성능이 개선되었음. 하지만, 혼자 한 번에 다하려하니까 복잡한 task(복잡한 질문 이해, 장기적 맥락 유지, 언어모델 사용 최적화(추론마다 다른 LLM 사용))에 있어서는 어려움을 겪어왔음
	- 추론마다 다른 LLM 사용 : 쉬운 질문은 값이 싼 LLM, 어려운 질문은 비싸고 성능좋은 LLM

- multi-agent란?
	- multi-agent란 여러 agent를 통해 ~~ 하는 거다
	- CrewAI 나 AutoGen 설명 참고 (쉬운 비유로 설명했으면 함)

#### feedback
- 정확한 문제가 뭐야?
- multi-agent는 무엇을 해결해준다는 거야?
	- 이 영상을 보면 무엇을 얻을 수 있다는 거야?

### 2) Multi-Agent를 구축하는 방법 (How Multi-agent?)
- 현재 Multi-agent system 현황
- ChatDev, MetaGPT로 부터 유명해지기 시작했으며,
  요즘은 아래의 기술들이 많이 사용되는 것으로 파악 됨
	- 압도적인 도구가 있는 상황이라 보기에는 어렵고, 각 특징에 따라서 현 상황과 문제에 적합하다고 생각되시는 도구를 먼저 익혀보시고 접해보시는 것을 권장
	- 모두 무료로 제공되는 Youtube, 온라인 강의 영상이 있기에 참고하실 수 있다
- a) LangChain 기반의 LangGraph
	- 오픈소스
	- graph 기반
	- 기존 LangChain, LangSmith와 통합이 용이하고, 비쥬얼라이제이션을 통한 구조를 보기 좋아서,
- b) CrewAI
	- 오픈소스
	- 특징 : 좀 더 쉽게 구축 가능
		- 최소한의 코드로 구축하기에 용이하다
- c) AutoGen
	- MS에서 만든 오픈소스로, 에이전트간 계층 구조 등 세부 조정하기에 좋음
	- GUI 형태의 AutoGen Studio도 있으니, 코드에 익숙하지 않은 분들도 찾아보시면 노코드 형태로 시도해보실 수 있을 것

- 이후 보여드릴 저희의 use case는 AutoGen을 통해 구현했기에,
  오늘은 autogen에 대해 소개하고, 다른 도구들은 기회가 있으면 이후 영상으로 소개드리겠다.

### 3) 본격 들어가기 전에, 앤드류응의 Agentic Design Pattern 언급
- [AI Agentic Design Patterns with AutoGen | DeepLearning.AI](https://learn.deeplearning.ai/courses/ai-agentic-design-patterns-with-autogen/lesson/1/introduction)
	- Reflection
	- Tool Use
	- Planning
### 4) AutoGen Hands-on : 1단계 - small wow
- [AI Agentic Design Patterns with AutoGen | DeepLearning.AI](https://learn.deeplearning.ai/courses/ai-agentic-design-patterns-with-autogen/lesson/1/introduction)
### 5) AutoGen Hands-on 의 구성요소에 대한 간단한 설명 : 2단계 - 각 구성요소 설명
- [AI Agentic Design Patterns with AutoGen | DeepLearning.AI](https://learn.deeplearning.ai/courses/ai-agentic-design-patterns-with-autogen/lesson/1/introduction)
### 6) AutoGen 실 적용 사례 : 3-1단계 - research agent worflow에 통합
- Problem) workflow가 분절된다 and 일관된 형식이나 퀄리티의 답변이 나오지않는다
- Solution) multi collaboration 디자인 패턴이 적용되면 개선된다
	- 1) 각 agent를 나누어서 하나의 역할만 담당하도록하면,
	  workflow를 보다 안정적으로 확장할 수 있다 (디버깅 가능)
		- agent마다 하나씩의 tool을 주며, 전체 workflow를 agent component를 기준으로 구성
		- research 이후에, report로 만들기 or 자동 publishing 시키기
		- 더 나아가면, 각 agent 마다 다른 LLM을 사용하게하여 workflow를 최적화 할 수도 있다
			- ex 1) 특정 작업은 Open LLM(Agent) 사용하여 cost 절감
			- ex 2) 특정 작업은 파인튜닝 LLM(Agent) 사용하여 task 수행
	- 2) 각 agent를 나누어서 하나의 역할만 담당하도록하면, 더 나은 성능을 얻을 수 있다
		- 한 agent에게 여러 도구를 주는 것보다, 여러 agent에게 하나씩의 도구를 주는 것이 더 나은 결과를 내는 것으로 여러 연구를 통해 알려져있다
### 7) AutoGen 실 적용 사례 : 3-2단계 - AI Outfit worflow 에 통합
- Problem) 한 번에 좋은 결과를 내지 못한다
- Solution) reflection 디자인 패턴을 적용하면, 성능이 올라간다
### 8) Outro : 여러 활용 사례를 보여주며 상상력 자극
- 이 외에도 이러한 problem 들을 해결할 수 있는 접근(solution)이다
	- github 오픈소스 예시 데모만 보여주기
- 여러분의 문제에대한 활용 사례와, 적용 아이디어가 궁금하다
- 공유해주시면 감사하겠습니다.


# 출처 (참고 문헌)
- 

# 연결 문서
- 