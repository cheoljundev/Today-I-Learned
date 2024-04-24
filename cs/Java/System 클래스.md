시스템 속성을 출력하거나 입출력 함수를 제공하는 등 여러 편리한 메서드를 제공하는 클래스이다.

```java
package lang.system;

import java.util.Arrays;

public class SystemMain {
    public static void main(String[] args) {
        // 현재 시간(밀리초)을 가져온다
        long currentTimeMillis = System.currentTimeMillis();
        System.out.println("currentTimeMillis = " + currentTimeMillis);

        // 현재 시간(나노초)을 가져온다
        long currentNano = System.nanoTime();
        System.out.println("currentNano = " + currentNano);

        // 환경변수를 읽는다
        System.out.println("getenv= " + System.getenv());

        // 시스템 속성을 읽는다
        System.out.println("properties= " + System.getProperties());
        System.out.println("Java Version= " + System.getProperty("java.version"));

        // 배열을 고속으로 복사한다
        char[] originalArray = {'h', 'e', 'l', 'o'};
        char[] copiedArray = new char[5];
        System.arraycopy(originalArray,0,copiedArray,0, originalArray.length);

        // 배열 출력
        System.out.println("copiedArray = " + copiedArray);
        System.out.println("Array.toString() = " + Arrays.toString(copiedArray));

        // 프로그램 종료
        System.exit(0);
        System.out.println("hello");
    }
}

```