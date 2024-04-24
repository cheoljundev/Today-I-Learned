- 모든 클래스의 메타 데이터를 확인할 수 있다.
- 클래스의 인스턴스를 생성할 수 있다.
- class는 예약어이기 때문에 관행적으로 사용시 clazz로 변수명, 패키지명으로 사용한다.

## 메타데이터 조회

```java
public class ClassMetaMain {
    public static void main(String[] args) throws Exception{
        // Class 조회
        Class clazz = String.class; // 1. 클래스에서 조회
        // Class clazz1 = new String().getClass(); // 2. 인스턴스에서 조회
        // Class clazz2 = Class.forName("java.lang.String");

        // 모든 필드 출력
        Field[] fields = clazz.getDeclaredFields();
        for (Field field : fields) {
            System.out.println("field = " + field.getType() + " " + field.getName());
        }

        // 모든 메서드 출력
        Method[] methods = clazz.getDeclaredMethods();
        for (Method method : methods) {
            System.out.println("method = " + method);
        }

        // 상위 클래스 정보 출력
        System.out.println("SuperClass: " + clazz.getSuperclass());

        // 인터페이스 정보 출력
        Class[] interfaces = clazz.getInterfaces();
        for (Class i : interfaces) {
            System.out.println("Interface = " + i);
        }
    }
}
```

## 인스턴스 생성

이런 식으로 인스턴스를 생성할 수 있도록 하는 것을 리플렉션이라 한다.

```java
public class ClassCreateMain {
    public static void main(String[] args) throws Exception{
        Class helloClass = Hello.class;
        // Class aClass = Class.forName("lang.clazz.Hello");

        Hello hello = (Hello) helloClass.getDeclaredConstructor().newInstance();
        String result = hello.hello();
        System.out.println("hello = " + hello);
        System.out.println("result = " + result);
    }
}
```