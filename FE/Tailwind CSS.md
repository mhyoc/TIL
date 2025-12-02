# Tailwind CSS란?

> **Tailwind CSS는 유틸리티 우선(Utility-First) CSS 프레임워크**이다.  
> 미리 정의된 클래스들을 조합하여 빠르게 스타일을 적용할 수 있으며, HTML에서 직접 스타일링을 할 수 있다.  
> 기존 CSS 프레임워크와 달리 **컴포넌트가 아닌 유틸리티 클래스**를 제공한다.

---

## 왜 Tailwind CSS가 필요한가?

전통적인 CSS 작성 방식에는 여러 문제점이 있었다:

- **CSS 파일이 커지고 관리가 어려워짐**  
  프로젝트가 커질수록 CSS 파일이 비대해지고, 클래스 이름 충돌이나 스타일 오버라이드 문제가 발생한다.
- **컴포넌트 재사용성 저하**  
  비슷한 스타일을 여러 곳에서 사용하려면 매번 새로운 클래스를 만들거나 CSS를 복사해야 한다.
- **컨텍스트 전환 비용**  
  HTML과 CSS 파일을 오가며 작업해야 하므로 개발 흐름이 끊긴다.

Tailwind CSS는 이러한 문제를 해결하기 위해 **유틸리티 우선 접근법**을 채택했다.

---

## Tailwind CSS의 특징

### 1. 유틸리티 우선(Utility-First)
- 미리 정의된 작은 단위의 클래스들을 조합하여 사용
- 예: `flex`, `items-center`, `justify-between`, `bg-blue-500`, `text-white`

### 2. 인라인 스타일링
- HTML에서 직접 클래스를 추가하여 스타일링
- 별도의 CSS 파일 작성 최소화

### 3. 반응형 디자인 내장
- 접두사를 사용하여 반응형 클래스 적용
- 예: `sm:`, `md:`, `lg:`, `xl:`, `2xl:`

### 4. 다크 모드 지원
- `dark:` 접두사로 다크 모드 스타일 적용
- 예: `dark:bg-gray-800`, `dark:text-white`

### 5. JIT(Just-In-Time) 모드
- 사용하는 클래스만 최종 CSS에 포함
- 번들 크기 최적화

---

## Tailwind CSS 동작 원리

### 1. 설정 파일 (tailwind.config.js)
```javascript
module.exports = {
  content: ['./src/**/*.{html,js}'],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

### 2. 클래스 스캔
- `content`에 지정된 파일들을 스캔하여 사용된 Tailwind 클래스를 찾는다.

### 3. CSS 생성
- 사용된 클래스들만 최종 CSS 파일로 생성한다.
- JIT 모드에서는 실시간으로 필요한 클래스만 생성한다.

### 4. 빌드 과정
- PostCSS를 통해 Tailwind가 처리한 CSS를 최종 번들에 포함한다.

---

## Tailwind CSS vs 전통적인 CSS

| 항목 | 전통적인 CSS | Tailwind CSS |
|------|-------------|--------------|
| **작성 방식** | 별도 CSS 파일에 클래스 정의 | HTML에 유틸리티 클래스 직접 사용 |
| **재사용성** | 클래스 재사용 시 CSS 파일 수정 필요 | 클래스 조합으로 즉시 재사용 |
| **컨텍스트 전환** | HTML ↔ CSS 파일 이동 필요 | HTML에서만 작업 |
| **번들 크기** | 사용하지 않는 CSS도 포함될 수 있음 | 사용한 클래스만 포함 (JIT 모드) |
| **학습 곡선** | CSS 문법만 알면 됨 | Tailwind 클래스명 학습 필요 |
| **커스터마이징** | 자유롭게 작성 가능 | 설정 파일로 확장 가능 |

---

## Tailwind CSS 장점

### 1. 빠른 개발 속도
- 미리 정의된 클래스를 조합하여 빠르게 스타일링 가능
- HTML과 CSS 간 컨텍스트 전환 불필요

### 2. 일관된 디자인 시스템
- 디자인 토큰(색상, 간격, 폰트 크기 등)이 일관되게 관리됨
- 팀 내 디자인 일관성 유지 용이

### 3. 작은 번들 크기
- JIT 모드로 사용하지 않는 스타일은 최종 번들에 포함되지 않음
- PurgeCSS와 유사한 트리 쉐이킹 효과

### 4. 반응형 디자인 용이
- 접두사만 추가하면 반응형 스타일 적용 가능
- 예: `md:flex`, `lg:text-2xl`

### 5. 커스터마이징 가능
- `tailwind.config.js`에서 테마 확장 가능
- 프로젝트에 맞는 디자인 시스템 구축 가능

---

## Tailwind CSS 단점

### 1. HTML 가독성 저하
- 클래스명이 길어지면 HTML이 복잡해 보일 수 있음
- 예: `flex items-center justify-between bg-blue-500 text-white p-4 rounded-lg`

### 2. 학습 곡선
- Tailwind 클래스명을 외워야 함
- 초기에는 문서를 자주 참조해야 할 수 있음

### 3. 복잡한 애니메이션 제한
- 복잡한 커스텀 애니메이션은 별도 CSS 작성 필요
- `@apply` 지시어 사용 시 일부 제약 존재

### 4. 디자인 시스템 의존
- Tailwind의 디자인 토큰에 의존하게 됨
- 완전히 독자적인 디자인 시스템 구축 시 제약 가능

---

## 주요 유틸리티 클래스 예시

### 레이아웃
- `flex`, `grid`, `block`, `inline-block`
- `items-center`, `justify-between`, `gap-4`

### 간격(Spacing)
- `p-4` (padding), `m-2` (margin)
- `px-6` (padding-x), `py-3` (padding-y)

### 색상
- `bg-blue-500` (배경색)
- `text-gray-800` (텍스트 색상)
- `border-red-300` (테두리 색상)

### 타이포그래피
- `text-sm`, `text-lg`, `text-2xl` (폰트 크기)
- `font-bold`, `font-semibold` (폰트 굵기)

### 반응형
- `sm:text-lg` (640px 이상)
- `md:flex` (768px 이상)
- `lg:grid` (1024px 이상)

---

## 설치 및 사용

### 1. npm 설치
```bash
npm install -D tailwindcss
npx tailwindcss init
```

### 2. 설정 파일 생성
```javascript
// tailwind.config.js
module.exports = {
  content: ['./src/**/*.{html,js,jsx,ts,tsx}'],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

### 3. CSS 파일에 추가
```css
/* input.css */
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### 4. 빌드 설정
- PostCSS와 함께 사용하여 빌드 과정에서 Tailwind 처리

---

## 언제 Tailwind CSS를 사용해야 할까?

### Tailwind CSS가 적합한 경우
- 빠른 프로토타이핑이 필요한 프로젝트
- 일관된 디자인 시스템이 필요한 팀 프로젝트
- 컴포넌트 기반 프레임워크(React, Vue 등) 사용 시
- 반응형 디자인을 자주 구현해야 하는 경우

### 다른 방법을 고려해야 하는 경우
- 매우 복잡한 커스텀 애니메이션이 필요한 경우
- 기존 CSS 코드베이스가 큰 레거시 프로젝트
- 완전히 독자적인 디자인 시스템이 필요한 경우

---

## 정리

| 항목 | 설명 |
|------|------|
| **Tailwind CSS** | 유틸리티 우선 CSS 프레임워크 |
| **핵심 개념** | 미리 정의된 클래스를 조합하여 스타일링 |
| **주요 장점** | 빠른 개발, 일관된 디자인, 작은 번들 크기 |
| **주요 단점** | HTML 가독성 저하, 학습 곡선 |
| **적합한 프로젝트** | 컴포넌트 기반 프레임워크, 빠른 프로토타이핑 |

---

### 참고
> https://tailwindcss.com/docs  
> https://tailwindcss.com/docs/utility-first  
> https://tailwindcss.com/docs/just-in-time-mode

