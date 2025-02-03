# DOM(Document Object Model)

- HTML 문서를 트리 구조로 표현하며, JavaScript를 통해 동적으로 문서를 조작할 수 있게 함
- DOM은 웹 페이지의 구조를 스크립트나 프로그래밍 언어와 연결하는 인터페이스를 제공

## DOM 트리 구조

- 주요 속성 및 메서드
  - `document.body`: 문서의 `<body>` 요소를 반환
  - `firstElementChild`, `lastElementChild`: 첫 번째와 마지막 자식 요소를 반환
  - `children`: 모든 자식 요소의 컬렉션을 반환
- DOM 트리는 HTML 문서를 트리 형태로 나타낸 구조로, 각 요소는 노드로 표현
- 루트 노드는 항상 `document` 객체

```jsx
// DOM 트리 탐색
const body = document.body;
const firstChild = body.firstElementChild;
const lastChild = body.lastElementChild;

console.log(firstChild.nodeName); // 첫 번째 자식 요소의 태그 이름
console.log(lastChild.nodeName); // 마지막 자식 요소의 태그 이름

// 자식 노드 순회
const children = Array.from(body.children);
children.forEach((child) => {
  console.log(child.nodeName);
});
```

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>DOM 트리 구조</title>
  </head>
  <body>
    <header>
      <h1>환영합니다!</h1>
    </header>
    <main>
      <p>메인 컨텐츠입니다.</p>
    </main>
    <footer>
      <p>&copy; 2025 웹 개발</p>
    </footer>
    <script>
      const body = document.body;
      console.log(body);

      const firstChild = body.firstElementChild;
      console.log(firstChild.nodeName);

      const lastChild = body.lastElementChild;
      console.log(lastChild.nodeName);

      const children = Array.from(body.children);
      children.forEach((child) => {
        console.log(child.nodeName);
      });
    </script>
  </body>
</html>
```

## DOM 요소 선택

- 주요 메서드:
  - `getElementById(id)`: ID로 요소를 선택
  - `getElementsByClassName(className)`: 클래스 이름으로 요소를 선택
  - `getElementsByTagName(tagName)`: 태그 이름으로 요소를 선택
  - `querySelector(selector)`: CSS 선택자로 첫 번째 요소를 선택
  - `querySelectorAll(selector)`: CSS 선택자로 모든 일치하는 요소를 선택
- DOM 요소를 선택하기 위해 여러 메서드가 제공
- 선택된 요소를 통해 트리를 탐색하거나 조작할 수 있음

### `getElementById`, `getElementsByClassName`, `getElementsByTagName`

- `getElementById`는 특정 ID를 가진 단일 요소를 선택
- `getElementsByClassName`은 특정 클래스 이름을 가진 요소들의 HTMLCollection을 반환
- `getElementsByTagName`은 특정 태그 이름을 가진 요소들의 HTMLCollection을 반환

```jsx
// ID로 요소 선택
const elementById = document.getElementById("uniqueId");
console.log(elementById);

// 클래스 이름으로 요소 선택
const elementsByClass = document.getElementsByClassName("myClass");
console.log(elementsByClass);

// 태그 이름으로 요소 선택
const elementsByTag = document.getElementsByTagName("div");
console.log(elementsByTag);
```

### `querySelector`와 `querySelectorAll`

- `querySelector`는 CSS 선택자를 사용하여 첫 번째로 일치하는 요소를 반환합니다.
- `querySelectorAll`은 CSS 선택자를 사용하여 일치하는 모든 요소의 NodeList를 반환합니다.

```jsx
// 첫 번째 일치하는 요소 선택
const firstParagraph = document.querySelector("p");
console.log(firstParagraph);

// 모든 일치하는 요소 선택
const allParagraphs = document.querySelectorAll("p");
console.log(allParagraphs);

// 복잡한 선택자 사용
const highlightedItems = document.querySelectorAll(
  "div.highlight > p:first-child"
);
console.log(highlightedItems);
```

## DOM 조작

- 주요 메서드:
  - `createElement(tagName)`: 새 HTML 요소를 생성합니다.
  - `appendChild(child)`: 요소를 부모 노드에 추가합니다.
  - `insertBefore(newNode, referenceNode)`: 새 노드를 참조 노드 앞에 삽입합니다.
  - `removeChild(child)`: 자식 노드를 제거합니다.
  - `replaceChild(newChild, oldChild)`: 기존 노드를 새 노드로 교체합니다.
  - `textContent`: 요소의 텍스트 콘텐츠를 설정하거나 반환합니다.

### 요소 생성 및 추가

- DOM 요소를 동적으로 생성하고 문서에 추가할 수 있음

```jsx
// 새 요소 생성
const newDiv = document.createElement("div");
newDiv.textContent = "새로운 콘텐츠";

// 요소 추가
const parentElement = document.getElementById("container");
parentElement.appendChild(newDiv);

// 특정 위치에 요소 삽입
const referenceElement = document.getElementById("reference");
parentElement.insertBefore(newDiv, referenceElement);

// 여러 요소를 한 번에 추가
const fragment = document.createDocumentFragment();
["Apple", "Banana", "Cherry"].forEach((fruit) => {
  const li = document.createElement("li");
  li.textContent = fruit;
  fragment.appendChild(li);
});
document.getElementById("fruitList").appendChild(fragment);
```

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>DOM 조작</title>
  </head>
  <body>
    <div id="container">
      <p id="reference">기준점</p>
    </div>

    <ul id="fruitList">
      <li>사과</li>
      <li>배</li>
    </ul>

    <script>
      const newDiv = document.createElement("div");
      newDiv.textContent = "새로운 콘텐츠";

      const container = document.querySelector("#container");
      const reference = document.querySelector("#reference");
      container.insertBefore(newDiv, reference);

      const fragment = document.createDocumentFragment();
      ["포도", "오렌지", "바나나"].forEach((fruit) => {
        const li = document.createElement("li");
        li.textContent = fruit;
        fragment.appendChild(li);
      });
      document.querySelector("#fruitList").appendChild(fragment);
    </script>
  </body>
</html>
```

### 요소 삭제 및 수정

- DOM 요소를 삭제하거나 수정할 수 있습니다.

```
// 요소 삭제
const parent = document.getElementById('parent');
const child = document.getElementById('child');
parent.removeChild(child);

// 요소 교체
const oldElement = document.getElementById('old');
const newElement = document.createElement('div');
newElement.textContent = '새로운 요소';
oldElement.parentNode.replaceChild(newElement, oldElement);

// 요소 내용 수정
const header = document.querySelector('h1');
header.textContent = '수정된 제목';
```
