# Surrounded Regions

> Concept - Start from all boundaries and trace neighbours using DFS.

[Problem link - Leetcode](https://leetcode.com/problems/surrounded-regions/description/){:target="_blank"}


## Intuition

- Check each boundary for "O". If it has not been visited already, start DFS from there
- Logic is, if we find an "O" at the boundary and find all its connected neighbours, we can definitely say those "O"s cannot be converted to "X" as they have a boundary "O"

```py
class Solution:
    def solve(self, board: List[List[str]]) -> None:
        """
        Do not return anything, modify board in-place instead.
        """
        m=len(board)
        n=len(board[0])
        vis=[[0 for _ in range(n)] for _ in range(m)]
        drow=[-1,0,1,0]
        dcol=[0,-1,0,1]
        for i in range(m):
            if board[i][0]=="O" and vis[i][0]!=1:
                self.dfs(board,i,0,vis, drow, dcol, m,n)
            if board[i][n-1]=="O" and vis[i][n-1]!=1:
                self.dfs(board,i,n-1,vis, drow, dcol, m,n)
        for i in range(n):
            if board[0][i]=="O" and vis[0][i]!=1:
                self.dfs(board,0,i,vis, drow, dcol, m,n)
            if board[m-1][i]=="O" and vis[m-1][i]!=1:
                self.dfs(board,m-1,i,vis, drow, dcol, m,n)
        
        for i in range(m):
            for j in range(n):
                if board[i][j]=="O" and vis[i][j]!=1:
                    board[i][j]="X"
        return board
    
    def dfs(self, board, r,c,vis, drow, dcol, m,n):
        vis[r][c]=1
        for i in range(4):
            nrow=r+drow[i]
            ncol=c+dcol[i]

            if nrow>=0 and nrow<m and ncol>=0 and ncol<n and board[nrow][ncol]=="O" and vis[nrow][ncol]!=1:
                self.dfs(board,nrow,ncol,vis, drow, dcol, m,n)             
```