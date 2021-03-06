# @staticmethod 데코레이터

## @staticmethod

---

해당 표기는 java에서는 어노테이션이라고 부르지만 파이썬에서는 데코레이터라고 부른다.

자바 메소드에서의 static메소드 선언과 비슷하다.

<br>

## 일반 메소드와의 차이점

- 클래스 메소드에 항상 붙는 self가 빠져있고 함수 자체가 별도의 자료형으로 선언 되어 있는 것을 알 수 있다.
- 인스턴스를 생성하지 않고 클래서에서 타입을 출력하면 같은 function으로 나오지만
- 인스턴스를 통해 출력해보면 method와 function으로 다르게 나오는 것을 볼 수 있다.
  - 여전히 독립된 함수의 의미를 갖는다.
  - 이에 따라 인스턴스에 자유롭게 접근하지 못하도록 하고 싶을 때에는 @staticmethod를 붙혀주면 된다.

```python
class CLASS:
    def a(self):
        pass

    @staticmethod
    def b():
        pass

print(type(CLASS.a), type(CLASS.b))
# <class 'function'> <class 'function'>

cls =CLASS()
print(type(cls.a), type(cls.b))
# <class 'method'> <class 'function'>
```
