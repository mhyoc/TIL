# SPA (Single Page Application)란?

> **SPA(Single Page Application)**는 **단일 HTML 페이지**를 기반으로 동작하는 웹 애플리케이션이다.  
> 페이지 전환 시 서버로부터 새로운 HTML을 받지 않고, **JavaScript를 통해 동적으로 콘텐츠를 업데이트**한다.  
> 사용자는 마치 네이티브 앱처럼 부드러운 화면 전환과 빠른 반응성을 경험할 수 있다.

---

## 왜 SPA가 필요한가?

전통적인 **MPA(Multi Page Application)** 방식에는 다음과 같은 한계가 있었다:

- **페이지 전환 시 전체 새로고침**  
  링크를 클릭할 때마다 서버에서 새로운 HTML을 받아와 전체 페이지가 다시 로드되어 깜빡임이 발생한다.
- **불필요한 리소스 재다운로드**  
  공통 요소(헤더, 푸터, CSS 등)도 매번 다시 다운로드되어 비효율적이다.
- **느린 사용자 경험**  
  페이지 전환마다 서버와의 통신이 필요하여 반응 속도가 느리다.
- **앱 같은 경험 제공 어려움**  
  네이티브 앱처럼 부드러운 전환과 즉각적인 피드백을 제공하기 어렵다.

SPA는 이러한 문제를 해결하여 **웹에서도 앱과 유사한 사용자 경험**을 제공하기 위해 등장했다.

---

## SPA의 특징

### 1. 단일 HTML 페이지
- 초기 로드 시 하나의 HTML 파일만 받아온다.
- 이후 모든 콘텐츠는 JavaScript로 동적으로 렌더링된다.

### 2. 클라이언트 사이드 라우팅
- 브라우저의 History API를 활용하여 URL 변경 없이 화면을 전환한다.
- `pushState`, `replaceState`를 사용하여 브라우저 히스토리를 관리한다.

### 3. 비동기 데이터 로딩
- AJAX/Fetch API를 통해 서버와 통신한다.
- 필요한 데이터만 JSON 형태로 받아와 화면을 업데이트한다.

### 4. 컴포넌트 기반 아키텍처
- React, Vue, Angular 같은 프레임워크와 함께 사용된다.
- 재사용 가능한 컴포넌트로 UI를 구성한다.

---

## SPA 동작 원리

### 1. 초기 로드
```
사용자 접속 → 서버에서 index.html + JS 번들 다운로드 → JS 실행 → 초기 화면 렌더링
```

### 2. 라우팅 처리
```
사용자가 링크 클릭 → JavaScript가 URL 변경 감지 → 해당 라우트의 컴포넌트 렌더링 → 필요한 데이터만 API로 요청
```

### 3. 데이터 업데이트
```
사용자 액션 → API 요청 → JSON 데이터 수신 → DOM 업데이트 (전체 새로고침 없음)
```

### 4. 브라우저 히스토리 관리
- `history.pushState()`: 새로운 히스토리 항목 추가
- `history.replaceState()`: 현재 히스토리 항목 교체
- `popstate` 이벤트: 뒤로가기/앞으로가기 처리

---

## SPA vs MPA (Multi Page Application)

| 항목 | MPA | SPA |
|------|-----|-----|
| **페이지 수** | 여러 개의 HTML 페이지 | 단일 HTML 페이지 |
| **페이지 전환** | 전체 새로고침 발생 | JavaScript로 동적 업데이트 |
| **서버 통신** | 매번 HTML 요청 | 필요한 데이터만 JSON으로 요청 |
| **초기 로딩** | 빠름 (작은 HTML) | 느림 (큰 JS 번들) |
| **이후 전환 속도** | 느림 (매번 서버 통신) | 빠름 (클라이언트에서 처리) |
| **SEO** | 우수 (완전한 HTML) | 취약 (초기 HTML 비어있음) |
| **서버 부하** | 높음 (매번 렌더링) | 낮음 (API만 제공) |
| **사용자 경험** | 전통적인 웹 경험 | 앱과 유사한 경험 |
| **캐싱** | 페이지 단위 | 컴포넌트/데이터 단위 |

---

## SPA 장점

### 1. 빠른 화면 전환
- 전체 페이지 새로고침 없이 필요한 부분만 업데이트
- 부드럽고 즉각적인 사용자 경험 제공

### 2. 서버 부하 감소
- 서버는 정적 파일과 API만 제공하면 됨
- 렌더링 로직이 클라이언트로 이동하여 서버 리소스 절약

### 3. 네이티브 앱과 유사한 UX
- 페이지 전환 애니메이션, 즉각적인 피드백 제공
- 오프라인 기능 구현 가능 (Service Worker 활용)

### 4. 개발 생산성 향상
- 컴포넌트 재사용으로 코드 중복 감소
- 상태 관리 라이브러리로 복잡한 상태 관리 용이

### 5. 모바일 친화적
- 네트워크 사용량 감소 (필요한 데이터만 전송)
- 터치 제스처, 스와이프 등 인터랙션 구현 용이

---

## SPA 단점

### 1. 초기 로딩 속도 느림
- 모든 JavaScript 번들을 처음에 다운로드해야 함
- 번들 크기가 크면 초기 로딩 시간이 길어짐
- **해결책**: 코드 스플리팅, 레이지 로딩, 트리 쉐이킹

### 2. SEO 취약
- 초기 HTML이 비어있어 검색 엔진이 콘텐츠를 인덱싱하기 어려움
- **해결책**: SSR(Server-Side Rendering), SSG(Static Site Generation), Prerendering

### 3. 브라우저 히스토리 관리 복잡
- 라우팅 로직을 직접 구현해야 함
- 뒤로가기/앞으로가기 처리 필요
- **해결책**: React Router, Vue Router 등 라우팅 라이브러리 사용

### 4. 메모리 관리 필요
- 페이지를 벗어나도 JavaScript가 계속 실행됨
- 메모리 누수 방지를 위한 주의 필요

### 5. 보안 고려사항
- XSS(Cross-Site Scripting) 공격에 취약할 수 있음
- 클라이언트 사이드에서 인증/인가 로직 처리 시 보안 주의 필요

---

## 주요 SPA 프레임워크/라이브러리

### React
- Facebook에서 개발한 UI 라이브러리
- 가상 DOM을 사용한 효율적인 렌더링
- 풍부한 생태계와 커뮤니티

### Vue.js
- 점진적으로 도입 가능한 프레임워크
- 쉬운 학습 곡선과 직관적인 문법
- React와 Angular의 중간 지점

### Angular
- Google에서 개발한 풀 프레임워크
- TypeScript 기반, 강력한 기능 내장
- 엔터프라이즈급 애플리케이션에 적합

### Svelte
- 컴파일 타임에 최적화
- 가상 DOM 없이 직접 DOM 조작
- 작은 번들 크기

---

## SPA 구현 예시

### 기본 구조
```html
<!-- index.html -->
<!DOCTYPE html>
<html>
<head>
  <title>SPA Example</title>
</head>
<body>
  <div id="app"></div>
  <script src="app.js"></script>
</body>
</html>
```

### 라우팅 예시 (의사 코드)
```javascript
// 라우트 정의
const routes = {
  '/': HomeComponent,
  '/about': AboutComponent,
  '/contact': ContactComponent
};

// 라우팅 처리
function router() {
  const path = window.location.pathname;
  const component = routes[path] || NotFoundComponent;
  render(component);
}

// History API 사용
function navigate(path) {
  window.history.pushState({}, '', path);
  router();
}
```

---

## SPA 최적화 기법

### 1. 코드 스플리팅
- 라우트별로 번들을 분리하여 필요한 부분만 로드
- 예: React의 `React.lazy()`, `Suspense`

### 2. 레이지 로딩
- 초기에 불필요한 리소스는 나중에 로드
- 이미지, 컴포넌트 등에 적용

### 3. 캐싱 전략
- Service Worker를 활용한 오프라인 지원
- API 응답 캐싱으로 불필요한 요청 감소

### 4. 번들 최적화
- 트리 쉐이킹으로 사용하지 않는 코드 제거
- 압축 및 최소화

### 5. SSR/SSG 하이브리드
- Next.js, Nuxt.js 등으로 초기 렌더링은 서버에서, 이후는 클라이언트에서 처리

---

## 언제 SPA를 사용해야 할까?

### SPA가 적합한 경우
- **대화형 웹 애플리케이션**  
  사용자 인터랙션이 많고 실시간 업데이트가 필요한 경우
- **관리자 대시보드**  
  SEO가 중요하지 않고 복잡한 UI가 필요한 경우
- **모바일 웹 앱**  
  네이티브 앱과 유사한 경험을 제공하고 싶은 경우
- **실시간 협업 도구**  
  채팅, 협업 플랫폼 등 즉각적인 피드백이 중요한 경우

### MPA가 더 적합한 경우
- **콘텐츠 중심 웹사이트**  
  블로그, 뉴스 사이트 등 SEO가 중요한 경우
- **마케팅 랜딩 페이지**  
  빠른 초기 로딩과 SEO가 최우선인 경우
- **간단한 웹사이트**  
  복잡한 인터랙션이 없고 정적 콘텐츠가 주인 경우

---

## 정리

| 항목 | 설명 |
|------|------|
| **SPA** | 단일 HTML 페이지로 동작하는 웹 애플리케이션 |
| **핵심 개념** | JavaScript로 동적 콘텐츠 업데이트, 클라이언트 사이드 라우팅 |
| **주요 장점** | 빠른 화면 전환, 앱과 유사한 UX, 서버 부하 감소 |
| **주요 단점** | 초기 로딩 느림, SEO 취약, 브라우저 히스토리 관리 복잡 |
| **대표 프레임워크** | React, Vue.js, Angular, Svelte |
| **적합한 프로젝트** | 대화형 웹앱, 관리자 대시보드, 모바일 웹 앱 |

---

### 참고
> https://developer.mozilla.org/ko/docs/Glossary/SPA  
> https://ko.wikipedia.org/wiki/%EC%8B%B1%EA%B8%80_%ED%8E%98%EC%9D%B4%EC%A7%80_%EC%95%A0%ED%94%8C%EB%A6%AC%EC%BC%80%EC%9D%B4%EC%85%98  
> https://developers.google.com/web/updates/2019/02/rendering-on-the-web?hl=ko

