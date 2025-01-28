# 기본 문법 구조

- JavaScript 코드는 명령어들의 집합으로 이루어져 있으며, 각 명령어는 세미콜론(`;`)으로 구분
- 코드의 가독성을 높이기 위해 들여쓰기와 줄바꿈을 사용

## 변수 선언

- **var**: 함수 스코프 또는 전역 스코프를 가지며, 재선언과 재할당이 가능
- **let**: 블록 스코프를 가지며, 재할당은 가능하지만 재선언은 불가능
- **const**: 블록 스코프를 가지며, 재할당과 재선언 모두 불가능합니다. 상수를 선언할 때 사용

```jsx
var x = 10;
var x = 20; // 재선언 가능
x = 30; // 재할당 가능

let y = 10;
y = 30; // 재할당 가능

const z = 10;
// z = 20;  // 오류: 재할당 불가능
```

## 세미콜론과 코멘트

- **세미콜론**: 각 명령어의 끝에 선택적으로 사용할 수 있음. JavaScript는 줄바꿈을 통해 명령어의 끝을 유추하기 때문에 세미콜론이 필수는 아니지만, 명시적으로 사용하는 것이 좋음
- **코멘트**: 코드에 설명을 추가하는 방법으로, 실행되지 않음
  - 한 줄 코멘트: `//`
  - 여러 줄 코멘트: `/* */`

```jsx
// 한 줄 코멘트
let x = 10; // 변수 선언과 초기화

/*
여러 줄 코멘트
변수 y를 선언하고 초기화합니다.
*/
let y = 20;
```

## console.log를 통한 출력

- `console.log`는 JavaScript에서 콘솔에 메시지를 출력하는 가장 기본적인 방법. 주로 디버깅 목적으로 사용

```jsx
console.log("Hello, World!"); // 문자열 출력

let a = 5;
let b = 10;
console.log(a + b); // 15 출력
```

## 스코프와 일급 객체

### 스코프(Scope)

- 스코프는 변수와 함수가 유효한 코드 영역을 의미
- JavaScript에는 **전역 스코프**, **함수 스코프**, 그리고 **블록 스코프**가 존재
  - **전역 스코프**: 코드 어디에서나 접근 가능.
  - **함수 스코프**: 함수 내에서만 유효한 변수.
  - **블록 스코프**: 블록(`{}`) 내에서만 유효한 변수 (`let`, `const` 사용 시).

### 일급 객체(First-Class Object)

- JavaScript에서 함수는 일급 객체로 취급
  - 변수에 할당할 수 있음.
  - 다른 함수의 인자로 전달할 수 있음.
  - 다른 함수의 결과값으로 반환할 수 있음.

```jsx
const sayHello = function () {
  console.log("Hello!");
};

function executeFunction(func) {
  func();
}

executeFunction(sayHello); // "Hello!" 출력
```

## 호이스팅(Hoisting)

- 호이스팅은 JavaScript에서 변수와 함수 선언이 그들이 속한 스코프의 최상단으로 끌어올려지는 것처럼 동작하는 특성을 말함
- `var`로 선언된 변수는 호이스팅되어 `undefined`로 초기화되지만, `let`과 `const`로 선언된 변수는 호이스팅되지만 초기화되지 않은 상태로 남아 있음 (Temporal Dead Zone).

```jsx
console.log(x); // 출력: undefined
var x = 5;

console.log(y); // 오류: Cannot access 'y' before initialization
let y = 10;

function sayHello() {
  console.log("Hello!");
}
sayHello(); // "Hello!" 출력
```

# 타입과 연산자

## 데이터 타입 (Data Type)

### 원시 타입 (Primitive Type)

1. **Number**: 정수와 실수를 포함한 숫자 타입

   ```jsx
   let num = 42; // 정수
   let pi = 3.14; // 실수
   ```

2. **String**: 문자열을 나타냅니다. 큰따옴표(""), 작은따옴표(''), 백틱(``)을 사용

   - **템플릿 리터럴**: 백틱(``)을 사용해 동적 문자열을 생성할 수 있음

   ```jsx
   let name = "Alice";
   let greeting = `Hello, ${name}!`;
   console.log(greeting); // Hello, Alice!
   ```

3. **Boolean**: 논리값을 나타내며, `true` 또는 `false`만 가질 수 있음

   ```jsx
   let isActive = true;
   let isLoggedIn = false;
   ```

4. **Undefined**: 값이 할당되지 않은 변수를 나타냄

   ```jsx
   let value;
   console.log(value); // undefined
   ```

5. **Null**: 의도적으로 값이 없음을 나타냄

   ```jsx
   let empty = null;
   ```

6. **Symbol**: 고유한 식별자를 생성하기 위해 사용

   ```jsx
   let sym = Symbol("id");
   ```

7. **BigInt**: 안전한 범위를 초과하는 큰 정수를 표현

   ```jsx
   let bigNumber = 123456789012345678901234567890n;
   ```

### 참조 타입(Reference Type)

1. **Object**: 키-값 쌍의 컬렉션으로 구성된 복잡한 데이터 구조

   ```jsx
   let person = {
     name: "Alice",
     age: 25,
   };
   console.log(person.name); // Alice
   console.log(person["age"]); // 25
   ```

2. **Array**: 순서가 있는 데이터의 집합으로, 0부터 시작하는 인덱스를 가짐

   - 주요 메서드: `push`, `pop`, `shift`, `unshift`

   ```jsx
   let numbers = [1, 2, 3];
   numbers.push(4); // [1, 2, 3, 4]
   numbers.pop(); // [1, 2, 3]
   console.log(numbers);
   ```

## 연산자

- JavaScript는 다양한 연산자를 제공하며, 이들을 활용해 값을 계산하거나 조작할 수 있음

### 산술 연산자

1. `+` (덧셈): 숫자나 문자열을 더함

   ```jsx
   console.log(5 + 3); // 8
   console.log("Hello" + " World"); // "Hello World"
   ```

2. `-` (뺄셈): 두 값을 뺌

   ```jsx
   console.log(10 - 4); // 6
   ```

3. `*` (곱셈): 두 값을 곱함

   ```jsx
   console.log(6 * 7); // 42
   ```

4. `/` (나눗셈): 첫 번째 값을 두 번째 값으로 나눔

   ```jsx
   console.log(10 / 2); // 5
   ```

5. `%` (나머지): 첫 번째 값을 두 번째 값으로 나눈 나머지를 반환

   ```jsx
   console.log(10 % 3); // 1
   ```

6. `**` (지수): 거듭제곱을 계산

   ```jsx
   console.log(2 ** 3); // 8
   ```

### 비교 연산자

1. `==` (느슨한 동등): 값이 같으면 true를 반환 (타입 변환 포함)

   ```jsx
   console.log(5 == "5"); // true
   ```

2. `===` (엄격한 동등): 값과 타입이 모두 같으면 true를 반환

   ```jsx
   console.log(5 === "5"); // false
   ```

3. `!=` (느슨한 부등): 값이 다르면 true를 반환

   ```jsx
   console.log(5 != "5"); // false
   ```

4. `!==` (엄격한 부등): 값이나 타입이 다르면 true를 반환

   ```jsx
   console.log(5 !== "5"); // true
   ```

5. `<`, `<=`, `>`, `>=`: 크기 비교를 수행

   ```jsx
   console.log(10 > 5); // true
   console.log(5 <= 5); // true
   ```

### 논리 연산자 (단축 평가)

1. `&&` (AND): 두 조건이 모두 true일 때 true를 반환

   ```jsx
   console.log(true && false); // false
   ```

2. `||` (OR): 두 조건 중 하나라도 true일 때 true를 반환

   ```jsx
   console.log(true || false); // true
   ```

3. `!` (NOT): 조건을 반전

   ```jsx
   console.log(!true); // false
   ```

### 삼항 연산자

삼항 연산자는 조건에 따라 다른 값을 반환하는 간결한 조건문 형태입니다.

```
조건 ? 값1 : 값2;
```

- `조건`이 `true`일 경우 `값1`을 반환합니다.
- `조건`이 `false`일 경우 `값2`를 반환합니다.

```jsx
let age = 18;
let status = age >= 18 ? "성인" : "미성년자";
console.log(status); // 성인
```

### 타입 반환 연산자

1. `typeof`: 변수나 표현식의 타입을 반환

   ```jsx
   console.log(typeof 42); // "number"
   console.log(typeof "hello"); // "string"
   ```

2. `instanceof`: 객체가 특정 생성자의 인스턴스인지 확인

   ```
   let arr = [];
   console.log(arr instanceof Array); // true
   ```

# JavaScript 핵심 2 (흐름 제어)

# 흐름 제어

- **흐름 제어**는 프로그램이 실행되는 순서를 제어하는 방식으로, 다양한 조건과 반복문을 통해 구현 → 특정 조건에 따라 동작을 다르게 하거나, 반복 작업을 자동화할 수 있음

# 조건문

- **조건문**은 특정 조건에 따라 다른 코드를 실행하도록 제어하는 구문

## if-else 문

`if-else` 문은 조건식의 결과에 따라 실행할 코드 블록을 결정

- `if` 블록은 조건이 `true`일 때 실행
- `else if` 블록은 이전 조건이 `false`이고, 현재 조건이 `true`일 때 실행
- `else` 블록은 모든 조건이 `false`일 때 실행

```jsx
let score = 85; // 점수 변수 선언

if (score >= 90) {
  console.log("A 등급"); // 90점 이상일 때 실행
} else if (score >= 80) {
  console.log("B 등급"); // 80점 이상 90점 미만일 때 실행
} else {
  console.log("C 등급"); // 80점 미만일 때 실행
}
```

## switch 문

`switch` 문은 하나의 값에 대해 여러 경우(case)를 비교하고 실행할 코드를 결정

- `case`는 검사할 값과 일치하면 해당 블록의 코드를 실행
- `break`는 실행을 중단하고 `switch` 문을 종료
- `default`는 일치하는 값이 없을 때 실행

```jsx
let day = "금요일"; // 요일 변수 선언

switch (day) {
  case "월요일":
  case "화요일":
  case "수요일":
  case "목요일":
  case "금요일":
    console.log("평일입니다."); // 평일 조건 실행
    break;
  case "토요일":
  case "일요일":
    console.log("주말입니다."); // 주말 조건 실행
    break;
  default:
    console.log("올바른 요일이 아닙니다."); // 잘못된 입력 처리
}
```

# 반복문

- **반복문**은 특정 조건에 따라 코드를 반복 실행

## for 루프

`for` 루프는 초기화, 조건식, 증감식을 설정하여 반복을 제어

```jsx
for (let i = 0; i < 5; i++) {
  console.log(i); // i 값 출력 (0부터 4까지)
}
```

## while 루프

`while` 루프는 조건이 `true`인 동안 코드를 실행

```jsx
let count = 0; // 초기화
while (count < 5) {
  console.log(count); // count 값 출력
  count++; // count 증가
}
```

## do-while 루프

`do-while` 루프는 최소 한 번 실행 후, 조건을 검사하여 반복을 결정

```jsx
let i = 0; // 초기화
do {
  console.log(i); // i 값 출력 (최소 한 번 실행)
  i++;
} while (i < 5); // 조건 검사
```

# 특수한 반복문

JavaScript에는 **배열**과 **객체**를 손쉽게 순회할 수 있는 반복문도 있음

## for...of 루프

`for...of`는 배열, 문자열과 같은 반복 가능한 객체의 값을 순회

```jsx
let fruits = ["사과", "바나나", "오렌지"];

for (let fruit of fruits) {
  console.log(fruit); // 배열의 각 요소 출력
}
```

## for...in 루프

`for...in`은 객체의 열거 가능한 속성을 순회

```jsx
let person = {
  name: "John",
  age: 30,
  job: "developer",
};

for (let key in person) {
  console.log(key + ": " + person[key]); // 객체의 키와 값 출력
}
```

## 배열과 객체 순회

```
const students = ["Alice", "Bob", "Charlie"];
const grades = { Alice: 90, Bob: 85, Charlie: 88 };

// forEach로 배열 순회
students.forEach(student => {
    console.log(`학생 이름: ${student}`); // 각 학생 이름 출력
});

// for...of로 배열 순회
for (const student of students) {
    console.log(`for...of 사용 - 학생 이름: ${student}`); // 각 학생 이름 출력
}

// 객체 순회: Object.keys() 사용
Object.keys(grades).forEach(name => {
    console.log(`${name}: ${grades[name]}`); // 각 학생 이름과 점수 출력
});

// 객체 순회: for...in 사용
for (const name in grades) {
    console.log(`for...in 사용 - ${name}: ${grades[name]}`); // 각 학생 이름과 점수 출력
}
```
