# 함수

- JavaScript에서 함수는 특정 작업을 수행하기 위한 독립된 코드 블록
- 프로그램의 재사용성과 가독성을 높임

# 함수 선언과 함수 표현식

## 함수 선언

- 함수 선언은 `function` 키워드로 독립적으로 정의
- 함수 선언은 **호이스팅(hoisting)**되므로, 함수 정의 이전에 호출이 가능

```jsx
function greet(name) {
  return `Hello, ${name}!`;
}

console.log(greet("Alice")); // 출력: Hello, Alice!
```

## 함수 표현식

- 함수 표현식은 변수에 익명 함수(이름이 없는 함수)를 할당하여 정의
- 함수 표현식은 호이스팅되지 않으므로, 함수 정의 이후에만 호출할 수 있음

```jsx
const greetExpression = function (name) {
  return `Hello, ${name}!`;
};

console.log(greetExpression("Bob")); // 출력: Hello, Bob!
```

# 화살표 함수

- **화살표 함수**는 ES6에서 도입된 간결한 함수 표현 방식
- 기존 함수 표현식보다 짧게 작성할 수 있으며, `this` 바인딩이 고정되는 특성이 있음

```jsx
const add = (a, b) => a + b;

const multiply = (a, b) => {
  let result = a * b;
  return result;
};

console.log(add(2, 3)); // 출력: 5
console.log(multiply(4, 5)); // 출력: 2
```

# 기본 매개변수와 나머지 매개변수

## 기본 매개변수

- 기본 매개변수를 사용하면, 함수 호출 시 인수가 전달되지 않았을 경우 사용할 기본값을 정의할 수 있음

```jsx
function greet(name = "Guest") {
  return `Hello, ${name}!`;
}

console.log(greet()); // 출력: Hello, Guest!
console.log(greet("Alice")); // 출력: Hello, Alice!
```

## 나머지 매개변수

- 나머지 매개변수는 함수가 전달받은 인수들을 배열로 처리할 수 있게 함

```jsx
function sum(...numbers) {
  return numbers.reduce((total, num) => total + num, 0);
}

console.log(sum(1, 2, 3, 4, 5)); // 출력: 15
```

## 콜백 함수

- **콜백 함수**는 다른 함수에 인자로 전달되어, 그 함수의 내부에서 실행되는 함수
- 콜백은 비동기 작업이나 고차 함수 구현에 유용

```jsx
function processArray(arr, callback) {
  const result = [];
  for (let i = 0; i < arr.length; i++) {
    result.push(callback(arr[i]));
  }
  return result;
}

const numbers = [1, 2, 3, 4, 5];
const doubled = processArray(numbers, function (num) {
  return num * 2;
});

console.log(doubled); // 출력: [2, 4, 6, 8, 10]
```

## 클로저와 렉시컬 환경

## 클로저

- **클로저**는 함수와 함수가 선언된 렉시컬 환경(lexical environment)의 조합
- 클로저를 통해 내부 함수는 외부 함수의 변수에 접근할 수 있음

```jsx
function createCounter() {
  let count = 0;
  return function () {
    return ++count;
  };
}

const counter = createCounter();
console.log(counter()); // 출력: 1
console.log(counter()); // 출력: 2
console.log(counter()); // 출력: 3
```

## 렉시컬 환경

- **렉시컬 환경**은 코드가 작성된 위치에 따라 변수와 스코프가 결정되는 방식
- JavaScript는 함수가 선언된 위치를 기준으로 변수와 상위 스코프를 기억
- 쉽게 말해, **함수가 어디에서 호출되었는지가 아니라, 어디에서 정의되었는지가 중요**

```jsx
function outer() {
  let outerVar = "I am outer";

  function inner() {
    console.log(outerVar); // 외부 함수의 변수에 접근 가능
  }

  return inner;
}

const myInner = outer(); // outer가 실행되고 inner 함수가 반환됨
myInner(); // 출력: I am outer
```

- 위 코드에서 `inner` 함수는 `outer` 함수의 스코프에 있는 `outerVar`에 접근할 수 있음 → `inner` 함수가 `outer` 함수 내부에서 정의되었기 때문

## 스코프

JavaScript에서 스코프는 변수에 접근할 수 있는 유효 범위를 정의

- **전역 스코프**: 함수 외부에서 선언된 변수는 모든 코드에서 접근 가능
- **지역 스코프**: 함수 내부에서 선언된 변수는 해당 함수 내부에서만 접근 가능

```jsx
let globalVar = "I am global";

function testScope() {
  let localVar = "I am local";
  console.log(globalVar); // 출력: I am global
  console.log(localVar); // 출력: I am local
}

console.log(globalVar); // 출력: I am global
// console.log(localVar); // 오류: localVar is not defined
```

# 함수의 반환값

- 함수는 `return` 키워드를 사용하여 결과를 반환할 수 있음
- 반환값이 없으면 함수는 undefined를 반환

```
function add(a, b) {
    return a + b;
}

console.log(add(2, 3)); // 출력: 5

function noReturn() {
    console.log("No return value");
}

console.log(noReturn()); // 출력: No return value \n undefined
```

# 화살표 함수 심화

## 화살표 함수

- 화살표 함수는 ES6에서 도입된 간결한 함수 표현식
  - **this 바인딩 고정**: `this`가 화살표 함수의 정의 위치에서 고정
  - **간결한 문법**: 함수 정의를 짧고 명확하게 표현할 수 있음
  - **객체 리터럴 반환**: 객체를 반환할 때 괄호로 감싸야 함

```jsx
const add = (a, b) => a + b;
const square = (x) => x * x;
const greet = () => "Hello, World!";
const createPerson = (name, age) => ({ name, age });
```

## 여러 줄 본문과 this 바인딩 차이

- 여러 줄 본문은 화살표 함수가 단일 표현식이 아니라 여러 줄로 구성된 경우를 말함
- 중괄호(`{}`)와 `return` 키워드를 사용해야 합니다
  - 중괄호를 사용하여 복잡한 로직 작성 가능
  - 명시적으로 값을 반환해야 함

```jsx
const multiply = (a, b) => {
  const result = a * b;
  return result;
};
```

- 전통적인 함수와 화살표 함수는 `this`의 바인딩 방식이 다릅니다
- 화살표 함수는 `this`가 작성된 위치의 컨텍스트를 고정합니다
  - 화살표 함수: `this`가 고정되어 예상치 못한 `this` 문제를 방지
  - 전통적 함수: 호출 맥락에 따라 `this`가 변경될 수 있음

```jsx
function Traditional() {
  this.value = 1;
  setTimeout(function () {
    this.value++;
  }, 1000);
}

function ArrowVersion() {
  this.value = 1;
  setTimeout(() => {
    this.value++;
  }, 1000);
}
```

# 고차 함수

## map

- `map` 함수는 배열의 각 요소를 변환하여 새로운 배열을 생성
- 기존 배열은 변경되지 않음
  - 배열 요소를 변환
  - 새로운 배열 반환
  - 원본 배열은 유지

```jsx
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map((num) => num * 2);
console.log(doubled); // [2, 4, 6, 8, 10]
```

## filter

- `filter` 함수는 배열에서 조건에 맞는 요소만 선택하여 새로운 배열을 생성
  - 조건을 만족하는 요소만 반환
  - 새로운 배열 생성
  - 원본 배열 유지

```jsx
const evens = numbers.filter((num) => num % 2 === 0);
console.log(evens); // [2, 4]
```

## reduce

- `reduce` 함수는 배열의 모든 요소를 순회하며 단일 값으로 축약
- 누적값(`accumulator`)을 활용하여 값을 계산
  - 배열 요소를 누적하여 단일 값 생성
  - 총합, 평균 등 집계 연산에 유용
  - 초기값 설정 가능

```jsx
const sum = numbers.reduce((acc, num) => acc + num, 0);
console.log(sum); // 15
```

## forEach

- `forEach` 함수는 배열의 각 요소에 대해 함수를 실행
- 반환값이 없으며, 주로 부수효과 처리에 사용
  - 배열 요소에 대해 함수 실행
  - 반환값 없음
  - 로깅이나 상태 변경에 활용

```jsx
numbers.forEach((num) => console.log(num));
```

# 구조 분해 할당

## 배열

- 배열의 요소를 변수에 할당하는 문법으로, 배열을 개별 변수로 분해할 수 있음
  - 배열 요소를 개별 변수에 할당
  - 스프레드 연산자(`...`)로 나머지 요소 처리

```jsx
const [a, b, ...rest] = [1, 2, 3, 4, 5];
console.log(a, b, rest); // 1 2 [3, 4, 5]
```

## 객체

- 객체의 속성을 변수에 할당하는 문법으로, 특정 속성을 쉽게 추출할 수 있음
  - 객체의 속성을 변수로 분해
  - 기본값 설정 가능
  - 중첩된 객체 처리 가능

```jsx
const { name, age, country = "Unknown" } = { name: "Bob", age: 25 };
console.log(name, age, country); // Bob 25 Unknown

function printPerson({ name, age }) {
  console.log(`${name} is ${age} years old`);
}
printPerson({ name: "Charlie", age: 35 });
```

# 스프레드 연산자

## 배열

- 스프레드 연산자는 배열을 펼치거나 병합하는 데 사용
  - 배열 복사 및 확장
  - 배열 병합
  - 원본 배열은 변경되지 않음

```jsx
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5];
console.log(arr2); // [1, 2, 3, 4, 5]
```

## 객체

- 객체를 복사하거나 확장하는 데 사용
  - 기존 객체 기반으로 새 객체 생성
  - 객체 병합 및 확장
  - 원본 객체 유지

```jsx
const obj1 = { a: 1, b: 2 };
const obj2 = { ...obj1, c: 3 };
console.log(obj2); // { a: 1, b: 2, c: 3 }
```

# 나머지 매개변수

- 함수에서 가변 인자를 배열 형태로 처리할 수 있도록 함
  - 동적 매개변수 처리
  - 여러 인자를 배열로 수집

```jsx
function multiply(multiplier, ...args) {
  return args.map((x) => multiplier * x);
}
console.log(multiply(2, 1, 2, 3)); // [2, 4, 6]
```

# 예외 처리

## try-catch

- `try-catch` 문은 코드 실행 중 발생하는 오류를 처리하는 구문
  - 오류 발생 시 실행 중단 방지
  - `catch` 블록에서 오류 처리
  - `finally` 블록에서 항상 실행되는 코드 작성

```jsx
try {
  let result = 10 / 0;
  console.log(result);
} catch (error) {
  console.log("에러 발생");
} finally {
  console.log("연산 종료");
}
```

## 에러 다시 던지기

- 오류 처리 중 특정 조건에서 오류를 다시 던질 수 있음
  - 예상치 못한 오류는 다시 상위로 전달
  - 로직에서 특정 조건 만족 시 재처리 가능

```jsx
try {
  throw new Error("예상치 못한 오류");
} catch (error) {
  if (error.message.includes("예상치 못한")) {
    throw error;
  }
  console.log("처리 가능한 오류");
}
```

## 공통 사용 변수

- 예외 처리 중 공통으로 사용하는 변수는 외부에 선언하여 블록 간 공유
  - try-catch도 일종의 block scope
  - 변수 범위를 try-catch-finally 외부로 설정
  - 공통 데이터의 일관성 유지

```
let sharedValue = 0
try {
  sharedValue++
  throw new Error("오류 발생")
} catch (error) {
  console.log(sharedValue)
  console.log("오류 처리", error.message)
} finally {
  sharedValue--
  console.log("마무리 작업")
}
```
