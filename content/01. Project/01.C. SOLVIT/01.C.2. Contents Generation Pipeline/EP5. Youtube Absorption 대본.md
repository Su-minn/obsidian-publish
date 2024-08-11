---
created_date: 2024-08-05 21:17
tags:
  - crew
  - solvit
aliases:
---
# Context
## 가설
- 'Key Message를 명확하게 전달하면 대중에게 더 소구될 것이다'
- '우리의 익스텐션을 실제 사용해보고 싶다는 사람이 생길 것이다'
- '기술에 대한 문제 - 해결 구조가 아닌, real-life에 대한 문제 - 해결'

## Backlog
- Self-Discovery의 내용을 우리 problem에 맞게 변형 적용 (차용하겠다)
- S(elect) -> A(dapt) -> I(mplement) 구조에서,
	- 1) 우리는 문제가 이미 정해져 있으니(기술 정보 영상으로 한정) SA를 먼저 합침
	- 2) 1)과 I를 합침 (속도, 성능과의 trade-off 관점에서 1스텝으로 통합하기)


- LLM Classification
	- 이전에는 아래와 같이 Instructor 를 사용해야했음
		- https://www.youtube.com/watch?v=yMXxmdwndsU
	- 이제는, Structured Output 사용하면 됨
		- https://www.youtube.com/watch?v=fuMKrKlaku4


## 구현 User Flow
### 0) 사전 준비 사항 (**노션**)
- **노션**에 적용할 Question 종류들이 (reasoning modules) 들어있음
#### Why Notion?
- Notion을 통해 Reasoning modules 을 관리할 수 있다면, 노코드 차원에서 의미가 있다
- Notion은 admin으로의 역할을 한다
#### feasibility Check
- [x] Notion의 DB를 가져올 수 있는가?
### 1) 영상 발견 (제목 정도만 알고(기술 영상 이구나), 세부 내용은 모름)
- 빠르게 구조를 확인하고 싶음
- why?
	- 1-1) 전체를 볼 시간이 없는 경우
	- 1-2) 풀 영상을 보기전, 내가 원하는 내용이 들어 있는 영상인지 확인하기 위해
	  (어그로 패싱)
### 2) 크롬 익스텐션 (단축키 활용) 실행
- 2-1) (백단) 노션의 Question Module 중 적합한 SELECT
	- Problem : Multi-classes classification 문제
	- `Selected Lists = M(transcript | question module Lists)`
		- INPUT : 대본 transcript, question module Lists
		- Output : Selected Lists -> List 형태로 반환
			- ex) `[0, 1, 3, 5]`
- 2-2) Selected List를 기반으로 Implementation
	- Output : Key-value 형태
- 2-3) Implementation 기반으로 Report 작성
	- Input : Key-value 형태
	- Output : Markdown의 Report 형태
### 3) 내가 주로 갖고 있는 질문(or 프레임워크) 리스트 중 영상에 포함되는 세부 질문에 대한 응답 반환
- P-S 구조
- 사용된 기술
- Insight
- (기존 지식 창고와의 연결(RAG 필요)) - 언급만
	- 연관 문서
	- RAG 연결
- (대체재에 대한 조사 (or Critical Analysis)) - 언급만
	- Research Agent 연결
		- ex) 인테리어 제품 소개, '그래서 이거 구매 가능하냐?' - research agent 와 연결이 필요

### 4) 추가로 전송하고 싶은 경우, 나의 Insight 입력란에 추가 입력하고, **Discord** 채널에 전송하기
- 영상 본 이후에 전달하고 싶은 내용을 공유하는 UseCase 해소
	- 영상 전-중-후 파이프라인 중 '후'에 해당

### + 알파)
- 크롬 익스텐션 로고를 좀 이쁘게하기

## Claude Project Prompt
```prompt
위의 SOLVIT 가치관과 스토리 텔링 가이드라인을 기반으로 다음 영상의 대본 시나리오를 작성하고자해.

주제 : 자신만의 관점(목적성)을 바탕으로 AI를 적용하여 유튜브 영상 내용을 요약하면 효과적일 것이다.

소재 : Youtube를 나만의 '관점'으로 요약하고 정리할 수 있는 크롬익스텐션 개발

- 시나리오 작성 시, 마크다운 형태로 각 구분된 chapter가 존재해야해.
- 각 챕터마다 어떠한 의도로 이렇게 표현했고 대본을 작성했는지 이유도 함께 제시해줘야해.
- 6 ~ 8 에 속하는 구현 1단계, 2단계, 3단계는 개발 과정을 보여주는 부분으로, 대본에서는 제외해야해.
    
<대본 개요>
{대본 내용}
```

# Content

## 시나리오 개요
```ad-tldr
Key Message : 당신의 관점(목적성)을 바탕으로, AI를 적용하고 요약하면 효과적일 것이다
```

### 0) Intro (Hook) : Youtube 영상을 빠르게, 효과적으로 볼 수 있다면 생산성 폭발
> 정보를 빠르게 습득하고자하는 사람들의 니즈 (낮은 depth의 표면적인 니즈)
- 보통 정보성 영상은 길이가 긴 경우가 많고,
   SOLVIT의 영상은 그 중에서도 긴 편이라 긴 영상은 40-50분에 육박합니다.

- 이 영상을 30초 안에 효과적으로 요약해서 볼 수 있다면,
  시간을 아끼고 생산성을 폭발시킬 수 있지 않을까요?

---
안녕하세요, 문제를 IT로 해결한다, 솔브잇입니다.
여러분, 혹시 이런 경험 있으신가요?

정보가 가득한 40-50분짜리 유튜브 영상을 보려다가, 시간이 없어서 포기한 경험.
아니면 긴 영상을 다 보고 나서 "아, 내가 원하는 정보는 없었네..."라고 실망한 적은요?

만약 그 긴 영상을 30초 안에 효과적으로 요약할 수 있다면 어떨까요?
시간도 아끼고, 원하는 정보만 쏙쏙 얻을 수 있다면 정말 좋지 않을까요?

### 1) Competitors : 니즈를 충족하기 위해 등장하는 많은 유튜브 요약 서비스
> 표면적인 니즈를 충족시켜주는 것'처럼 보이는' 기존 서비스들
- 실제로 이러한 니즈가 많다는 것을 반증하듯이, 
  (예시. Lilys)와 같은 훌륭한 웹서비스를 포함하여, Youtube Summary 크롬 익스텐션 등 정말 많은
  요약 서비스와, 유튜브 요약 튜토리얼(외국 사례)들이 등장하고 있습니다.

---
실제로 이런 니즈를 충족시키기 위한 서비스들은 많이 나와 있고, 지금도 새로운 서비스들이 등장하고 있습니다.
예를 들어, Lilys.ai 같은 웹 서비스부터 'YouTube Summary with ChatGPT' 같은 크롬 익스텐션까지 다양한 요약 서비스들이 존재합니다.

이런 서비스들은 AI를 이용해 영상의 내용을 빠르게 요약해주죠. 언뜻 보면 우리의 시간을 아껴주는 훌륭한 도구 같아 보입니다. 하지만 과연 이것만으로 충분할까요?

#### 참고 자료
- SaaS
	- Lilys.ai
		- Lliys.ai는 퀄리티 좋게 모든 것을 다 제공해주는 느낌이라
		  요약보다는 정보 습득 support의 느낌이기는 함
		- 한국 말고 해외 SaaS 소개해도 괜찮을 것 같고, 찾아봐야할듯
- Chrome Extension
	- Youtube Summary with ChatGPT
- 영상
	- [How to Summarize a YouTube Video with ChatGPT? (2024) by Cem Eygi | Youtube](https://www.youtube.com/watch?v=BErxU9o_gOk)
		- 'Youtube Summary with ChatGPT' extension 사용하는 법 소개
### 2) Problem : 내 목적성에 맞지 않는 단순 요약은, 나의 니즈를 온전히 충족시키지 못한다
#### 문제 인지
- 저도 처음에는 위의 서비스를 잘 활용했고, 신기함을 느끼며 유용하게 사용했습니다.

- 그런데, 사용하는 과정에서 요약을 보고도 영상을 처음부터 끝까지 보거나,
  요약을 봐도 원하는 정보를 전혀 얻지 못했다는 느낌이 종종 들기 시작했습니다.
- 그리고, 그냥 이 서비스는 저의 성향과는 맞지않다고 생각하고 안쓰게 되었죠.
- 예시를 보여드리면, 이런 5줄 요약을 보는 것에는 별 효용을 못느꼈다는 이야기입니다.
	- ex) 솔브잇의 AI Outfit 영상을 5줄로 요약한 추상적인 문장 보여주기
		- (5줄 요약 SaaS 사용 예시)
#### 문제 정의
- 왜 영상을 잘 요약해서줘도 유용함을 못느끼는지 스스로 곱씹어보면서,
  저의 사고 과정을 한 번 돌아보았고 다음과 같은 결론을 내렸습니다.

> '아, 나는 내 머릿 속 질문에 대한 답이 안나오면 답답함을 느끼는구나'

- 저는 영상을 클릭하는 순간 머릿 속에 어떤 호기심이나 질문을 가지고 들어왔고,
  그 내용이 충족되지 않았을 때 답답함이나 허무감을 느꼈던 거죠.
- 특히, 자연스럽게 알고리즘에 빠져 쇼츠를 보거나 재미를 위한 영상을 보는 것과는 달리,
  목적을 가지고 보게되는 정보성 영상을 볼 때 말이죠.

### 3) Solution : 나의 관점을 기반으로 정보 추출, 내용 요약을 하는 서비스
- 저의 문제를 보다 정확하게 정의하고나니, 솔루션을 떠올리는 것은 그렇게 어렵지 않았습니다.

- 제 머릿 속의 질문, 관점, 그리고 생각의 프레임워크를 기반으로
  정보를 추출하거나 영상을 요약하도록하면 해결될 것이라고 봤기 때문이죠.
#### 유저 시나리오 설명
> 간단한 flow chart나 표로 시각화하면 깔끔할 듯
- 빠르게 영상의 전체 내용을 제가 원하는 관점으로 요약하여 확인했을 때,
- 1) 원하는 질문에 대한 답이 없는 경우
	- 끝까지 보고 원하는 내용이 없다고 실망할 일이 없으니 시간 save
	- + 간혹 존재하는 낚시성 영상도 회피하는 스크리닝 역할
- 2) 원하는 질문에 대한 답이 있는 경우
	- 요약으로 충분했다면 -> skip
	- 더 자세히 알아보고 싶다면 -> 영상 더 자세히 확인

- 이러한 시나리오로 실제 사용할 수 있겠다고 그림을 그려봤습니다.

- + 이후에 나올 시연을 아주 간단하게 preview로 보여주기
### 4) Cognitive Engineering 소개
- 위의 솔루션을 구현하는 것은 기존의 룰베이스 기반의 IT 만으로는 -유의미한 성능의 AI 없이는-
  불가능할 것입니다
- 이런 자연어를 가공하고 처리하는 분야는 AI가 잘하는 영역이기에,
  AI 기술을 문제해결의 도구로 사용하기에 적합한 분야 중 하나인 것이죠

- 구현에 들어가기 전, LLM 활용 대표 프레임워크 LangChain의 CEO인 Harrison chase의 글들을 살짝 공유드리고자합니다.
- 오늘 소개 시켜드리고 싶은 개념은 'cognitive architecture' 인데요.
- https://blog.langchain.dev/what-is-a-cognitive-architecture/
- 위 블로그 핵심 내용 한 두 문장으로 간단 설명

- 앞으로 설명할 구현 방식은 langchain, autogen 등 프레임워크를 활용하면 기술적 구현 난이도는 높은 편은 아닙니다.
- 하지만, 어떤 인지적인 설계를 하느냐에 따라 큰 차이가 생길 수 있고, 이는 AI 서비스의 효용성을 결정하는 핵심 요소라고 볼 수도 있을 것 같습니다.

### 5) 구현 개요
- a -> b -> c 로 이어지는 단계에 대한 개요 설명
- 서비스의 UX 관점의 내용은 설득되도록 설명하기 - 설득이 잘 안된다면 과감하게 빼도 됨
	- why 크롬 익스텐션?
	- why 노션?
	- why 디스코드?
### 6) 구현 1단계
### 7) 구현 2단계
### 8) 구현 3단계
### 9) Outro : 당신의 관점(목적성)을 바탕으로, AI를 적용하고 요약하면 효과적일 것이다
> 1) Key message를 전달하며 수미상관 구조 가져가기
> 2) SOLVIT 방향성에서 언급했던, 개인화(customization)에 대한 상상력을 자극하며,
>    적용 사례를 제시해주기

- AI를 잘 활용함에 있어서 프롬프트 엔지니어링이 많이 뜨고 관심을 받았었는데요.
  
  역할 부여(role), 예시 제공(Few shot) 등 형식적인 부분을 잘 갖췄을 때의 성능 향상도 물론 있지만,
  어떠한 질문을 할 것인가에 따라 활용할 수 있는 편차가 매우 컸기 때문이라고 생각합니다.

- 유사한 관점에서, 유튜브 영상을 통해 학습하거나 정보를 얻음에 있어서도
  여러분만의 관점을 녹여서 AI를 활용한다면, 정말 10x 생산성에 가까워질 수 있다고 생각합니다.

# 출처 (참고 문헌)
- 

# 연결 문서
## Self-Discover Paper Approach 적용하기
- [Self-Discover: Large Language Models Self-Compose Reasoning Structures (24.02) | Arxiv](https://arxiv.org/abs/2402.03620)
	- Google Deepmind Paper

### 정리 예정
- [LLM의 추론 능력 높이기 : Self Discover | Notion](https://blog.sionic.ai/self-discover)
- https://linknf.com/entry/%EA%B5%AC%EA%B8%80-LLM%EC%9D%84-%EC%9C%84%ED%95%9C-%EC%9E%90%EA%B8%B0-%EB%B0%9C%EA%B2%AC-self-discover-%ED%94%84%EB%A1%AC%ED%94%84%ED%8A%B8-%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0
- https://ai.atsit.in/posts/6860860808/
- https://tilnote.io/pages/65d56c9dc8ecac8926cdfcbc
- https://www.youtube.com/watch?v=zKw_qsXIF84
- https://ostin.tistory.com/446
- https://ostin.tistory.com/587
- https://github.com/kailashsp/SELF-DISCOVER
- https://jrodthoughts.medium.com/meet-self-discover-google-deepminds-new-method-for-llm-reasoning-4f3fdc547926
- https://brunch.co.kr/@heir480/2759
- https://blog.naver.com/horajjan/223350450399
- https://discuss.pytorch.kr/t/2024-02-05-02-11-ml-top-ml-papers-of-the-week/3497