---
created_date: 2024-07-22 22:10
tags:
  - solvit
  - crew
aliases:
---
# Context


# Content
## 고려 사항
- 수요가 있는 시장(및 Keyword)을 찾고, SOLVIT 다운 접근을 적용한다 (SOLVIT스러운 해결)

- 기존 방식과의 차이
	- 하나의 영상을 레퍼런스 삼아서 진행하는 것이 아니라,
	  다양한 영상을 살펴보고 해당 영상들을 종합하여 더 나은 결과물을 만든다

- 문제를 먼저 정의하고 소개한다
	- 기술이 적용되지 않았을 때의 어려움, pain point를 설명하여 공감을 얻는다(설득 단계)
- 다른 사람들의 접근법을 소개한다
- 우리의 차별성을 어필하고(직접 만들기로 했습니다.), 개요를 설명한다
	- 단계적으로, agile하게 해결 단계를 보여준다
	- 1단계(단순 automation - n8n) -> 2단계(AI (LLM) 적용) -> 3단계 (Agent or Multi agent)
		- 필요 시, RAG, fine-tuning 등 접근법 적용
### SOLVIT 컨텐츠 파이프라인
- 1) 기술 흡수와 기획
- 2) 실현 가능성 검증
- 3) 녹화와 편집자님 1차 전달
- 4) 다지기와 시야 확장
- 5) 편집자님 피드백 요청
- 6) 업로드

## 아이디어 백로그
### 1) Youtube Research Agent
- 1단계
	- 단순 python script or n8n
		- 노코드 n8n 활용하여 대중성 확보
	- Youtube API 활용하여 특정 keyword 검색하고, 제목, 채널, 내용 등을 리포트로 만들어서,
	  노션 페이지로 아카이빙 -> 이후 디스코드에 알림 봇
- 2단계
	- LLM을 통해 스크립트 핵심을 요약하여 추가
- 3단계
	- 멀티 에이전트 구조로, 우리만의 인사이트를 추가
	- 평가 agent를 만들어서 (뷰트랩 접근과 유사하게), 점수를 매기고 다른 page에 아카이빙
#### 참고 영상
- Youtube API + CrewAI
	- [How to build a ROBUST AI Agent stack | CrewAI + YouTube API + Ollama + Groq + AgentOps](https://www.youtube.com/watch?v=SFXlvPo-CEs)
	- [I Automated My YouTube Channel With CrewAI - Free Source Code Included](https://www.youtube.com/watch?v=OumQe3zotGU&t=722s)
- [LangChain Youtube App | Chat With Your Favortie Youtuber](https://www.youtube.com/shorts/b2JRgUe0A4E)

### 2) AI News Publishing
- 1단계 : 문제를 정확히 정의해야함 - 사람이 24/365 트렌드를 힘들다, 빠르게 올리기 힘들다
	- 단순 python script or n8n
	- 빠르게 Key news 파악하여 리포트 생성 후 publishing - human confirm 과정은 추가 (브랜딩 중요)
- 2단계 : 1단계는 이런 부분이 아쉽고, LLM은 이것을 해결해줄 수 있다
- 3단계 : 2단계는 이런 부분이 아쉽고, Multi Agent or Agent 는 이런 것을 해결해줄 수 있다
- GPT-4o-mini, llama 405B 등

## 시나리오 개요
### 시나리오 선정 조건
- 1) SOLIVT의 컨텐츠 파이프라인에 적용되는 영역
	- SOLVIT 파이프라인 중 '기술 흡수와 기획' 영역에 해당
- 2) 업무 자동화 영역
- 3) 단계적으로 시연 가능한 영역
	- 각 단계가 완결성이 있어야함 - 1단계만 하더라도 사용은 할 수 있어야함
### T&T
- Youtube를 흡수하는 미친 방법
- Youtube를 보고, 읽는 획기적인 방법
- AI와 Youtube를 보고, 읽는 혁신적인 방법 | Agent 활용
- Youtube를 AI로 갖고노는 

### 주제 : '유튜브 흡수' 자동화 (Youtube Summarization)
- SOLVIT의 컨텐츠 파이프라인에 적용되는가? -> O
	- 기술 흡수와 기획 파트에서 수많은 유튜브 레퍼런스를 참고하게 됨
- 업무 자동화 영역에 적용되는가? -> 절반 O
	- 자동화의 영역을 너무 좁히면 주제 선정에 어려움이 있는 듯함
	- '자동화' 의 툴 안에서 어느정도의 유연성은 두고 진행해야겠음
- 단계적으로 시연이 가능한가? -> O
	- 1단계) python 스크립트 기반의 자동화 
	- 2단계) Summary, Extract Wisdom 과 같은 서로 다른 프롬프트로 다른 결과 생성
		- LLM의 장점은, 유연한 자동화도 있지만,
		  중간에 이런 비정형성 데이터, 자연어 처리를 할 수 있게 해준다는 것이다
	- 3단계) PM agent가 영상을 분류하고,
	  Summary agent or extract_wisdom agent에게 전달
		- Multi-Agent의 장점은 자동화 워크플로우의 신뢰성과 퀄리티를 높여준다는 것
		- 병렬로 처리하면 속도 개선도 가능

### 참고 사항
#### n8n
- n8n을 사용하려고 코드가 더 편한 부분을 굳이 노코드로 변경할 이유는 없음
- 이미 잘 갖춰진 툴이 필요할 때 활용하는 것을 원칙으로 하기
	- ex) Read Google Sheet, Read Gmail, Send Slack or Discord 등을 앞 뒤에 연결하는데
	  적극적으로 활용
- 코드가 더 편한 부분은 python script 노드를 만들어서 연결해주면 됨

- n8n 에 대한 간단한 소개는 하되(왜 사용하는지 - 무료, 유연한 커스터마이징(오픈소스)),
  튜토리얼은 하지 않고 바로 간단한 워크플로우 적용을 보여주어 영상을 간결하고 압축적으로 만들기

## Customer
### 문제
Youtube 정보성 영상을 대상으로,
"영상 내용을 제대로 흡수하고 싶어 but 영상 내용을 빠르게 흡수하고 싶어"
#### 인용구
- [Harvard Biologist E.O. Wilson](https://ko.wikipedia.org/wiki/E._O._%EC%9C%8C%EC%8A%A8) famously said that,
  “We are drowning in information, while starving for wisdom.”
	- 정보의 홍수 속에서 살고 있지만, 지혜의 기근에 있다
	- AI로 뽑아낸 컨텐츠가 쏟아져나오는 지금, 다시 생각해보게되는 말이라고 본다.
## Competitors
> SaaS는 영상에서 소개하되(강점도 언급해주기 - 우리보다 product 완결성은 좋음 대신 freemium), 
> 다른 튜토리얼 영상은 소개할 필요 없어 보임
- [풀버전-튜토리얼 : AI로 유튜브 영상 요약하는 방법 ✍️ by 시현의 모험 | Youtube](https://www.youtube.com/watch?v=FAoAIPEFtmY)
	- Make 활용하여, 유튜브 영상을 짧은 글 5개로 만드는 웹페이지(프레이머 활용) 구축 시연
	- Flow : Webhook -> Claude -> Gmail and Notion
- [How to Summarize a YouTube Video with ChatGPT? (2024) by Cem Eygi | Youtube](https://www.youtube.com/watch?v=BErxU9o_gOk)
	- 'Youtube Summary with ChatGPT' extension 사용하는 법 소개
- SaaS
	- Lilys.ai - 꽤나 Wow이긴하다
	- traw.ai
- Chrome Extension
	- Youtube Summary with ChatGPT
## Company
> 왜 직접 만드는가?
> 우리의 product은 무엇이 더 좋은가? (fact -> merit & benefit)

- 직접 만들고 사용하니까 무료
	- API 비용은 들겠지만 비용이 최소화되며,
	  상황에 따라 최근에 Llama 3.1이 나왔듯이, Open LLM로 변경도 가능

- 요약 이외에도,
  더 다양하게, active하게, 영상 내용을 파악하고 질문할 수 있도록 함

- 이러한 정보(우리 입장에서는 가공되지 않은 데이터)를 가져와서,
  우리가 이해하고 활용하기 쉬운 방식으로 소화하는 것은 아주 중요하고 임팩트가 큰 영역이라 판단
	- 이에, 우리는 개인 도구로 만들어서 더 커스텀된 우리만의 시스템을 만들어가고자함

### 개선에 대한 아이디어
- UX 및 Input 측면
	- UX : 크롬 확장 프로그램, 개인 웹/앱, GPTs 등 여러 진입점으로 사용 가능하도록 적용 가능
	- Input : 유튜브 뿐만 아니라, 타 영상, 다른 글 등 source를 확장성 있게 개선해나가려고 함
- Processing 측면
	- 중간에서 어떻게 처리하느냐에 따라 판이한 결과가 나온다
	- 목적 : Summary, Extract Wisdom
	- 방식 : Single Agent, Multi-Agent, 그 외 Tool Use 등
- Output 측면
	- 우리만의 채널인 discord, 카카오톡 오픈 채팅 등 다양한 채널에 퍼블리싱하기 위함
### 참고 Resource
- 크롬 익스텐션 만들기 : [요즘 완전 대세! 크롬 확장앱 만들기. 5분컷. by 노마드코더 | Youtube](https://www.youtube.com/watch?v=QJSLtK2bY_A)

## 시나리오
### 1) Intro
> 컨셉 수업의 4C 반영 Flow
- Customer 문제제기
### 2) 다른 접근 방식 소개
- Competitors 간략 소개
### 3) 우리의 접근 소개
- Company 및 Concept 소개
### 4) 구현 1단계 : python + n8n
> e2e 시스템 (UX 차원에서, entrypoint와 Output이 깔끔)
> entrypoint : 크롬 익스텐션
> Output : 화면 or 디스코드 채널, notion 아카이빙 (use case 가정하여 적용)
- 1단계 목표 : '대본 쉽게 볼 수 있게' 만드는 e2e 시스템
	- UX : 크롬 익스텐션
	- Business logic : python (n8n x)
		- Youtube API 호출해서, 대본, 채널명
	- Output : 디스코드 or 노션 다른데 넘겨주기 (n8n)
		- 디스코드 특정 채널에 뿌릴건지?
		- notion에 아카이빙 할건지?
		- 바로 웹 화면에 보여줄건지?
- YoutubeAPI 써서, transcribe -> 대본 가져오기
### 5) 구현 2단계 : LLM(단일 Agent)
- Business logic : python 고도화
	- Youtube API 호출해서, 대본, 채널명
### 6) 구현 3단계 : Multi-Agent
- Business logic : python 고도화
	- Youtube API 호출해서, 대본, 채널명
### Outro : 정리
- python 스크립트 정도는 공유?


# 출처 (참고 문헌)
- 

# 연결 문서
- [[AI Automation Youtuber List]]
- [SOLVIT 컨셉과 방향성 | Notion](https://janghoo.notion.site/SOLVIT-957ebf3269844580890f17aadacf89f5)
- [[SOVLIT DECK 작업 자료]]