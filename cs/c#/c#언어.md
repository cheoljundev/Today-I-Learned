## 확장자

*.cs이다

## 프로그램 진입점

Main() 메서드가 진입점이다. 따라서 c#프로그램은 반드시 하나의 Main()메서드가 필요하다.

## 클래스로 감싼다

클래스로 감싸야 한다. 필요하다면 namespace로도 감싼다.

```cs
namespace Hellos
{
    class Hello
    {
        static void Main(string[] args)
        {
            System.Console.WriteLine("Hello, World!");
        }
    }
}
```