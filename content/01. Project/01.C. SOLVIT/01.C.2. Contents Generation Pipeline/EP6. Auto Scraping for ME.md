---
created_date: 2024-08-25 20:43
tags:
  - solvit
  - crew
  - AI
aliases:
---
# Context
- SOLVIT 파이프라인에 있어서,
  트렌드 파악 및 주제 선정에 있어서 항상 진행되는 정보 수집을 효율화하기 위한 시스템 개발
- SOLVIT 파이프라인이 아니라 다른 환경에서도 특정 주제를 지속적으로 스크랩하고 정리하여
  대시보드와 같은 형태로 확인할 수 있으면 유용할 것이다

# Content
## EP 6. 검증하고자하는 가설
> EP5. 의 가설 대부분을 그대로 유지
> 
> 이전 EP5. 'Youtube 요약' 이 아닌,
> 'Scraping'과 같은 다른 real-life 주제도 유사한 수준의 조회수가 나올까?
- 1) Key Message를 명확하게 전달하면 대중에게 더 소구될 것이다
- 2) 우리의 'Scraping 시스템' 사용에 흥미를 갖는 사람이 생길 것이다
- 3) '기술에 대한 문제 - 해결 구조'가 아닌,
  'real-life에 대한 문제 - 해결 구조'는 보다 대중성이 있을 것이다

## **이번 EP에서의 고려 사항 - 컨센 필요**
- 1) 가설은 아니지만, 이전 Youtube Absoprtion과 마찬가지로,
  "**SOLVIT 컨텐츠 생성 파이프라인 자체를 개선**" 할 수 있는 '문제 - 솔루션'을 대상으로 함
	- EP5. Youtube Absoprtion 와 달라지는 점이 있다면,
	  이전은 나의 Use Case를 너무 맞추려했다면 이번에는 너의 UseCase를 많이 반영했으면 함
	- 실제 사용자 입장에서 유용한 UseCase인가? 자연스러운 User Flow 인가? 고민 필요
- 2) 아래 내용은 큰 범주의 기획에 가깝고, 실제 UseCase 구체화 - Feasibility 검증 에서는 여러 논의와 시행착오가 수반될 예정임
	- 해당 과정에서 문제와 솔루션의 범위, 난이도 등은 모두 조율 가능함
	- 가급적 범위는 좁히고 난이도는 낮췄으면 함
	- 즉, 어렵거나 범위가 너무 크다 생각하면, 해당 부분을 좁히는 방향으로 제안 부탁
## 개발 System
### 해결하는 문제
- 사람이 직접 여러 소스(유튜브, X, 정보 공유 사이트(reddit, GeekNews, 파이토치 한국사용자 모임) 등)를 돌아다니며, 최신 정보와 유의미한 정보를 수집하고 정리해서 인사이트를 도출하는 것의 어려움

- 기존 Research Agent가 해결하지 못하는 문제
	- 이전 Research Agent 1.0(우리 영상) 수준으로 구글링 수준의 research를 시키면,
	  '할루시네이션 + 정보 신뢰성' 문제로 사용하기 어려움이 있었음
#### 구체적으로는 아래의 문제가 있음
> 리서치의 단계를 정보 수집 - 정리 - 인사이트 도출의 단계로 나눠볼 수 있음
##### 정보 수집 과정 문제
> 아래는 사람이 수집하는 경우의 문제점과 기존 Research Agent 문제점을 구분하지는 않았음
- 1) 시간적인 문제
	- 각 웹사이트를 매번 방문하고 정보를 찾는 데 많은 시간이 걸림
	- 특히, 여러 플랫폼에서 정보를 동시에 모아야하는 것은 시간과 에너지 소모를 유발함
- 2) 정보 누락 가능성 존재
	- 수많은 웹사이트와 커뮤니티를 돌아다니다 보면 일부 중요한 정보를 놓치기도 함
	- 저번에 말한 medium(유료 구독 필요) 사이트와 같이 퀄리티의 하방이 어느정도 보장된
	  플랫폼을 쉽사리 구독하지 못하는 것도, 포용할 수 있는 정보에 한계가 있기 때문
		- 구독해놓고 못보면 돈 아까움
- 3) 중복 정보 발생
	- 같은 내용의 정보를 여러 번 접하게 되는 경우, 이를 수작업으로 필터링하는 것은 비효율적임
		- 수집 - 정보 정리 과정을 머리에서 동시에 처리하는 경우, 피로도가 높아짐 
		  (기존 정리한 내용과 비교하며 수집할지 고민하는 경우)
	- 여러 사이트는 서로의 정보를 가져가고 가져오면서 중복된 내용이 많아짐
- 4) 빠른 업데이트의 어려움
	- 정보가 실시간으로 빠르게 변하는 상황에서,
	  수작업으로 정보를 업데이트하는 것은 실시간성을 보장할 수 없음
- 5) 신뢰성의 문제
	- 정보를 발견했다고 하더라도, 해당 정보가 정말 fact가 맞는지 신뢰성을 담보하기 어려움
##### 정보 정리 과정 문제
- 1) 비일관성 발생
	- 수작업으로 정보를  정리할 때, 서로 다른 사이트에서 가져왔기에 정보의 형식에 일관성이 없음
	- 이후 데이터를 분석하거나 인사이트를 도출할 때 어려움이 생김
- 2) 공통점을 도출하는 Task 자체의 어려움
	- 정보를 잘 정리하는 것도 노동집약적인 리소스가 많이 투여되는 task
##### 인사이트 도출 단계
- 사실 상, 정보 수집 - 정리까지만 하더라도 많은 리소스가 들어가기에,
  시스템 없이 데이터에 기반한 인사이트 도출은 거의 불가능한 상태
- 정보 정리를 일관된 형식으로만 할 수 있더라도 최소한의 정성적 분석은 가능해짐
	- ex) SOLVIT Youtube 아카이빙 DB
- 특정 지표를 수치화하여 통계 데이터를 생성하면 최소한의 정량적 분석이 가능해짐
	- 더 고도화된 데이터 분석도 시도해볼 수 있음
### 솔루션 : 개발 System
#### 가제 : Auto Scraping for ME
- SOLVIT의 브랜드 Keyword인, '자동화(Automation)'와 '개인화(Customization)' 가 녹아든 시스템
#### 기술 스택
- n8n
- AI Agent (n8n 내부 기능) or GPT
	- OpenAI, HTTP 노드, AI Agent 기능 등 열어두고 feasibility 확인하며 가장 적합한 기술 선택
- Deploy (가급적 hosting 진행)
	- webhook 형태로 돌아간다면, 로컬이 아닌 별도 서버 필요
		- 후보
			- 컨테이너 기반 : fly.io, render.com
				- 둘 다 free-tier 활용 가능할듯
			- n8n hosting 서비스 (가치가 있다고 판단되면 사용)
			- AWS EC2 or lightsail (가치가 있다고 판단되면 사용)
#### 요구사항 명세
> 장후 UseCase 반영하여 구체화 필요
> 
> 프로젝트 난이도와 범위를 고려하여,
> 수집 대상 정보는 새로운 Post를 대상으로 한정하는 것을 제안
> 
> 구체적으로 들어가면, 새로 올라오는 정보 모니터링과 기존 정보 리서치는 다소 차이가 있음
> - 이번 대상은 새로 올라오는 정보 모니터링으로 한정

| Category | 요구사항 상세                                                                                                                                                       | 비고                                                            |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------- |
| 정보 수집    | 미리 정해둔 Source(Youtube(특정 Youtuber or 특정 Keyword), X(특정 user의 tweet), Hacker News, ProductHunt, 디스콰이엇, LangChain Blog, GeekNews, Medium(?) 등)의 New Posts를 가져오기 | 신뢰성이 어느정도 보장된 source를 정해두고 정보를 가져와서 신뢰성 문제를 어느정도 해소           |
| 정보 가공    | 가져온 Posts 들을 미리 정해준 형식에 맞게 정리하여 노션 데이터베이스에 저장하기                                                                                                               |                                                               |
| 인사이트 도출  | Notion에 새로 출시된 '차트' 기능 활용하여 대시보드화                                                                                                                             | 정보 가공 시, 인사이트 도출이 가능한 형태의 column 정의 필요                        |
| 공유 및 전송  | 그 중에서도 특정 대상은 discord로 New posts 정보를 전송한다                                                                                                                     | n8에서 커버 가능할 것으로 보여 아이디에이션으로 추가<br><br>UseCase 구체화 과정에서 정하면 될듯 |
#### User Flow
> feasibilty 검증을 진행해나가며 구체화 필요한 영역
#### 예상되는 어려움과 해결 방안 (feasbility 확인 필요)
- 1) 스크래핑 웹사이트 source 구조의 차이 존재
	- 각 사이트마다 다른 형태의 크롤링 코드를 작성해야할 수 있으며,
	   사이트 구조 변경 시 기존 코드가 동작하지 않게 됨
	- 최근에 많이 사용되는 firecrawl과 같은 도구를 사용하면,
	  구조 독립적으로 크롤링이 가능할 수도 있음
- 2) 데이터 정제 및 필터링
	- LLM 을 통해 미리 맞춰둔 데이터 구조에 잘 맞춰서 정리가 될지?
		- 미리 맞춰둔 데이터 구조 = Self-discover와 유사한 플로우로 진행 가능하지 않을지?
	- 중복 내용이 수집되는 것을 최소화하고 싶은데 어떠한 방식으로 가능할지?
		- 그냥 LLM에 기존에 수집된 내용을 다 넣고 중복인지 확인하는 방안이 최선일지
- 3) 웹 스크래핑의 법적/도의적 문제
	- 스크래핑하여 혼자 사용하는 것도 문제가 될지?
		- 조금 더 확인 필요
	- 컨텐츠화하여 퍼블리싱하였을 때 문제가 발생하지 않을지를 고려하며 안전한 내용 위주로 컨텐츠화
		- 실제 사용하는 것과는 조금 달라도 된다고 생각함
- 4) bot 문제
	- bot으로 인식되어 scraping이 막히는 사이트가 있지 않을지?
	- 최하단에 추가한 [scrappey](https://scrappey.com/)와 같은 도구로 해결 가능할지 검증 필요

---
## Content Key Message
```ad-tldr
(현 AI 기술 수준에서도)
사람이 잘하는 부분과 AI가 잘하는 부분을 쪼개서 적용하면 AI를 더 잘 활용할 수 있다
```
### Key Message 상세
- <사람이 정해주는 부분>
	- 어느 source에서 정보를 가져올 지
	- 어떠한 형식으로 정리할 지
- <AI 활용 부분>
	- 웹사이트 구조를 알아서 파악해서 크롤링하기(feasibility 확인 필요)
	- 특정 형식에 맞춰서 정리하기
- <기존 개발 영역(n8n 활용)>
	- webhook을 활용한 자동화 (준실시간 모니터링)

## 시나리오 개요
> UseCase 및 feasibility 구체화 이후 작성 예정


## 연결 문서
### Reference
- [odevtube - 개발 관련 유튜브 모아둔 사이트](https://mp4.okdevtv.com/?page=3)
![](https://i.imgur.com/hUawqy3.png)
### firecrawl
- Turn websites into LLM-ready data : 웹사이트에서 구조화된 데이터 추출 가능
- [firecrawl.dev](https://www.firecrawl.dev/)
- [firecrawl | Github](https://github.com/mendableai/firecrawl)
### n8n agent 레퍼런스
- [AI agent that can scrape webpages | n8n](https://n8n.io/workflows/2006-ai-agent-that-can-scrape-webpages/?_gl=1*1tcfnvu*_ga*MTMwMDc5NTg1Ni4xNzIxNDc4Nzk5*_ga_0SC4FF2FH9*MTcyNDU5MzIyMS4xMy4wLjE3MjQ1OTMyMjEuNjAuMC4w)
- [Scrape every url on the web without getting blocked by Anti-Bot technologies with Scrappey | n8n](https://n8n.io/workflows/2299-scrape-every-url-on-the-web-without-getting-blocked-by-anti-bot-technologies-with-scrappey/)
	- [scrappey](https://scrappey.com/)
	- bot 감지를 다 뚫어버린다는 API?
- [Autonomous AI crawler | n8n](https://n8n.io/workflows/2315-autonomous-ai-crawler/)