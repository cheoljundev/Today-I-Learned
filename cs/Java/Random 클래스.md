- 내부적으로는 Math.random() 메서드를 사용하지만, 좀 더 다양한 랜덤을 사용하고 싶다면 Random 클래스를 사용한다.
- Random의 생성자의 인수로 들어가는 seed가 같으면 계속 같은 결과가 나타나는데, 테스트 코드 작성시 유용.

```java
package lang.math;

import java.util.Random;

public class RandomMain {
    public static void main(String[] args) {
        Random random = new Random();
        // Random random = new Random(1); // seed가 같으면 random의 결과가 같다.

        int randomInt = random.nextInt();
        System.out.println("randomInt = " + randomInt);

        double randomDouble = random.nextDouble();
        System.out.println("randomDouble = " + randomDouble); // 0.0d ~ 1.0d

        boolean randomBoolean = random.nextBoolean();
        System.out.println("randomBoolean = " + randomBoolean);

        // 범위 조회
        int randomRange1 = random.nextInt(10); // 0 ~ 9까지
        System.out.println("randomRange1 = " + randomRange1);
        System.out.println("0 ~ 9 : " + randomRange1);

        int randomRange2 = random.nextInt(10) + 1; // 1 ~ 10까지
        System.out.println("1 ~ 10 : " + randomRange2);
    }
}

```