# 싱글톤 패턴, Enum, Package, 재귀(Recursion)

## 1. Java 싱글톤 패턴 (Singleton Pattern)

[Design Patterns and Refactoring](https://sourcemaking.com/design_patterns)

[Patterns.dev.kr  - 모던 웹 앱 디자인 패턴](https://patterns-dev-kr.github.io/)

**개념:**

싱글톤 패턴은 한 클래스에 단 하나의 인스턴스만 생성되도록 보장하는 디자인 패턴입니다. 주로 데이터베이스 연결, 로깅, 설정 관리 등 전역적으로 하나의 객체만 있으면 되는 경우에 사용합니다.

**구현 방법:**

- **private 생성자:** 외부에서 객체 생성을 막음
- **private static 인스턴스 변수:** 클래스 내부에 자기 자신을 참조하는 변수를 선언
- **public static getInstance() 메서드:** 인스턴스가 없으면 생성하고, 있으면 기존 인스턴스를 반환

**실습 예제 (데이터베이스 연결 예):**

```java
class Database {
    // 단 하나의 인스턴스를 참조할 private static 변수
    private static Database instance;

    // private 생성자: 외부에서 객체 생성을 방지
    private Database() {
        // 초기화 작업 (예: DB 연결 설정)
    }

    // 인스턴스를 생성하거나 기존 인스턴스를 반환하는 public static 메서드
    public static Database getInstance() {
        if (instance == null) {
            instance = new Database();
        }
        return instance;
    }

    public void getConnection() {
        System.out.println("데이터베이스에 연결되었습니다.");
    }
}

public class Main {
    public static void main(String[] args) {
        Database db1 = Database.getInstance();
        db1.getConnection();  // 출력: 데이터베이스에 연결되었습니다.

        // 여러번 호출해도 동일한 인스턴스가 반환됨
        Database db2 = Database.getInstance();
        System.out.println("db1과 db2는 같은 객체인가요? " + (db1 == db2));  // 출력: true
    }
}
```

---

## 2. Java 열거형 (Enum)

**개념:**

열거형은 정해진 상수들의 집합을 표현하는 특별한 클래스입니다. 코드 가독성을 높이고 컴파일 시 타입 안전성을 보장할 수 있습니다.

**기본 사용법 및 확장:**

- 열거형은 `enum` 키워드를 사용하여 정의하며, 상수는 대문자로 작성합니다.
- 열거형에 생성자와 메서드를 추가하여 각 상수에 대한 부가 정보를 제공할 수 있습니다.

**실습 예제 1: 기본 열거형 사용**

```java
enum Size {
    SMALL, MEDIUM, LARGE, EXTRALARGE
}

public class Main {
    public static void main(String[] args) {
        Size pizzaSize = Size.SMALL;
        System.out.println("피자 크기: " + pizzaSize);
        // 출력: 피자 크기: SMALL
    }
}
```

**실습 예제 2: 열거형에 생성자와 메서드 추가**

```java
enum Size {
    SMALL("작은 사이즈"),
    MEDIUM("중간 사이즈"),
    LARGE("큰 사이즈"),
    EXTRALARGE("특대 사이즈");

    private final String description;

    // private 생성자: 각 상수에 대한 설명 초기화
    private Size(String description) {
        this.description = description;
    }

    public String getDescription() {
        return description;
    }
}

public class Main {
    public static void main(String[] args) {
        System.out.println("피자의 크기는 " + Size.SMALL.getDescription());
        // 출력: 피자의 크기는 작은 사이즈
    }
}
```

---

## 3. Java 패키지 (Package)

**개념:**

패키지는 관련된 클래스, 인터페이스, 열거형 등을 그룹화하여 관리하는 컨테이너입니다. 이를 통해 클래스 네임스페이스를 보호하고 유지보수를 쉽게 합니다.

**종류:**

- **내장 패키지:** JDK에 포함된 패키지 (예: `java.util`, `java.io` 등)
- **사용자 정의 패키지:** 개발자가 직접 생성하여 관리하는 패키지

**실습 예제 1: 사용자 정의 패키지 생성 및 사용**

*파일 경로: com/example/Helper.java*

```java
package com.example;

public class Helper {
    public static String formatPrice(double value) {
        return String.format("$%.2f", value);
    }
}
```

*파일 경로: Main.java (같은 프로젝트 내)*

```java
import com.example.Helper;

public class Main {
    public static void main(String[] args) {
        double price = 49.99;
        String formattedPrice = Helper.formatPrice(price);
        System.out.println("Formatted Price: " + formattedPrice);
        // 출력: Formatted Price: $49.99
    }
}
```

**실습 예제 2: 내장 패키지 사용 (ArrayList 예)**

```java
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        ArrayList<String> list = new ArrayList<>();
        list.add("Apple");
        list.add("Banana");
        list.add("Cherry");
        System.out.println("List: " + list);
        // 출력: List: [Apple, Banana, Cherry]
    }
}
```

---

## 4. Java 재귀 (Recursion)

**개념:**

재귀는 메서드가 자기 자신을 호출하는 방식으로 문제를 해결하는 기법입니다. 재귀 함수는 종료 조건(기저 조건)을 반드시 포함해야 하며, 이를 통해 무한 반복을 방지합니다.

**재귀의 작동 원리:**

- **자기 호출:** 함수 내에서 자신을 다시 호출하여 문제를 더 작은 문제로 나눕니다.
- **종료 조건:** 특정 조건이 만족되면 재귀 호출을 중지하고 결과를 반환합니다.

**실습 예제 1: 팩토리얼 계산**

```java
class Factorial {
    // 팩토리얼을 재귀적으로 계산하는 메서드
    static int factorial(int n) {
        if (n != 0)  // 종료 조건: n이 0이 아니면
            return n * factorial(n - 1);  // 재귀 호출
        else
            return 1;  // n이 0이면 1 반환
    }

    public static void main(String[] args) {
        int number = 4;
        int result = factorial(number);
        System.out.println(number + " factorial = " + result);
        // 출력: 4 factorial = 24
    }
}
```

**실습 예제 2: 문자열 뒤집기**

```java
public class StringReverser {
    // 재귀를 이용하여 문자열을 뒤집는 메서드
    public static String reverse(String str) {
        // 종료 조건: 문자열의 길이가 0 또는 1이면 그대로 반환
        if (str == null || str.length() <= 1) {
            return str;
        }
        // 재귀 호출: 문자열의 첫 문자를 마지막에 붙이고 나머지 부분을 뒤집음
        return reverse(str.substring(1)) + str.charAt(0);
    }

    public static void main(String[] args) {
        String original = "hello";
        String reversed = reverse(original);
        System.out.println("Original: " + original);
        System.out.println("Reversed: " + reversed);
        // 출력:
        // Original: hello
        // Reversed: olleh
    }
}
```

**설명:**

- **종료 조건:** 문자열의 길이가 0 또는 1이면 더 이상 뒤집을 필요 없이 그대로 반환합니다.
- **재귀 호출:** 첫 번째 문자 이후의 부분 문자열을 재귀적으로 뒤집은 후, 마지막에 첫 번째 문자를 추가합니다.
- 재귀를 사용하면 코드가 간결해지지만, 호출 스택에 많은 메모리가 할당되므로 큰 입력에서는 주의해야 합니다.