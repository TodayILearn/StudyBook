# Arrays

## 1. 배열의 개요 및 선언

- **정의:**
  배열은 동일한 타입의 데이터를 연속된 메모리 공간에 저장하는 자료구조입니다.
  예를 들어, 100명의 이름을 저장하려면 100개의 요소를 가진 String 배열을 생성할 수 있습니다.
- **선언 방법:**
  ```java
  // 타입과 식별자를 이용하여 선언
  dataType[] arrayName;

  // 예: double 타입 배열 선언
  double[] data;
  ```
- **메모리 할당:**
  선언 후 배열의 크기를 지정하여 메모리를 할당합니다.
  ```java
  data = new double[10]; // 10개의 double 값을 저장할 수 있음
  // 또는 한 줄로 선언과 할당을 동시에
  double[] data = new double[10];
  ```

---

## 2. 배열 초기화 및 요소 접근

- **초기화:**
  배열 선언 시 중괄호를 사용해 초기값을 지정할 수 있습니다.
  ```java
  int[] age = {12, 4, 5, 2, 5};  // 요소 개수는 5
  ```
  혹은 선언 후 인덱스를 이용하여 각 요소에 값을 할당할 수 있습니다.
  ```java
  int[] age = new int[5];
  age[0] = 12;
  age[1] = 4;
  age[2] = 5;
  // ...
  ```
- **인덱스 접근:**
  배열의 첫 번째 요소는 인덱스 0, 마지막 요소는 (크기-1) 인덱스입니다.
  ```java
  System.out.println(age[0]);  // 첫 번째 요소 출력
  ```

---

## 3. 배열 순회(Looping Through Array Elements)

- **for문 사용:**
  배열의 인덱스를 이용하여 순차적으로 접근합니다.
  ```java
  int[] age = {12, 4, 5};
  for (int i = 0; i < age.length; i++) {
      System.out.println(age[i]);
  }
  ```
- **for-each문 사용:**
  배열의 각 요소를 직접 순회할 때 유용합니다.
  ```java
  for (int a : age) {
      System.out.println(a);
  }
  ```
- **예제: 배열 요소의 합과 평균 구하기**
  ```java
  public class Main {
      public static void main(String[] args) {
          int[] numbers = {2, -9, 0, 5, 12, -25, 22, 9, 8, 12};
          int sum = 0;

          for (int num : numbers) {
              sum += num;
          }

          double average = (double) sum / numbers.length;
          System.out.println("Sum = " + sum);
          System.out.println("Average = " + average);
      }
  }
  ```
  _출력 예:_
  Sum = 36
  Average = 3.6

---

## 4. 다차원 배열 (Multidimensional Arrays)

- **정의:**
  다차원 배열은 배열의 각 요소가 또 다른 배열인 구조입니다.
  예를 들어, 2차원 배열은 행과 열로 구성됩니다.
- **2차원 배열 선언 및 초기화:**
  ```java
  // 선언과 동시에 초기화 (각 행의 길이는 다를 수 있음)
  int[][] a = {
      {1, 2, 3},
      {4, 5, 6, 9},
      {7}
  };
  ```
- **2차원 배열 요소 접근:**
  ```java
  System.out.println(a[0][1]);  // 첫 번째 행, 두 번째 요소 출력 (2)
  ```
- **다중 반복문을 통한 순회:**
  ```java
  for (int i = 0; i < a.length; i++) {
      for (int j = 0; j < a[i].length; j++) {
          System.out.println(a[i][j]);
      }
  }
  ```
  또는 for-each 문을 이용하면:
  ```java
  for (int[] row : a) {
      for (int value : row) {
          System.out.println(value);
      }
  }
  ```
- **3차원 배열 예제:**
  ```java
  String[][][] data = new String[3][4][2]; // 3 x 4 x 2 크기의 3차원 배열
  ```

---

## 5. 배열 복사 (Copying Arrays)

배열 복사에는 얕은 복사(shallow copy)와 깊은 복사(deep copy)가 있으며, 여러 방법을 사용할 수 있습니다.

### 5.1. 할당 연산자(=) 사용

- **특징:**
  단순히 참조를 복사하므로, 두 배열이 같은 객체를 참조하게 되어 한쪽의 변경이 다른 쪽에 영향을 줍니다.
      ```java
      int[] numbers = {1, 2, 3, 4, 5, 6};
      int[] positiveNumbers = numbers;
      ```

### 5.2. for문을 이용한 복사 (깊은 복사)

- **예제:**
  ```java
  int[] source = {1, 2, 3, 4, 5, 6};
  int[] destination = new int[source.length];
  for (int i = 0; i < source.length; i++) {
      destination[i] = source[i];
  }
  System.out.println(java.util.Arrays.toString(destination));
  ```

### 5.3. System.arraycopy() 사용

- **문법:**
  ```java
  System.arraycopy(src, srcPos, dest, destPos, length);
  ```
- **예제:**
  ```java
  int[] n1 = {2, 3, 12, 4, 12, -2};
  int[] n2 = new int[n1.length];
  System.arraycopy(n1, 0, n2, 0, n1.length);
  System.out.println("n2 = " + java.util.Arrays.toString(n2));
  ```

### 5.4. Arrays.copyOfRange() 사용

- **예제:**
  ```java
  int[] source = {2, 3, 12, 4, 12, -2};
  int[] destination1 = java.util.Arrays.copyOfRange(source, 0, source.length);
  int[] destination2 = java.util.Arrays.copyOfRange(source, 2, 5);
  System.out.println("destination1 = " + java.util.Arrays.toString(destination1));
  System.out.println("destination2 = " + java.util.Arrays.toString(destination2));
  ```

### 5.5. 2차원 배열 복사

- **for문을 이용한 복사 (깊은 복사):**
  ```java
  int[][] source = {
      {1, 2, 3, 4},
      {5, 6},
      {0, 2, 42, -4, 5}
  };

  int[][] destination = new int[source.length][];
  for (int i = 0; i < source.length; i++) {
      destination[i] = new int[source[i].length];
      for (int j = 0; j < source[i].length; j++) {
          destination[i][j] = source[i][j];
      }
  }
  System.out.println(java.util.Arrays.deepToString(destination));
  ```
- **내부 반복문을 System.arraycopy()로 대체:**

```
for (int i = 0; i < source.length; i++) {
    destination[i] = new int[source[i].length];
    System.arraycopy(source[i], 0, destination[i], 0, source[i].length);
}
System.out.println(java.util.Arrays.deepToString(destination));
```
