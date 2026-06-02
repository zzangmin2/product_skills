# product_skills
 
PM·기획 업무에서 반복되는 작업을 자동화하는 AI 스킬 모음입니다.  
Claude Cowork에서 즉시 설치해 사용할 수 있고, ChatGPT·Gemini에서는 프롬프트로 활용할 수 있습니다.
 
---
 
## ⚡ 추천 사용 순서
 
> 스킬 4개는 **기획 → 문서화**로 이어지는 하나의 흐름입니다.  
> 순서대로 쓰면 아이디어에서 화면 스펙까지 한 번에 완성됩니다.
 
```
① pm-feature-analysis     기능 아이디어·PRD를 PM 관점으로 분석
         ↓
② scenario-maker           분석 결과를 단계별 시나리오 문서로 구체화
         ↓
③ scenario-wireframe       시나리오를 모바일/태블릿 와이어프레임으로 시각화
         ↓
④ screen-spec-writer       확정된 화면을 Storyboard + Description 스펙 문서로 정리
```
 
> **짧게 쓸 때:** 시나리오가 이미 있으면 ③부터, 화면이 이미 있으면 ④만 써도 됩니다.
 
---
 
## Skills
 
### 1. `pm-feature-analysis`
 
기능 또는 서비스에 대한 PM 관점의 4단계 분석을 자동으로 수행합니다.
 
기능 설명이나 PRD를 붙여넣으면 아래 순서로 구조화된 분석 문서를 만들어줍니다.
 
1. **배경과 맥락** — 이 기능이 왜 필요한지, 어떤 문제를 푸는지
2. **문제와 가설** — 발생 가능한 리스크와 검증 가능한 가설
3. **루트코즈 후보** — 각 문제의 근본 원인 후보
4. **솔루션과 인수 조건** — 루트코즈를 건드리는 솔루션과 성공 기준 지표
```
# 사용 예시
"이 기능의 배경과 맥락 정리해줘"
"문제와 가설 뽑아줘"
"루트코즈 후보 알려줘"
"솔루션이랑 인수 조건 정리해줘"
"이 기능 전체 PM 관점으로 분석해줘"
```
 
---
 
### 2. `scenario-maker`
 
기능 배경이나 아이디어를 받아서, 개발·디자인팀이 바로 쓸 수 있는 시나리오 문서로 구체화합니다.
 
rough한 아이디어나 단계 구성을 입력하면 전체 플로우, 각 단계의 세부 조건·UX·필요 항목, 소요 시간, 미결 사항까지 작성합니다. 정보가 부족한 경우 먼저 핵심 항목만 골라 질문한 뒤 작성합니다.
 
**출력 구성:**
- 전체 플로우 (단계 흐름도)
- 단계별 세부 조건, 통과/실패 처리, UX 포인트
- 전체 예상 소요 시간 테이블
- 미결 사항 체크리스트
```
# 사용 예시
"시나리오 만들어줘"
"이 기능 시나리오로 정리해줘"
"플로우 구체화해줘"
"단계별 시나리오 써줘"
```
 
---
 
### 3. `scenario-wireframe`
 
화면 기획이나 시나리오 설명을 입력받아 모바일·태블릿 와이어프레임을 인라인으로 렌더링합니다.
 
시나리오 문서, 간단한 텍스트, 기능 아이디어 등 무엇이든 입력하면 폰/태블릿 프레임 와이어프레임을 바로 그려줍니다. 모바일과 태블릿 둘 다 요청하면 나란히 비교해서 보여줍니다.

```
# 사용 예시
"와이어프레임 그려줘"
"화면 시안 만들어줘"
"이 기능 화면으로 보여줘"
"모바일이랑 태블릿 둘 다 그려줘"
```
 
---
 
### 4. `screen-spec-writer`
 
화면 기획 스펙 문서(Storyboard + Description)를 자동으로 작성합니다.
 
스크린샷 또는 화면 설명을 제공하면, 앞뒤 플로우 맥락을 반영한 Storyboard와 번호 기반 Description을 작성합니다.

```
# 사용 예시
"이 화면 스펙 써줘" + 스크린샷 첨부
"Storyboard랑 Description 작성해줘"
"기획 문서 작성해줘"
```
 
---
 
## 사용 방법
 
### Claude (Cowork)
 
`.skill` 파일을 다운로드한 뒤 Cowork에서 설치합니다.
 
1. 이 레포에서 `.skill` 파일 다운로드
2. Claude Cowork 실행
3. 설정 → 스킬 → 파일에서 설치
4. 설치 후 스킬 이름을 입력해서 사용
---
 
### ChatGPT
 
SKILL.md 파일의 내용을 시스템 프롬프트 또는 대화 시작 시 붙여넣어 사용합니다.
 
**방법 A. Custom Instructions에 등록 (GPT-4 이상)**
1. ChatGPT 설정 → Custom Instructions 열기
2. "How would you like ChatGPT to respond?" 항목에 SKILL.md 전체 내용 붙여넣기
3. 이후 대화에서 바로 사용 가능
**방법 B. 대화 시작 시 붙여넣기**
1. 새 대화 시작
2. SKILL.md 전체 내용을 첫 메시지로 붙여넣고 전송
3. "이제부터 이 스킬에 따라 동작해줘"라고 입력
4. 이후 요청 입력
---
 
### Gemini
 
ChatGPT와 동일하게 SKILL.md 내용을 프롬프트로 활용합니다.
 
**방법 A. System Instructions에 등록 (Gemini Advanced)**
1. Gemini Advanced → Gems 만들기
2. Gem 지침에 SKILL.md 내용 붙여넣기
3. 저장 후 해당 Gem에서 사용
**방법 B. 대화 시작 시 붙여넣기**
1. 새 대화 시작
2. SKILL.md 전체 내용을 첫 메시지로 붙여넣고 전송
3. "이 지침에 따라 동작해줘"라고 입력
4. 이후 요청 입력
---
 
## 파일 구조
 
```
product_skills/
├── pm-feature-analysis/
│   ├── SKILL.md
│   └── pm-feature-analysis.skill
├── scenario-maker/
│   ├── SKILL.md
│   └── scenario-maker.skill
├── scenario-wireframe/
│   ├── SKILL.md
│   └── scenario-wireframe.skill
└── screen-spec-writer/
    ├── SKILL.md
    └── screen-spec-writer.skill
```
 
---
 
## 기여
 
새로운 스킬 제안이나 개선 사항은 Issue 또는 PR로 남겨주세요.
