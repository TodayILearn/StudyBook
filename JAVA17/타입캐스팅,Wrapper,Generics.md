# 타입 캐스팅, Wrapper, Generics

## 1. 자바 타입 캐스팅 (Type Casting)

타입 캐스팅은 한 데이터 타입의 값을 다른 데이터 타입으로 변환하는 과정입니다. 자바에서는 주로 두 가지 방식으로 타입 캐스팅을 사용합니다.

### 1.1. 암묵적 형변환 (Widening Conversion)

- **정의:** 작은 크기의 데이터 타입을 큰 크기의 데이터 타입으로 자동 변환합니다.
- **특징:** 데이터 손실이 없으며, 컴파일러가 자동으로 처리합니다.

**예제:** `int`를 `double`로 변환

```java
class CastingExample {
    public static void main(String[] args) {
        int value = 20;
        double result = value;  // 암묵적 형변환 발생
        System.out.println("정수 값: " + value);
        System.out.println("실수 값: " + result);
    }
}

```

### 1.2. 명시적 형변환 (Narrowing Conversion)

- **정의:** 큰 크기의 데이터 타입을 작은 크기의 데이터 타입으로 변환할 때 개발자가 직접 형변환 연산자를 사용합니다.
- **특징:** 데이터 손실 가능성이 있으며, 반드시 명시적으로 캐스팅해야 합니다.

**예제:** `double`을 `int`로 변환

```java
class CastingExample {
    public static void main(String[] args) {
        double value = 15.75;
        int result = (int) value;  // 명시적 형변환: 소수점 이하가 버려짐
        System.out.println("실수 값: " + value);
        System.out.println("정수 값 (소수점 제거): " + result);
    }
}

```

### 1.3. 기타 타입 변환

자바에서는 기본 타입 간의 변환 외에도 문자열과 숫자 간의 변환이 자주 사용됩니다.

- **숫자 → 문자열:** `String.valueOf()` 메소드를 사용
    
    ```java
    class ConversionExample {
        public static void main(String[] args) {
            int num = 30;
            String str = String.valueOf(num);
            System.out.println("정수: " + num);
            System.out.println("문자열: " + str);
        }
    }
    
    ```
    
- **문자열 → 숫자:** `Integer.parseInt()` 등의 메소드를 사용
    
    ```java
    class ConversionExample {
        public static void main(String[] args) {
            String str = "45";
            int num = Integer.parseInt(str);
            System.out.println("문자열: " + str);
            System.out.println("정수: " + num);
        }
    }
    
    ```
    

---

## 2. 자바 Wrapper 클래스

자바의 **Wrapper 클래스**는 기본 자료형을 객체로 다루기 위해 사용됩니다. 주요 특징은 다음과 같습니다.

- **자동 박싱 (Auto-boxing):** 기본 타입을 자동으로 Wrapper 객체로 변환
- **자동 언박싱 (Unboxing):** Wrapper 객체를 기본 타입으로 자동 변환

**예제:** 자동 박싱 및 언박싱

```java
class WrapperExample {
    public static void main(String[] args) {
        int primitiveVal = 10;
        // 자동 박싱
        Integer objectVal = primitiveVal;
        System.out.println("Wrapper 객체: " + objectVal);

        // 자동 언박싱
        int newPrimitive = objectVal;
        System.out.println("기본 타입: " + newPrimitive);
    }
}

```

**추가 정보:**

- Wrapper 클래스를 사용하면 컬렉션 프레임워크에서 기본 자료형도 객체처럼 다룰 수 있습니다.
- 객체는 `null` 값을 가질 수 있으나, 기본 타입은 그렇지 않습니다.

---

## 3. 자바 제네릭 (Generics)

제네릭은 클래스나 메소드를 작성할 때, 처리할 데이터 타입을 매개변수화하여 다양한 타입에 대해 재사용할 수 있게 합니다.

### 3.1. 제네릭 클래스

제네릭 클래스를 사용하면 하나의 클래스에서 다양한 타입의 데이터를 처리할 수 있습니다.

**예제:** 제네릭 클래스를 활용한 박스 클래스

```java
class GenericBox<T> {
    private T data;

    public GenericBox(T data) {
        this.data = data;
    }

    public T getData() {
        return data;
    }
}

public class TestGeneric {
    public static void main(String[] args) {
        GenericBox<Integer> intBox = new GenericBox<>(100);
        System.out.println("Integer 값: " + intBox.getData());

        GenericBox<String> strBox = new GenericBox<>("Hello Java");
        System.out.println("String 값: " + strBox.getData());
    }
}
```

### 3.2. 제네릭 메소드

제네릭 메소드는 메소드 자체에 타입 매개변수를 선언하여 호출 시 타입을 유연하게 지정할 수 있게 합니다.

**예제:** 제네릭 메소드 사용

```java
class GenericUtil {
    public <T> void display(T element) {
        System.out.println("제네릭 메소드 호출: " + element);
    }
}

public class TestGenericMethod {
    public static void main(String[] args) {
        GenericUtil util = new GenericUtil();
        util.display("Java Programming");
        util.display(25);
    }
}
```

### 3.3. 제한된 타입 (Bounded Types)

제네릭 타입 매개변수에 제한을 두어 특정 타입 또는 그 하위 타입만 허용할 수 있습니다.

**예제:** `Number` 타입만 허용하는 제네릭 클래스

```java
class NumericBox<T extends Number> {
    private T num;

    public NumericBox(T num) {
        this.num = num;
    }

    public double getDoubleValue() {
        return num.doubleValue();
    }
}

public class TestBoundedGeneric {
    public static void main(String[] args) {
        NumericBox<Integer> intBox = new NumericBox<>(100);
        System.out.println("Double 값: " + intBox.getDoubleValue());

        // NumericBox<String> strBox = new NumericBox<>("Hello"); // 컴파일 에러 발생
    }
}
```

### 3.4. 제네릭의 장점

- **코드 재사용성:** 하나의 코드로 다양한 타입에 대해 작동 가능
- **컴파일 타임 타입 체크:** 잘못된 타입 사용 시 컴파일 에러 발생
- **컬렉션과의 결합:** 타입 안전한 컬렉션 사용이 가능 (예: `ArrayList<String>`)