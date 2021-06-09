# 53. 이진 탐색 트리(BST) 노드 간 최소 거리

- [문제 링크](https://leetcode.com/problems/minimum-distance-between-bst-nodes/)

<br>

## 내 풀이

- 실행 시간: 40 ms
- 중위 순회를 통한 풀이
  - 중위 순회를 통해 리스트에 담게 되면 오름 차순으로 숫자들이 담기게 되고 인접한 숫자와 비교를 하면 가장 작은 수를 찾을 수 있다.

```python
class Solution:
    def minDiffInBST(self, root: TreeNode) -> int:
        node_list = []
        answer = sys.maxsize
        def inorder(node: TreeNode):
            if not node:
                return
            inorder(node.left)
            node_list.append(node.val)
            inorder(node.right)
        inorder(root)
        for i in range(0, len(node_list) - 1):
            answer = node_list[i + 1] - node_list[i] if node_list[i + 1] - node_list[i] < answer else answer
        return answer
```

<br>

## 풀이 1

- 실행 시간: 48ms
- 마찬가지로 중위 순회를 활용한 풀이법이다.
  - 하지만 나처럼 추가적인 리스트를 선언하지 않고 중위 순회를 하면서 처리했다.
  - 중위 순회가 일어나는 순서를 따라 비교를 해주면된다.
  - 기본적으로 가장 적은 차이가 나려면 현재 자신보다 왼쪽에 있는 노드중 가장 큰 값 혹은 오른쪽에 있는 노드들 중 가장 작은 값과 비교해야하는데 중위 순회는 이 순서대로 비교가 가능하다.

```python
class Solution:
    prev: int = -sys.maxsize
    result: int = sys.maxsize
    def minDiffInBST(self, root: TreeNode) -> int:
        if root.left:
            self.minDiffInBST(root.left)

        self.result = min(self.result, root.val - self.prev)
        self.prev = root.val
        if root.right:
            self.minDiffInBST(root.right)

        return self.result
```

<br>

## 풀이 2

- 실행 시간: 32ms
- stack을 활용한 반복문 방식이다.
  - 특이한 점은 스택을 활용한 중위 순회라는 점이다.
  - 일단 왼쪽으로 쭉 이동을 하고 리프 노드에 도달하면 pop()한 뒤 작업을 처리하고 node를 오른쪽 자식으로 이동시킨다.

```python
class Solution:
    def minDiffInBST(self, root: TreeNode) -> int:
        prev: int = -sys.maxsize
        result: int = sys.maxsize
        stack = []
        node = root

        while stack or node:
            while node:
                stack.append(node)
                node = node.left

            node = stack.pop()
            result = min(result, node.val - prev)
            prev = node.val
            node = node.right
        return result
```
