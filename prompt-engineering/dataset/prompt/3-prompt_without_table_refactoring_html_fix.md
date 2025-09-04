## 프로젝트 개요
- HTML과 CSS를 참조하여 shadcn/ui 컴포넌트를 사용한 완전한 React 컴포넌트로 변환해주세요.
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

### 4단계: Next.js App Router 클라이언트 컴포넌트 설정

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

### 5단계: 개발 서버 실행 테스트

```bash
npm start

```

에러 없이 실행되면 환경 설정 완료!

---

## 중요한 구현 요구사항

- 모든 시각적 요소와 레이아웃, 화면 구조, 픽셀 단위 위치가 원본 결과와 100% 동일하게 재현되는 것입니다.
- HTML 및 CSS 화면에서 노출되는 모든 컨텐츠(타이틀, 입력 필드, 체크박스, 버튼, 테이블 등)가 React 컴포넌트 코드에서 하나도 누락되지 않도록 주의해서 작성해 주세요.

### 세부 요구사항
- shadcn/ui 컴포넌트만 사용하며, 각 요소의 스타일이나 레이아웃이 원본과 다를 경우 반드시 스타일 오버라이드로 원본을 100% 복제
- 모든 컨텐츠, 필드, 버튼, 체크박스(이름, 위치, 상태 아이콘 등)가 원본과 같이 완전히 포함되어야 합니다
- 컴포넌트 분리, 추상화보다는 원본 HTML/CSS 구조대로 각 요소를 빠짐없이 변환하는 데 집중해 주세요
- 코드 변환 후, 모든 버튼과 체크박스 등 UI 요소가 제대로 렌더링되는지 한 번씩 꼭 검토/확인한 후 코드를 완성해 주세요
- 픽셀 단위의 크기, 배치, 색상, 간격, hover/active 등 효과도 Fastidious하게 원본과 일치시켜 주세요
- 실제 바로 적용 가능한 완전한 TypeScript 기반 React 컴포넌트 코드와, 사용된 CSS를 별도로 제공해 주세요

### 모달 구현
모달 구현이 필요한 경우는 아래 요구사항을 충족하세요.
- shadcn/ui 모달의 기본 max-width와 max-height 고정 스타일을 반드시 오버라이드하여, 모달 크기가 내부 콘텐츠 크기에 따라 자동으로 유동적으로 늘어나도록 구현해주세요.
- 콘텐츠가 많을 경우에만 내부에 스크롤이 생기도록 overflow-y: auto를 적용하세요.
- 고정 크기 제한을 제거하거나 충분히 크게 설정해, 모달 내부 모든 콘텐츠가 잘리지 않고 전부 보이도록 보장해 주세요.

아래가 변환 요청 대상의 HTML과 CSS입니다:

## HTML 구조
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Optimized Modal</title>
    <link rel="stylesheet" href="optimized-modal.css">
</head>
<body>
    <div class="modal-overlay">
        <div class="modal">
            <!-- Modal Header -->
            <header class="modal-header">
                <h1 class="modal-title">Modal Title Inputplace-A</h1>
                <button class="close-button" aria-label="닫기">
                    <span class="close-icon"></span>
                </button>
            </header>

            <!-- Modal Content -->
            <main class="modal-content">
                <!-- Form Section -->
                <section class="form-section">
                    <div class="form-row">
                        <div class="form-group">
                            <label class="form-label required">Titleinputplace</label>
                            <select class="form-select">
                                <option>선택하세요.</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label class="form-label required">Area</label>
                            <select class="form-select">
                                <option>선택하세요.</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label class="form-label">Model 3</label>
                            <select class="form-select">
                                <option>선택하세요.</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label class="form-label">Car No.</label>
                            <select class="form-select">
                                <option>선택하세요.</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label class="form-label">ID Number</label>
                            <select class="form-select">
                                <option>선택하세요.</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label class="form-label">Child ID</label>
                            <select class="form-select">
                                <option>선택하세요.</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label class="form-label">Panamera</label>
                            <select class="form-select">
                                <option>선택하세요.</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label class="form-label">PPF Film</label>
                            <select class="form-select">
                                <option>선택하세요.</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label class="form-label">Film Type</label>
                            <select class="form-select">
                                <option>선택하세요.</option>
                            </select>
                        </div>
                    </div>

                    <div class="form-row">
                        <div class="form-group">
                            <label class="form-label">Section</label>
                            <select class="form-select">
                                <option>선택하세요.</option>
                            </select>
                        </div>
                        <div class="checkbox-group">
                            <input type="checkbox" id="recent-spec" class="checkbox">
                            <label for="recent-spec" class="checkbox-label">Recent 10years Spec(last use date not null)</label>
                        </div>
                        <button class="search-button">검색</button>
                    </div>
                </section>

                <!-- Data Display Section -->
                <section class="data-section">
                    <div class="data-table-container">
                        <!-- Table content would go here -->
                    </div>
                    <div class="data-summary">
                        <!-- Summary content would go here -->
                    </div>
                </section>
            </main>

            <!-- Modal Footer -->
            <footer class="modal-footer">
                <div class="footer-checkboxes">
                    <div class="checkbox-group">
                        <input type="checkbox" id="mail" class="checkbox">
                        <label for="mail" class="checkbox-label">Mail</label>
                    </div>
                    <div class="checkbox-group">
                        <input type="checkbox" id="later" class="checkbox">
                        <label for="later" class="checkbox-label">후결</label>
                    </div>
                    <div class="checkbox-group">
                        <input type="checkbox" id="pre-apply" class="checkbox">
                        <label for="pre-apply" class="checkbox-label">선적용</label>
                    </div>
                </div>
                <div class="footer-buttons">
                    <button class="button button-primary">Next</button>
                    <button class="button button-secondary">닫기</button>
                </div>
            </footer>
        </div>
    </div>
</body>
</html>
```

## CSS
```css
/* CSS Variables (Design Tokens) */
:root {
    /* Colors */
    --color-white: #FFFFFF;
    --color-neutral-1: #283037;
    --color-neutral-2: #384047;
    --color-neutral-9: #CCD1D6;
    --color-neutral-15: #565E66;
    --color-neutral-17: #90969D;
    --color-brand-primary: #3392D3;
    --color-danger: #FF4337;
    --color-bg-light: #F7F9FB;
    
    /* Borders */
    --border-color-light: #E4E9ED;
    --border-color-medium: #DADFE4;
    --border-color-dark: #CCD1D6;
    
    /* Typography */
    --font-family: 'SamsungOneKoreanNoF', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
    --font-size-xs: 12px;
    --font-size-sm: 14px;
    --font-size-md: 16px;
    --font-weight-normal: 400;
    --font-weight-bold: 700;
    --line-height-sm: 14px;
    --line-height-md: 20px;
    --letter-spacing: 0.8px;
    
    /* Spacing */
    --spacing-xs: 2px;
    --spacing-sm: 4px;
    --spacing-md: 6px;
    --spacing-lg: 8px;
    --spacing-xl: 16px;
    --spacing-xxl: 20px;
    
    /* Border Radius */
    --radius-sm: 2px;
    --radius-md: 6px;
    --radius-lg: 8px;
    
    /* Shadows */
    --shadow-modal: 0px 8px 14px 4px rgba(40, 48, 55, 0.14);
}

/* Reset and Base Styles */
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: var(--font-family);
    font-size: var(--font-size-sm);
    line-height: var(--line-height-md);
    color: var(--color-neutral-2);
    background-color: rgba(0, 0, 0, 0.5);
}

/* Modal Overlay */
.modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 1000;
}

/* Modal Container */
.modal {
    width: 1200px;
    height: 744px;
    background: var(--color-white);
    border-radius: var(--radius-lg);
    box-shadow: var(--shadow-modal);
    overflow: hidden;
    display: flex;
    flex-direction: column;
}

/* Modal Header */
.modal-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: var(--spacing-xl) var(--spacing-xxl) var(--spacing-xl) var(--spacing-xxl);
    border-bottom: 1px solid var(--border-color-light);
    background: var(--color-white);
    border-top-left-radius: var(--radius-md);
    border-top-right-radius: var(--radius-md);
}

.modal-title {
    font-size: var(--font-size-md);
    font-weight: var(--font-weight-normal);
    color: var(--color-neutral-1);
    margin: 0;
}

.close-button {
    background: transparent;
    border: none;
    padding: var(--spacing-xs);
    cursor: pointer;
    border-radius: var(--radius-sm);
    display: flex;
    align-items: center;
    justify-content: center;
}

.close-icon {
    width: 16px;
    height: 16px;
    position: relative;
}

.close-icon::before,
.close-icon::after {
    content: '';
    position: absolute;
    width: 10px;
    height: 10px;
    top: 3px;
    left: 3px;
    border: 1.2px solid var(--color-neutral-15);
    border-radius: var(--radius-sm);
}

/* Modal Content */
.modal-content {
    flex: 1;
    display: flex;
    flex-direction: column;
    background: var(--color-white);
}

/* Form Section */
.form-section {
    padding: var(--spacing-xl) var(--spacing-xxl);
}

.form-row {
    display: flex;
    align-items: flex-end;
    gap: var(--spacing-lg);
    margin-bottom: var(--spacing-xl);
}

.form-row:last-child {
    margin-bottom: 0;
    align-items: center;
}

.form-group {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-xs);
    min-width: 120px;
    max-width: 160px;
}

.form-label {
    font-size: var(--font-size-xs);
    font-weight: var(--font-weight-bold);
    color: var(--color-neutral-2);
    letter-spacing: var(--letter-spacing);
}

.form-label.required::after {
    content: '*';
    color: var(--color-danger);
    margin-left: 2px;
}

.form-select {
    width: 100%;
    padding: var(--spacing-xs) var(--spacing-md);
    background: var(--color-white);
    border: 1px solid var(--border-color-dark);
    border-radius: var(--radius-sm);
    font-family: var(--font-family);
    font-size: var(--font-size-sm);
    color: var(--color-neutral-17);
    letter-spacing: var(--letter-spacing);
    appearance: none;
    background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' fill='none' viewBox='0 0 20 20'%3e%3cpath stroke='%23565E66' stroke-linecap='round' stroke-linejoin='round' stroke-width='1.5' d='m6 8 4 4 4-4'/%3e%3c/svg%3e");
    background-position: right 6px center;
    background-repeat: no-repeat;
    background-size: 16px;
    padding-right: 28px;
}

.form-select:focus {
    outline: none;
    border-color: var(--color-brand-primary);
}

/* Checkbox Styles */
.checkbox-group {
    display: flex;
    align-items: center;
    gap: var(--spacing-md);
}

.checkbox {
    width: 14px;
    height: 14px;
    appearance: none;
    background: var(--color-white);
    border: 1px solid var(--border-color-dark);
    border-radius: 1.5px;
    cursor: pointer;
    position: relative;
}

.checkbox:checked {
    background: var(--color-brand-primary);
    border-color: var(--color-brand-primary);
}

.checkbox:checked::after {
    content: '✓';
    position: absolute;
    top: -2px;
    left: 2px;
    color: var(--color-white);
    font-size: 10px;
    font-weight: bold;
}

.checkbox-label {
    font-size: var(--font-size-xs);
    color: var(--color-neutral-15);
    letter-spacing: var(--letter-spacing);
    cursor: pointer;
    user-select: none;
}

/* Search Button */
.search-button {
    background: var(--color-brand-primary);
    color: var(--color-white);
    border: none;
    border-radius: var(--radius-sm);
    padding: var(--spacing-xs) var(--spacing-lg);
    font-family: var(--font-family);
    font-size: var(--font-size-sm);
    font-weight: var(--font-weight-bold);
    letter-spacing: var(--letter-spacing);
    cursor: pointer;
    margin-left: var(--spacing-xl);
}

.search-button:hover {
    background: #2a7bb8;
}

/* Data Section */
.data-section {
    flex: 1;
    display: flex;
    flex-direction: column;
    margin: 0 var(--spacing-xxl);
    border-top: 1px solid var(--border-color-light);
}

.data-table-container {
    flex: 1;
    background: var(--color-white);
    border: 1px solid var(--border-color-medium);
    min-height: 238px;
}

.data-summary {
    height: 238px;
    background: var(--color-bg-light);
    border: 1px solid var(--border-color-medium);
    border-top: none;
}

/* Modal Footer */
.modal-footer {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: var(--spacing-xl) var(--spacing-xxl);
    background: var(--color-white);
    border-top: 1px solid var(--border-color-light);
    border-bottom-left-radius: var(--radius-md);
    border-bottom-right-radius: var(--radius-md);
    position: relative;
}

.footer-checkboxes {
    display: flex;
    align-items: center;
    gap: var(--spacing-xl);
}

.footer-buttons {
    display: flex;
    align-items: center;
    gap: var(--spacing-md);
}

/* Button Styles */
.button {
    border: none;
    border-radius: var(--radius-sm);
    padding: var(--spacing-sm) var(--spacing-lg);
    font-family: var(--font-family);
    font-size: var(--font-size-sm);
    letter-spacing: var(--letter-spacing);
    cursor: pointer;
    transition: background-color 0.2s ease;
}

.button-primary {
    background: var(--color-brand-primary);
    color: var(--color-white);
    font-weight: var(--font-weight-bold);
}

.button-primary:hover {
    background: #2a7bb8;
}

.button-secondary {
    background: var(--color-white);
    color: var(--color-neutral-2);
    border: 1px solid var(--border-color-medium);
    font-weight: var(--font-weight-normal);
    min-width: 48px;
}

.button-secondary:hover {
    background: #f8f9fa;
}

/* Responsive Design */
@media (max-width: 1280px) {
    .modal {
        width: 95vw;
        height: 90vh;
        max-width: 1200px;
        max-height: 744px;
    }
}

@media (max-width: 768px) {
    .form-row {
        flex-wrap: wrap;
    }
    
    .form-group {
        min-width: 100px;
        max-width: 140px;
    }
    
    .modal-header {
        padding: var(--spacing-lg) var(--spacing-xl);
    }
    
    .form-section {
        padding: var(--spacing-lg) var(--spacing-xl);
    }
    
    .modal-footer {
        padding: var(--spacing-lg) var(--spacing-xl);
        flex-direction: column;
        gap: var(--spacing-lg);
        align-items: stretch;
    }
    
    .footer-checkboxes {
        justify-content: center;
    }
    
    .footer-buttons {
        justify-content: center;
    }
}
```

## 중요
**Windows PowerShell 환경에서 실행하며, 명령어 연결 시 `;`를 사용합니다.**

**모달 크기가 고정되거나 잘리는 현상이 발생하지 않도록 반드시 스타일 검토 및 수정 병행 바랍니다.**

**shadcn/ui 또는 기타 라이브러리에서 기본으로 포함된 CSS 중, 특히 미디어 쿼리(@media) 내부에서 강제하는 max-width 스타일(예: .sm\:max-w-lg)은 절대 적용하지 말고, 존재한다면 무조건 제거 또는 주석 처리 후 오버라이드 해 주세요.**

**반드시 위의 환경 설정을 순서대로 완료한 후 개발을 시작해주세요. 모든 차이점이 해결된 완벽한 구현을 목표로 합니다.**