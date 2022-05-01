# HackerRank_Advanced Select_Binary Tree Nodes

### Problem

Write a query to find the node type of Binary Tree ordered by the value of the node. Output one of the following for each node:

    - Root: If node is root node.
    - Leaf: If node is leaf node.
    - Inner: If node is neither root nor leaf node.

Link(https://www.hackerrank.com/challenges/binary-search-tree-1/problem?isFullScreen=true)

    - 최상위에 위치한 값 - P값이 없으면 Root 반환
    - 최하단에 위치한 값 - N 값이 N과 P 칼럼 둘다 들어있다면 Inner 반환
    - 중간에 낀 값 -  나머지는 Leaf 반환

### Solution


```python
SELECT N, 
    CASE WHEN P IS NULL THEN 'Root'
         WHEN N in (SELECT P FROM BST) THEN 'Inner'
    ELSE 'Leaf'
    END
FROM BST
ORDER BY N 
```

![image.png](attachment:image.png)


```python
### 오답

SELECT N,nodeType
FROM(SELECT CASE WHEN P IS NULL THEN 'Root',
          WHEN N = P THEN 'Leaf', #이런 식은 어디서 나온거.....ㅎ
     ELSE 'Inner'
     END) AS nodeType
FROM BST
ORDER BY N 
```
