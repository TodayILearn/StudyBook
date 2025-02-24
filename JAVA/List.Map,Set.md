# List, Map, Set

## 1. ArrayList

**개요:**

- **동적 배열:** 기존 배열은 고정 크기인 반면, ArrayList는 요소의 추가/삭제에 따라 자동으로 크기가 조정되는 동적 배열입니다.
- **제네릭 사용:** 원시 타입은 사용할 수 없으며, 반드시 Wrapper 클래스를 사용해야 합니다.

**생성 및 기본 사용법:**

```java
java
복사
import java.util.ArrayList;

public class ArrayListExample {
    public static void main(String[] args) {
        // ArrayList 생성 (문자열 타입)
        ArrayList<String> languages = new ArrayList<>();

        // 요소 추가 (add)
        languages.add("Java");
        languages.add("Python");
        languages.add("Swift");
        System.out.println("ArrayList: " + languages);

        // 요소 접근 (get)
        String lang = languages.get(1);  // 인덱스 1의 요소
        System.out.println("Element at index 1: " + lang);

        // 요소 변경 (set)
        languages.set(2, "JavaScript");
        System.out.println("Modified ArrayList: " + languages);

        // 요소 삭제 (remove)
        String removed = languages.remove(0);
        System.out.println("Removed Element: " + removed);
        System.out.println("Updated ArrayList: " + languages);

        // 반복문을 통한 순회 (for-each)
        System.out.print("Iterating: ");
        for (String language : languages) {
            System.out.print(language + ", ");
        }
    }
}
```

**추가 메서드 및 특징:**

- `size()`: 리스트의 길이를 반환
- `contains()`: 특정 요소의 존재 여부 확인
- `sort()`: 리스트 정렬 (Java 8 이상에서는 `Collections.sort()` 또는 `list.sort()` 사용)
- `clone()`: 리스트 복제 (얕은 복사)
- Iterator나 forEach 메서드를 통한 다양한 순회 방법 제공

---

## 2. HashMap

**개요:**

- **키-값 매핑:** HashMap은 키와 값의 쌍으로 데이터를 저장합니다. 키는 중복될 수 없으며, 각 키는 하나의 값에만 매핑됩니다.
- **빠른 검색:** 해시 함수를 이용해 요소에 빠르게 접근할 수 있습니다.
- **비동기적:** 기본적으로 동기화되어 있지 않으므로 멀티스레드 환경에서는 외부에서 동기화가 필요합니다.

**생성 및 기본 사용법:**

```java
java
복사
import java.util.HashMap;

public class HashMapExample {
    public static void main(String[] args) {
        // HashMap 생성 (키: String, 값: Integer)
        HashMap<String, Integer> languages = new HashMap<>();

        // 요소 추가 (put)
        languages.put("Java", 8);
        languages.put("Python", 3);
        languages.put("JavaScript", 1);
        System.out.println("HashMap: " + languages);

        // 요소 접근 (get)
        Integer version = languages.get("Java");
        System.out.println("Version for Java: " + version);

        // 요소 변경 (replace)
        languages.replace("Python", 4);
        System.out.println("After replace: " + languages);

        // 요소 삭제 (remove)
        Integer removedValue = languages.remove("JavaScript");
        System.out.println("Removed value: " + removedValue);
        System.out.println("Updated HashMap: " + languages);

        // 키, 값, 키/값 쌍에 대한 조회
        System.out.println("Keys: " + languages.keySet());
        System.out.println("Values: " + languages.values());
        System.out.println("Entries: " + languages.entrySet());
    }
}
```

**추가 메서드 및 특징:**

- `getOrDefault()`: 지정 키가 없으면 기본값 반환
- `putIfAbsent()`: 키가 없을 경우에만 추가
- `compute()`, `merge()` 등으로 복잡한 연산 가능
- `clear()`: 모든 요소 삭제

---

## 3. HashSet

**개요:**

- **집합 자료구조:** HashSet은 중복을 허용하지 않는 요소들의 집합으로, 순서가 보장되지 않습니다.
- **빠른 검색:** 내부적으로 해시 테이블을 사용하여 빠른 검색이 가능합니다.

**생성 및 기본 사용법:**

```java
java
복사
import java.util.HashSet;
import java.util.Iterator;

public class HashSetExample {
    public static void main(String[] args) {
        // HashSet 생성 (정수 타입)
        HashSet<Integer> numbers = new HashSet<>();

        // 요소 추가 (add, addAll)
        numbers.add(2);
        numbers.add(4);
        numbers.add(6);
        System.out.println("HashSet: " + numbers);

        // Iterator를 이용한 접근
        Iterator<Integer> iterator = numbers.iterator();
        System.out.print("Iterating: ");
        while (iterator.hasNext()) {
            System.out.print(iterator.next() + ", ");
        }
        System.out.println();

        // 요소 삭제 (remove)
        boolean removed = numbers.remove(4);
        System.out.println("Is 4 removed? " + removed);
        System.out.println("After removal: " + numbers);

        // 모든 요소 삭제 (clear)
        numbers.clear();
        System.out.println("After clear, isEmpty(): " + numbers.isEmpty());
    }
}
```

**집합 연산:**

- **합집합 (Union):** `addAll()` 사용
- **교집합 (Intersection):** `retainAll()` 사용
- **차집합 (Difference):** `removeAll()` 사용
- **부분집합 여부:** `containsAll()` 사용

**추가 메서드:**

- `contains()`: 특정 요소 존재 여부 확인
- `clone()`: 집합 복사 (얕은 복사)
- `size()`, `isEmpty()`, `clear()`

---

## 결론

Java Collection Framework는 ArrayList, HashMap, HashSet 등 다양한 클래스를 제공하여 데이터 저장, 검색, 수정 및 삭제 등의 작업을 효율적으로 수행할 수 있게 합니다.

- **ArrayList:** 동적 배열로 순차적 데이터 저장 및 접근에 유리
- **HashMap:** 키-값 매핑을 통한 빠른 검색과 수정 기능 제공
- **HashSet:** 중복 없이 요소를 관리하며 집합 연산을 수행하는 데 적합

각 클래스는 용도와 상황에 따라 적절히 선택하여 사용할 수 있으며, Java 17의 최신 API 문서를 참고하면 보다 자세한 정보를 얻을 수 있습니다.