# 상속, 메서드 오버라이딩, super

## 1. 기본 상속 (Basic Inheritance)

**개념:**

부모 클래스(슈퍼클래스)의 필드와 메서드를 자식 클래스(서브클래스)가 물려받아 재사용하고 확장할 수 있습니다.

**예제:**

`Vehicle` 클래스를 부모로 하고, `Car` 클래스가 상속받아 추가 기능을 구현합니다.

```java
class Vehicle {
    String brand;

    public void start() {
        System.out.println("Vehicle is starting.");
    }
}

class Car extends Vehicle {
    public void drive() {
        System.out.println("Car is driving. Brand: " + brand);
    }
}

public class Main {
    public static void main(String[] args) {
        Car myCar = new Car();
        myCar.brand = "Toyota";
        myCar.start();   // 출력: Vehicle is starting.
        myCar.drive();   // 출력: Car is driving. Brand: Toyota
    }
}
```

---

## 2. 메서드 오버라이딩 (Method Overriding)

**개념:**

자식 클래스가 부모 클래스와 동일한 이름, 반환형, 매개변수를 가진 메서드를 재정의하여, 호출 시 자식 클래스의 메서드가 실행되도록 합니다.

※ `@Override` 어노테이션을 사용하면 컴파일러가 올바른 오버라이딩을 확인해 줍니다.

**예제:**

부모 클래스 `Vehicle`의 `fuelType()` 메서드를 자식 클래스 `ElectricCar`에서 재정의합니다.

```java
class Vehicle {
    public void fuelType() {
        System.out.println("Uses generic fuel.");
    }
}

class ElectricCar extends Vehicle {
    @Override
    public void fuelType() {
        System.out.println("Uses electric power.");
    }
}

public class Main {
    public static void main(String[] args) {
        ElectricCar ecoCar = new ElectricCar();
        ecoCar.fuelType();   // 출력: Uses electric power.
    }
}
```

---

## 3. super 키워드 활용

### 3-1. 부모 메서드 호출

**개념:**

자식 클래스에서 부모 클래스의 메서드를 호출할 때 `super`를 사용하면, 오버라이딩된 메서드 중 부모의 구현을 명시적으로 실행할 수 있습니다.

**예제:**

`Vehicle`의 `fuelType()`과 자식 클래스 `HybridCar`에서 부모의 메서드를 호출한 후 추가 동작을 실행합니다.

```java
class Vehicle {
    public void fuelType() {
        System.out.println("Uses generic fuel.");
    }
}

class HybridCar extends Vehicle {
    @Override
    public void fuelType() {
        super.fuelType();  // 부모의 fuelType() 호출
        System.out.println("Also uses electric power.");
    }
}

public class Main {
    public static void main(String[] args) {
        HybridCar hybrid = new HybridCar();
        hybrid.fuelType();
        // 출력:
        // Uses generic fuel.
        // Also uses electric power.
    }
}
```

### 3-2. 부모 생성자 및 필드 접근

**개념:**

자식 클래스의 생성자에서 `super()`를 사용하면 부모 클래스의 생성자를 명시적으로 호출할 수 있으며, 동일한 이름의 필드가 있는 경우 `super.field`로 부모 필드에 접근할 수 있습니다.

**예제:**

`Employee` 클래스와 이를 상속한 `Manager` 클래스에서 부모 생성자를 호출하고, 오버라이딩한 `getSalary()` 메서드에서 부모의 값을 사용합니다.

```java
class Employee {
    protected double baseSalary;

    Employee(double baseSalary) {
        this.baseSalary = baseSalary;
    }

    public double getSalary() {
        return baseSalary;
    }
}

class Manager extends Employee {
    private double bonus;

    Manager(double baseSalary, double bonus) {
        super(baseSalary);  // 부모 생성자 호출
        this.bonus = bonus;
    }

    @Override
    public double getSalary() {
        // 부모의 getSalary()를 호출하여 기본 급여에 보너스를 더함
        return super.getSalary() + bonus;
    }
}

public class Main {
    public static void main(String[] args) {
        Manager mgr = new Manager(3000, 1500);
        System.out.println("Manager's salary: " + mgr.getSalary());
        // 출력: Manager's salary: 4500.0
    }
}
```

또한, 부모와 자식 클래스에 동일한 이름의 필드가 있을 경우 아래와 같이 구분할 수 있습니다.

```java
class Person {
    protected String name = "Unnamed";
}

class Student extends Person {
    public String name = "StudentName";

    public void printNames() {
        System.out.println("Child name: " + name);       // 자식 필드
        System.out.println("Parent name: " + super.name);  // 부모 필드
    }
}

public class Main {
    public static void main(String[] args) {
        Student s = new Student();
        s.printNames();
        // 출력:
        // Child name: StudentName
        // Parent name: Unnamed
    }
}
```

---

## 4. protected 멤버 활용 (Protected Members in Inheritance)

**개념:**

`protected` 접근 제어자를 사용하면, 같은 패키지 내와 서브클래스에서 해당 필드나 메서드에 접근할 수 있습니다.

**예제:**

`Person` 클래스의 protected 필드를 자식 클래스 `Student`에서 사용합니다.
```
class Person {
    protected String name;

    public void introduce() {
        System.out.println("Hello, I am " + name);
    }
}

class Student extends Person {
    public void setName(String name) {
        this.name = name;
    }

    public void study() {
        System.out.println(name + " is studying.");
    }
}

public class Main {
    public static void main(String[] args) {
        Student student = new Student();
        student.setName("Alice");
        student.introduce();   // 출력: Hello, I am Alice
        student.study();       // 출력: Alice is studying.
    }
}
```