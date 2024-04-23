char 타입을 편하게 사용하기 위해 자바에서 만든 클래스이다.

## equals 비교

- 동일성(identity)과 동등성(equality) 비교 결과가 생성자와 리터럴이 결과가 다르다.
    - 동일성 (==) : 물리적으로 같은지
    - 동등성 (equals()) : 논리적으로 같은지
    - 리터럴로 문자열을 생성하면, 문자열 풀에서 같은 문자열은 하나의 인스턴스를 참조하므로 동일성 비교도 true가 나타난다.

하지만, 반드시 동등성을 사용해야만한다. 어떻게 생성한지 구분이 불가능하다.

## String은 불변객체

때문에 메서드들은 새 String을 반환하는 식으로 작동

## StringBuilder 클래스를 이용하면 가변객체

직접 조작할 일이 많아 새 인스턴스 생성 자체가 자원 낭비인 경우가 많아 StringBuilder로 조작 후 다시 String 변수에 담는 식으로 작업.

### String 컴파일러 최적화

- 하지만 실제로 자바 컴파일러 내부에서는 String + String인 경우 내부적으로 StringBuilder을 사용하기 때문에, 간단한 + 연산인 경우 그냥 String을 해도 무방하다.
- 단, loop 안에서는 크게 의미가 없다. 내부에서 계속 StringBuilder 객체를 생성하기 때문이다.
    - 이럴 때는 직접 StringBuilder 객체를 생성해서 최적화를 해주는 게 좋다.

### StringBuilder vs StringBuffer

StringBuffer는 기능은 같지만 StringBuilder보다 성능이 떨어진다. 단, 멀티스레드 상황에서 사용한다. 멀티스레드 상황에서 StringBuilder는 문제가 생길 수 있다.

### StringBuilder는 메서드체이닝 기능제공

StringBuilder는 가변객체이기 때문에, 메서드에서 메서드체이닝 기법을 제공한다. StringBuilder의 메서드들은 작업을 하고 자기 자신을 반환한다.

```java
StringBuilder sb = new StringBuilder();
StringBuilder sb = new StringBuilder();
String string = sb.append("A").append("B").append("C").append("D")
        .insert(4,"Java")
        .delete(4, 8)
        .reverse()
        .toString();
System.out.println("string = " + string);
```