# CSS 문법 기초

- **선택자(Selector)**: 스타일을 적용할 HTML 요소를 지정
- **속성(Property)**: 변경하고자 하는 스타일의 종류
- **값(Value)**: 속성에 적용할 구체적인 스타일 값
- **선언(Declaration)**: 속성과 값의 쌍
- **규칙(Rule)**: 선택자와 선언 블록의 조합

```css
선택자 {
  속성: 값;
  속성: 값;
}

/* 구체적인 예시 */
h1 {
  color: blue;
  font-size: 18px;
}
```

## CSS 적용 방법

### 인라인 스타일

- HTML 요소 내부에 직접 스타일 적용
- 우선순위가 가장 높지만, 재사용성이 낮음

```html
<p style="color: red; font-size: 16px;">이것은 빨간색 텍스트입니다.</p>
```

### 내부 스타일시트

- HTML 문서의 `<head>` 섹션 내 `<style>` 태그에 CSS 작성
- 해당 HTML 문서에만 적용되는 스타일

```html
<head>
  <style>
    p {
      color: blue;
      font-size: 14px;
    }
  </style>
</head>
```

### 외부 스타일시트

- 별도의 .css 파일에 스타일 정의
- HTML 문서의 `<head>` 섹션에서 링크로 연결
- 가장 권장되는 방식으로, 여러 페이지에 일관된 스타일 적용 가능

```html
<!-- HTML 파일 -->
<head>
  <link rel="stylesheet" href="styles.css" />
</head>
```

styles.css 파일:

```css
/* CSS 파일 */
p {
  color: green;
  font-size: 18px;
}
```

## CSS 주석

- CSS 주석은 코드의 설명을 추가하거나 특정 코드를 비활성화하는 데 사용
- 주석은 브라우저에서 무시되며, 코드 가독성을 높이는 데 유용
- CSS 주석은 `/*`와 `*/` 사이에 작성

```css
/* 이 코드는 본문 배경색을 설정합니다 */
body {
  background-color: #f0f0f0;
}

/* 다음 코드는 테스트 목적으로 작성된 주석입니다 */
p {
  color: gray;
}
```

## CSS 프로퍼티 값의 단위

### 키워드

- 각 프로퍼티에 따라 사용할 수 있는 키워드가 존재합니다.
- 예: `display` 프로퍼티의 키워드 - `block`, `inline`, `none` 등

### 크기 단위

- **px**: 픽셀 단위, 절대값
- **%**: 백분율 단위, 상대값
- **em**: 요소에 지정된 폰트사이즈에 상대적인 배수 단위
- **rem**: 최상위 요소(html)의 폰트사이즈 기준 배수 단위
- **Viewport** 단위: vh, vw, vmin, vmax

```css
/* 픽셀 단위 */
h1 {
  font-size: 16px;
}

/* 상대값 단위 */
.container {
  width: 50%;
}

/* Viewport 단위 */
.header {
  height: 10vh;
}
```

## 상속

- 상속되는 속성:
  - 폰트 관련 속성 (예: `font-family`, `color`)
- 상속되지 않는 속성:
  - 레이아웃 및 크기 관련 속성 (예: `width`, `margin`)

### 상속의 이점

- 중복 코드 감소
- 스타일 관리 효율성 향상

## 선택자 (Selector)

### 기본 선택자

- **요소 선택자**: HTML 태그 이름을 사용하여 요소 선택
- **클래스 선택자**: 특정 클래스를 가진 요소 선택 (`.` 사용)
- **ID 선택자**: 특정 ID를 가진 요소 선택 (`#` 사용)
- **전체 선택자**: 모든 요소 선택 (`*` 사용)

```css
/* 요소 선택자 */
p {
  color: blue;
}

/* 클래스 선택자 */
.highlight {
  background-color: yellow;
}

/* ID 선택자 */
#header {
  font-size: 24px;
}

/* 전체 선택자 */
* {
  margin: 0;
  padding: 0;
}
```

## 결합자

- 자손 선택자 (공백): 지정된 요소의 모든 자손 요소 선택
- 자식 선택자 (`>`): 지정된 요소의 직접적인 자식 요소만 선택
- 인접 형제 선택자 (`+`): 지정된 요소의 바로 다음에 오는 형제 요소 선택
- 일반 형제 선택자 (`~`): 지정된 요소 이후의 모든 형제 요소 선택

```css
/* 자손 선택자 */
div p {
  font-style: italic;
}

/* 자식 선택자 */
ul > li {
  list-style-type: square;
}

/* 인접 형제 선택자 */
h1 + p {
  font-weight: bold;
}

/* 일반 형제 선택자 */
h1 ~ p {
  color: gray;
}
```

## 선택자 우선순위와 명시도(Specificity)

CSS에서 여러 규칙이 동일한 요소에 적용될 때, 어떤 스타일이 우선적으로 적용될지 결정하는 방법

### 우선순위 (높은 순)

1. !important
2. 인라인 스타일
3. ID 선택자
4. 클래스 선택자
5. 요소 선택자

### 명시도 계산

- ID 선택자: 100점
- 클래스 선택자, 속성 선택자: 10점
- 요소 선택자: 1점

# CSS 배치1 (Box Model)

# 박스 모델의 개념과 구성 요소

- `CSS 박스 모델`은 웹 페이지의 레이아웃을 구성하는 기본 개념
- 모든 HTML 요소는 박스로 취급되며, 이 박스는 다음 네 가지 영역으로 구성
  1. **Content**: 요소의 실제 내용이 들어가는 영역
  2. **Padding**: 내용과 테두리 사이의 여백
  3. **Border**: 패딩 주변을 감싸는 테두리
  4. **Margin**: 요소의 외부 여백, 다른 요소와의 간격을 조정

```css
.box {
  /* Content */
  width: 300px;
  height: 200px;

  /* Padding */
  padding: 20px;

  /* Border */
  border: 2px solid black;

  /* Margin */
  margin: 30px;
}
```

# width, height, padding, border, margin

- `**width, height**`: 요소의 내용 영역의 너비와 높이를 지정
- `**padding**`: 내용과 테두리 사이의 여백을 지정
- `**border**`: 요소의 테두리를 지정
- `**margin**`: 요소의 외부 여백을 지정

<aside>
👉

각 속성은 top, right, bottom, left 값을 개별적으로 지정할 수 있음

</aside>

```css
.box {
  /* 너비와 높이 */
  width: 300px;
  height: 200px;

  /* 패딩 (시계 방향: 상 우 하 좌) */
  padding: 10px 20px 15px 25px;

  /* 테두리 */
  border-width: 2px;
  border-style: solid;
  border-color: #000;
  /* 축약형 */
  border: 2px solid #000;

  /* 마진 */
  margin: 10px 20px 15px 25px;
}
```

# box-sizing 속성 (content-box vs border-box)

>box-sizing 속성은 요소의 전체 크기를 계산하는 방식을 결정

- **content-box** (기본값): width와 height가 내용 영역만을 지정
- **border-box**: width와 height가 padding과 border를 포함한 전체 박스 크기를 지정

```css
/* content-box */
.box-content {
  box-sizing: content-box;
  width: 300px;
  padding: 20px;
  border: 10px solid black;
  /* 실제 너비: 300px + (20px * 2) + (10px * 2) = 360px */
}

/* border-box */
.box-border {
  box-sizing: border-box;
  width: 300px;
  padding: 20px;
  border: 10px solid black;
  /* 실제 너비: 300px (padding과 border 포함) */
}
```

# display 속성 (block, inline, inline-block)

display 속성은 요소가 문서 흐름에서 어떻게 배치되고 다른 요소와 어떻게 상호작용하는지를 결정

- **block**: 요소가 새 줄에서 시작하고, 사용 가능한 전체 너비를 차지
- **inline**: 요소가 현재 줄에 머물며, 내용만큼의 공간만 차지
- **inline-block**: inline처럼 한 줄에 표시되지만, block처럼 width, height, padding, margin 설정 가능

```css
.block-element {
  display: block;
  width: 300px;
  height: 100px;
  margin: 10px;
}

.inline-element {
  display: inline;
  /* width와 height는 적용되지 않음 */
  padding: 10px;
  /* margin은 좌우만 적용됨 */
}

.inline-block-element {
  display: inline-block;
  width: 100px;
  height: 100px;
  margin: 10px;
}
```

# overflow 처리

overflow 속성은 요소의 내용이 지정된 크기를 초과할 때 어떻게 처리할지를 결정

- **visible** (기본값): 내용이 요소 밖으로 넘쳐서 표시됨
- **hidden**: 넘치는 내용을 숨김
- **scroll**: 항상 스크롤바를 표시
- **auto**: 필요할 때만 스크롤바를 표시

```
.overflow-box {
  width: 200px;
  height: 100px;
  border: 1px solid black;
}

.overflow-visible { overflow: visible; }
.overflow-hidden { overflow: hidden; }
.overflow-scroll { overflow: scroll; }
.overflow-auto { overflow: auto; }
```

# CSS 배치 2 (Float, Position, Flex)

[Browse Fonts - Google Fonts](https://fonts.google.com/?lang=ko_Kore)

- 폰트 선택 → 우측 하단 `Get font` → `Get embed code`

```html
<!-- head -->
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link
  href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@100..900&display=swap"
  rel="stylesheet"
/>
```

```css
/* style */
body {
  font-family: "Noto Sans KR", serif;
  font-optical-sizing: auto;
  font-style: normal;
}
```

## Float

### float의 개념과 사용법

- float는 CSS에서 요소를 띄워서 텍스트 및 인라인 요소가 그 주위를 감싸도록 하는 속성
- 원래 이미지를 텍스트 왼쪽이나 오른쪽에 배치하기 위해 만들어졌지만, 현재는 레이아웃을 구성하는 데에도 널리 사용
  - 요소를 normal flow에서 벗어나게 함
  - 부모 요소의 왼쪽이나 오른쪽으로 이동시킴
  - 다른 콘텐츠가 float 요소 주위를 감싸게 함
  - float 요소는 다른 float 요소 옆에 위치할 수 있음

```css
.element {
  float: left | right | none | inherit;
}
```

- `left`: 요소를 왼쪽으로 띄웁니다.
- `right`: 요소를 오른쪽으로 띄웁니다.
- `none`: 기본값으로, float를 적용하지 않습니다.
- `inherit`: 부모 요소의 float 값을 상속받습니다.

### clear 속성

- clear 속성은 float의 영향을 제어하는 데 사용
- 특정 요소가 이전의 float 요소 아래로 내려가게 하여, float의 효과를 '해제'
  - float 요소 다음에 오는 요소에 적용
  - 해당 요소의 위쪽 마진이 float 요소 아래로 내려가게 함
  - 레이아웃에서 float로 인한 문제를 해결하는 데 유용

```css
.element {
  clear: left | right | both | none | inherit;
}
```

- `left`: 왼쪽의 float 요소를 clear합니다.
- `right`: 오른쪽의 float 요소를 clear합니다.
- `both`: 양쪽의 float 요소를 모두 clear합니다.
- `none`: 기본값으로, clear를 적용하지 않습니다.
- `inherit`: 부모 요소의 clear 값을 상속받습니다.


## **Position**

## position 속성 값

### **static (기본값)**

- 요소의 기본 위치 지정 방식
- 문서의 일반적인 흐름을 따름
- top, right, bottom, left, z-index 속성이 적용되지 않음

```css
.element {
  position: static;
}
```

### **relative**

- 요소를 일반적인 문서 흐름에 따라 배치한 후, 자신의 원래 위치를 기준으로 오프셋을 적용
- top, right, bottom, left 속성으로 위치를 조정할 수 있음
- 다른 요소의 레이아웃에 영향을 주지 않음

```css
.element {
  position: relative;
  top: 10px;
  left: 20px;
}
```

### **absolute**

- 요소를 일반적인 문서 흐름에서 제거하고, 가장 가까운 위치 지정 조상 요소(position이 static이 아닌 조상)를 기준으로 배치
- 조상 중 위치 지정 요소가 없다면 초기 컨테이닝 블록(보통)을 기준으로 함
- top, right, bottom, left 속성으로 위치를 지정

```css
.parent {
  position: relative;
}

.child {
  position: absolute;
  top: 50px;
  left: 50px;
}
```

### **fixed**

- 요소를 일반적인 문서 흐름에서 제거하고, 뷰포트(브라우저 창)를 기준으로 고정 위치에 배치
- 스크롤해도 항상 같은 위치에 유지
- top, right, bottom, left 속성으로 위치를 지정

```css
.element {
  position: fixed;
  top: 20px;
  right: 20px;
}
```

### **sticky**

- 요소를 일반적인 문서 흐름에 따라 배치하다가, 지정된 임계점(threshold)에 도달하면 fixed처럼 동작
- 스크롤 위치가 임계점을 넘어가면 요소가 화면에 고정
- 부모 컨테이너 내에서만 고정

```css
.element {
  position: sticky;
  top: 20px;
}
```

## z-index

- z-index는 요소의 쌓임 순서(stacking order)를 제어
- 높은 값을 가진 요소가 낮은 값을 가진 요소 위에 표시
- position 값이 static이 아닌 요소에만 적용
- 음수 값도 사용 가능

```css
.element1 {
  position: absolute;
  z-index: 2;
}

.element2 {
  position: absolute;
  z-index: 1;
}
```

# Flex

## Flex(Flexbox)의 개념과 장점

- **Flexbox(Flexible Box Layout Module)**는 컨테이너 내의 아이템 간 공간 배분과 정렬 기능을 제공하는 1차원 레이아웃 모델
- 주로 행이나 열 단위로 작동하며, 복잡한 계산 없이도 요소들의 크기와 순서를 유연하게 배치할 수 있음

### **장점**

- 복잡한 레이아웃을 간단하게 구현할 수 있음
- 컨테이너 내 요소의 크기가 불명확하거나 동적인 경우에도 효과적으로 대응
- 콘텐츠를 중앙 정렬하거나 균등하게 분배하는 것이 쉬움
- 요소의 순서를 CSS로 변경할 수 있어 반응형 디자인에 유용
- float나 position을 사용할 때보다 코드가 간결해짐

## Flex 컨테이너와 Flex 아이템

- **Flex 컨테이너**: `display: flex`를 적용한 부모 요소. Flexbox의 컨텍스트를 생성
- **Flex 아이템**: Flex 컨테이너의 직계 자식 요소. Flexbox 규칙에 따라 배치됨

```html
<div class="flex-container">
  <div class="flex-item">아이템 1</div>
  <div class="flex-item">아이템 2</div>
  <div class="flex-item">아이템 3</div>
</div>
```

```css
.flex-container {
  display: flex;
}
```

## 주요 Flexbox 속성

### display: flex

요소를 Flex 컨테이너로 정의

```css
.container {
  display: flex;
}
```

### flex-direction

Flex 아이템들의 배치 방향을 결정

```css
.container {
  flex-direction: row | row-reverse | column | column-reverse;
}
```

### justify-content

주축(main axis)을 따라 Flex 아이템들을 정렬

```css
.container {
  justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly;
}
```

### align-items

교차축(cross axis)을 따라 Flex 아이템들을 정렬

```css
.container {
  align-items: stretch | flex-start | flex-end | center | baseline;
}
```

### flex-wrap

Flex 아이템들이 컨테이너를 초과할 경우 줄 바꿈 여부를 결정

```css
.container {
  flex-wrap: nowrap | wrap | wrap-reverse;
}
```

### align-content

여러 행(row)이 있을 때 교차축(cross axis)을 따라 행 간의 정렬 방식을 지정

```css
.container {
  align-content: flex-start | flex-end | center | space-between | space-around | stretch;
}
```

## Flex 아이템 속성

### flex-grow

아이템이 Flex 컨테이너 내에서 남은 공간을 얼마나 차지할지 비율로 지정

```css
.item {
  flex-grow: 0 | 1 | <number>;
}
```

### flex-shrink

Flex 컨테이너의 크기가 줄어들 때 아이템이 축소되는 비율을 지정

```css
.item {
  flex-shrink: 0 | 1 | <number>;
}
```

### flex-basis

아이템의 기본 크기를 지정. `auto`는 내용에 따라 크기를 결정.

```css
.item {
  flex-basis: auto | <length>;
}
```

### flex (축약형)

`flex-grow`, `flex-shrink`, `flex-basis`를 한 번에 설정하는 축약 속성

```css
.item {
  flex: none | [<flex-grow> <flex-shrink> <flex-basis>];
}
```

### order

아이템의 배치 순서를 지정. 기본값은 `0`

```css
.item {
  order: <integer>;
}
```