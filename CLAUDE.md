# CLAUDE.md

이 파일은 Claude Code(claude.ai/code)가 이 저장소에서 작업할 때 참고하는 안내 문서입니다.

## 프로젝트 개요

빌드 도구, 프레임워크, 패키지 매니저가 없는 단일 페이지 정적 웹 애플리케이션입니다. 모든 코드는 `index.html` 하나에 HTML, CSS, JavaScript 인라인으로 작성되어 있습니다.

## 아키텍처

모든 코드는 `index.html` 안에 자급자족 형태로 존재합니다:

- **데이터** — `<script>` 블록 상단의 `quotes` 배열이 모든 명언 객체(`{ text, author, category }`)를 보관
- **상태** — 세 개의 변수로 관리: `filtered`(현재 필터된 명언 목록), `currentIndex`(현재 위치), `activeCategory`
- **렌더링** — `showQuote()`가 CSS 페이드 전환과 함께 카드 갱신을 담당; `buildFilters()`는 카테고리 변경 시 필터 버튼을 재렌더링
- **이벤트** — 다음 버튼, 랜덤 버튼, 필터 버튼이 각각 상태를 변경한 후 `showQuote()`를 호출

## 개발 방법

`index.html`을 브라우저에서 바로 열면 됩니다 — 별도 서버 불필요.

명언 추가 방법: `<script>` 블록의 `quotes` 배열에 객체를 추가하면 새 카테고리는 필터 바에 자동으로 나타납니다.
