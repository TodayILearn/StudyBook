# CSS 문법 (Selector, Property)

# CSS란?

## CSS의 정의와 목적

- CSS는 "Cascading Style Sheets"의 약자
- 웹 페이지의 시각적 표현을 담당하는 스타일 언어
    - HTML 문서의 레이아웃과 디자인을 제어
    - 웹 페이지의 모양과 느낌을 개선
    - 다양한 디바이스와 화면 크기에 대응하는 반응형 디자인 구현
    - 콘텐츠와 디자인의 분리로 유지보수성 향상

```css
body {
  font-family: Arial, sans-serif;
  background-color: #f0f0f0;
  color: #333;
}
```

## HTML과 CSS의 관계

- HTML: 웹 페이지의 구조와 콘텐츠를 정의
- CSS: HTML 요소의 스타일과 레이아웃을 지정
- 분리의 이점:
    - 코드의 가독성과 유지보수성 향상
    - 동일한 HTML에 다양한 스타일 적용 가능
    - 여러 페이지에 일관된 스타일 적용 용이

### HTML

```html
<h1>환영합니다</h1>
<p>이것은 단락입니다.</p>
```

### CSS

```css
h1 {
  color: blue;
  font-size: 24px;
}

p {
  color: gray;
  line-height: 1.6;
}
```
