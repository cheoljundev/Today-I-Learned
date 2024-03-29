# Stack을 이용한 괄호검사 프로그램

## 괄호 검사 프로그램

- Stack 자료구조를 통하면 여러 가지 프로그램을 만들 수 있다. (웹 브라우저의 뒤로가기 등)
- 이와 같이 Stack을 이용해서 한 줄짜리 코드에서 괄호가 적절히 들어가 있는지 검사하는 프로그램도 만들 수 있다.
- 자료구조 도서에서 예제로 나온 함수이다.

### 괄호 검사 규칙

- 조건 1 : 왼쪽 괄호의 개수와 오른쪽 괄호의 개수가 같아야 합니다.
- 조건 2 : 같은 종류인 경우 왼쪽 괄호가 오른쪽보다 먼저 나와야 합니다.
- 조건 3 : 다른 종류의 괄호 쌍이 서로 교차하면 안 됩니다.

### 어려웠던 점

- 단순히 따라 치기는 하기 싫어서 직접 구현을 시도해보았다.
- 하지만 직접 구현은 실패하였다. 자꾸만 조건문을 추가하는 식으로 생각하다 보니 실패한 것 같다.
- 책에 실린 코드를 보면, Stack식으로 문제를 해결한다.
- 내가 생각한 방법은 중간 중간에 True와 False를 반환하는 방법이지만, 책에 실린 코드에서는 검사에 위반되는 경우 False를 반환하며 하나씩 pop해서 Stack을 비운다. 결국에 Stack이 완전 비었다면 검사에서 통과하는 식이다. 만약 마지막에 통과하지 못한다면, 괄호의 짝이 맞지 않는다는 의미이므로 이 역시 False를 반환한다. 이는 isEmpty 메서드 호출을 반환하는 것으로 대체한다.

### 배운 점

- Stack 자료구조를 이용해서 프로그램을 작성할 때는 Stack식으로 생각해보자.

### 소소하게 배운 점

- `\`를 이용해서 개행하면서 코드 작성이 가능하다.
- `in ()` 을 사용해서 조건문을 간소화 할 수 있다.

### 코드

```python
from Arraystack import ArrayStack

def checkBrakets(statement:str) -> bool:
    """

    괄호를 검사하는 함수

    - 조건 1 : 왼쪽 괄호의 개수와 오른쪽 괄호의 개수가 같아야 합니다.
    - 조건 2 : 같은 종류인 경우 왼쪽 괄호가 오른쪽보다 먼저 나와야 합니다.
    - 조건 3 : 다른 종류의 괄호 쌍이 서로 교차하면 안 됩니다.
    
    Parameters:
    statement (str): 검사할 문장

    Returns:
    bool: 주어진 문장에 오류가 없으면 True, 있으면 False
    
    """
    
    stack = ArrayStack(100)

    for char in statement:
        if char in ('[', '{', '('):
            stack.push(char)
        elif char in (']', '}', ')'):
            if stack.isEmpty():
                return False
            else:
                left = stack.pop()
                if char == ']' and left != '[' or \
                char == '}' and left != '{' or \
                char == ')' and left != '(':
                    return False
    return stack.isEmpty()

print(checkBrakets("{[a + b * (c - d)] / (e + f)}"))
print(checkBrakets("{[a + b * (c - d)] / (e + f}"))
```

## 참고 자료

[자료구조와 알고리즘 with 파이썬](https://www.yes24.com/Product/Goods/123451810)