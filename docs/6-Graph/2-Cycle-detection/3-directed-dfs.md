# Cycle Detection - directed - DFS

> Concept - To detect cycle in a directed graph, we need to keep track of a pathVisited array instead of parent. Then during DFS, we need to mark both vis and pathVis array. When we encounter a node with both vis and pathVis set to 1, we can conclude that this node has already been visited along the same path, hence cycle. If we do not see any such instance, we need to backtrack, that is mark pathVis for that node to 0.

[Problem link - GFG](https://www.geeksforgeeks.org/problems/detect-cycle-in-a-directed-graph/1){:target="_blank"}


## Notice

```py
if self.dfs(it, adj, vis,pathVis )==True:
    return True
```

This is very important to return from DFS any time we get True. Otherwise DFS will continue and return False

DFS works as we need to backtrack. To do BFS, we need a different approach(Topo sort)
# Code

```py
from typing import List
class Solution:
    #Function to detect cycle in a directed graph.
    def isCyclic(self, V : int , adj : List[List[int]]) -> bool :
        # code here
        vis=[0 for _ in range(V)]
        pathVis=[0 for _ in range(V)]
        for i in range(V):
            if vis[i] ==0:
                if self.dfs(i,adj,vis, pathVis) == True:
                    return True
        return False
    
    def dfs(self,node, adj,vis, pathVis):
        vis[node]=1
        pathVis[node]=1
        for it in adj[node]:
            if vis[it]==1 and pathVis[it]==1:
                return True
            if vis[it]==0:
                if self.dfs(it, adj, vis,pathVis )==True:
                    return True
        pathVis[node]=0
        return False
             
```