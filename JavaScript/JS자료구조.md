# 객체 (Object)

- **특징**: 키-값 쌍의 데이터를 저장하며, 키는 문자열이나 심볼이어야 함
- **용도**: 구조화된 데이터를 표현하거나 메서드를 포함한 복잡한 데이터 구조를 생성할 때 사용

```jsx
const person = {
  name: "Alice",
  age: 30,
  greet() {
    return `Hello, my name is ${this.name}`;
  },
};

console.log(person.name); // Alice
console.log(person.greet()); // Hello, my name is Alice

// 동적 속성 추가 및 삭제
person.job = "Developer";
delete person.age;
```

## 주요 메서드

- `Object.keys()`: 객체의 키를 배열로 반환
- `Object.values()`: 객체의 값을 배열로 반환
- `Object.assign()`: 객체 복사 및 병합에 사용
- `Object.entries()`: 키-값 쌍 배열 반환

```jsx
const obj = { name: "Alice", age: 30 };
console.log(Object.keys(obj)); // ["name", "age"]
console.log(Object.values(obj)); // ["Alice", 30]
```

# 배열 (Array)

- **특징**: 순서가 있는 데이터를 저장하며, 인덱스로 요소에 접근
- **용도**: 리스트나 컬렉션 형태의 데이터를 처리할 때 사용

```jsx
const fruits = ["apple", "banana", "orange"];
console.log(fruits[0]); // apple

// 배열 조작 메서드
fruits.push("grape"); // 추가
fruits.pop(); // 제거
fruits.sort(); // 정렬
```

## 주요 메서드

- `map()`: 요소 변환
- `filter()`: 조건에 맞는 요소 반환
- `reduce()`: 값 축소
- `slice()`: 부분 배열 반환
- `concat()`: 배열 병합

```jsx
const upperCaseFruits = fruits.map((fruit) => fruit.toUpperCase());
console.log(upperCaseFruits); // ["APPLE", "BANANA", "ORANGE"]
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

# 맵 (Map)

- **특징**: 키-값 쌍의 데이터를 저장하며, 키의 타입 제한이 없음
- **용도**: 복잡한 키를 사용하는 데이터 저장

```jsx
const map = new Map();
map.set("name", "Alice");
map.set(1, "one");

console.log(map.get("name")); // Alice
console.log(map.has(1)); // true
console.log(map.size); // 2

map.delete(1);
```

## 주요 메서드

- `set()`: 데이터 추가
- `get()`: 값 가져오기
- `delete()`: 데이터 삭제
- `keys()`, `values()`, `entries()`: 순회

```jsx
const recipeMap = new Map([
  ["cucumber", 500],
  ["tomatoes", 350],
]);
for (const [key, value] of recipeMap) {
  console.log(`${key}: ${value}`);
}
```

# 셋 (Set)

- **특징**: 중복 없는 값의 집합
- **용도**: 고유한 값만 저장해야 할 때 사용

```jsx
const set = new Set(["apple", "banana", "orange"]);
set.add("grape");
console.log(set.size); // 4

set.delete("banana");
console.log(set.has("banana")); // false
```

주요 메서드
add(): 값 추가
delete(): 값 제거
has(): 값 존재 여부 확인
keys(), values(), entries(): 순회

```
set.forEach(value => console.log(value));
```
