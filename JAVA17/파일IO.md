# File I/O

## 1. Java File 클래스를 이용한 파일 작업

### 1.1. 파일 객체 생성 및 새 파일 만들기

1. **File 객체 생성**
    - `java.io.File` 클래스를 이용하여 파일 경로를 지정한 객체를 생성합니다.
    - 이때, 파일 객체를 생성하는 것만으로 실제 파일이 만들어지지는 않습니다.
2. **파일 존재 여부 확인 후 파일 생성**
    - `createNewFile()` 메서드를 사용하여 실제 파일을 생성합니다.
    - 파일이 이미 존재하면 `false`를 반환하므로, 이를 통해 존재 여부를 확인할 수 있습니다.

```java
import java.io.File;
import java.io.IOException;

public class FileCreateExample {
    public static void main(String[] args) {
        // 1. 파일 객체 생성 (현재 디렉터리에 example.txt)
        File file = new File("example.txt");

        try {
            // 2. 파일이 존재하지 않으면 새 파일 생성
            if (file.createNewFile()) {
                System.out.println("새 파일이 생성되었습니다.");
            } else {
                System.out.println("파일이 이미 존재합니다.");
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

---

### 1.2. 파일에 데이터 쓰기

1. **FileWriter 객체 생성**
    - `java.io.FileWriter`를 사용하여 파일에 데이터를 기록할 수 있습니다.
    - try-with-resources 구문을 사용하면 자동으로 자원을 해제할 수 있습니다.
2. **데이터 쓰기**
    - `write()` 메서드를 이용하여 문자열 데이터를 파일에 씁니다.

```java
import java.io.File;
import java.io.FileWriter;
import java.io.IOException;

public class FileWriteExample {
    public static void main(String[] args) {
        File file = new File("example.txt");

        try (FileWriter writer = new FileWriter(file)) {
            // 파일에 데이터 기록
            writer.write("Java 17의 파일 작업 예제입니다.");
            System.out.println("파일에 데이터를 썼습니다.");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

---

### 1.3. 파일에서 데이터 읽기

1. **FileReader 및 BufferedReader 사용**
    - `java.io.FileReader`와 `java.io.BufferedReader`를 사용하여 파일의 내용을 한 줄씩 읽어올 수 있습니다.
    - try-with-resources 구문을 사용하면 스트림을 자동으로 닫습니다.
2. **데이터 읽기**
    - `readLine()` 메서드를 통해 한 줄씩 읽어와서 화면에 출력합니다.

```java
import java.io.File;
import java.io.FileReader;
import java.io.BufferedReader;
import java.io.IOException;

public class FileReadExample {
    public static void main(String[] args) {
        File file = new File("example.txt");

        try (BufferedReader reader = new BufferedReader(new FileReader(file))) {
            String line;
            System.out.println("파일 내용:");
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

---

### 1.4. 파일 삭제하기

1. **delete() 메서드 사용**
    - `File` 클래스의 `delete()` 메서드를 이용하여 파일을 삭제합니다.
    - 삭제에 성공하면 `true`, 실패하면 `false`를 반환합니다.

```java
import java.io.File;

public class FileDeleteExample {
    public static void main(String[] args) {
        File file = new File("example.txt");

        // 파일 삭제 시도
        if (file.delete()) {
            System.out.println("파일이 삭제되었습니다.");
        } else {
            System.out.println("파일 삭제에 실패했습니다.");
        }
    }
}
```

---

## 2. Java 17 내장 HttpClient를 이용한 HTTP 파일 다운로드

### 2.1. HttpClient와 HttpRequest 생성

1. **HttpClient 생성**
    - `java.net.http.HttpClient`를 사용하여 HTTP 클라이언트 객체를 생성합니다.
2. **HttpRequest 생성**
    - 다운로드할 파일의 URL을 지정하여 `HttpRequest` 객체를 생성합니다.

```java
import java.net.URI;
import java.net.http.HttpClient;
import java.net.http.HttpRequest;

public class HttpDownloadStep1 {
    public static void main(String[] args) {
        // 다운로드할 파일의 URL 설정
        String fileURL = "https://example.com/sample.txt";

        // HttpClient 생성
        HttpClient client = HttpClient.newHttpClient();

        // HttpRequest 객체 생성
        HttpRequest request = HttpRequest.newBuilder()
                .uri(URI.create(fileURL))
                .build();

        System.out.println("HttpClient와 HttpRequest가 생성되었습니다.");
    }
}
```

---

### 2.2. 파일 다운로드 및 저장

1. **파일 저장 경로 설정**
    - `java.nio.file.Path`를 이용하여 저장할 파일의 경로를 지정합니다.
2. **파일 다운로드 요청 보내기**
    - `HttpResponse.BodyHandlers.ofFile()`을 사용하여 다운로드한 데이터를 파일로 바로 저장합니다.
    - `client.send()` 메서드를 호출하여 동기적으로 HTTP 요청을 수행합니다.

```java
import java.net.URI;
import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;
import java.nio.file.Path;
import java.io.IOException;

public class HttpDownloadStep2 {
    public static void main(String[] args) {
        String fileURL = "https://example.com/sample.txt";
        Path destination = Path.of("downloaded_sample.txt");

        HttpClient client = HttpClient.newHttpClient();
        HttpRequest request = HttpRequest.newBuilder()
                .uri(URI.create(fileURL))
                .build();

        try {
            // HTTP 요청을 보내고 응답을 파일로 저장
            HttpResponse<Path> response = client.send(request,
                    HttpResponse.BodyHandlers.ofFile(destination));
            System.out.println("파일 다운로드 완료: " + response.body());
        } catch (IOException | InterruptedException e) {
            e.printStackTrace();
        }
    }
}
```

---

## 3. Base64 텍스트를 이미지 파일로 변환하여 저장하기

### 3.1. Base64 문자열 디코딩 준비

1. **Base64 문자열 준비**
    - Base64 인코딩된 문자열을 준비합니다. (실제 사용 시에는 긴 문자열이 될 수 있음)
2. **Base64 디코더 사용**
    - `java.util.Base64` 클래스의 `getDecoder()`를 사용하여 디코딩할 준비를 합니다.

```java
import java.util.Base64;

public class Base64DecodeStep1 {
    public static void main(String[] args) {
        // 예시 Base64 인코딩 문자열 (짧은 예제)
        String base64Image = "iVBORw0KGgoAAAANSUhEUgAAAAUA"
                + "AAAFCAYAAACNbyblAAAAHElEQVQI12P4"
                + "//8/w38GIAXDIBKE0DHxgljNBAAO"
                + "9TXL0Y4OHwAAAABJRU5ErkJggg==";

        // Base64 문자열 디코딩 준비
        Base64.Decoder decoder = Base64.getDecoder();
        byte[] imageBytes = decoder.decode(base64Image);

        System.out.println("Base64 문자열이 디코딩되었습니다. 바이트 수: " + imageBytes.length);
    }
}
```

---

### 3.2. 디코딩된 데이터를 이미지 파일로 저장

1. **FileOutputStream 사용**
    - `java.io.FileOutputStream`을 사용하여 디코딩된 바이트 배열을 이미지 파일로 저장합니다.
2. **try-with-resources 구문으로 자원 관리**
    - 스트림을 열고 데이터를 기록한 후 자동으로 닫히도록 합니다.

```
import java.io.FileOutputStream;
import java.io.IOException;
import java.util.Base64;

public class Base64DecodeStep2 {
    public static void main(String[] args) {
        String base64Image = "iVBORw0KGgoAAAANSUhEUgAAAAUA"
                + "AAAFCAYAAACNbyblAAAAHElEQVQI12P4"
                + "//8/w38GIAXDIBKE0DHxgljNBAAO"
                + "9TXL0Y4OHwAAAABJRU5ErkJggg==";

        byte[] imageBytes = Base64.getDecoder().decode(base64Image);

        // 디코딩된 데이터를 이미지 파일로 저장 (예: PNG 파일)
        try (FileOutputStream fos = new FileOutputStream("decoded_image.png")) {
            fos.write(imageBytes);
            System.out.println("디코딩된 이미지 파일이 생성되었습니다.");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```