# Cycle Detection - Undirected - BFS

> Concept - To detect cycle, pass parent and keep marking visited array. If we encounter that visisted array is already marked for one element, and its not the parent element, we can say it is a cycle. Can use both DFS and BFS

[Problem link - GFG](https://www.geeksforgeeks.org/problems/detect-cycle-in-an-undirected-graph/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=detect-cycle-in-an-undirected-graph){:target="_blank"}


```py
from typing import List
from collections import deque
class Solution:
    #Function to detect cycle in an undirected graph.
	def isCycle(self, V: int, adj: List[List[int]]) -> bool:
		#Code here
        vis=[0 for _ in range(V)]
        for i in range(V):
            if vis[i] ==0:
                if self.solve(i,adj,vis) == True:
                    return True
        return False
    
    def solve(self,node, adj,vis):
        q=deque()
        q.append((node,-1))
        
        while q:
            el,parent = q.popleft()
            vis[el]=1
            for it in adj[el]:
                if vis[it]==1 and it!=parent:
                    return True
                if vis[it]==0:
                    q.append((it,el))
                    vis[it]=1
        return False
             
```