# any( )와 all( ) 함수

## any( ) 함수

---

any( ) 함수는 포함된 값 중 어느 하나가 참이라면 항상 참으로 출력한다. OR 연산과 비슷하다.

```python
print(any([True, False, False]))
# True
print(True or False or False)   
# True
```

<br>

## all( ) 함수

---

all( ) 함수는 모든 값이 참이어야 True를 리턴한다. AND 연산과 비슷하다.

```python
print(all([True, False, False]))
# False
print(all([True, True, True]))
# True
print(True and True and True)
# True
```
