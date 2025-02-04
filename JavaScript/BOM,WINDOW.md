# JavaScript 웹 3 (BOM, Window)

- **실습1** : https://codeshare.io/R7oJ03

# BOM (Browser Object Model)

- 브라우저와 상호작용하는 객체의 집합
- DOM과 별도로 브라우저 환경 제어를 담당
- 핵심 객체: `window`

# Window 객체

## 주요 특징

- 모든 전역 JavaScript 객체, 함수, 변수의 최상위 객체
- 전역 객체로서 전역 변수와 함수 접근 가능

## 주요 속성 및 메서드

- `window.innerWidth`, `window.innerHeight`: 뷰포트 크기 반환
- `window.outerWidth`, `window.outerHeight`: 창 크기 반환
- `window.screen`: 디스플레이 화면 정보 제공
- `window.location`: 현재 URL 정보 제공
- `window.navigator`: 브라우저 정보 제공
- `window.alert(message)`: 경고 창 표시
- `window.confirm(message)`: 확인 창 표시
- `window.prompt(message, default)`: 입력 창 표시
- `window.open(url, name, specs)`: 새 창 열기

```jsx
// 예제
console.log(window.innerWidth, window.innerHeight);
console.log(window.location.href);
window.alert("알림창");
```

# 타이머 함수

## `setTimeout`

- 일정 시간 후 코드 실행
- `setTimeout(callback, delay)`

## `setInterval`

- 일정 간격으로 코드 실행
- `setInterval(callback, interval)`

## `clearTimeout`, `clearInterval`

- 타이머 취소

```jsx
// 예제
const timeoutId = setTimeout(() => console.log("3초 후 실행"), 3000);
clearTimeout(timeoutId);

let count = 0;
const intervalId = setInterval(() => {
  console.log(++count);
  if (count === 5) clearInterval(intervalId);
}, 1000);
```

# 위치와 크기 관련 속성

### 주요 속성

- `window.innerWidth`, `window.innerHeight`: 뷰포트 크기
- `window.outerWidth`, `window.outerHeight`: 창 크기
- `window.pageXOffset`, `window.pageYOffset`: 스크롤 위치
- `window.screen`: 디스플레이 화면 정보
- `window.devicePixelRatio`: 장치 픽셀 비율

```jsx
// 예제
console.log(`뷰포트 크기: ${window.innerWidth} x ${window.innerHeight}`);
console.log(`스크롤 위치: (${window.pageXOffset}, ${window.pageYOffset})`);
```

# 네비게이션과 히스토리

## `window.location`

- `location.href`: 현재 URL
- `location.reload()`: 페이지 새로고침
- `location.assign(url)`: 새로운 페이지로 이동

## `window.history`

- `history.back()`: 이전 페이지로 이동
- `history.forward()`: 다음 페이지로 이동
- `history.go(n)`: 특정 페이지로 이동

```jsx
// 예제
location.href = "https://example.com";
history.back();
history.go(-1);
```

# localStorage와 sessionStorage

## 주요 특징

- 키-값 쌍으로 데이터 저장
- `localStorage`: 브라우저 종료 후에도 데이터 유지
- `sessionStorage`: 탭 종료 시 데이터 삭제

## 주요 메서드

- `setItem(key, value)`: 데이터 저장
- `getItem(key)`: 데이터 가져오기
- `removeItem(key)`: 데이터 삭제
- `clear()`: 모든 데이터 삭제
- `key(index)`: 특정 인덱스의 키 반환
- `length`: 저장된 항목 개수 반환

```jsx
// 예제
localStorage.setItem("username", "John Doe");
console.log(localStorage.getItem("username"));
localStorage.removeItem("username");
sessionStorage.setItem("sessionKey", "sessionValue");
```

# storage 이벤트

## 주요 특징

- `setItem`, `removeItem`, `clear` 호출 시 발생
- 여러 창이나 탭에서 데이터 변경 감지

## 속성

- `event.key`: 변경된 키
- `event.oldValue`: 이전 값
- `event.newValue`: 새로운 값
- `event.url`: 변경이 발생한 URL
- `event.storageArea`: 변경된 스토리지 객체

```
window.addEventListener('storage', (event) => {
    console.log(`${event.key} 변경됨: ${event.oldValue} -> ${event.newValue}`)
})
```
