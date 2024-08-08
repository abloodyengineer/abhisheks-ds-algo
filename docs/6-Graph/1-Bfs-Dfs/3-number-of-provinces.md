# Number of Provinces

> Concept - count number of components using a for and vis array 

[Problem link - Leetcode](https://leetcode.com/problems/number-of-provinces/description/){:target="_blank"}


## Intuition

- Create adjacency list. Undirected so need to append both i and j
- Keep looping through all the vertices and putting them in visited array using DFS
- Everytime we find a new vertex which is not in DFS means it is not in a cycle hence it is a new component
- keep counting and return cnt

```py
class Solution:
    def findCircleNum(self, isConnected: List[List[int]]) -> int:
        
        n=len(isConnected)

        adjLst={}

        for i in range(n):
            for j in range(n):
                if isConnected[i][j]==1:
                    if i in adjLst:
                        adjLst[i].append(j)
                    else:
                        adjLst[i]=[j]
                    if j in adjLst:
                        adjLst[j].append(i)
                    else:
                        adjLst[j]=[i]
        vis=[0]*n
        cnt=0
        for i in range(n):
            if vis[i]!=1:
                cnt+=1
                self.dfs(adjLst,vis,i)
        return cnt
    def dfs(self, adjLst, vis,node):
        vis[node] =1
        for it in adjLst[node]:
            if vis[it] !=1:
                self.dfs(adjLst, vis,it)
                
```