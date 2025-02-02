# 객체

## 객체 리터럴과 프로퍼티

- **객체**는 관련된 데이터와 함수(메서드)의 집합
- 객체 리터럴 표기법을 사용하여 간단히 객체를 생성할 수 있으며, 프로퍼티는 객체의 특성을 나타냄

```jsx
const person = {
  name: "Alice",
  age: 30,
  greet: function () {
    return `Hello, my name is ${this.name}`;
  },
};

console.log(person.name); // 출력: Alice
console.log(person.greet()); // 출력: Hello, my name is Alice
```

## 함수

- 함수는 특정 작업을 수행하기 위한 코드 블록
- 함수는 재사용이 가능하며, 프로그램의 가독성을 높이고 유지보수를 쉽게 만듦

```jsx
function add(a, b) {
  return a + b;
}

console.log(add(2, 3)); // 출력: 5

const multiply = (a, b) => a * b;
console.log(multiply(4, 5)); // 출력: 20
```

## 메서드

- **메서드**는 객체에 속한 함수
- ES6부터는 객체 리터럴 내에서 메서드를 정의할 때 더 간결한 문법을 사용할 수 있음

```jsx
const calculator = {
  add(a, b) {
    return a + b;
  },
  subtract(a, b) {
    return a - b;
  },
};

console.log(calculator.add(5, 3)); // 출력: 8
console.log(calculator.subtract(10, 4)); // 출력: 6
```

# 클래스

## 생성자 (constructor)

- **생성자**는 객체가 생성될 때 호출되며, 객체의 초기 상태를 설정
- **constructor** 메서드는 클래스 내부에 하나만 정의할 수 있습니다.

```jsx
class Animal {
  constructor(name) {
    this.name = name;
  }

  sayHello() {
    return `Hello, I'm ${this.name}`;
  }
}

const animal = new Animal("Charlie");
console.log(animal.sayHello()); // 출력: Hello, I'm Charlie
```

## 메서드

- 메서드는 클래스 내부에 정의된 함수로, 객체가 수행할 동작을 정의
- 인스턴스 메서드는 생성된 객체에서 호출할 수 있음

```jsx
class Calculator {
  add(a, b) {
    return a + b;
  }

  subtract(a, b) {
    return a - b;
  }
}

const calc = new Calculator();
console.log(calc.add(10, 5)); // 출력: 15
console.log(calc.subtract(10, 5)); // 출력: 5
```

## 상속

- 상속은 기존 클래스의 속성과 메서드를 재사용하여 새로운 클래스를 정의할 수 있게 함
- `extends` 키워드를 사용하며, 부모 클래스의 생성자는 `super`를 통해 호출합니다.

```
class Animal {
    constructor(name) {
        this.name = name;
    }

    sayHello() {
        return `Hello, I'm ${this.name}`;
    }
}

class Dog extends Animal {
    constructor(name, breed) {
        super(name);
        this.breed = breed;
    }

    bark() {
        return "Woof!";
    }
}

const myDog = new Dog("Buddy", "Golden Retriever");
console.log(myDog.sayHello()); // 출력: Hello, I'm Buddy
console.log(myDog.bark()); // 출력: Woof!
```

## Getter와 Setter

- **getter**와 **setter**는 객체의 프로퍼티에 접근하고 수정하는 방법을 제어할 수 있게 해주는 특별한 메서드
- getter는 프로퍼티 값을 읽을 때, setter는 프로퍼티 값을 설정할 때 호출

```
class Circle {
    constructor(radius) {
        this._radius = radius;
    }

    get radius() {
        return this._radius;
    }

    set radius(newRadius) {
        if (newRadius > 0) {
            this._radius = newRadius;
        } else {
            console.error("Radius must be positive");
        }
    }

    get area() {
        return Math.PI * this._radius ** 2;
    }
}

const circle = new Circle(5);
console.log(circle.radius); // 출력: 5
console.log(circle.area); // 출력: 약 78.54

circle.radius = 7;
console.log(circle.radius); // 출력: 7
console.log(circle.area); // 출력: 약 153.94

circle.radius = -1; // 콘솔에 에러 메시지 출력
```
