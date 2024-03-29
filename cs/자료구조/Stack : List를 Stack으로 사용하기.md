# List를 Stack으로 사용하기

## List를 Stack으로 사용할 수 있다.

- 항상 스택을 구현할 때, 클래스를 직접 구현할 필요는 없다. 파이썬의 리스트 자료형을 이용하면 간편하게 구현이 가능하다.

### List로 Stack 대체 방법

|연산|List에서|예시|
|----|---|---|
|Stack()|List()|s.List()|
|push()|append()|s.append(e)|
|pop()|pop()|s.pop()|
|size()|len()|len(s)|
|isEmpty()|len()|len(s) == 0|
|isFull()|list는 용량이 무한대라서 항상 False|False|
|peek()|첨자 연산자 사용|s[len(s)-1], s[-1]|

### 코드

```python
s = list() # 리스트를 객체를 생성해 스택으로 사용

msg = input("문자열 입력: ")
for c in msg:
    s.append(c) # c를 스택에 삽입

print("문자열 출력 : ", end='')
print()

print("사이즈 : ", len(s))

print("마지막 요소 : ", s[-1])

while len(s) > 0: # 스택이 공백이 아니라면
    print(s.pop(), end='')
print()
print("사이즈 : ", len(s))
```

## 참고 자료

[자료구조와 알고리즘 with 파이썬](https://www.yes24.com/Product/Goods/123451810)