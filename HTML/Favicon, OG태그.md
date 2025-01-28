# HTML 응용 (Favicon, OG)

## Favicon

- 웹 브라우저의 탭, 북마크, 즐겨찾기 목록 등에 표시되는 작은 아이콘
- **목적**: 사용자가 웹사이트를 쉽게 식별하도록 돕는 것

### Favicon 추가 방법

#### **이미지 준비**

- 정사각형 형태, 권장 크기: `16x16`, `32x32`
- 파일 형식: `.ico`, `.png`, `.svg`

#### **Realfavicongenerator 활용**

1. [Realfavicongenerator.net](https://realfavicongenerator.net/) 접속 → `Pick your favicon image`
2. 이미지 업로드 → 우측 하단 `Next`
3. 플랫폼별 설정 조정 (iOS, Android 등)
4. 생성된 Favicon 패키지 다운로드 `Download`

#### **HTML 코드 삽입**

```html
<head>
  <link rel="icon" type="image/png" href="./favicon-96x96.png" sizes="96x96" />
  <link rel="icon" type="image/svg+xml" href="./favicon.svg" />
  <link rel="shortcut icon" href="./favicon.ico" />
  <link rel="apple-touch-icon" sizes="180x180" href="./apple-touch-icon.png" />
  <link rel="manifest" href="./site.webmanifest" />
</head>
```

## Open Graph (OG) 태그

- Facebook에서 개발한 메타 태그 표준
- **목적**: 소셜 미디어 플랫폼에서 웹사이트를 공유할 때 콘텐츠 미리보기를 제어

### **주요 태그**

```html
<head>
  <meta property="og:title" content="페이지 제목" />
  <meta property="og:description" content="페이지 설명" />
  <meta property="og:image" content="https://www.example.com/image.jpg" />
</head>
```

### SEO와 OG 태그

#### **SEO(검색 엔진 최적화)**

- OG 태그는 소셜 미디어에서 콘텐츠 노출을 최적화하며 간접적으로 SEO에 기여
- 주요 SEO 메타 태그
  ```html
  <head>
    <meta name="description" content="검색 결과에 표시될 페이지 설명" />
    <meta name="keywords" content="HTML, Open Graph, SEO" />
  </head>
  ```
- 사용자 참여율과 클릭율 증가로 검색 엔진 순위 향상
- **권장 사항**:
  - `og:title` 및 `og:description`은 명확하고 매력적으로 작성
  - `og:image`는 고해상도 이미지 사용
  ## 예제

```html
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>OG 및 Favicon 예제</title>

    <!-- Favicon -->
    <link rel="icon" href="favicon.ico" type="image/x-icon" />
    <link rel="icon" href="favicon-32x32.png" sizes="32x32" type="image/png" />

    <!-- OG 태그 -->
    <meta property="og:title" content="내 웹사이트" />
    <meta property="og:description" content="OG 태그 사용 예제" />
    <meta property="og:image" content="https://www.example.com/og-image.jpg" />

    <!-- SEO 메타 태그 -->
    <meta name="description" content="검색 결과에 표시될 페이지 설명" />
  </head>
  <body>
    <h1>OG 및 Favicon 설정 예제</h1>
    <p>이 페이지는 Favicon과 OG 태그 설정 방법을 보여줍니다.</p>
  </body>
</html>
```
