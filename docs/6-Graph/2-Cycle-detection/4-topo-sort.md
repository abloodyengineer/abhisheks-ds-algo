# Topo Sort

> Concept - In a topological sort, for every directed edge u -> v,  u must come before v in the ordering.

[Problem link - GFG](https://www.geeksforgeeks.org/problems/detect-cycle-in-a-directed-graph/1){:target="_blank"}


## Intuition

- Take a stack
- Add nodes to stack using DFS, only whiile returning back from the node
- Explanation for above point - Only append to stack after all DFS calls for a particular node is over
- To get the topo sort, pop from the top of stack and push to ans array. ans array is the topo sort
- logic- if we put node to stack after all dfs calls for that node is done, we can make sure that there is no nodes unvisited to the right of the current node. Hence present position is the correct position for the node in the topo sort and `for every directed edge u -> v,  u must come before v in the ordering` - This holds

# Code

```py
class Solution:
    #Function to return list containing vertices in Topological order.
    def topoSort(self, V, adj):
        # Code here
        stack=[]
        vis=[0 for _ in range(V)]
        ans=[]
        for i in range(V):
            if vis[i]==0:
                self.dfs(i,adj, stack, vis)
        while stack:
            ans.append(stack.pop())
        return ans
    
    def dfs(self,node, adj, stack, vis):
        vis[node]=1
        for it in adj[node]:
            if vis[it]!=1:
                self.dfs(it, adj, stack, vis)
        stack.append(node)
```