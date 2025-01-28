# Bootstrap이란? ([Bootstrap](https://getbootstrap.com/))

- Bootstrap은 Twitter에서 개발한 오픈소스 CSS 프레임워크로, 웹사이트와 애플리케이션의 빠른 개발을 지원
- HTML, CSS, JavaScript 기반의 컴포넌트와 유틸리티 클래스를 제공
- 다양한 디자인과 인터랙션을 쉽게 구현할 수 있음
  - 반응형 디자인 지원
  - 사전 정의된 스타일 및 컴포넌트
  - 커스터마이징 가능한 테마
  - 풍부한 문서화와 커뮤니티 지원

## CDN을 통한 설치

- Bootstrap을 설치하는 가장 간단한 방법은 CDN을 사용하는 것
- 아래 코드를 HTML 문서의 `<head>` 섹션에 추가하여 사용할 수 있음

```html
<!-- CSS (head) -->
<link
  href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
  rel="stylesheet"
  integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH"
  crossorigin="anonymous"
/>
<!-- JavaScript (body) -->
<script
  src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"
  integrity="sha384-YvpcrYf0tY3lHB60NNkmXc5s9fDVZLESaAA55NDzOxhy9GkcIdslK1eN7N6jIeHz"
  crossorigin="anonymous"
></script>
```

# **기본 사용법**

## Typography

- Bootstrap은 다양한 텍스트 스타일링 클래스를 제공

```html
<h1 class="display-1">디스플레이 헤딩</h1>
<p class="text-muted">흐린 텍스트</p>
<p class="text-primary">주요 텍스트</p>
<p class="fw-bold">굵은 텍스트</p>
```

### 종류

- **헤딩**: `display-{1-6}`, `h1` ~ `h6`
- **텍스트 강조**: `fw-bold`, `fw-light`, `fst-italic`, `fst-normal`
- **정렬**: `text-start`, `text-center`, `text-end`
- **트렁케이션**: `text-truncate` (긴 텍스트를 말줄임표로 표시)
- **색상**: `text-{color}` (예: `text-primary`, `text-danger`)

## Colors

- 색상 클래스를 사용해 텍스트와 배경에 스타일을 적용할 수 있음

```html
<p class="text-danger">위험 텍스트</p>
<p class="bg-warning text-dark">경고 배경</p>
```

### 주요 색상 목록

- **기본 색상**: `primary`, `secondary`, `success`, `danger`, `warning`, `info`, `light`, `dark`
- **텍스트 색상**: `text-{색상}` (예: `text-primary`, `text-danger`)
- **배경 색상**: `bg-{색상}` (예: `bg-warning`, `bg-info`)

## Buttons

- 버튼 스타일은 다양한 변형과 크기를 지원

```html
<button class="btn btn-primary">Primary</button>
<button class="btn btn-secondary btn-sm">Small Button</button>
<button class="btn btn-success btn-lg">Large Button</button>
```

### 종류

- **버튼 색상**: `btn-{color}` (예: `btn-primary`, `btn-danger`)
- **크기**: `btn-sm`, `btn-lg`
- **모양**: `btn-outline-{color}` (테두리만 있는 버튼)
- **비활성화**: `disabled` 속성 또는 `btn-disabled` 클래스
- **블록 버튼**: `btn-block` (부모 컨테이너의 전체 폭을 차지)

# 레이아웃

## Container

컨테이너는 콘텐츠를 중앙에 정렬하고 여백을 설정

```html
<div class="container">
  <p>중앙 정렬된 콘텐츠</p>
</div>
```

### 종류

- `container`: 고정 폭
- `container-fluid`: 화면 전체 폭
- `container-{breakpoint}`: 특정 반응형 단위에서 고정 폭

### 주요 Breakpoint 목록

- `sm`: 작은 화면 (≥576px)
- `md`: 중간 화면 (≥768px)
- `lg`: 큰 화면 (≥992px)
- `xl`: 매우 큰 화면 (≥1200px)
- `xxl`: 초대형 화면 (≥1400px)

## Grid

- Bootstrap의 Grid 시스템은 12개의 열로 구성되며, 반응형 레이아웃을 지원
- 반응형 레이아웃은 다양한 화면 크기에 따라 콘텐츠가 자동으로 조정되도록 설계된 구조를 의미 → 동일한 코드로 모바일, 태블릿, 데스크톱 환경에서 최적의 레이아웃을 제공할 수 있음

```html
<div class="row">
  <div class="col-6">50% 폭</div>
  <div class="col-6">50% 폭</div>
</div>
```

### 주요 클래스

- `col-{breakpoint}-{n}`: 열의 크기를 지정
- `row`: 행 생성
- `g-{n}`: 열과 행 간의 간격 설정

## Utility Class

- 유틸리티 클래스는 간단한 작업을 빠르게 수행할 수 있도록 도와줌

```html
<p class="m-3 p-2 bg-light">여백과 패딩이 있는 박스</p>
<p class="text-center">가운데 정렬 텍스트</p>
<p class="d-none d-md-block">중간 화면 이상에서만 보이는 요소</p>
```

### 주요 유틸리티 클래스 종류

- **간격 설정**: `m-{number}`, `p-{number}` (예: `m-3`는 마진 3 적용, `p-2`는 패딩 2 적용)
- **텍스트 정렬**: `text-start`, `text-center`, `text-end`
- **디스플레이**: `d-none`, `d-block`, `d-{breakpoint}-none`, `d-{breakpoint}-block`
- **색상**: `text-{color}`, `bg-{color}`
- **가시성**: `visible`, `invisible`
- **플로트**: `float-start`, `float-end`, `clearfix`
- **Flex 관련**: `d-flex`, `justify-content-{option}`, `align-items-{option}`

## Flexbox

### Flex 컨테이너와 아이템

- Flexbox는 1차원 레이아웃 모델로, 행(row) 또는 열(column) 방향으로 아이템을 배치할 수 있음
- Flex 컨테이너는 `display: flex` 속성을 사용해 정의

```html
<div class="d-flex">
  <div class="p-2">아이템 1</div>
  <div class="p-2">아이템 2</div>
  <div class="p-2">아이템 3</div>
</div>
```

### Flex 컨테이너 속성

- `flex-direction`: 아이템 배치 방향 (`row`, `row-reverse`, `column`, `column-reverse`)
- `justify-content`: 주축 정렬 (`flex-start`, `flex-end`, `center`, `space-between`, `space-around`, `space-evenly`)
- `align-items`: 교차축 정렬 (`stretch`, `flex-start`, `flex-end`, `center`, `baseline`)
- `flex-wrap`: 아이템 줄바꿈 (`nowrap`, `wrap`, `wrap-reverse`)

### Flex 아이템 속성

- `order`: 아이템의 배치 순서 지정
- `flex-grow`: 남은 공간에서 아이템이 차지하는 비율 지정
- `flex-shrink`: 공간 부족 시 아이템의 축소 비율
- `flex-basis`: 아이템의 기본 크기 지정

```html
<div class="d-flex justify-content-center align-items-center">
  <div class="p-2 flex-grow-1">늘어나는 아이템</div>
  <div class="p-2">고정 아이템</div>
</div>
```

[UI | 디자인베이스](https://designbase.co.kr/dictionary_categories/ui/)

[Components – Material Design 3](https://m3.material.io/components)

[](https://getbootstrap.com/docs/5.3/components/)

# 주요 컴포넌트 (Component)

## 카드 (Card)

- 카드는 콘텐츠를 그룹화하거나 정리된 방식으로 정보를 표시할 때 사용

```html
<div class="card" style="width: 18rem;">
  <img src="..." class="card-img-top" alt="..." />
  <div class="card-body">
    <h5 class="card-title">카드 제목</h5>
    <p class="card-text">카드 내용</p>
    <a href="#" class="btn btn-primary">더 보기</a>
  </div>
</div>
```

### 주요 클래스

- `card`: 카드의 기본 클래스
- `card-body`: 카드의 본문 콘텐츠
- `card-title`, `card-text`: 제목과 텍스트 요소
- `card-img-top`: 카드 상단의 이미지
- `card-footer`: 카드 하단 영역
- `bg-{color}`: 카드 배경색 설정

## 캐러셀 (Carousel)

- 캐러셀은 여러 콘텐츠(예: 이미지 슬라이드)를 순차적으로 보여주는 컴포넌트

```html
<div id="carouselExample" class="carousel slide" data-bs-ride="carousel">
  <div class="carousel-inner">
    <div class="carousel-item active">
      <img src="..." class="d-block w-100" alt="..." />
    </div>
    <div class="carousel-item">
      <img src="..." class="d-block w-100" alt="..." />
    </div>
    <div class="carousel-item">
      <img src="..." class="d-block w-100" alt="..." />
    </div>
  </div>
  <button
    class="carousel-control-prev"
    type="button"
    data-bs-target="#carouselExample"
    data-bs-slide="prev"
  >
    <span class="carousel-control-prev-icon" aria-hidden="true"></span>
    <span class="visually-hidden">Previous</span>
  </button>
  <button
    class="carousel-control-next"
    type="button"
    data-bs-target="#carouselExample"
    data-bs-slide="next"
  >
    <span class="carousel-control-next-icon" aria-hidden="true"></span>
    <span class="visually-hidden">Next</span>
  </button>
</div>
```

### 주요 클래스

- `carousel`: 캐러셀의 기본 클래스
- `carousel-inner`: 캐러셀 아이템을 포함하는 컨테이너
- `carousel-item`: 각각의 슬라이드 콘텐츠
- `active`: 현재 활성화된 슬라이드
- `carousel-control-prev`, `carousel-control-next`: 이전 및 다음 버튼
- `carousel-indicators`: 슬라이드 인디케이터

## 모달 (Modal)

- 모달은 팝업 창을 제공하여 추가 정보를 표시하거나 사용자 입력을 받을 때 사용

```html
<button
  type="button"
  class="btn btn-primary"
  data-bs-toggle="modal"
  data-bs-target="#exampleModal"
>
  모달 열기
</button>

<div
  class="modal fade"
  id="exampleModal"
  tabindex="-1"
  aria-labelledby="exampleModalLabel"
  aria-hidden="true"
>
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">모달 제목</h5>
        <button
          type="button"
          class="btn-close"
          data-bs-dismiss="modal"
          aria-label="Close"
        ></button>
      </div>
      <div class="modal-body">모달 내용</div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">
          닫기
        </button>
        <button type="button" class="btn btn-primary">저장</button>
      </div>
    </div>
  </div>
</div>
```

### 주요 클래스

- `modal`: 모달의 기본 클래스
- `modal-dialog`: 모달 창 레이아웃
- `modal-content`: 모달 콘텐츠를 감싸는 컨테이너
- `modal-header`, `modal-body`, `modal-footer`: 모달의 세부 구성 요소
- `fade`: 모달이 부드럽게 나타나는 애니메이션 효과

## 네비게이션 (Navigation)

- Bootstrap의 네비게이션은 메뉴와 탐색 기능을 제공하는 데 사용
- 일반적으로 헤더나 사이드바에 사용되며, 반응형 디자인을 지원

```html
<nav class="navbar navbar-expand-lg navbar-light bg-light">
  <a class="navbar-brand" href="#">Brand</a>
  <button
    class="navbar-toggler"
    type="button"
    data-bs-toggle="collapse"
    data-bs-target="#navbarNav"
    aria-controls="navbarNav"
    aria-expanded="false"
    aria-label="Toggle navigation"
  >
    <span class="navbar-toggler-icon"></span>
  </button>
  <div class="collapse navbar-collapse" id="navbarNav">
    <ul class="navbar-nav">
      <li class="nav-item">
        <a class="nav-link active" href="#">Home</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">Features</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">Pricing</a>
      </li>
    </ul>
  </div>
</nav>
```

### 주요 클래스

- `navbar`: 네비게이션 바의 기본 클래스
- `navbar-expand-{breakpoint}`: 특정 반응형 화면에서 확장
- `navbar-light`, `navbar-dark`: 네비게이션 바 색상 테마
- `bg-{color}`: 배경색 설정
