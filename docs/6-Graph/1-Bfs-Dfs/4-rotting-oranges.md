# Rotting oranges

> Concept - Time taken to do something - BFS using a time counter. Increment time counter while pushing to queue

[Problem link - Leetcode](https://leetcode.com/problems/rotting-oranges/){:target="_blank"}


## Intuition

- Find all rotten oranges and push its index to queue along with time =0
- Maintain drow dcol
- Maintain an ans_time which is the final time
- Keep ading neighbouring good oranges to vis to track what good oranges have been marked bad
- Loop through grid and return -1 if some good orange still left, else retutn ans_time

```py
from collections import deque
class Solution:
    def orangesRotting(self, grid: List[List[int]]) -> int:
        m=len(grid)
        n=len(grid[0])
        q=deque()
        vis=[[None for _ in range(n+1)] for _ in range(m+1)]
        for i in range(m):
            for j in range(n):
                if grid[i][j]==2:
                    q.append((i,j,0))
                    vis[i][j]=2
        drow=[0,-1,0,1]
        dcol=[-1,0,1,0]
        ans_time=0
        while q:
            row,col,time=q.popleft()
            ans_time=max(ans_time,time)
            for i in range(4):
                nrow=row+drow[i]
                ncol=col+dcol[i]
                if nrow>=0 and nrow<m and ncol>=0 and ncol<n and grid[nrow][ncol] ==1 and vis[nrow][ncol]!=2:
                    q.append((nrow,ncol,time+1))
                    
                    vis[nrow][ncol]=2
        for i in range(m):
            for j in range(n):
                if grid[i][j]==1 and vis[i][j]!=2:
                    return -1
        return ans_time    
```