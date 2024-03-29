# queue.LifoQueue 사용하기

## queue모듈의 LifoQueue 클래스로 Stack구현이 가능하다.

- 항상 스택을 구현할 때, 클래스를 직접 구현할 필요는 없다. 파이썬 queue모듈의 LifoQueue클래스를 이용하면 간편하게 구현이 가능하다.
- 클래스명이 Stack이 아닌 LifoQueue인 것에 주의.

### LifoQueue로 Stack 대체 방법

#### queue 모듈 사용하기

queue모듈을 import 하는 작업이 필요하다.

`import queue`

##### 연산 대체
|연산|LifoQueue에서|예시|
|----|---|---|
|Stack()|queue.LifoQueue|s = queue.LifoQueue(maxsize=100)|
|push()|put()|s.put(e)|
|pop()|get()|s.get()|
|size()|qsize()|s.qsize()|
|isEmpty()|empty()|s.empty()|
|isFull()|full()|s.full()|
|peek()|queue[] 사용|s.queue[-1]|

### 코드

```python
import queue # 파이썬 큐 모듈 포함

s = queue.LifoQueue(maxsize=100) # 스택 객체 생성(최대 크기 20), maxsize가 0이면 무한대임.

msg = input("문자열 입력 : ")
for c in msg:
    s.put(c) # c를 스택에 삽입

print("사이즈 : ", s.qsize())

print("마지막 요소 : ",s.queue[-1])

print("문자열 출력 : ", end='')
while not s.empty(): # 스택이 공백 상태가 아니라면
    print(s.get(), end='')
print()
```

## 참고 자료

[자료구조와 알고리즘 with 파이썬](https://www.yes24.com/Product/Goods/123451810)