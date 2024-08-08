# Flood Fill

> Concept - DFS to fill up colour

[Problem link - Leetcode](https://leetcode.com/problems/flood-fill/){:target="_blank"}


## Intuition

- Maintain drow dcol
- store initial colour in sr,sc
- Do a dfs
- Call dfs recursively if the neighbour is having ini colour and is not equal the final colour
- return the grid(image)

```py
class Solution:
    def floodFill(self, image: List[List[int]], sr: int, sc: int, color: int) -> List[List[int]]:
        drow=[-1,0,1,0]
        dcol=[0,-1,0,1]
        m=len(image)
        n=len(image[0])
        ini=image[sr][sc]
        self.dfs(image,sr,sc,color,drow,dcol,m,n,ini)
        return image

    def dfs(self, image,row,col,color,drow,dcol,m,n,ini):
        image[row][col]=color
        for i in range(4):
            nrow=row+drow[i]
            ncol=col+dcol[i]
            if nrow>=0 and nrow<m and ncol>=0 and ncol<n and image[nrow][ncol]==ini and image[nrow][ncol]!=color:
                self.dfs(image,nrow,ncol,color,drow,dcol,m,n,ini)
             
```