Java에서 사용하는 사용자 입력을 위해 사용하는 클래스이다.

- nextLine() : 한 줄 입력받음, nextInt()는 개행문자를 포함하지 않으므로, 이전 줄에 개행문자가 없을 경우 그냥 넘어간다.
- nextInt() : 정수 입력받음
- nextDouble() : 실수 입력받음

```java
Scanner scanner = new Scanner(System.in);

System.out.print("문자열을 입력하세요 : ");
String str = scanner.nextLine();
System.out.println("입력한 문자열: " + str);

System.out.print("정수를 입력하세요 : ");
int intValue = scanner.nextInt();
System.out.println("입력한 정수: " + intValue);

System.out.print("실수를 입력하세요 : ");
double doubleValue = scanner.nextDouble();
System.out.println("입력한 실수: " + doubleValue);
```