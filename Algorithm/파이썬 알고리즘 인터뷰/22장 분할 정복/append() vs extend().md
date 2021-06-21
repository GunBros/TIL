# append() vs extend()

- `append()`를 사용하여 리스트에 리스트를 삽입하게 되면 리스트가 엘리먼트 그 자체로 들어가게 된다.

```python
a = [1,2,3]
b = [4, 5]
a.append(b)
print(a)
# a = [1,2,3]

```

- `extend()`를 사용하면 들어가는 리스트를 풀어서 각각의 엘리먼트로 확장을 하게 된다.

```python
a = [1,2,3]
b = [4,5]
a.extend(b)
print(a)
# [1, 2, 3, 4, 5]
```