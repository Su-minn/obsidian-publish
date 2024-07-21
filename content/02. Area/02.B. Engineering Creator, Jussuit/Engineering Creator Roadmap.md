---
created_date: 2024-07-20 17:47
tags:
  - jussuit
  - 🌈
aliases:
---
# Context
- [[Engineering Creator, Jussuit]]에는 좋은 가치관과 철학들이 많이 담겨있지만,
  그래서 어떻게 되어갈 것인지(How), 어떤 결과물을 만들어 갈 것인지(What)는
  잘 담겨 있지 않다.

# Content
## Speciality : Target Skill
> Core가 되는 전문성과, speciality는 필요하다
> Why이자 Vision에 가까운, Engineering Creator, IT Connector는 다소 추상적일 수 밖에없다
> 
> 이에, Step을 잘 세워서 단계적으로 Target Skill을 하나씩 단련시킬 필요가 있다
> 다만 접근 방식은 구체적인 Skill(ex. ChatGPT) 능력을 기르는 기술 중심 접근이 아니라,
> Area(ex. Productivity)에 기반한 문제 중심 접근을 해야한다

```ad-tldr
1차 Target : 생산성(Productivity) - 자동화(Automation) 중 아래 기준에 해당하는 영역
- SW 기반 자동화
- AI 활용 자동화 (단, 바닥부터 모두 개발하지 않고 자동화 기반 기술(n8n, LangFlow 등) 활용)
	- AI 하위 기술 : Agents, Multi-Agent, RAG
- 소규모에 해당하는 영역 (Customization, Long-tail, 구체적인 Use case)
	- [[Engineering Creator Roadmap#조직 규모 기준 (Organizational Size Criteria|조직 규모 수준에 따른 자동화 분류]] 참고
	- Customization(Use Case) : [[문제 해결을 제텔카스텐으로 보면, 문제와 솔루션 노트의 연결로 볼 수 있다]]
- 단순 노코드 활용 이상의 Advanced Customization 및 코딩을 통한 기술 적용
	- base : n8n
	- AI : LangChain, AutoGen 등
	- Deploy : AWS SAM
	- OpenSource : SWE-code, Devika, [[Danswer 오픈소스 분석하기|Danswer]] 등
```

### 생산성 : Productivity
> 인구가 줄어들고있는 우리나라는 특히 더 인당 생산성을 향상시킬 필요가 있다.
> 
> 창의성(Creativity)과는 다른 영역으로 분리하여 생각해야한다고 보며,
> 창의성은 신규 Project에 가깝다면, 생산성은 기존 프로세스에대한 Operation에 가깝다.

- 생산성 카테고리는 '일'을 하는 입장에서는 거의 모두 타겟층이 되기에,
  너무 광범위하여 좁힐 필요가 있다
#### 생산성(Productivity)의 하위 분류에서의 자동화(Automation)
- 아래는 생산성의 하위 구성요소를 간단하게 나눈 카테고리이며,
  기술(IT)적인 접근에서 '자동화' 영역을 1차 타겟 영역(Area)으로 한다
- 생산성의 분류 속에서 자동화로 영역을 좁히더라도,
  사실상 생산성 향상 = 자동화 수준으로 매우 긴밀하게 결합되어있기에 더 영역을 좁힐 필요가 있다

| **관점**   | **카테고리**                                                                                        |
| -------- | ----------------------------------------------------------------------------------------------- |
| 기술적 관점   | **자동화 (Automation)**, 소프트웨어 도구 (Software Tools), 데이터 분석 (Data Analytics)                        |
| 인적 자원 관점 | 교육 및 훈련 (Training and Development), 동기 부여 (Motivation), 팀워크 및 협력 (Teamwork and Collaboration)   |
| 프로세스 관점  | 프로세스 개선 (Process Improvement), LEAN 및 6시그마 (LEAN and Six Sigma), 프로젝트 관리 (Project Management)   |
| 시간 관리 관점 | 우선순위 설정 (Prioritization), 타임 매니지먼트 기법 (Time Management Techniques), 디지털 디톡스 (Digital Detox)     |
| 환경적 관점   | 물리적 환경 (Physical Environment), 디지털 환경 (Digital Environment), 심리적 환경 (Psychological Environment) |

#### 자동화 : Automation
> 자동화는 효율적이지만, 전부는 아니다.
> 
> 자동화를 하는 과정에서 더 리소스가 크게 들어가는 부분을 경계해야하며,
> Process Innovation(PI) 관점에서 바라보는 것이 더 나을 수 있음을 고려해야한다.

- 자동화 문제에 꼭 AI가 들어가는 것은 아니다
	- AI가 적용되었을 때에,
	  기존의 rule 기반 자동화에서 할 수 없었던 부분을 할 수 있게 된 것일 뿐이다
	- 문제 해결의 입장에서는 AI 없는 Make, Zapier, n8n 기반 자동화도 충분할 수 있다

- 특정 환경과 상황에 따라, 전략적으로 AI를 얹어서 'add value' 할 수 있다
	- 유튜브 : Keyword 전략 관점에서 'AI' Keyword 의 효과를 볼 수 있다
		- 최근 추세를 보면, 단순 '자동화'보다 'AI 자동화'가 훨씬 강력한 keyword로 보인다
	- 회사 : 회사 장기 전략과 평가 관점에서 'AI' 영역을 얹었을 때 value가 더해진다
	- Domaint driving forces 차원에서도, 이를 활용하였을 때에 큰 임팩트가 나올 수 있다
		- [["Identify the dominant driving forces behind the change"]]
##### 자동화의 하위 분류
###### 기능적 기준 (Functional Criteria)
| **기능적 기준**  | **세부 항목**                             |
| ----------- | ------------------------------------- |
| 업무 자동화      | 반복 작업 자동화, 전자 메일 자동화, 데이터 입력 자동화      |
| 프로세스 자동화    | 비즈니스 프로세스 자동화, 로봇 프로세스 자동화, 워크플로우 자동화 |
| 기술 및 도구     | 자동화 소프트웨어, 스크립팅 및 매크로, 인공지능 및 머신러닝    |
| IT 인프라 자동화  | 서버 관리 자동화, 네트워크 관리 자동화, 클라우드 자동화      |
| 제조 및 공정 자동화 | 산업 자동화, 품질 관리 자동화, 생산 계획 자동화          |
###### 산업별 기준 (Industry Criteria)
| **산업별 기준** | **세부 항목**             |
| ---------- | --------------------- |
| 제조업        | 산업 자동화, 생산 계획 자동화     |
| 금융업        | 트랜잭션 자동화, 보고서 자동화     |
| 헬스케어       | 환자 관리 자동화, 진단 자동화     |
| IT 및 소프트웨어 | 코드 배포 자동화, 서버 관리 자동화  |
| 소매업        | 재고 관리 자동화, 고객 서비스 자동화 |
###### 조직 규모 기준 (Organizational Size Criteria)
- 삼성 SDS에서 하는 Brity Automation은
  통합 자동화 시스템, 중소기업-대기업 향 자동화 도구라고 볼 수 있다

| **조직 규모 기준** | **세부 항목**                   |
| ------------ | --------------------------- |
| 소규모 기업       | 소규모 프로세스 자동화, 기본적인 업무 자동화   |
| 중간 규모 기업     | 중간 규모 프로세스 자동화, 맞춤형 자동화 솔루션 |
| 대기업          | 대규모 프로세스 자동화, 통합 자동화 시스템    |
###### 기술 수준 기준 (Technology Level Criteria)
> 기본적인 노코드 활용은 기본-중간 수준으로 볼 수 있고,
> 코드 작성을 통한 Multi-Agent 활용은 고급 수준으로 볼 수 있다.
> 
> Service 판매에 있어서는 고급 수준 자동화가 적합하나,
> 대중향 컨텐츠에 있어서는 기본 수준 자동화가 적합할 수 있다
> 
> 구체적으로는, [[SOVLIT DECK 작업 자료#상품 전략에 매칭한 예시|콘텐츠 전략]]에 따르면 Core Product는 고급 수준 자동화,
> 유입 콘텐츠는 기본 수준 자동화에 적합하다고 볼 수 있다

| **기술 수준 기준** | **세부 항목**                   |
| ------------ | --------------------------- |
| 기본 수준 자동화    | 기본적인 매크로 및 스크립트, 간단한 자동화 도구 |
| 중간 수준 자동화    | 로봇 프로세스 자동화, 비즈니스 프로세스 관리   |
| 고급 수준 자동화    | 인공지능 및 머신러닝, 복잡한 워크플로우 자동화  |
###### 사용자 유형 기준 (User Type Criteria)
> 위의 기술 수준 기준과 유사하게 Target 관점에서 생각해볼 수 있다

| **사용자 유형 기준** | **세부 항목**              |
| ------------- | ---------------------- |
| 일반 사용자        | 일상 업무 자동화, 개인 생산성 도구   |
| 전문 사용자        | 전문 소프트웨어 자동화, 고급 분석 도구 |
| 개발자           | 개발 및 배포 자동화, 코드 통합 자동화 |
###### 응용 분야 기준 (Application Domain Criteria)
| **응용 분야 기준** | **세부 항목**                   |
| ------------ | --------------------------- |
| 사무 자동화       | 문서 관리 자동화, 일정 관리 자동화        |
| 생산 자동화       | 생산 라인 자동화, 품질 검사 자동화        |
| 고객 서비스 자동화   | 챗봇 및 고객 지원 자동화, CRM 시스템 자동화 |

###### Youtube 자동화 채널 기준
> [[SOVLIT DECK 작업 자료|SOLVIT]]과 align시켜야하는 영역이다
- Monentization 관련 : 부업, 수익 자동화
	- Youtube(shorts) 자동화 : 최근 많은 portion 차지
	- 주식 자동화
	- 스마트스토어 자동화
- AI tool 소개
	- 기묘한 자동화
- 업무 자동화
	- 장PM : 업무 자동화를 포괄하지만 최근에는 AI 자동화 위주
	- 노션다움
- 그 외
	- 시현의 모험 : Make + AI + (SNS-인스타 릴스)
	- 10x AI Club : GPTs, 가벼운 수준의 Agent(개발)
	- 커리어해커 알렉스 : ChatGPT 위주, 업무 생산성, 자동화 언급도 일부
	- 테디노트 : 개발자 대상 RAG로 자동화 영역은 아니라고 판단
	- 한국타잔 : 최근 챗GPT 스페인 학습 영상이 34만회 폭발
		- '챗GPT 유즈케이스에 대한 관심이 높을 것이다'는 가설이 생김
		- 평소 조회수 대비 약 100배 (평균 3천회 정도)

## Job : SKT - AI Engineer & PM
- 현재 AI Coding Assistant 과제를 하며,
  AI Engineering에 필요한 Skill과 PM 역량을 함께 기르고 있다
- 특히, 일을 해나가는데 필요한 Soft Skill은 눈에 잘 띄지 않지만,
  매우 주요하게 작용하는 요소라는 생각이 점점 크게 들고있다
### Target Skill 과의 Align
- AI Coding Assistant에서,
  개발 과정(issue generation -> code generation -> test -> deploy, SWE Agent) 자동화
- Advanced RAG 등을 활용하여 각 영역 Automation에 최적화된 Agent 개발
	- [[코드 리뷰 Agent 도입 아이디어]]
	- [[AI coding assistant를 만드는 AI Agent]]
## CREW : SOLVIT 
- SOLVIT은 가장 나의 방향성에 가까운, 함께 나아가는 조직이자 Crew이다
### Target Skill 과의 Align
- [[EP4. Multi-Agent 시나리오 개요]]와 같이, Agent 관련 리서치 및 학습 진행
	- [[Multi-Agent 및 Agentic Workflow 정리]]
### 관련 문서
- [[SOVLIT DECK 작업 자료]]

# 출처 (참고 문헌)
- 

# 연결 문서
- [[Engineering Creator, Jussuit]]
	- 나의 Why가 주로 담겨있는 Branding DECK
- [[What can I do right NOW?]]
- [["Identify the dominant driving forces behind the change"]]
	- 최근에 나에게 큰 영감을 준 문장으로,
	  dominan driving forces를 레버리징 삼아서 활용한다면, 큰 임팩트를 낼 수 있다고 본다
	- 현재는 **AI 레버리징을 통하여 기존에 할 수 없었던 것들을 해내는 것** 이,
	  큰 임팩트를 가져온다고 보고있다
- [[이키가이_다이어그램.png|이키가이 Diagram]]
	- 이키가이 Framework를 통해 Why를 정리해보았다