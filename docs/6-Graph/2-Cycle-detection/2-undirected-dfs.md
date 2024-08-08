# Cycle Detection - Undirected - DFS

> Concept - To detect cycle, pass parent and keep marking visited array. If we encounter that visisted array is already marked for one element, and its not the parent element, we can say it is a cycle. Can use both DFS and BFS

[Problem link - GFG](https://www.geeksforgeeks.org/problems/detect-cycle-in-an-undirected-graph/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=detect-cycle-in-an-undirected-graph){:target="_blank"}


## Notice

```py
if self.dfs(it,node, adj, vis )==True:
    return True
```

This is very important to return from DFS any time we get True. Otherwise DFS will continue and return False

# Code

```py
from typing import List
class Solution:
    #Function to detect cycle in an undirected graph
	def isCycle(self, V: int, adj: List[List[int]]) -> bool:
		#Code here
		# DFS
		vis=[0 for _ in range(V)]
        for i in range(V):
            if vis[i] ==0:
                if self.dfs(i,-1,adj,vis) == True:
                    return True
        return False
    
    def dfs(self,node,parent, adj,vis):
        vis[node]=1
        for it in adj[node]:
            if vis[it]==1 and it!=parent:
                return True
            if vis[it]==0:
                
                if self.dfs(it,node, adj, vis )==True:
                    return True
        return False
             
```