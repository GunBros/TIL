# 52. 이진 탐색 트리(BST) 합의 범위

- [문제 링크](https://leetcode.com/problems/range-sum-of-bst/)

<br>

## 내 풀이

- 실행 시간: 204 ms
- 만약 현재 노드의 값이 high보다 크면 왼쪽 자식들을 탐색하게 된다.
- low보다 작게 되면 오른쪽 자식들만 탐색한다.
- low와 high사이에 존재하면 값을 더하고 왼쪽 오른쪽 자식들 모두를 탐색하게 된다.

```python
class Solution:
    sum_value: int = 0
    def rangeSumBST(self, root: TreeNode, low: int, high: int) -> int:
        if not root
            return
        if root.val > high:
            self.rangeSumBST(root.left, low, high)
        elif root.val < low:
            self.rangeSumBST(root.right, low, high)
        else:
            self.sum_value += root.val
            self.rangeSumBST(root.left, low, high)
            self.rangeSumBST(root.right, low, high)
        return self.sum_value
```

<br>

## 풀이 1

- 실행 시간: 496 ms
- 단순한 부르트 포스 방식, 매우 오래걸린다.

```python
class Solution:
    def rangeSumBST(self, root: TreeNode, low: int, high: int) -> int:
        if not root:
            return 0
        return (root.val if low <= root.val <= high else 0) + self.rangeSumBST(root.left, low, high) + self.rangeSumBST(root.right, low, high)
```

<br>

## 풀이 2

- 실행 시간: 432 ms
- 내 풀이와 비슷하지만 더 깔끔하게 짰다.
  - 클래스 변수도 사용하지 않았고 dfs 내부함수만을 통해 해결

```python
class Solution:
    def rangeSumBST(self, root: TreeNode, low: int, high: int) -> int:
        def dfs(node: TreeNode):
            if not node:
                return 0

            if node.val < low:
                return dfs(node.right)
            elif node.val > high:
                return dfs(node.left)
            else:
                return node.val + dfs(node.left) + dfs(node.right)

        return dfs(root)
```

<br>

## 풀이 3

- 실행 시간: 208ms
- stack을 활용한 반복문 풀이(동일한 방식으로 큐를 사용해 BFS를 해도 똑같다)
  - 처음에는 조건문을 보고 이상하다고 생각했지만 유망한 노드들을 stack에 넣어준다는 것을 알게 되었다.

```python
class Solution:
    def rangeSumBST(self, root: TreeNode, low: int, high: int) -> int:
        stack, sum = [root], 0

        while stack:
            node = stack.pop()
            if node:
                if node.val > low:
                    stack.append(node.left)
                if node.val < high:
                    stack.append(node.right)
                if low <= node.val <= high:
                    sum += node.val
        return sum
```
