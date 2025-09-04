## 프로젝트 개요

- HTML 구조를 shadcn/ui 컴포넌트를 사용한 완전한 React 컴포넌트로 변환해주세요.
- Windows PowerShell 환경에서 실행하며, 명령어 연결 시 `&&`을 사용하지 않고 `;`를 사용합니다.

## 핵심 체크리스트 (반드시 모두 완료)

### 환경 설정 (빈 프로젝트 기준 - 반드시 순서대로 실행)

### 1단계: React 프로젝트 생성

```bash
git clone <https://github.com/fluidcoding-agent/next-js-template.git> my-project
cd my-project
Remove-Item -Recurse -Force .git

```

### 2단계: shadcn/ui 필요한 컴포넌트 설치

```bash
npx shadcn@latest add dialog button sonner table select input checkbox

```

### 3단계: Samsung 폰트 설정 추가

- Tailwind CSS v4에서는 `app/globals.css` 파일의 `@theme` 섹션에 다음 폰트 설정을 추가:
    
    ```css
    @theme inline {
      --font-sans: var(--font-geist-sans), SamsungOneKoreanNoF, Samsung Sharp Sans, NotoSans, sans-serif;
      // 기존 설정들 유지
    }
    
    ```
    

### 4단계: CSS 변수 및 커스텀 클래스 설정

### CSS 변수 정의

```css
/* app/globals.css에 추가 */
:root {
  --modal-font-family: 'SamsungOneKoreanNoF', 'Samsung Sharp Sans', 'NotoSans', sans-serif;
  --modal-overlay-bg: rgba(0, 0, 0, 0.3);
  --modal-border-color: #f0f0f1;
  --modal-title-color: #2c3036;
  --modal-text-color: #000000;
  --modal-error-color: #ff4337;
  --modal-link-color: #515e94;
  --modal-copy-bg: #edf2f4;
  --modal-button-border: #dadfe4;
  --modal-button-hover: #b2b6bb;
  --modal-focus-color: #0077c8;
}

```

### 접근성 숨김 클래스

```css
.a11y-hidden {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}

/* shadcn/ui VisuallyHidden 대안 */
.visually-hidden {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}

```

### 5단계: Next.js App Router 클라이언트 컴포넌트 설정

### A. 페이지 파일에 "use client" 추가

`app/page.tsx` 파일 최상단에 다음을 추가:

```tsx
"use client";

// 기존 import 문들...

```

### B. 모달 컴포넌트에 "use client" 추가

생성할 모달 컴포넌트 파일 최상단에도 다음을 추가:

```tsx
"use client";

// React Hook (useState, useEffect 등) 사용을 위해 필수

```

### 6단계: 개발 서버 실행 테스트

```bash
npm start

```

에러 없이 실행되면 환경 설정 완료!

---

## HTML 구조

```html

```

## 컴포넌트 트리 예시

```
Page
└─ body
   └─ #app
      └─ .modal-wrap.shared-link   <!-- 전체 모달 배경/컨테이너 -->
         ├─ .modal-dialog          <!-- 중앙정렬 다이얼로그 래퍼 -->
         │  └─ .modal-content      <!-- 모달 콘텐츠 박스 -->
         │     ├─ .modal-header    <!-- 헤더: 제목 + 닫기 버튼 -->
         │     ├─ .modal-body      <!-- 본문: 안내 텍스트 + 복사 박스 -->
         │     └─ .modal-footer    <!-- 푸터: 닫기 버튼 -->
         └─ .note-layer-wrap       <!-- 추가 노트 레이어 (숨김 처리) -->

```

- 위의 예시와 같은 컴포넌트 트리 구조를 고려해서 구현해주세요.

## 중요한 구현 요구사항

### 1. **전체 레이아웃 요구사항**

- 전체 모달의 크기는 1200px 너비, 744px 높이로 고정합니다.
- 모달의 position은 relative로 설정하고, 내부 주요 섹션(타이틀, 입력 필드, 테이블, 버튼 등)은 position: absolute 또는 flex를 활용해 정확한 위치에 배치하세요.
- 모달에 box-shadow(0px 8px 14px 4px rgba(40, 48, 55, 0.14)), border-radius(8px), overflow: hidden을 적용하세요.
- 각 내부 영역의 크기와 위치를 px 단위로 명확히 지정하세요.
- 

### 2. **섹션별 상세 구현**

아래와 같이 모달 내부를 여러 섹션으로 나눠서 구현하세요:

### 2.1 상단 타이틀 영역

- 모달의 최상단에 위치하며, 배경색과 높이(53px), 좌우 padding(20px, 16px), border-radius(6px) 적용
- flex 레이아웃으로 제목과 닫기 버튼을 양쪽 끝에 배치
- 제목은 좌측 정렬, 닫기 버튼은 우측 정렬

### 2.2 입력 필드 그룹

- Titleinputplace, Area, Model 3, Car No., ID Number, Child ID, Panamera, PPF Film, Film Type 등
- 각 필드는 라벨과 필수 표시(*)를 포함하고, 가로로 나란히 배치
- 각 필드 너비 120~160px, gap 8px

### 2.3 체크박스 그룹

- Mail, 후결, 선적용 등 체크박스를 하단 또는 우측에 배치
- 각 체크박스는 라벨과 상태(Enabled/Off)를 명확히 표현
- 상태별 디자인: Enabled/Disabled, Checked/Unchecked 구분
- 각 상태별로 아이콘(체크 표시 등)의 유무와 위치를 명확히 표현
- hover 및 active 시의 스타일 변화를 구체적으로 구현

### 2.4 테이블 영역

- 2개의 테이블(상단/하단), 각 테이블은 행/열 구조로 구성
- Total 값(예: 10)을 표시
- 테이블의 크기, 위치, border, 배경색을 명확히 지정
- 각 셀에 들어가는 데이터 타입(텍스트, 숫자 등) 명시
- 동적 데이터와 연동되는 부분을 명확히 기술

### 2.5 하단 버튼 영역

- 버튼 2개(Primary, Secondary) 또는 필요에 따라 배치
- 위치와 스타일(색상, border-radius 등) 명확히 지정

### 3. **디자인 시스템 준수**

- 모든 컴포넌트와 UI 요소는 삼성 디자인 시스템을 따라야 합니다
- SamsungOneKoreanNoF 폰트를 사용하고, 색상 변수, 간격, border, background 등 디자인 시스템의 가이드라인을 반드시 준수하세요
- CSS 변수를 활용한 색상 관리
- `:hover`, `:focus`, `:active` 상태 정확히 구현

### 4. **정확한 배치 및 정렬**

- Page: `position: fixed; inset: 0;`
- `.modal-dialog`: 화면 전체를 덮는 부모 컨테이너, `display: flex; align-items: center; justify-content: center;`
- `.modal-content`: 카드 형태의 박스, `display: flex; flex-direction: column;`
- `.modal-header`: `display: flex; justify-content: space-between; align-items: center;`, `margin-bottom: 16px; border-bottom: 1px solid #e0e0e0;`
- `.modal-body`: `display: flex; flex-direction: column; gap: 12px;`, `flex: 1; margin-bottom: 24px;`
- `.modal-footer`: `display: flex; justify-content: flex-end;`, `padding-top: 16px; border-top: 1px solid #e0e0e0;`

### 5. **접근성 구현 (필수)**

- **DialogTitle 필수 포함**: DialogContent 사용 시 반드시 DialogTitle을 포함해야 합니다
- **VisuallyHidden 사용**: 제목을 시각적으로 숨기려면 `<VisuallyHidden><DialogTitle>제목</DialogTitle></VisuallyHidden>` 형태로 구현
- ESC 키로 모달 닫기
- Tab 키로 요소 간 이동
- Enter/Space로 버튼 활성화
- 적절한 ARIA 속성 설정
- 스크린 리더를 위한 숨김 텍스트(a11y-hidden 클래스)

**디자인 스펙:**

- **모달 크기**: 1200px 너비, 744px 높이, 중앙 정렬
- **배경**: box-shadow(0px 8px 14px 4px rgba(40, 48, 55, 0.14)), border-radius(8px), overflow: hidden
- **모달 배경**: 흰색 (#ffffff)
- **헤더**: 높이 53px, padding(20px, 16px), flex 레이아웃
- **입력 필드**: 각 필드 너비 120~160px, gap 8px, 라벨과 필수 표시(*) 포함
- **체크박스**: 상태별 디자인 구분, hover/active 효과
- **테이블**: 2개 테이블, 행/열 구조, Total 값 표시, 동적 데이터 연동
- **버튼**: Primary/Secondary 스타일, 정확한 위치와 크기

**사용할 shadcn/ui 컴포넌트:**

- Dialog, DialogContent, DialogOverlay, DialogTitle (필수)
- Button, Checkbox, Input, Select
- Table (테이블 컴포넌트)

**중요한 접근성 요구사항:**

- DialogContent를 사용할 때 반드시 DialogTitle을 포함해야 합니다
- 제목을 시각적으로 숨기려면 DialogTitle을 VisuallyHidden 컴포넌트로 감싸세요
- 예시: `<VisuallyHidden><DialogTitle>Modal Title</DialogTitle></VisuallyHidden>`
- 이는 스크린 리더 사용자를 위한 필수 접근성 요구사항입니다

**요청사항:**

1. 위의 환경 설정을 먼저 완료한 후 코딩을 시작해주세요
2. **접근성 필수 준수**: DialogContent와 함께 DialogTitle을 반드시 포함하고, 필요시 VisuallyHidden으로 감싸세요
3. **정확한 위치 구현**: HTML 구조의 모든 position: absolute 좌표를 정확히 재현해주세요
4. **픽셀 단위 정확성**: 모든 크기와 위치를 px 단위로 정확히 구현해주세요
5. 완전한 TypeScript React 컴포넌트 코드를 작성해주세요
6. CSS 변수와 커스텀 클래스를 활용하여 원본과 정확히 일치하는 스타일링을 구현해주세요
7. shadcn/ui 기본 스타일을 필요시 오버라이드하여 원본 HTML과 일치시켜주세요
8. 모든 상태(기본, 호버, 포커스, 액티브)에서 정확한 색상과 효과를 구현해주세요
9. 상태 관리 (모달 열기/닫기, 폼 입력 상태)를 포함해주세요
10. 실제로 바로 사용할 수 있는 완성된 코드를 제공해주세요
11. 타입 안전성을 보장하는 완전한 TypeScript 구현을 해주세요

**Windows PowerShell 환경에서 실행하며, 명령어 연결 시 `;`를 사용합니다.**

**중요: 반드시 위의 환경 설정을 순서대로 완료한 후 개발을 시작해주세요. 모든 차이점이 해결된 완벽한 구현을 목표로 합니다.**