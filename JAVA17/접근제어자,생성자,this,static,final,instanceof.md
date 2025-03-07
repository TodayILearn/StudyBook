# 접근 제어자, 생성자, this, static, final, instanceof

## 1. 접근 제어자 (Access Modifiers)

클래스, 멤버 변수, 메서드 등에 적용되는 접근 제어자는 외부에서의 접근 범위를 제어합니다.

- **private:** 해당 클래스 내부에서만 접근 가능
- **default:** 같은 패키지 내에서만 접근 가능
- **protected:** 같은 패키지나 서브클래스에서 접근 가능
- **public:** 어디서나 접근 가능

**예시 코드 (private 변수와 getter/setter 사용):**

```java
class Data {
    private String info;

    public String getInfo() {
        return info;
    }

    public void setInfo(String info) {
        this.info = info;
    }
}

public class Main {
    public static void main(String[] args) {
        Data data = new Data();
        data.setInfo("Example");
        System.out.println("Info: " + data.getInfo());
    }
}
```

---

## 2. 생성자 (Constructors)

생성자는 클래스와 같은 이름을 가지며 반환형이 없고, 객체 생성 시 자동으로 호출되어 멤버 변수를 초기화합니다.

- **No-Arg 생성자:** 매개변수가 없는 생성자
    
    ```java
    class Sample {
        int number;
    
        Sample() {
            number = 10;
            System.out.println("No-Arg 생성자가 실행되었습니다.");
        }
    
        public static void main(String[] args) {
            Sample s = new Sample();
            System.out.println("number = " + s.number);
        }
    }
    ```
    
- **Parameterized 생성자:** 매개변수를 받아 초기화하는 생성자
    
    ```java
    class Sample {
        String message;
    
        Sample(String msg) {
            this.message = msg;
            System.out.println("메시지: " + msg);
        }
    
        public static void main(String[] args) {
            Sample first = new Sample("Hello");
            Sample second = new Sample("World");
        }
    }
    ```
    
- **Default 생성자 (암묵적 생성자):** 생성자를 명시하지 않으면 컴파일러가 자동으로 생성하여 기본값으로 초기화
    
    ```java
    class Sample {
        int value;
        boolean flag;
    
        public static void main(String[] args) {
            Sample s = new Sample();
            System.out.println("value = " + s.value);   // 0
            System.out.println("flag = " + s.flag);     // false
        }
    }
    ```
    
- **생성자 오버로딩:** 같은 이름의 생성자를 매개변수 종류나 개수를 달리하여 여러 개 정의
    
    ```java
    class Sample {
        String info;
    
        // 기본 생성자
        Sample() {
            this.info = "Default";
        }
    
        // 매개변수를 가진 생성자
        Sample(String info) {
            this.info = info;
        }
    
        void printInfo() {
            System.out.println("Info: " + this.info);
        }
    
        public static void main(String[] args) {
            Sample one = new Sample();
            Sample two = new Sample("Custom");
            one.printInfo();   // 출력: Info: Default
            two.printInfo();   // 출력: Info: Custom
        }
    }
    ```
    

---

## 3. this 키워드

현재 객체 자신을 참조하는 키워드로, 멤버 변수와 매개변수의 이름이 중복될 때 모호성을 해소하거나 생성자 간 호출(this())에 사용합니다.

- **멤버 변수와 매개변수 구분:**
    
    ```java
    class Person {
        int age;
    
        Person(int age) {
            this.age = age;
        }
    
        public static void main(String[] args) {
            Person p = new Person(30);
            System.out.println("Age: " + p.age);
        }
    }
    ```
    
- **생성자 간 호출 (this() 사용):**
    
    ```java
    class NumberPair {
        int first, second;
    
        NumberPair(int first, int second) {
            this.first = first;
            this.second = second;
        }
    
        NumberPair(int value) {
            this(value, value);
        }
    
        NumberPair() {
            this(0);
        }
    
        public String toString() {
            return first + ", " + second;
        }
    
        public static void main(String[] args) {
            System.out.println(new NumberPair(5, 7));  // 출력: 5, 7
            System.out.println(new NumberPair(10));    // 출력: 10, 10
            System.out.println(new NumberPair());      // 출력: 0, 0
        }
    }
    ```
    

---

## 4. static 키워드

static 키워드를 사용하면 객체 생성 없이 클래스 이름으로 직접 변수나 메서드에 접근할 수 있습니다.

- **static 변수와 메서드:**
    
    ```java
    class Counter {
        static int count = 0;
    
        Counter() {
            count++;
        }
    
        static void showCount() {
            System.out.println("Current count: " + count);
        }
    }
    
    public class Main {
        public static void main(String[] args) {
            new Counter();
            new Counter();
            Counter.showCount();  // 출력: Current count: 2
        }
    }
    ```
    
- **static 블록:**
    
    클래스가 메모리에 로드될 때 한 번 실행되어 static 변수를 초기화합니다.
    
    ```java
    class Demo {
        static int value;
    
        static {
            value = 50;
            System.out.println("Static 블록 실행됨.");
        }
    
        public static void main(String[] args) {
            System.out.println("value = " + value);
        }
    }
    ```
    

---

## 5. final 키워드

final 키워드는 변수, 메서드, 클래스에 사용되어 한 번 초기화되면 변경할 수 없음을 의미합니다.

- **final 변수:** 한 번 초기화된 후 재할당할 수 없습니다.
    
    ```java
    class ConstantExample {
        public static void main(String[] args) {
            final int MAX_LIMIT = 100;
            // MAX_LIMIT = 200; // 컴파일 오류 발생
            System.out.println("Maximum limit: " + MAX_LIMIT);
        }
    }
    ```
    
- **final 메서드와 클래스:**
    - final 메서드는 서브클래스에서 오버라이드할 수 없습니다.
    - final 클래스는 상속이 불가능합니다.

---

## 6. instanceof 연산자

instanceof 연산자는 객체가 특정 클래스나 인터페이스의 인스턴스인지 확인할 때 사용합니다.

```
class Vehicle { }
class Car extends Vehicle { }

public class Main {
    public static void main(String[] args) {
        Car myCar = new Car();
        System.out.println(myCar instanceof Car);      // 출력: true
        System.out.println(myCar instanceof Vehicle);  // 출력: true
    }
}
```
```
public class Solution05 {
    public static void main(String[] args) {
        System.out.println("Programmer.job = " + Programmer.job);
//        Programmer programmer = new Programmer(); // 새로운 객체를 new 키워드를 통해 만듭니다
        Programmer programmer = new Programmer("최인프라"); // 새로운 객체를 new 키워드를 통해 만듭니다
//        System.out.println("programmer.name = " + programmer.name);
        System.out.println("programmer.name = " + programmer.getName());
        // private으로 감춘 멤버 변수(필드)를 외부에서 접근할 수 있게 하는 함수
        programmer.setName("박백엔");
        System.out.println("programmer.name = " + programmer.getName());
//        programmer.call(); // private으로 막아서 접근 불가
        Programmer programmer2 = new Programmer("이", "풀스택");
        System.out.println("programmer2.name = " + programmer2.getName());
        // 문제가 무엇이냐? -> 그럼 애초에 우리는 생성자를 만든 적이 없는데? 그 땐 어떻게 한거야?
        // 그땐 굳이 지정을 안하면 '패러미터가 없는' 빈 생성자가 기본으로 주어집니다.
        // new Programmer() -> 멤버변수와 메서드만 가지고 객체를 인스턴스화해서 생성
        // new Programmer(programmerName)이 생기면서 직전 빈 생성자가 기본으로 주어지지 않음
        // 수동으로 만들어야함.
        programmer.setName("나는 파이썬 프로그래머다");
        programmer2.setName("나도 파이썬 프로그래머다");
        System.out.println("programmer.getName() = " + programmer.getName());
        System.out.println("programmer2.getName() = " + programmer2.getName());
        Programmer.job = "Coder";
        System.out.println("Programmer.job = " + Programmer.job);
        System.out.println("programmer.getName() = " + programmer.getName());
        System.out.println("programmer2.getName() = " + programmer2.getName());
    }
}

class Programmer {
    
    static String job = "Programmer";

//    Programmer(String programmerName) {
    Programmer(String name) {
//        name = name; // 멤버변수 name을 찾아서
        this.name = name;
        // 매개변수 > 멤버변수 > 클래스변수 순으로 찾아요. 찾으면 해당 값으로 표시
        // 꼭 멤버변수로 찾고 싶으면?
        System.out.println("Programmer.job = " + Programmer.job);
    }

    Programmer(String familyName, String myName) {
        name = familyName + myName;
    }

    public String getName() {
//        return name;
        // 얼마나 호출되었는지 카운트를 한다던가...
        // 특정 자원(외부의 리소스, 연결...)이 요청될 때 메서드를 통해서 처리되도록...
//        return "나의 이름은 " + name; // 출력을 제한하거나 처리하고 싶어...
        return "나의 이름은 " + this.name + " " + job; // 출력을 제한하거나 처리하고 싶어...
    }

    public void setName(String name) {
        this.name = name;
    }

    // 접근제어자로 지정해줄 수 있음
    // public, protected, default, private
    // 변수명 블록 > 생성 > getter 및 setter
    private String name = "김개발";
    // public하고 private만 대부분 씀
    // 나는 롬복! -> 나는 어노테이션으로 모든 걸 할 수 있지...하다가...
    // 너 왜 롬복 써? 대답 못하면 바로... 사수에게 특강 들을 수 있다.
    private void call() {
        System.out.println("엉엉");
    }
}

```