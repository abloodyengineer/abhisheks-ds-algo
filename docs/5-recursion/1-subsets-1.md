# Subsets - 1 - Elements are unique and ans cannot contain duplicates

## Intuition

- Start off with empty array
- Recursively solve by either selecting a number or not
- Base condition - ind>n

# Example

Input: nums = [1,2,3]
Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]

```py
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        arr=[]
        ans=[]
        ind=0
        n=len(nums)
        self.solve(nums, arr, ind,n,ans)
        return ans
    
    def solve(self, nums ,arr, ind, n, ans):
        if ind>=n:
            ans.append(arr.copy())
            return
        arr.append(nums[ind])
        self.solve(nums, arr, ind+1, n, ans)
        arr.pop()
        self.solve(nums, arr, ind+1, n, ans)
```