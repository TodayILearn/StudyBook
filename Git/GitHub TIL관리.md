# GitHub를 통한 TIL 관리

## TIL

`Today I Learn`

- TIL은 매일 학습하거나 경험한 것을 기록하는 형태의 학습 방법
- 주로 짧고 간결하게 작성하여 지속 가능성과 기록의 간편함을 목표로 함

## 회고

`Retrospective`

- 회고는 자신이 학습하거나 경험한 내용을 되돌아보고 분석하는 과정
  - 학습한 내용을 이해하고 정리
  - 개선해야 할 점과 앞으로의 방향성을 도출
  - 지속적인 학습과 성장의 기반을 제공

## TIL 관리에 GitHub 활용하기

### GitHub Repository 생성

#### 저장소 생성

- GitHub에서 새로운 TIL 저장소를 원격으로 생성
- 저장소 이름 (예: TIL)
- GitHub 웹 UI에서 직접 Add README.md 선택하여 초기화
- `New issue`

## Issue를 활용한 기록

### Issue를 이용한 일일 기록

- GitHub Issues 활용:
  - 매일 학습 내용을 새로운 Issue로 생성
  - Issue 제목은 날짜 또는 학습 주제 (예: 2025-01-31 TIL)
  - Markdown 문법을 활용해 내용을 정리
- 빈 템플릿 예시:

```
# TIL - 2025-01-31

## 오늘의 학습
- [ ] 주요 학습 내용 1
- [ ] 주요 학습 내용 2

## 느낀 점

## 참고 자료

```

- 채운 템플릿 예시:

```
# TIL - 2025-01-31

## 오늘의 학습
- **HTML**: `<div>` 태그의 역할과 활용 사례
- **HTML5 태그**: `<nav>` 태그를 활용한 내비게이션 구조 설계

## 느낀 점
- `<div>`는 단순 컨테이너지만 스타일링과 구조 설계에서 매우 유용함
- `<nav>` 태그를 사용하니 구조적이고 시맨틱한 내비게이션을 구현할 수 있었음

## 참고 자료
- [MDN HTML Div Element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/div)
- [MDN HTML Nav Element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/nav)
```

- Label 사용:
  - Issue에 Label을 붙여 카테고리 분류 (예: HTML, Learning, Tips)

### Issue Template 설정

- 효율적 기록을 위한 템플릿 작성:

  - Issue Template을 사용하여 일관된 형식 유지
  - Settings > Features > Set up templates

    1. Custom template

    2. Preview and edit

    3. Close preview

    4. Commit changes

    - GitHub 저장소에서 직접 .github/ISSUE_TEMPLATE/til.md 파일 생성

```
---
name: TIL
about: TIL
title: "TIL - YYYY-MM-DD"
labels: [TIL]
assignees: ''
---

# TIL - YYYY-MM-DD

## 오늘의 학습
- [ ] 주요 학습 내용 1
- [ ] 주요 학습 내용 2

## 느낀 점

## 참고 자료
```

## 작성 방식 선택

### 4줄 일기법

```
학습 내용, 이유, 결과, 느낀 점을 네 줄로 요약

```

- 빈 템플릿

```
# 4줄 일기 - YYYY-MM-DD

- **내용**:
- **이유**:
- **결과**:
- **느낀 점**:
```

- 채운 예시

```
# 4줄 일기 - 2025-01-31

- **내용**: `<section>` 태그를 활용하여 문서를 주제별로 구분
- **이유**: 복잡한 문서를 시맨틱하게 설계하기 위해
- **결과**: `<section>` 태그로 구조가 더 명확해지고 가독성이 향상됨
- **느낀 점**: 시맨틱 태그는 접근성과 유지보수성에 큰 도움이 됨
```

### 3F 방법 (Fact, Feeling, Finding)

`사실, 느낀 점, 배운 점 순서로 정리`

- 빈 템플릿

```
# 3F - YYYY-MM-DD

- **Fact**:
- **Feeling**:
- **Finding**:
```

- 채운 예시

```
# 3F - 2025-01-31

- **Fact**: `<header>` 태그를 활용해 문서의 헤더를 정의
- **Feeling**: HTML 구조가 시맨틱하게 설계되어 기분이 좋았음
- **Finding**: `<header>` 태그는 반복되는 상단 정보를 간결하게 정의하는 데 유용
```

- 4F & 5F:
  - 4F (Fact, Feeling, Finding, Future)
    - Future: 앞으로 적용하거나 학습할 계획
  - 5F (Fact, Feeling, Finding, Future, Feedback)
    - Feedback: 학습 내용에 대한 피드백 또는 개선 방안

### KPT 방법 (Keep, Problem, Try)

```
Keep: 유지할 점
Problem: 해결해야 할 문제
Try: 시도할 개선 방안
```

- 빈 템플릿

```
# KPT - YYYY-MM-DD

## Keep

## Problem

## Try
```

- 채운 예시

```
# KPT - 2025-01-31

## Keep
- 매일 TIL 작성 습관 유지
- HTML `<footer>` 태그의 활용 학습

## Problem
- `<footer>` 내의 스타일링이 제대로 적용되지 않음

## Try
- `<footer>`를 포함한 태그 구조를 다시 점검
- 다음 주까지 HTML5 레이아웃 설계 방식 추가 학습
```
