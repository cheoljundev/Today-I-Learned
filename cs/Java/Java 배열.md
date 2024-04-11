## 배열 선언

```java
타입[] 변수명 = new 타입[길이];
```

## 배열의 길이

배열명.length

## 배열의 범위

0 ~ 배열의 길이-1

## 배열 길이 변경 방법

1. 더 큰 길이의 배열로 복사한다(보통 2배)
2. 그 배열을 참조한다.

## 배열 복사

보통 Sysyem.arraycopy() 메서드를 많이 사용.

## String 배열

String 클래스의 인스턴스 생성. 하지만 예외적으로 배열처럼 선언할 수 있다.
char 배열 + 메서드 = String 클래스

메서드로는 substring()등이 있다.

### Char - > String

```java
String[] strArr = new String(charArr);
```

### String -> Char

```java
char[] charArr = strArr.toCharArray();
```

## 다차원 배열

두 번째 차원이 고정.

```java
int[][] num = new int[5][3];
```

## 가변 배열

두 번째 차원이 가변적.

```java
int[][] num = new int[5][];
num[0] = new int[3];
num[1] = new int[3];
num[2] = new int[3];
num[3] = new int[3];
num[4] = new int[3];

int[][] num2 = new int[5][];
num[0] = new int[3];
num[1] = new int[2];
num[2] = new int[4];
num[3] = new int[4];
num[4] = new int[10];
```
