---
created_date: 2024-08-05 21:17
tags:
  - crew
  - solvit
aliases:
---
# Context
## EP5. 가설
- 1) 'Key Message를 명확하게 전달하면 대중에게 더 소구될 것이다'
- 2) '우리의 익스텐션을 실제 사용해보고 싶다는 사람이 생길 것이다'
- 3) '기술에 대한 문제 - 해결 구조'가 아닌,
  'real-life에 대한 문제 - 해결 구조'는 보다 대중성이 있을 것이다

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


## 구현에대한 User Flow
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
	- `Selected Lists = M(transcript | question module Lists | meta-prompt)`
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
- 단축키 활용해서 빠르게 사용하는 예시 최종적으로 보여주기

## Claude Project Prompt
- 프로젝트에 SOLVIT 브랜드 덱을 정리해서 넣고, 초안 작성 시 활용
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
- 수동적인 정보 습득이 아닌, 능동적인 정보 습득을 하자.
```

### 0) Intro (Hook) : Youtube 영상을 빠르게, 효과적으로 볼 수 있다면 생산성 폭발
> 정보를 빠르게 습득하고자하는 사람들의 니즈 (낮은 depth의 표면적인 니즈)

안녕하세요, 문제를 IT로 해결한다, 솔브잇입니다.
여러분, 혹시 정보가 가득한 40-50분짜리 유튜브 영상을 보려다가,
시간이 없거나 지쳐서 포기한 경험 있으신가요?
- 시각화 : 솔브잇의 40-50분 영상 을 보여주면 재밌을 듯

아니면 제목과 썸네일에 후킹되어 영상을 다 보고 나서
"아, 내가 원하는 정보는 없었네..."라고 실망한 적은요?
- 시각화 : 다른 채널 영상 쓰면 안되고, 유튜브 썸네일과 제목을 살짝 편집해서 풍자하면 재미있을 듯
	- 아래 예시와 같은 느낌
	- ex) 제목 : '10분 만에 1억 버는 법', 썸네일 : 그 비밀은 바로 '이것' 입니다

네, 다 저의 이야기입니다. 그리고 유튜브로 재밌는 영상 뿐만 아니라,
정보 검색, 학습도 해결을 하는 요즘 이러한 일은 더 빈번해지고 있습니다.


만약 그 긴 영상을 30초 안에 효과적으로 요약할 수 있다면 어떨까요?
시간도 아끼고, 원하는 정보만 빠르게 얻을 수 있다면 생산성이 10배는 올라가지 않을까요?
- 시각화 : 우리의 최종 솔루션을 바로 빠르게 보여줘버리는게 더 hooking이 있을지?
	- 아래의 문제정의가 너무 길어지면 지루함이 생길 것도 같아서,
	  한 번 고민해보고 반영 부탁함

### 1) Competitors : 니즈를 충족하기 위해 등장하는 많은 유튜브 요약 서비스
> 표면적인 니즈를 충족시켜주는 것'처럼 보이는' 기존 서비스들

실제로 저 말고도 이런 니즈가 많다는 것을 반증하듯,
이를 충족시키기 위한 요약 서비스들은 많이 나와 있고, 지금도 새로운 서비스들이 등장하고 있습니다.
- 시각화 : 스쳐지나가는 예시 서비스는 해외 위주로 보여주는 것이 좋을 듯
  (우리나라 서비스는 더 호의적으로 소개)
	- 1) [YouTube Summary with ChatGPT & Claude | Glasp](https://glasp.co/youtube-summary)
	- 2) [NoteGPT](https://notegpt.io/youtube-video-summarizer)
	- 3) [HarpaAI](https://www.youtube.com/shorts/v5brHQ4C12k)
		- 외국 영상 댓글에 보면 key takeway + timestamp로 많이 보이는 서비스

이런 서비스들은 AI를 이용해 영상의 내용을 빠르게 요약해주고,
해외 영상 댓글을 보면 아래와 같이 timestamp와 함께 요약한 내용도 많이 보셨을 겁니다.
- 시각화 : 해외 영상 댓글에 정리한 내용 (아이디만 모자이크?)
- 참고 자료 : [How I Made AI Assistants Do My Work For Me: CrewAI](https://www.youtube.com/watch?v=kJvXT25LkwA)
![](https://i.imgur.com/nUcoUGe.png)

(특히 국내에서 만드신 서비스인 LilysAI는 사용성에 감탄을 했습니다.
영상을 글로 노트화 해서 핵심 주제를 확인하고 살펴볼 때는 최고의 서비스 중 하나라는 생각이 듭니다.)
- 호의적으로 언급하고 서비스 퀄리티를 인정하고 싶어서 대본에 추가했으나,
  너무 길어진다고 느끼거나 뜬금없다고 생각하면 빼도 됨

### 2) Problem : 내 목적성에 맞지 않는 단순 요약은, 나의 니즈를 온전히 충족시키지 못한다
#### 문제 인지
- 저도 처음에는 위의 서비스들을 잘 활용했고, 신기함을 느끼며 유용하게 사용했습니다.

- 그런데, 사용하는 과정에서 요약을 보고도 영상을 다시 보거나,
  요약을 봐도 원하는 정보를 전혀 얻지 못했다는 느낌이 종종 들기 시작했습니다.
	- 시각화 : 사람 이모지로 말하는 느낌 (너 자유롭게 하면 될듯)
- 예시를 보여드리면, 이런 5줄 요약을 보는 것에 큰 효용을 느끼기는 어려웠다는 이야기죠.
	- 시각화 : 솔브잇의 AI Outfit 영상을 5줄로 요약한 추상적인 문장 보여주기
		- (5줄 요약 SaaS 사용 예시)
		- 일부로 Lilys.AI와 같은 한국 서비스는 언급을 피함 

- 시각화 예시 (아래의 SaaS는 [YouTube Summary with ChatGPT & Claude | Glasp](https://glasp.co/youtube-summary))
	- 크롬익스텐션을 설치하면 유튜브 영상 옆에 생기는 summary 버튼을 누르면,
	  chatGPT 팝업이 뜨면서 아래 프롬프트가 자동 입력되고 엔터가 쳐짐
	- 1) 영어로 'summarize the following in 5 bullet points' 가 입력되며 영어 로 요약된 문제
	- 2) 영상의 내용을 온전히 파악하기 어려운 5 bullet points 요약
![](https://i.imgur.com/F8FVwdW.png)


#### 문제 정의
- 왜 영상을 잘 요약해서봐도 유용함을 못느끼는지 스스로 곱씹어보면서,
  저의 사고 과정을 한 번 돌아보았고 다음과 같은 결론을 내렸습니다.

> '아, 나는 내 머릿 속 질문에 대한 답이 안나오면 답답함을 느끼는구나'

- 저는 영상을 클릭하는 순간 머릿 속에 어떤 호기심이나 질문을 가지고 들어왔고,
  그 내용이 충족되지 않았을 때 답답함이나 허무감을 느꼈던겁니다.
- 특히, 자연스럽게 알고리즘에 빠져 쇼츠를 보거나 재미를 위한 영상을 보는 것과는 달리,
  목적을 가지고 보게되는 정보성 영상을 볼 때 말이죠.

### 3) Solution : 나의 관점을 기반으로 정보 추출, 내용 요약을 하는 서비스
- 저의 문제를 보다 정확하게 정의하고나니, 솔루션을 떠올리는 것은 그렇게 어렵지 않았습니다.

- 제 머릿 속의 질문과 생각의 프레임워크를 기반으로
  정보를 추출하고 영상을 요약하도록하면 해결될 것이라고 봤기 때문이죠.

- 화면의 내용과 같이, 문제와 솔루션을 정의하고, 최소한의 핵심 요구사항을 도출하였습니다.
- Self-discovery와 관련된 내용은 잠시 후에 설명드리겠습니다.

시각화
- 아래 워딩은 조금씩 수정해도 좋을 듯
![](https://i.imgur.com/4UU3tY6.png)

#### 유저 시나리오 설명

- 빠르게 영상의 전체 내용을 제가 원하는 관점으로 요약하여 확인했을 때,
- 1) 원하는 질문에 대한 답이 없는 경우
	- 끝까지 보고 원하는 내용이 없다고 실망할 일이 없으니 시간 save
	- + 간혹 존재하는 낚시성 영상도 회피하는 스크리닝 역할
- 2) 원하는 질문에 대한 답이 있는 경우
	- 요약으로 충분했다면 -> skip
	- 더 자세히 알아보고 싶다면 -> 영상 더 자세히 확인


- 이러한 시나리오로 실제 사용할 수 있겠다고 그림을 그려봤습니다.

- FLOW 시각화
![](https://i.imgur.com/BlUL6Hu.png)

- 시각화 : 최종 결과물에 대한 user flow도 간단하게 섞어서 보여주면 좋을 듯
	- 가능한지는 영상화해봐야 알 것 같기도.. 잘 부탁..

### 4) Self-discovery 소개
- 안될공학이 해당 논문을 쉽게 풀어서 설명한 영상인데 참고하면 도움이 될듯
	- https://www.youtube.com/watch?v=zKw_qsXIF84

- 구현에 들어가기 전, 이전에 설명드렸던 Self-discovery에 대해서 먼저 간단히 소개드리려고 합니다.
- 해당 내용은 24년 2월에 Google Deepmind에서 발표된 논문에 소개된 내용입니다.
	- [Self-Discover: Large Language Models Self-Compose Reasoning Structures (24.02) | Arxiv](https://arxiv.org/abs/2402.03620)

- 해당 내용은 LLM 모델이 직접 task 내에 내재된 추론 구조를 발견하여,
  복잡한 추론 문제를 해결할 수 있도록 하는 프롬프팅 기법인데요.
- 1단계 SELECT 과정에서는, 'atomic reasoning modules'라고 하는,
  critical thinking, step-by-step-thinking과 같은 최소 단위로 모듈화된 사고 과정, 혹은 멘탈 모델을 미리 모아두고, 해당 문제에 적합한 모듈을 뽑습니다.
- 다음으로 2단계 과정에서는, 해당 문제에 적합하도록 선택된 Module들을 변형하여 더 문제에 fit한
  사고 모듈로 바꾸게 됩니다.
- 마지막으로 3단계 에서는, 이렇게 만들어진 Adapted Modules를 이용하여 Reasoning Structure(추론 구조)를 만들고, 실제 instance 문제를 해결하는 데 사용하게 됩니다.
![](https://i.imgur.com/frMiTfG.png)

- 39개의 atomic reasoing modules 참고 
![](https://i.imgur.com/5LtX4pU.png)

- 저희의 문제는 이미, '기술 관련 정보성 영상'을 저의 관점으로 정리하는 것으로 정의했기에,
  Adapted Modules을 이미 만들어두었다고 볼 수 있습니다.
- 이에 Self-Discover 방식을 그대로 적용하기에는 적합하지 않지만,
  흐름에 대한 아이디어를 차용해봤는데요.

- 화면의 구조에서, Select와 Adapt STEP을 합치는 방식으로 구현할 예정입니다.
- 즉, LLM이 영상의 내용을 보고
  만들어 둔 Adapted Modules(질문 세트) 중 어떠한 질문을 답할 수 있는지 선택(Select)하도록 하고,
  그에 대한 Implement 이후, 마크다운 형식으로 정리를 하는 방향으로 구현을 하려고합니다.
- 아직까지는, 헷갈리는 부분이 있으실 것 같아 구현 단계에서 짚어가며 보여드리도록 하겠습니다.

- 시각화
![](https://i.imgur.com/HsRZubE.png)

### 5) 구현 개요
- 아래의 구현 단계는 만들어가며 다소 수정이 필요할 듯

- Notion은 어드민과 유사한 기능을 한다는 것을 짚어주면 좋을 것 같음
	- **노션**에 적용할 Question 종류들이 (reasoning modules) 들어있음
#### Why Notion?
- Notion을 통해 Reasoning modules 을 관리할 수 있다면, 노코드 차원에서 의미가 있다
- Notion은 admin으로의 역할을 한다
	- Notion에서 관리 및 직접 추가, 삭제 및 수정이 편리하다
### 6, 7, 8) 구현 1~3단계
[[EP5. Youtube Absorption 대본#구현에대한 User Flow|구현 Flow]] 참고

### 9) Outro : 당신의 관점(목적성)을 바탕으로, AI를 적용하고 요약하면 효과적일 것이다
> 1) Key message를 전달하며 수미상관 구조 가져가기
> 2) SOLVIT 방향성에서 언급했던, 개인화(customization)에 대한 상상력을 자극하며,
>    적용 사례를 제시해주기

- AI를 잘 활용함에 있어서 프롬프트 엔지니어링이 많이 뜨고 관심을 받았었는데요.
  
- 같은 질문을 할 때에, 어떻게 질문을 해야 더 좋은 답변을 받을 수 있을까도 성능 차원에서 주요한 부분이겠지만,
  
- AI에게 어떤 질문을 할까를 고민해보는 것도 더 많은 활용처와 유즈케이스를 발굴할 수 있는 접근이라고 생각합니다.
	- 시각화 : 자주 사용했던 이모지가 다양한 질문을 하는 화면

- 유사한 관점에서, 유튜브 영상을 통해 학습하거나 정보를 얻음에 있어서도
  여러분만의 관점을 녹여서 AI를 활용한다면, 정말 10x 생산성에 가까워질 수 있다고 생각합니다.

# 출처 (참고 문헌)
- 

# 연결 문서
## Self-Discover Paper Approach 적용하기
- [Self-Discover: Large Language Models Self-Compose Reasoning Structures (24.02) | Arxiv](https://arxiv.org/abs/2402.03620)
	- Google Deepmind Paper
### 관련 참고 자료
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