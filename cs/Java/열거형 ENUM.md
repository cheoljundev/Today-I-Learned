String형은 타입 안정성과 일관성이 부족하다. 이를 위해 타입 안전 열거형 패턴(enum)을 사용한다.

- 타입 안정성 문제 : 오타나 소문자/대문자 잘못 입력
    - 정해진 인스턴스만 생성해 사용하므로 문제 방지
- 일관성 문제 : 어떤 문자든 입력 가능
    - 해당 타입만 넣을 수 있으므로 문제 방지

이 패턴은 직접 구현할 수도 있지만, 코드가 복잡하여 JAVA에서 ENUM타입을 제공한다.

## ENUM 직접 구현

```java
public class ClassGrade {
    public static final ClassGrade BASIC = new ClassGrade();
    public static final ClassGrade GOLD = new ClassGrade();
    public static final ClassGrade DIAMOND = new ClassGrade();
}


public class DiscountService {
    public int discount(ClassGrade classGrade, int price) {
        int discountPercent = 0;

        if (classGrade == ClassGrade.BASIC) {
            discountPercent = 10;
        } else if (classGrade == ClassGrade.GOLD) {
            discountPercent = 20;
        } else if (classGrade == ClassGrade.DIAMOND) {
            discountPercent = 30;
        } else {
            System.out.println("할인X");
        }

        return price * discountPercent / 100;
    }
}

public class ClassGradeEx2_1 {
    public static void main(String[] args) {
        int price = 10000;
        DiscountService discountService = new DiscountService();
        int basic = discountService.discount(ClassGrade.BASIC, price);
        int gold = discountService.discount(ClassGrade.GOLD, price);
        int diamond = discountService.discount(ClassGrade.DIAMOND, price);

        System.out.println("BASIC 등급의 할인금액: " + basic);
        System.out.println("GOLD 등급의 할인금액: " + gold);
        System.out.println("DIAMOND 등급의 할인금액: " + diamond);
    }
}
```

### 직접 구현의 한계

- 다른 개발자가 생성자로 인스턴스를 만들어 직접 넣을 수 있다.
- ClassGrade 클래스에서 생성자를 private 생성자로 만들면 이를 막을 수 있다.

```java
public class ClassGradeEx2_2 {
    public static void main(String[] args) {
        int price = 10000;

        DiscountService discountService = new DiscountService();
        ClassGrade newClassGrade = new ClassGrade();
        
        int result = discountService.discount(newClassGrade, price);
        System.out.println("newClassGrade 등급의 할인 금액 = " + result);
    }
}
```

## Enum 생성

- 열거형 정의시 class 대신 enum을 사용하고 원하는 상수를 나열하기만 하면 된다. 내부적으로 ENUM도 클래스이다.
- 자동으로 ENUM 클래스를 상속받게 된다.
- 열거형은 switch문에도 사용이 가능하다.
- static import문을 사용하면 클래스명 생략 가능
- 생성자 사용도 가능하다.

```java
public enum Grade {
    BASIC, GOLD, DIAMOND
}

public class DiscountService {
    public int discount(Grade classGrade, int price) {
        int discountPercent = 0;

        if (classGrade == Grade.BASIC) {
            discountPercent = 10;
        } else if (classGrade == Grade.GOLD) {
            discountPercent = 20;
        } else if (classGrade == Grade.DIAMOND) {
            discountPercent = 30;
        } else {
            System.out.println("할인X");
        }

        return price * discountPercent / 100;
    }
}

import static enumeration.ex3.Grade.*;

public class ClassGradeEx3_1 {
    public static void main(String[] args) {
        int price = 10000;
        DiscountService discountService = new DiscountService();
        int basic = discountService.discount(BASIC, price);
        int gold = discountService.discount(GOLD, price);
        int diamond = discountService.discount(DIAMOND, price);

        System.out.println("BASIC 등급의 할인금액: " + basic);
        System.out.println("GOLD 등급의 할인금액: " + gold);
        System.out.println("DIAMOND 등급의 할인금액: " + diamond);
    }
}


```

## 주요 메서드

- valueOf() : String을 받아 일치하는 ENUM 상수 반환
- name() : 상수 이름 반환
- ordinal() : 순서 반환, 데이터베이스 등에 사용 비추천 (중간에 추가시 모두 뒤로 밀림)

## 열거형 심화

```java
public enum Grade {
    BASIC(10), GOLD(20), DIAMOND(30);

    private final int discountPercent;

    Grade(int discountPercent) {
        this.discountPercent = discountPercent;
    }

    public int getDiscountPercent() {
        return discountPercent;
    }

    // 추가

    public int discount(int price) {
        return price * discountPercent / 100;
    }
}

public class EnumRefMain3_4 {
    public static void main(String[] args) {
        int price = 10000;
        Grade[] grades = Grade.values();
        for (Grade grade : grades) {
            printDiscount(grade, price);
        }
    }

    private static void printDiscount(Grade grade, int price) {
        System.out.println(grade.name() + " 등급의 할인금액: " + grade.discount(price));
    }
}
```