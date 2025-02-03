# 이벤트 리스너 추가 및 제거

- 이벤트 리스너는 특정 이벤트가 발생했을 때 실행될 함수
- `addEventListener()`: 이벤트 리스너 추가
- `removeEventListener()`: 이벤트 리스너 제거
- `once: true` 옵션으로 한 번만 실행되는 이벤트 설정 가능

```jsx
const button = document.getElementById("myButton");

const clickHandler = () => {
  console.log("Button clicked!");
};
button.addEventListener("click", clickHandler);

button.removeEventListener("click", clickHandler);

button
  .addEventListener(
    "click",
    () => {
      console.log("This will only run once");
    },
    { once: true }
  )

  [("mousedown", "mouseup", "click")].forEach((eventType) => {
    button.addEventListener(eventType, (event) => {
      console.log(`Event type: ${event.type}`);
    });
  });
```

# 이벤트 객체

- 이벤트 핸들러 함수는 이벤트 객체를 매개변수로 받아 상세 정보를 제공
- `event.key`: 눌린 키
- `event.clientX`, `event.clientY`: 클릭 좌표
- `event.target`: 이벤트 발생 요소

```jsx
const input = document.getElementById("myInput");

input.addEventListener("keydown", (event) => {
  console.log(`Key pressed: ${event.key}`);
});

document.addEventListener("click", (event) => {
  console.log(`Clicked at coordinates: (${event.clientX}, ${event.clientY})`);
});
```

# 이벤트 위임

- 여러 요소에 각각 이벤트 리스너를 추가하지 않고 공통 조상 요소에 이벤트 리스너 추가
- 동적으로 추가된 요소도 처리 가능

```jsx
const ul = document.getElementById("myList");

ul.addEventListener("click", (event) => {
  if (event.target.tagName === "LI") {
    console.log(`Clicked on item: ${event.target.textContent}`);
  }
});

const addItem = (text) => {
  const li = document.createElement("li");
  li.textContent = text;
  ul.appendChild(li);
};

addItem("New Item");
```

# 콜백 함수

- 콜백 함수는 특정 조건에서 실행되는 함수
- `this` 바인딩이 일반 함수와 화살표 함수에서 다르게 동작

```jsx
const button = document.getElementById("myButton");
button.addEventListener("click", () => {
  console.log("Button clicked!");
});

const createClickHandler = (id) => (event) => {
  console.log(`Button ${id} clicked at: (${event.clientX}, ${event.clientY})`);
};

document
  .getElementById("button1")
  .addEventListener("click", createClickHandler(1));
document
  .getElementById("button2")
  .addEventListener("click", createClickHandler(2));

const loadData = (callback) => {
  setTimeout(() => {
    const data = { id: 1, name: "John" };
    callback(data);
  }, 1000);
};

loadData((data) => {
  console.log(`Data loaded: ${JSON.stringify(data)}`);
});
```

# 기본 동작 방지

- `event.preventDefault()`: 브라우저의 기본 동작 방지

```
const form = document.getElementById('myForm')

form.addEventListener('submit', (event) => {
    event.preventDefault()
    const formData = new FormData(form)
    for (let [key, value] of formData.entries()) {
        console.log(`${key}: ${value}`)
    }
})

const link = document.getElementById('myLink')

link.addEventListener('click', (event) => {
    event.preventDefault()
    console.log('Link click prevented')
})
```
