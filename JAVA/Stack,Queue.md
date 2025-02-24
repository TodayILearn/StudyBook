# Stack, Queue

## 1. 스택과 큐의 개념

### 스택 (Stack)

- **LIFO (Last In, First Out)**
  마지막에 삽입된 요소가 가장 먼저 삭제됩니다.
- **주요 연산:**
  - **push()**: 요소를 스택의 맨 위에 삽입
  - **pop()**: 스택의 맨 위의 요소를 삭제하고 반환
  - **peek()**: 스택의 맨 위의 요소를 확인 (삭제하지 않음)

**대표적 문제 예시:**

- **문자열 뒤집기:**
  입력된 문자열의 각 문자를 스택에 push한 후, 스택에서 하나씩 pop하여 순서를 반전시킵니다.
  (예: "Hello" → "olleH")

---

### 큐 (Queue)

- **FIFO (First In, First Out)**
  가장 먼저 삽입된 요소가 가장 먼저 삭제됩니다.
- **주요 연산:**
  - **offer()**: 큐의 뒤쪽에 요소를 삽입
  - **poll()**: 큐의 앞쪽의 요소를 삭제하고 반환
  - **peek()**: 큐의 앞쪽의 요소를 확인 (삭제하지 않음)

**대표적 문제 예시:**

- **프린터 작업 대기열:**
  인쇄 요청이 들어오면 큐에 순서대로 저장하고, 프린터는 큐에서 가장 먼저 들어온 작업부터 처리합니다.

---

## 2. ArrayDeque를 활용한 구현

Java에서는 ArrayDeque 클래스를 사용하면 스택과 큐 모두를 효율적으로 구현할 수 있습니다.

### 2.1. ArrayDeque를 사용한 스택 구현 (LIFO)

```java
import java.util.ArrayDeque;

public class StackExample {
    public static void main(String[] args) {
        // ArrayDeque를 스택처럼 사용 (LIFO)
        ArrayDeque<String> stack = new ArrayDeque<>();

        // 스택에 문자열의 각 문자를 push하여 문자열 뒤집기 예제
        String input = "Hello";
        for (char ch : input.toCharArray()) {
            stack.push(String.valueOf(ch));
        }

        // 스택에서 pop하여 뒤집힌 문자열 구성
        StringBuilder reversed = new StringBuilder();
        while (!stack.isEmpty()) {
            reversed.append(stack.pop());
        }

        System.out.println("원본 문자열: " + input);
        System.out.println("뒤집힌 문자열: " + reversed);
    }
}
```

### 2.2. ArrayDeque를 사용한 큐 구현 (FIFO)

```java
import java.util.ArrayDeque;
import java.util.Queue;

public class QueueExample {
    public static void main(String[] args) {
        // ArrayDeque를 큐처럼 사용 (FIFO)
        Queue<String> printerQueue = new ArrayDeque<>();

        // 프린터 작업 대기열에 작업 추가 (offer)
        printerQueue.offer("문서1");
        printerQueue.offer("문서2");
        printerQueue.offer("문서3");
        System.out.println("대기 중인 프린터 작업: " + printerQueue);

        // 프린터 작업 처리 (poll)
        String job = printerQueue.poll();
        System.out.println("처리한 작업: " + job);
        System.out.println("남은 작업: " + printerQueue);
    }
}
```

---

## 3. 결론

- **스택(LIFO):**
  마지막에 추가된 데이터가 먼저 처리되는 자료구조로, 문자열 뒤집기, undo 기능 등 다양한 응용 문제에 활용됩니다.
- **큐(FIFO):**
  먼저 추가된 데이터가 먼저 처리되는 자료구조로, 프린터 작업 대기열, 요청 처리 시스템 등에서 사용됩니다.
- **ArrayDeque 사용:**
  ArrayDeque는 스택과 큐 모두의 기능을 효율적으로 제공하며, 성능 면에서 LinkedList보다 유리한 경우가 많습니다.
