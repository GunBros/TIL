# defaultdict 순회 문제

## 39번 문제에서 `x in graph`가 아니라  `x in list(graph)`를 한 이유는?

---

- 이렇게 하지 않으면 `RuntimeError : dictionary changed size during iteration` 에러가 발생하기 때문이다.
- 이런 오류가 나는 이유는 `graph`가 `collections.defaultdict(list)`라 dfs를 진행하는 과정에서 존재하지 않는 key에 접근하게 되면 빈 list를 할당해서 사이즈가 커지기 때문이다.
- 이런 에러를 막기 위해 `list(graph)`를 통해 복사하여 사용한다.