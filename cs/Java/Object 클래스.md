부모가 없으면 묵시적으로 모든 클래스가 상속받는다. 결국엔 부모가 Object를 묵시적으로 상속받으므로 모든 클래스는 Object를 상속받는다.

## Object 클래스 무조건 상속받는 이유

- 공통된 기능 제공
- 다형성 기본 구현

## toString() 메서드

- toString() 메서드는 객체의 이름 + 객체의 참조값(해시코드)를 String으로 반환한다.
- println 메서드는 사실 객체 자체를 인수로 넣으면 toString()을 호출하게 되어 있다.

```java
public String toString() {
    return getClass().getName() + "@" + Integer.toHexString(hashCode());
}
```

### toString() 오버라이딩

단, 이런 식으로 객체를 나타내는 것은 큰 도움이 되지 못 하므로, 일반적으로는 toString()을 오버라이딩해서 적절히 객체의 정보를 나타내는 메서드로 만든다.

```java
@Override
public String toString() {
    return "dogName=" + dogName + "/" + "age=" + age;
}
```

println 메서드 내부에서 객체만 인수로 넣어 호출할 때 println을 호출하므로 결과가 같다.

```java
public static void main(String[] args) {
    Car car = new Car("Model Y");
    Dog dog1 = new Dog("멍멍이1", 2);
    Dog dog2 = new Dog("멍멍이2", 3);

    System.out.println("1. 단순 toString 호출");
    System.out.println(car.toString());
    System.out.println(dog1.toString());
    System.out.println(dog2.toString());

    System.out.println("2. println 내부에서 toString 호출");
    System.out.println(car);
    System.out.println(dog1);
    System.out.println(dog2);
}
```

#### Object 클래스의 기본 다형성 활용하기 

- Object 클래스의 기본 다형성을 활용한 메서드를 만들어도 같은 결과가 나온다.
- 단, 사실 ObjectPrinter같은 클래스를 만들 필요는 없다. println이 같은 원리로 구현되어 있다.

```java
public class ObjecrPrinter {
    public static void print(Object obj) {
        String string = "객체 정보 출력: " + obj.toString();
        System.out.println(string);
    }
}
```

```java
System.out.println("3. Object 다형성 활용");
ObjecrPrinter.print(car);
ObjecrPrinter.print(dog1);
ObjecrPrinter.print(dog2);
```

#### 참조값을 확인하는 법

오버라이딩 해버린 객체는 참조값을 알기 어려워진다. 이럴 때는 참조값을 반환하는 메서드를 16진수로 변환하는 메서드로 감싸서 호출하면 된다.

```java
String refValue = Integer.toHexString(System.identityHashCode(dog1));
System.out.println("refValue = " + refValue);
```

## equals() 메서드

### 동일성(identity)과 동등성(equality)

- 동일성 (==) : 물리적으로 같은지
- 동등성 (equals()) : 논리적으로 같은지

- 단, String 같은 경우 동등성 비교가 문자열이지만, 동등성은 각 클래스마다 기준이 다르다. Person이라는 클래스에서 이름을 기준으로 논리적으로 같은지, 주민번호를 가지고 논리적으로 같은지 비교한다. 따라서, 동등성 구현은 equals()메서드를 오버라이딩 해야 한다.
- 매우 간단한 구현방법이다. 실제로는 이렇게 구현하지는 않고 엄밀히 구현한다. 실제로 개발자가 외워서 하기는 어려우므로 IDE의 도움을 받는다.

```java
public class UserV2 {
    private String id;

    public UserV2(String id) {
        this.id = id;
    }

    @Override
    public boolean equals(Object obj) {
        UserV2 user = (UserV2) obj;
        return id.equals(user.id);
    }
}
```

```java
public static void main(String[] args) {
    UserV2 user1 = new UserV2("id-100");
    UserV2 user2 = new UserV2("id-100");

    System.out.println("identity = " + (user1 == user2)); // false
    System.out.println("equality = " + (user1.equals(user2))); // true
}
```
