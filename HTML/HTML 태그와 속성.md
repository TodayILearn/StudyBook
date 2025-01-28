# 태그와 속성

## HTML 태그의 개념과 구조

- HTML 태그는 웹 페이지의 구조와 내용을 정의하는 기본 구성 요소
- 태그는 꺾쇠괄호(`<>`)로 둘러싸인 키워드로 표현

```html
<태그명>내용</태그명>
```

### 열린 태그와 닫힌 태그

1. 열린 태그와 닫힌 태그가 있는 요소

   ```html
   <태그명>내용</태그명>
   ```

2. 빈 요소

   ```html
   <태그명 />
   ```

## 속성의 정의와 사용 방법

- 속성은 HTML 요소에 대한 추가 정보를 제공
- 속성은 항상 열린 태그 안에 위치하며, 이름과 값으로 구성

```html
<태그명 속성명="속성값">내용</태그명>
```

### 주요 글로벌 속성

- **class**: 요소를 분류하거나 그룹화하는 데 사용
- **id**: 페이지 내에서 요소를 고유하게 식별
- **style**: 인라인 CSS 스타일을 적용할 때 사용

```html
<div class="container" id="main-content" style="background-color: #f0f0f0;">
  <p>이것은 단락입니다.</p>
</div>
```

# 주요 태그

## 문서 구조 태그

- `<html>`: 전체 HTML 문서의 루트 요소
- `<head>`: 문서의 메타데이터 포함
- `<body>`: 웹 페이지에 표시되는 모든 콘텐츠 포함

```html
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <title>페이지 제목</title>
  </head>
  <body>
    <h1>웹 페이지 내용</h1>
  </body>
</html>
```

## 텍스트 관련 태그

- `<h1>` ~ `<h6>`: 제목을 나타냄
- `<p>`: 단락을 나타냄
- `<span>`: 인라인 텍스트를 그룹화
- `<strong>`: 중요한 텍스트를 강조

```html
<h1>가장 중요한 제목</h1>
<p>이것은 <span style="color: blue;">단락</span>입니다.</p>
<p>이것은 <strong>중요한</strong> 내용입니다.</p>
```

## 목록 태그

- `<ul>`: 순서가 없는 목록
- `<ol>`: 순서가 있는 목록
- `<li>`: 목록의 각 항목

```html
<ul>
  <li>항목 1</li>
  <li>항목 2</li>
</ul>
<ol>
  <li>항목 1</li>
  <li>항목 2</li>
</ol>
```

## 링크와 이미지 태그

a: 하이퍼링크 생성

```
<a href="https://www.example.com">링크 텍스트</a>
```

img: 이미지를 삽입

```
<img src="image.jpg" alt="이미지 설명">
```

## 테이블 태그

- 테이블 태그는 데이터를 행(row)과 열(column) 형태로 표시하기 위해 사용
- 각 테이블은 `<table>` 요소로 정의
- 행은 `<tr>`(table row), 열은 `<td>`(table data)로 구성
- 헤더 셀은 `<th>`(table header)로 정의

### 주요 태그

- `<table>`: 테이블의 전체 구조 정의
- `<tr>`: 테이블의 행 정의
- `<td>`: 행 내의 데이터 셀 정의
- `<th>`: 테이블 헤더 셀 정의, 기본적으로 굵게 표시되고 중앙 정렬됨

```html
<table>
  <tr>
    <th>이름</th>
    <th>나이</th>
    <th>직업</th>
  </tr>
  <tr>
    <td>김자바</td>
    <td>25</td>
    <td>개발자</td>
  </tr>
  <tr>
    <td>박파이썬</td>
    <td>30</td>
    <td>데이터 분석가</td>
  </tr>
</table>
```

# 블록과 인라인 요소

## 블록 레벨 요소

- 새 줄에서 시작하며 전체 너비를 차지
- 수직으로 쌓이는 특성을 가지며, 주로 페이지 레이아웃과 구조를 정의하는 데 사용

### 대표적인 블록 레벨 요소

- `<div>`: 일반 컨테이너로 다른 요소를 그룹화할 때 사용
- `<p>`: 단락을 나타냄
- `<h1>` ~ `<h6>`: 제목을 정의
- `<ul>`, `<ol>`, `<li>`: 목록을 구성

## 인라인 요소

- 콘텐츠의 흐름을 방해하지 않고 같은 줄에 표시
- 필요한 만큼의 너비만 차지하며, 주로 텍스트나 이미지와 같은 간단한 콘텐츠를 나타냄

### 대표적인 인라인 요소

- `<span>`: 텍스트의 특정 부분을 그룹화하거나 스타일을 적용하는 데 사용
- `<a>`: 하이퍼링크를 생성
- `<strong>`: 텍스트를 강조

# 폼과 인풋

## `<form>` 태그

- `<form>` 태그는 사용자 입력을 수집하고 서버로 전송하는 대화형 영역을 정의
- 이 태그는 `action` 속성을 통해 데이터를 보낼 URL을 지정하고, `method` 속성으로 전송 방식을 결정 (`GET` 또는 `POST`)

```html
<form action="/submit-form" method="post">
  <label for="username">사용자 이름:</label>
  <input type="text" id="username" name="username" placeholder="이름 입력" />

  <label for="password">비밀번호:</label>
  <input
    type="password"
    id="password"
    name="password"
    placeholder="비밀번호 입력"
  />

  <button type="submit">제출</button>
</form>
```

## `<input>` 태그

- `<input>` 태그는 다양한 형태의 사용자 입력을 수집하기 위해 사용
- `type` 속성을 통해 입력 형식을 지정할 수 있음
- `text`: 텍스트 입력 필드
- `password`: 비밀번호 입력 필드
- `radio`: 라디오 버튼
- `checkbox`: 체크박스
- `submit`: 폼 전송 버튼

```html
<label for="gender-male">남성:</label>
<input type="radio" id="gender-male" name="gender" value="male" />

<label for="gender-female">여성:</label>
<input type="radio" id="gender-female" name="gender" value="female" />
```

## 시맨틱 태그

HTML5에서 추가된 시맨틱 태그는 문서의 의미를 명확히 표현하고, 검색 엔진 및 스크린 리더와 같은 접근성 도구의 해석을 도움

### 주요 시맨틱 태그

- `<header>`: 문서나 섹션의 헤더를 정의
- `<nav>`: 내비게이션 링크를 그룹화
- `<section>`: 문서의 주제를 구분하는 섹션을 정의
- `<article>`: 독립적인 콘텐츠를 나타냄
- `<footer>`: 문서나 섹션의 바닥글을 정의
