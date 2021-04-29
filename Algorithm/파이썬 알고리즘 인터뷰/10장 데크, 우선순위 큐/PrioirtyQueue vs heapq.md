# PrioirtyQueue vs heapq

## PriorityQueue를 사용하지 않고 heapq를 사용하는 이유?

---

파이썬의 PriorityQueue는 내부적으로 heapq를 사용도록 구현 되어 있다.

```python
class PriorityQueue(Queue):
	...
	def _put(self, item):
		heappush(self.queue, item)

	def _pop(self):
		return heappop(self.queue)
```

<br>

## 그렇다면 두개의 차이점은 무엇인가?

---

PriorityQueue는 스레드 세이프 클래스이고 heapq는 스레드 세이프를 보장하지 않는다.

→ 스레드 세이프를 보장한다는 얘기는 내부적으로 락킹을 제공한다는 의미이므로 라킹 오버헤드가 발생해 성능에 영향을 끼친다.

→ 굳이 멀테스레드로 구현할 것이 아니라면 PrioirtyQueue모듈을 사용할 이유가 없다.

실무에서도 우선순위 큐는 대부분 heapq로 구현하고 있다.

- 스레드 세이프란?
  - 멀티 스레드에도 안전한 프로그래밍 개념. 만약 스레드 세이프 하지 않은 경우 1번 스레드의 값이 2번 스레드에서 변경될 수 있어 문제가 발생한다.
