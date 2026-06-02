---
name: scenario-wireframe
description: |
  화면 기획이나 시나리오 설명을 입력받아 모바일·태블릿 와이어프레임 HTML을 자동 생성하는 스킬. show_widget으로 폰/태블릿 프레임 와이어프레임을 인라인 렌더링한다. "와이어프레임 그려줘", "화면 시안 만들어줘", "UI 그려줘", "화면 mockup 만들어줘", "이 기능 화면으로 보여줘", "모바일 화면 만들어줘", "태블릿 화면도 그려줘" 같은 요청에 반드시 사용한다. onboarding-scenario 출력물뿐만 아니라 간단한 설명 텍스트, 기능 아이디어, 화면 플로우 메모가 있을 때도 항상 이 스킬을 사용한다.
---

# 와이어프레임 메이커

화면에 대한 설명(시나리오 문서, 간단한 텍스트, 기능 아이디어 등 무엇이든)을 받아 **show_widget**으로 모바일·태블릿 와이어프레임을 그린다.

---

## STEP 0. 역질문 — 정보가 부족하면 먼저 물어보기

입력이 너무 짧거나 아래 항목이 불명확하면, 와이어프레임을 그리기 전에 **한 번에 모아서** 물어본다. 항목마다 따로따로 묻지 말고, 필요한 것만 골라서 한 메시지로 정리해서 질문한다.

**필수로 알아야 하는 것**
- 서비스/기능 이름 (없으면 임시 이름을 제안하고 확인)
- 화면 흐름: 어떤 순서로 무슨 화면이 나오는지
- 각 화면에 들어갈 핵심 요소 (버튼, 입력 필드, 목록, 이미지 등)

**있으면 좋은 것 (없으면 합리적으로 추정)**
- 디바이스: 모바일만 / 태블릿만 / 둘 다
- 브랜드 컬러 (없으면 `#157FFF` 사용)
- 주요 사용자 (10대 앱인지, 기업용인지 등)

**역질문 멘트 스타일**: `~요` 체로 짧고 친근하게. 예시:
> 몇 가지만 확인할게요!
> - 어떤 순서로 화면이 이어지나요? (예: 로그인 → 홈 → 상세)
> - 모바일이랑 태블릿 둘 다 필요한가요, 아니면 하나만요?

입력이 충분하면(화면 흐름과 구성 요소가 명확하면) 바로 STEP 1로 넘어간다.

---

## STEP 1. 입력 파악

아래를 추출한다:
- 전체 플로우 (단계 수, 각 단계명)
- 화면 목록 (단계별 1~2개)
- 각 화면의 구성 요소 (입력, 버튼, 리스트, 업로드, 상태 표시 등)
- 강조·주의가 필요한 UX 포인트
- 디바이스 타입 (모바일 / 태블릿 / 둘 다)

---

## STEP 2. 화면 수 결정

- 단계 3개 이하 → 단계당 대표 화면 1~2개
- 단계 많으면 핵심만 선별 (총 4~6개 권장)
- 완료/결과 화면은 항상 포함

---

## STEP 3. HTML 생성 원칙

### 디바이스 프레임

**모바일 폰 프레임**
```css
width: 280px; border-radius: 24px; border: 1.5px solid; overflow: hidden;
```
- 상단 status bar (시간, 배터리 아이콘)
- nav bar (뒤로가기 + 타이틀)
- 진행 단계 dots

**태블릿 프레임**
```css
width: 480px; border-radius: 16px; border: 1.5px solid; overflow: hidden;
```
- 상단 status bar (더 넓게)
- 좌측 사이드바 또는 상단 탭바로 네비게이션 표현
- 콘텐츠 영역을 2컬럼으로 활용 가능 (좌: 목록/메뉴, 우: 상세/입력)

둘 다 요청된 경우: 같은 화면을 폰 + 태블릿으로 나란히 배치하고, 태블릿은 폰 아래 별도 섹션으로 모아서 보여준다.

### 컬러

- 브랜드 블루: `#157FFF`
- 강조/선택: `#EBF5FF` 배경 + `#157FFF` 테두리
- 완료: `#E8F5E9` + `#2E7D32`
- 대기/미완료: `var(--color-background-secondary)`
- 텍스트: 반드시 CSS 변수 사용 (`var(--color-text-primary)` 등), 하드코딩 금지

### 컴포넌트 패턴

| 상황 | 패턴 |
|------|------|
| 체크박스 동의 | 18px 체크박스 + 타이틀 + 설명 + chevron |
| 중요 강조 박스 | `#EBF5FF` 배경, `#B3D7FF` 테두리 |
| 파일 업로드 | 점선 업로드 존 + 촬영/갤러리 버튼 |
| 목록 행 | 아이콘 + 텍스트 + 우측 상태 칩 |
| 태그/칩 선택 | pill 형태, 선택 시 파란 배경 |
| 녹음/타이머 | 빨간 점 + 타이머 + 파형 바 |
| 완료 화면 | 중앙 정렬, 아이콘 원 + 타이틀 + CTA |
| 태블릿 2컬럼 | 좌 240px 목록 + 우 flex 상세, border-right로 구분 |

### 버튼

- Primary: `background:#157FFF; color:#fff; border-radius:8px; padding:13px; width:100%`
- Outline: `background:transparent; color:#157FFF; border:1.5px solid #157FFF`

### 아이콘

Tabler outline 웹폰트만 사용: `<i class="ti ti-NAME" aria-hidden="true">` — `-filled` suffix 금지.

### 텍스트 크기

- 화면 제목: 14px, weight 500
- 항목 타이틀: 13px, weight 500
- 설명/보조: 11~12px, `var(--color-text-secondary)`
- 레이블: 11px, `var(--color-text-tertiary)`

### UX 멘트 작성 규칙

와이어프레임 안에 들어가는 모든 텍스트(버튼명, 안내문구, 레이블, 상태 메시지)는:
- **`~요` 체**로 통일 (예: "제출하기" → "제출할게요", "확인" → "확인했어요", "완료되었습니다" → "완료됐어요!")
- **짧고 명확하게** — 한 줄 안에 끝내기
- **행동 유도 버튼**은 결과 중심으로 (예: "다음" 대신 "서류 제출할게요", "등록 완료" 대신 "다 됐어요!")
- **안내 문구**는 사용자 입장에서 (예: "파일을 업로드하세요" 대신 "여기에 파일 올려주세요")
- **상태 메시지**는 친근하게 (예: "심사 중입니다" 대신 "지금 확인하고 있어요")

---

## STEP 4. 레이아웃 구성

단계별로 구분선(`divider`)으로 묶어 세로 배치.

```
[모바일 섹션]
  [단계1 구분선]  폰A  폰B
  [단계2 구분선]  폰C
  [완료 구분선]   폰D

[태블릿 섹션] ← 태블릿이 요청된 경우만
  [단계1 구분선]  태블릿A
  ...
```

---

## STEP 5. show_widget 호출

- `title`: `{서비스명}_wireframes`
- `loading_messages`: 한국어, 3~4개
- `widget_code`: `<style>` + HTML. DOCTYPE/html/head/body 태그 불필요.

---

## 주의사항

- `position: fixed` 금지
- `localStorage` 금지
- `display: none` 금지 (스트리밍 중 invisible)
- 외부 리소스: cdnjs, esm.sh, cdn.jsdelivr.net, unpkg.com, fonts.googleapis.com만 허용
- 프레임 내 최소 font-size 11px, line-height 1.5~1.7
- 시나리오에 "미결 사항" 있으면 와이어프레임 아래 간단한 메모로 표시

---

## 예시 출력 구조

```html
<style>
  .phone { width:280px; background:var(--color-background-primary); border-radius:24px; border:1.5px solid var(--color-border-secondary); overflow:hidden; display:inline-block; vertical-align:top; }
  .tablet { width:480px; background:var(--color-background-primary); border-radius:16px; border:1.5px solid var(--color-border-secondary); overflow:hidden; display:inline-block; vertical-align:top; }
  /* ... */
</style>

<h2 class="sr-only">서비스명 와이어프레임</h2>

<div style="padding:8px 4px;">
  <div class="divider">모바일</div>
  <div class="divider">1단계 — 약관 동의</div>
  <div style="display:flex;gap:20px;flex-wrap:wrap;padding:8px 0 12px;">
    <div><div class="phone">...</div><div class="screen-label">약관 동의</div></div>
  </div>

  <div class="divider">태블릿</div>
  <div class="divider">1단계 — 약관 동의</div>
  <div style="display:flex;gap:20px;flex-wrap:wrap;padding:8px 0 12px;">
    <div><div class="tablet">...</div><div class="screen-label">약관 동의</div></div>
  </div>
</div>
```
