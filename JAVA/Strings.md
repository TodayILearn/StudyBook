# Strings

## 1. 문자열의 개요

Java에서 문자열은 문자들의 연속이며, `String` 클래스의 객체로 관리됩니다.

- **불변(Immutable):** 한 번 생성된 문자열은 수정할 수 없으며, 변경 작업은 새로운 문자열 객체를 생성합니다.
- **객체 특성:** 기본 자료형처럼 다루지만, 실제로는 다양한 내장 메서드를 제공하는 객체입니다.

---

## 2. 문자열 생성 방법

### 2.1. 리터럴 방식

문자열 리터럴은 큰따옴표(`" "`)를 사용하여 생성하며, JVM은 **String Pool**을 활용해 동일한 내용의 문자열을 재사용합니다.

```java
String str1 = "Java Programming";
```

### 2.2. `new` 키워드 사용

`new` 키워드를 사용하면 항상 새로운 객체가 생성되므로, 동일한 내용이라도 별도의 객체가 됩니다.

```java
String str2 = new String("Java Programming");
```

> 참고: 리터럴 방식은 메모리 사용 측면에서 효율적입니다.
> 

---

## 3. 주요 문자열 메서드 및 예제

Java는 문자열을 다루기 위해 다양한 메서드를 제공합니다. 중요도 순으로 자주 사용되는 메서드와 예제를 살펴보겠습니다.

### 3.1. 문자열 길이 확인: `length()`

문자열에 포함된 문자 수를 반환합니다.

```java
String str = "Hello, Java!";
int len = str.length();
System.out.println("길이: " + len);  // 출력: 길이: 12

```

### 3.2. 문자열 연결: `concat()` 또는 `+` 연산자

두 문자열을 연결하여 하나의 문자열로 만듭니다.

```java
String first = "Hello, ";
String second = "World!";

// concat() 사용
String result = first.concat(second);
System.out.println(result);  // 출력: Hello, World!

// 또는 + 연산자 사용
String result2 = first + second;
System.out.println(result2);  // 출력: Hello, World!

```

### 3.3. 문자열 비교: `equals()`

문자열의 내용을 비교합니다. (대소문자 구분)

```java
String a = "Java";
String b = "Java";
String c = "java";

System.out.println(a.equals(b));  // 출력: true
System.out.println(a.equals(c));  // 출력: false

```

> 주의: == 연산자는 객체의 참조를 비교하므로, 리터럴과 new 키워드로 생성된 문자열은 다르게 판단될 수 있습니다.
> 

### 3.4. 부분 문자열 추출: `substring()`

특정 범위의 부분 문자열을 추출합니다.

```java
String text = "Java Programming";
String sub = text.substring(5, 16);  // 인덱스 5부터 15까지 추출
System.out.println(sub);  // 출력: Programming
```

### 3.5. 특정 위치의 문자 반환: `charAt()`

지정한 인덱스의 문자를 반환합니다.

```java
String text = "Hello";
char ch = text.charAt(1);  // 인덱스 1의 문자 'e'
System.out.println("문자: " + ch);  // 출력: 문자: e
```

### 3.6. 특정 문자 또는 문자열의 위치: `indexOf()`

특정 문자나 문자열이 처음 등장하는 인덱스를 반환합니다.

```java
String text = "Hello, Java!";
int index = text.indexOf("Java");
System.out.println("인덱스: " + index);  // 출력: 인덱스: 7
```

### 3.7. 공백 제거: `trim()`

문자열의 앞뒤 공백을 제거합니다.

```java
String text = "   Java   ";
String trimmed = text.trim();
System.out.println("Trimmed: '" + trimmed + "'");  // 출력: 'Java'
```

### 3.8. 대소문자 변환: `toLowerCase()` / `toUpperCase()`

문자열을 모두 소문자 또는 대문자로 변환합니다.

```java
String text = "Java Programming";
System.out.println(text.toLowerCase());  // 출력: java programming
System.out.println(text.toUpperCase());  // 출력: JAVA PROGRAMMING
```

### 3.9. 문자열 분할: `split()`

지정한 구분자를 기준으로 문자열을 분할하여 배열로 반환합니다.

```java
String csv = "apple,banana,cherry";
String[] fruits = csv.split(",");
for (String fruit : fruits) {
    System.out.println(fruit);
}
// 출력:
// apple
// banana
// cherry
```

### 3.10. 문자열 교체: `replace()`, `replaceFirst()`, `replaceAll()`

문자열 내의 특정 문자나 문자열을 다른 값으로 대체합니다.

```java
String text = "Java is fun. Java is powerful.";

// 모든 "Java"를 "Python"으로 교체
String replaced = text.replace("Java", "Python");
System.out.println(replaced);
// 출력: Python is fun. Python is powerful.

// 첫 번째 "Java"만 교체
String replacedFirst = text.replaceFirst("Java", "Python");
System.out.println(replacedFirst);
// 출력: Python is fun. Java is powerful.
```

### 3.11. 문자열 포함 여부 확인: `contains()`

특정 문자열이 포함되어 있는지 확인합니다.

```java
String text = "Java programming is fun";
boolean hasJava = text.contains("Java");
System.out.println("포함 여부: " + hasJava);  // 출력: 포함 여부: true
```

### 3.12. 문자열 포맷 지정: `format()`

형식 문자열과 인수를 사용해 새로운 문자열을 생성합니다.

```java
String formatted = String.format("Hello, %s! Today is %s.", "Java", "Friday");
System.out.println(formatted);  // 출력: Hello, Java! Today is Friday.
```

---

## 4. 이스케이프 문자 사용

문자열 내에서 큰따옴표나 특수 문자를 표현할 때 백슬래시(`\`)를 사용합니다.

```java
String example = "This is the \"String\" class.";
System.out.println(example);  // 출력: This is the "String" class.
```

---

## 5. 텍스트 블록 (Text Blocks) - """ 사용

Java 15부터 도입된 텍스트 블록은 여러 줄의 문자열을 보다 간편하게 작성할 수 있도록 도와줍니다.

- **표현:** 삼중 큰따옴표(`"""`)를 사용하여 문자열을 감쌉니다.
- **특징:**
    - 여러 줄에 걸친 문자열을 작성할 때, 줄바꿈과 공백을 보존합니다.
    - 가독성이 높아지며, JSON, SQL, HTML 등의 형식을 작성할 때 유용합니다.
    - 내부적으로는 일반 문자열과 동일하게 불변이며, escape 시퀀스도 사용할 수 있습니다.

**예제:**

```java
String textBlock = """
    {
        "name": "Java",
        "type": "Programming Language",
        "features": [
            "Object-oriented",
            "Platform-independent",
            "Robust"
        ]
    }
    """;

System.out.println(textBlock);

```

> 참고: 텍스트 블록은 들여쓰기를 자동으로 조정하여 코드의 가독성을 높이는 기능도 제공합니다.