# Is graph bipartite

> Concept - Bipartite can be checked by coloring approach. colour alternate nodes with 2 different colours. if no two nodes have same colour, graph is bipartite, else not.

[Problem link - Leetcode](https://leetcode.com/problems/is-graph-bipartite/description/){:target="_blank"}


## Intuition

- Can be solved using both DFS and BFS
- Keep multiple components in mind
- Using Bfs- assign all neighbouring nodes opposite colour. If at any point any neighbouring node has same colour, we can return False
- in for loop for multiple components, check if false, return false. At the end, return True

```py
from collections import deque
class Solution:
    def isBipartite(self, graph: List[List[int]]) -> bool:
        
        n=len(graph)
        vis=[-1 for _ in range(n)]
        for i in range(n):
            if vis[i]==-1:
                if self.check(i, vis, graph) ==False:
                    return False
        return True
    
    def check(self,start, vis, graph):
        q=deque()
        q.append((start,0))
        vis[start]=0
        while q:
            node,color=q.popleft()
            newColor=int(not color)
            for it in graph[node]:
                if vis[it] == color:
                    return False
                if vis[it] ==-1:
                    vis[it]=newColor
                    q.append((it,newColor))
        return True          
```