## /bin 디렉터리의 주요 실행파일

### javac

자바 컴파일러. *.java파일(소스코드)을 *.class(바이트코드)로 컴파일해준다.

```bash
javac hello.java
```

### java

자바 인터프리터. *.class파일을 번역해서 실행한다.

```bash
java hello
```

### javap

- 자바 역 어셈블러. 바이트코드를 java파일로 역 어셈블한다.
- 소스 코드를 완벽하게 어셈블 할 수는 없다. 선언부만 복구한다.
    - 목적은, 클래스 구조 이해 목적이다.
        - 멤버변수
        - 상속
        - 메서드
- `-c` 옵션을 사용하면 바이트 코드 부분도 확인이 가능하다.

### javadoc

java API 문서 형식으로 doc파일을 자동 생성해주는 파일이다.

/**
*
*/

형식이 javadoc 형식의 주석이다.


```java
/**
 * 이 클래스는 간단한 "Hello, world"를 출력하는 예제입니다.
 */
public class hello {
    
    /**
     * 프로그램의 진입점입니다.
     * @param args 명령행 인수 (사용되지 않음)
     */
    public static void main(String[] args) {
        // "Hello, world"를 출력합니다.
        System.out.println("Hello, world");
    }
}
```

### jar

java파일 실행에 필요한 클래스, 파일을 묶어서 압축, 압축해제한다.